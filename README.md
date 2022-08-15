let form = document.getElementById("entrar");
let login = document.getElementById("login");
let senha = document.getElementById("senha");
    form.addEvenListener("click", function(){
        let formData = new FormData();
        formData.append('login', `${login.value}`);
        formData.append('senha',`${senha.value}`);
        fetch("seuSITEaqui/usuario.php",
        {
            body: formData,
            method: "post",
            mode: 'cors',
            cache: 'default'
        }) .then(Response => {Response.json()
           .then(data => {
               if(data.dados.erros){
                   alert("Usuário e/ou senha inválidos");
               }else{
                   alert(data.dados.nome);
               }
           })
        });
    });
