# 🧭 Estudos em C

Exercícios de programação em C, do nível **trainee** ao **sênior**.
Cada exercício tem o enunciado, os conceitos usados e o código completo.

> Trilha: Trainee → Júnior → Pleno → Sênior

---

## 🔐 Validador de senha

**Nível:** Trainee

Pede uma senha e repete o pedido até ela cumprir todas as regras:

- de **8 a 15** caracteres
- pelo menos **uma letra maiúscula**
- pelo menos **um número**

Se alguma regra falhar, o programa mostra qual foi.

| Conceito | Onde aparece |
|---|---|
| `while` | repete o pedido até a senha ser válida |
| `for` | percorre a senha caractere por caractere |
| `if / else if / else` | confere as regras e avisa qual falhou |
| `strlen` | mede o tamanho da senha |
| `isupper`, `isdigit`, `islower` | testam cada caractere |

### Código

```c
#include <stdio.h>   // printf e scanf
#include <ctype.h>   // isdigit, isupper e islower
#include <string.h>  // strlen

int main() {
    char senha[16];   // 15 caracteres + o '\0' que marca o fim da string
    int ok = 0;       // vira 1 quando a senha passa em todas as regras

    // Repete até a senha cumprir todas as regras
    while(!ok){
        printf("Digite uma senha: ");
        scanf("%15s", senha);   // lê no máximo 15 caracteres

        // Contadores zerados a cada tentativa
        int temMaior = 0;
        int temMenor = 0;
        int temNumero = 0;

        // Percorre a senha até o fim da string
        for(int i = 0; senha[i] != '\0'; i++){
            if(isdigit(senha[i])) temNumero++;
            if(isupper(senha[i])) temMaior++;
            if(islower(senha[i])) temMenor++;
        }

        int tamanho = strlen(senha);

        // Confere as regras e mostra qual falhou
        if(tamanho < 8){
            printf("Senha curta\n");
        }
        else if(temMaior == 0){
            printf("Falta maiuscula\n");
        }
        else if(temNumero == 0){
            printf("Falta numero\n");
        }
        else{
            printf("Senha forte!!\n");
            ok = 1;   // encerra o while
        }
    }
    return 0;
}
```

### Exemplo de execução

```text
Digite uma senha: dad
Senha curta
Digite uma senha: vini606020.
Falta maiuscula
Digite uma senha: Vini606020.
Senha forte!!
```

### Como rodar

```bash
gcc validador-senha.c -o validador
./validador
```

---

## 📌 Próximos exercícios

- [ ] Tabuada
- [ ] Contador de vogais
- [ ] Maior e menor do vetor
- [ ] Calculadora com funções
- [ ] Cadastro com struct
- [ ] Troca de valores com ponteiros
- [ ] Salvar usuários em arquivo
