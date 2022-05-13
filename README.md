# Terraform CI/CD centralizado
Github Actions para ser reutilizado nos projetos de Terraform. Faz a validação da sintaxe do código terraform. 

- terraform init
- terraform fmt
- terraform validate
- terraform apply

## Inputs
| Nome | Descrição | Requirida |Default |
|------|-----------|-----------|--------|
|`tf_version` | Versão do terraform | não | 1.0.0 |
|`os_version` | Versão do sistema operacional | não | ubuntu-20.04 |


## Como utilizar 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

```yaml
name: "Terraform Valida Modulo"
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  terraform:
      uses: "yagoalmeida/cicd_tf_centralizado/.github/workflows/terraform_centralizado.yaml@v1"
      with: 
        tf_version: "1.0.0"
        os_version: "ubuntu-20.04"
      secrets:
        aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```