# Produto Resource

Esta API permite o controle total das produto. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/produto/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se o produto está ou não ativo
categoria | (object) | Categoria do produto
codigo | (string) | Código do produto
comissao | (float) | Define o valor da comissão do produto (0 = não permite)
contador | (integer) | Código automático do produto
descontoMaximo | (integer) | Valor do desconto máximo permitido
descricao | (string) | Descrição do produto
editarProdutosDependentes | (boolean) | Define se é permitido ou não a remoção dos produtos dependentes nas oportunidades
id | (long) | Identificador no sistema
isComissaoPorcentual | (boolean) | Define se o valor do desconto máximo é porcentual ou real
isDescontoPorcentual | (boolean) | Define se o valor do desconto máximo é porcentual ou real
moeda | (string) | Código monetário da moeda (BRL e USD)
possuiEstoque | (boolean) | Define se o produto possui controle de estoque
produtos | (array)(produto) | Produtos dependentes
quantidadeEstoque | (integer) | Define a quantidade do estoque desse produto
recorrencia | (integer) | Recorrência de valor do produto (0 = único, 1 = mensal, 2 = anual)
subcategoria | (object) | SubCategoria do produto
valorBase | (float) | Valor base do produto
valorEditavel | (boolean) | Indica se o valor base do produto é ou não editável
fracionario | (boolean) | Indica se o produto permite quantidade fracionada
itensDeCusto | (array)(ItemFormacaoPreco) | Lista de formações de preço do produto(torna a precificação do produto como composto)
faixasPreco | (array)(FaixaPreco) | Lista de faixas de preço do produto(torna a precificação do produto como faixa de preço)

Exemplo
```js
    [
      {
        "ativo": true,
        "categoria": {
          "ativo": true,
          "id": 7,
          "nome": "Categoria de produto 1"
        },
        "codigo": "2.1",
        "comissao": 0,
        "isComissaoPorcentual": true,
        "contador": 128,
        "descontoMaximo": 15,
        "isDescontoPorcentual": true,
        "id": 1,
        "moeda": "BRL",
        "nome": "Nome do produto",
        "permiteDesconto": true,
        "possuiEstoque": false,
        "recorrencia": 1,
        "subCategoria": {
          "ativo": true,
          "id": 2,
          "nome": "Manutenção"
        },
        "valorBase": 150, //caso precificação simples
        "fracionario": false,
        "produtos": [
            {
                "id": 2,
                "nome" : "Nome do produto dependente",
                "contador": 129,
                "ativo": true,
                "valorBase" : 100,
                "recorrencia": 0,
                "permiteDesconto": true,
                "codigo": "p2",
                "moeda": "BRL",
                "descontoMaximo": 10,
                "comissao": 0,
                "isComissaoPorcentual": true,
                "descontoMaximo": 15,
                "isDescontoPorcentual": true
            }
        ],
        "editarProdutosDependentes": false,
        itensDeCusto:[//somente se precificaçao for composta
            {
                "id":2,
                "nome": "Custo 1"//necessario somente quando o item de custo nao existir(será criado)
                "valor" : 100.00,
                "quantidade" : 3,
                "valorBase" : 100.00,//necessario somente quando o item de custo nao existir(será criado)
                "porcentagem" : false,//necessario somente quando o item de custo nao existir(será criado)
                "multiplicador" : false//necessario somente quando o item de custo nao existir(será criado)
            }
        ]
        faixasPreco:[//somente se precificaçao for por faixas de preço
            {
                "quantidadeInicial" : 1,
                "quantidadeInicial" : 10,
                "valor" : 100.00
            },
            {
                "quantidadeInicial" : 11,
                "quantidadeInicial" : 20,
                "valor" : 90.00
            }
        ]
        
      }
  ]
```
