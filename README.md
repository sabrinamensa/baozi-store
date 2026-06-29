# 🥟 Baozi Store - API REST

API REST desenvolvida em Java com Spring Boot para gerenciamento de clientes, produtos e pedidos da Baozi Store.

---

## 🛠️ Tecnologias Utilizadas

- **Java 17**
- **Spring Boot 3.2.5**
- **Spring Data JPA**
- **H2 Database** (em memória, padrão) — troque por MySQL se preferir
- **Maven**

---

## 🚀 Como Executar

### Pré-requisitos
- Java 17+
- Maven 3.8+

### Passos

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/baozi-store.git
cd baozi-store

# 2. Execute com Maven
mvn spring-boot:run
```

A API estará disponível em: `http://localhost:8080`

Console H2 (banco em memória): `http://localhost:8080/h2-console`
- JDBC URL: `jdbc:h2:mem:baozidb`
- User: `sa` | Senha: *(vazia)*

---

## 📦 Estrutura do Projeto

```
baozi-store/
├── src/main/java/com/baozistore/
│   ├── BaoziStoreApplication.java        ← Classe principal
│   ├── model/
│   │   ├── Produto.java                  ← Entidade Produto
│   │   ├── Cliente.java                  ← Entidade Cliente
│   │   └── Pedido.java                   ← Entidade Pedido
│   ├── repository/
│   │   ├── ProdutoRepository.java        ← Repositório JPA Produto
│   │   ├── ClienteRepository.java        ← Repositório JPA Cliente
│   │   └── PedidoRepository.java         ← Repositório JPA Pedido
│   └── controller/
│       ├── ProdutoController.java        ← Endpoints REST Produto
│       ├── ClienteController.java        ← Endpoints REST Cliente
│       └── PedidoController.java         ← Endpoints REST Pedido
└── src/main/resources/
    └── application.properties            ← Configurações
```

---

## 📡 Endpoints da API

### 👤 Clientes — `/api/clientes`

| Método | Endpoint            | Descrição            |
|--------|---------------------|----------------------|
| POST   | /api/clientes       | Criar cliente        |
| GET    | /api/clientes       | Listar todos         |
| GET    | /api/clientes/{id}  | Buscar por ID        |
| PUT    | /api/clientes/{id}  | Atualizar cliente    |
| DELETE | /api/clientes/{id}  | Deletar cliente      |

**Exemplo de corpo (POST):**
```json
{
  "nome": "Maria Silva",
  "clienteDesde": "2025-01-15"
}
```

---

### 🥟 Produtos — `/api/produtos`

| Método | Endpoint            | Descrição            |
|--------|---------------------|----------------------|
| POST   | /api/produtos       | Criar produto        |
| GET    | /api/produtos       | Listar todos         |
| GET    | /api/produtos/{id}  | Buscar por ID        |
| PUT    | /api/produtos/{id}  | Atualizar produto    |
| DELETE | /api/produtos/{id}  | Deletar produto      |

**Exemplo de corpo (POST):**
```json
{
  "nome": "Baozi Tradicional",
  "preco": 5.50,
  "estoque": true
}
```

---

### 📋 Pedidos — `/api/pedidos`

| Método | Endpoint            | Descrição            |
|--------|---------------------|----------------------|
| POST   | /api/pedidos        | Criar pedido         |
| GET    | /api/pedidos        | Listar todos         |
| GET    | /api/pedidos/{id}   | Buscar por ID        |
| PUT    | /api/pedidos/{id}   | Atualizar pedido     |
| DELETE | /api/pedidos/{id}   | Deletar pedido       |

**Exemplo de corpo (POST):**
```json
{
  "clienteId": 1,
  "produtoId": 1,
  "quantidade": 3
}
```

---

## 🗄️ Configuração MySQL (opcional)

No arquivo `application.properties`, comente as configurações H2 e descomente as do MySQL:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/baozidb?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=sua_senha
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
```

---

## 📊 Modelo de Dados

```
CLIENTE             PRODUTO
--------            --------
id (PK)             id (PK)
nome                nome
clienteDesde        preco
                    estoque

          PEDIDO
          --------
          id (PK)
          clienteId (FK → CLIENTE)
          produtoId (FK → PRODUTO)
          quantidade
```

---

*Trabalho acadêmico — Disciplina: Desenvolvimento Web Back-End | UNINTER*
