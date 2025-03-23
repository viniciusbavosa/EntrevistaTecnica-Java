# Perguntas Técnicas - Nível Junior

## Menu

- [Back End](#back-end)
- [Java](#java)
- [Spring Boot](#spring-boot)

---

## Back End

### Explique o que é uma API.

Uma API é um meio de comunicação entre um cliente e um servidor. Em outras palavras, o cliente envia uma requisição e o servidor responde com as informações solicitadas. As APIs podem conectar aplicações na web ou até mesmo serem utilizadas localmente para processar e devolver dados.

### Quais são as principais diferenças entre um serviço e um programa na programação?

Um **programa de computador** tradicional (baseado na ideia de uma Máquina de Turing) recebe um input, retorna um output e é encerrado.  
Já um **serviço** é um tipo especial de programa que **nunca é encerrado** – ele permanece em execução contínua, aguardando requisições (geralmente via rede) para responder a solicitações.  
_Exemplo de programa:_ Calculadora  
_Exemplo de serviço:_ Servidores  
Na prática, essa distinção pode se sobrepor, pois muitos programas modernos podem rodar em segundo plano e aguardar interações do usuário.

### Como você implementaria autenticação em uma API?

Uma abordagem comum é utilizar JWT (JSON Web Token) como token de acesso. No fluxo típico, ao fazer o login, as informações do usuário são enviadas para um endpoint específico da API, onde são processadas, validadas e sanitizadas. Se os dados estiverem corretos, a API retorna um **JWT access token** (geralmente via cookie) para o cliente. Em requisições subsequentes, o servidor verifica se o JWT é válido para permitir o acesso às áreas protegidas da aplicação.  
_Observação:_ Pode ser implementado também o uso de Refresh Token para renovar o acesso.

### Liste os principais métodos HTTP e seus usos.

- **GET**: Solicita dados.
- **POST**: Envia dados para o servidor, podendo receber dados no corpo da resposta.
- **PUT**: Atualiza dados.
- **DELETE**: Remove dados.

### Explique o conceito de **Concorrência** e **Paralelismo**.

- **Concorrência**: É a abordagem em que o sistema simula a execução simultânea de múltiplas tarefas por meio da alternância entre elas, utilizando um "agendador de tarefas". Esse método permite que código assíncrono seja executado sem bloquear a aplicação.
- **Paralelismo**: Refere-se à execução real de múltiplas tarefas ao mesmo tempo, utilizando **multi-threading**, onde diferentes threads executam tarefas simultaneamente.

### O que são estados na programação?

Estado é a capacidade de uma aplicação de "memorizar" ou armazenar dados ao longo do tempo, permitindo que certas informações sejam mantidas e reutilizadas em diversas operações. Ele representa a condição atual de um sistema, variável, objeto ou componente, influenciando seu comportamento nas operações subsequentes.

### O que é JSON?

JSON (JavaScript Object Notation) é um formato de serialização de dados muito utilizado para a troca de informações na web. Ele substituiu o XML por ser mais legível e simples, permitindo transformar objetos e estruturas de dados em texto plano que pode ser facilmente transmitido via HTTP e, posteriormente, desserializado.

### O protocolo HTTP é um protocolo **stateless** ou **statefull**? Cite um exemplo de protocolo **stateless** e **statefull**.

O protocolo HTTP é **stateless**, ou seja, cada requisição é tratada de forma independente sem que o servidor mantenha informações sobre requisições anteriores.  
_Exemplo de protocolo stateless:_ HTTP propriamente dito.  
_Exemplo de protocolo statefull:_ SMTP, que mantém o contexto da sessão durante a transmissão de um e-mail, passando por várias etapas (HELO, MAIL FROM, RCPT TO, DATA, QUIT).

### Você tem experiência em construir APIs RESTful? Explique o conceito da Arquitetura REST.

A arquitetura REST é um conjunto de regras e princípios definidos por Roy Fielding que padronizam a comunicação entre aplicações. Em um sistema RESTful:

- O servidor é **stateless** (não guarda estado entre as requisições);
- A comunicação normalmente ocorre por meio de JSON, embora outros formatos possam ser utilizados;
- Existe uma clara separação entre o cliente (que consome os recursos) e o servidor (que os fornece).  
  Além disso, as APIs RESTful utilizam os métodos HTTP (GET, POST, PUT, DELETE) para manipular recursos de forma previsível e consistente.

### O que é um **load balancer**?

Um load balancer é um tipo de proxy que se conecta a vários servidores e distribui as requisições entre eles, garantindo que nenhum servidor fique sobrecarregado.

### O que é idempotência? E como ela se relaciona a APIs RESTful?

Idempotência é a característica de uma operação onde a execução repetida da mesma ação, com os mesmos parâmetros, gera sempre o mesmo resultado, independentemente de quantas vezes seja realizada.  
Em APIs RESTful, essa propriedade é essencial para garantir que, ao enviar a mesma requisição várias vezes, a resposta permaneça constante – com exceção do método **POST**, que, por sua natureza, não é idempotente. A idempotência pode ser associada ao conceito de funções puras, onde o mesmo input gera sempre o mesmo output.

---

## Java

### Explique como o Java gerencia a memória e quais são as principais diferenças em relação a linguagens como C.

O Java utiliza o **Garbage Collector (GC)** para gerenciar a memória, removendo objetos que não estão mais referenciados, o que libera o programador da necessidade de gerenciar a memória manualmente.  
Em contraste, linguagens como C exigem que o desenvolvedor aloque (com `malloc`, `calloc`, `realloc`) e libere (com `free`) a memória manualmente, aumentando o risco de vazamentos e erros de acesso.

#### Diferenças na gestão de memória:

- **Java:**
  - Variáveis primitivas e referências a objetos são armazenadas na **stack**.
  - Objetos são armazenados no **heap** e liberados automaticamente pelo GC.
- **C:**
  - Variáveis locais e ponteiros são armazenados na **stack**.
  - Dados alocados dinamicamente ficam no **heap** e devem ser liberados manualmente.

### Java é uma linguagem fortemente influenciada pelo paradigma de Programação Orientada a Objetos. Fale um pouco sobre os conceitos de POO.

Java é uma linguagem fortemente influenciada pelo paradigma de Programação Orientada a Objetos (POO), que organiza o software em “objetos” que combinam dados e comportamentos. A seguir, veja alguns dos conceitos fundamentais deste paradigma:

#### 1. Classes e Objetos

- **Classes:** São moldes ou “blueprints” que definem atributos (dados) e métodos (comportamentos) comuns a um conjunto de objetos.
- **Objetos:** São instâncias das classes, representando entidades do mundo real com estados (valores dos atributos) e comportamentos (métodos).

#### 2. Encapsulamento

Oculta os detalhes internos de uma classe, expondo apenas o necessário. Em Java, isso é feito utilizando modificadores de acesso como `private`, `protected` e `public` para proteger os dados e garantir um acesso controlado.

#### 3. Herança

Permite que uma classe “filha” herde atributos e métodos de uma classe “mãe”. Isso promove o reuso de código e facilita a criação de hierarquias, onde classes mais especializadas podem estender os comportamentos de classes mais gerais.

#### 4. Polimorfismo

Refere-se à capacidade de uma mesma operação se comportar de maneira diferente em classes distintas. Em Java, isso é frequentemente implementado através da sobrescrição (override) de métodos, possibilitando que uma chamada de método seja resolvida dinamicamente conforme o objeto que a recebe.

#### 5. Abstração

Consiste em representar os aspectos essenciais de um objeto, ignorando detalhes não relevantes. Em Java, classes abstratas e interfaces são utilizadas para definir contratos que especificam o que um objeto deve fazer, sem se preocupar com a implementação exata.

Esses conceitos colaboram para a criação de sistemas modulares, reutilizáveis e de fácil manutenção, permitindo que os desenvolvedores mapeiem problemas do mundo real para soluções de software de forma mais eficaz.

### Quais são os modificadores de acesso em Java e suas funções?

- **Default (sem modificador):** Acesso permitido apenas dentro do mesmo pacote.
- **Private:** Acesso restrito à própria classe onde foi declarado.
- **Protected:** Acesso permitido dentro do mesmo pacote ou por subclasses em pacotes diferentes.
- **Public:** Acesso liberado para qualquer parte do código.

### O que são interfaces em Java e como elas se diferenciam de classes?

Em Java, uma interface define um conjunto de métodos que uma classe deve implementar, sem fornecer uma implementação concreta (exceto a partir do Java 8, com métodos default).  
Enquanto as classes podem conter atributos e métodos com implementação, as interfaces servem como um contrato que outras classes devem seguir.

### O que o princípio **SOLID** representa?

O SOLID representa cinco princípios fundamentais para o design de software:

- **S**: Responsabilidade Única – Uma classe deve ter uma única responsabilidade.
- **O**: Aberto/Fechado – Módulos devem estar abertos para extensão, mas fechados para modificação.
- **L**: Substituição de Liskov – Subclasses devem ser substituíveis por suas classes base sem alterar o comportamento esperado.
- **I**: Segregação de Interfaces – Uma classe não deve ser forçada a implementar métodos que não utiliza.
- **D**: Inversão de Dependência – Módulos de alto nível não devem depender de módulos de baixo nível; ambos devem depender de abstrações.

### Quais são os tipos de dados primitivos?

Em Java, os tipos primitivos são:

- **byte:** Inteiro de 1 byte (8 bits), com valores de -128 a 127.
- **short:** Inteiro de 2 bytes (16 bits), com valores de -32.768 a 32.767.
- **int:** Inteiro de 4 bytes (32 bits), com valores de -2<sup>31</sup> a 2<sup>31</sup>-1.
- **long:** Inteiro de 8 bytes (64 bits), com valores de -2<sup>63</sup> a 2<sup>63</sup>-1.
- **float:** Número de ponto flutuante de 4 bytes (32 bits) com precisão limitada a 7 dígitos.
- **double:** Número de ponto flutuante de 8 bytes (64 bits) com precisão de 15 a 16 dígitos.
- **boolean:** Representa os valores **true** ou **false**.
- **char:** Representa um único caractere Unicode de 16 bits.

### Me fale um pouco sobre a ordem de execução dos blocos de inicialização e construtores em Java.

A ordem de execução é a seguinte:

1. **Bloco de inicialização estático (Static Block):** Executado uma única vez quando a classe é carregada, antes de qualquer instância ser criada.
2. **Blocos de inicialização de instância:** Executados sempre que uma nova instância é criada, antes do construtor.
3. **Construtor:** Executado após os blocos de inicialização para inicializar o objeto.

### Qual a diferença entre funções Lambda e Closures?

- **Lambda:** Introduzidas no Java 8, são funções anônimas que permitem tratar ações como objetos, simplificando a escrita de código.
- **Closure:** É uma função que "lembra" e mantém acesso ao escopo léxico onde foi declarada, mesmo após esse contexto ter sido encerrado.

### Quais novas funções foram adicionadas no Java 8?

Entre as principais novidades do Java 8 estão:

- **Lambda Expressions:** Permitem a criação de funções anônimas.
- **Method References:** Possibilitam referenciar métodos diretamente pelo nome.
- **Optional:** Uma classe wrapper para expressar a optionalidade de valores.
- **Functional Interfaces:** Interfaces com um único método abstrato, facilitando o uso de lambdas.
- **Default Methods:** Permitem que interfaces tenham métodos com implementação.
- **Nashorn JavaScript Engine:** Motor de execução para código JavaScript em Java.
- **Stream API:** Facilita o processamento funcional de coleções.
- **Date API:** Uma nova API para manipulação de datas, imutável e inspirada no JodaTime.

---

## Spring Boot

### O que é Spring Boot?

Spring Boot é um framework open-source que simplifica o desenvolvimento de aplicações Java baseadas no Spring Framework. Ele reduz a necessidade de configurações manuais e permite a criação de aplicações standalone, incorporando servidores de aplicação (como Tomcat ou Jetty) diretamente no projeto.

### Qual a finalidade do Spring Boot e como ele facilita o desenvolvimento de aplicações Java?

O Spring Boot foi criado para agilizar o desenvolvimento de aplicações Java. Ele oferece:

- **Configuração Automática:** Reduz a complexidade de configurações manuais.
- **Dependências Gerenciadas (Starters):** Facilita a adição de funcionalidades (como banco de dados, segurança, etc.).
- **Aplicações Standalone:** Elimina a necessidade de servidores externos, simplificando o deploy.
- **Produtividade:** Permite iniciar rapidamente projetos e focar na lógica de negócio.

### Como o Spring Boot lida com diferentes perfis de ambiente (development, test, production) e como você os configura?

O Spring Boot permite configurar perfis de ambiente (como development, test e production) por meio de arquivos de propriedades específicos, como `application-dev.properties` e `application-prod.properties`. O perfil ativo é definido através da propriedade `spring.profiles.active`, permitindo que a aplicação carregue automaticamente as configurações corretas para cada ambiente.

### Como você integraria o Spring Security a uma aplicação Spring Boot para gerenciar autenticação e autorização?

A integração do Spring Security é feita adicionando a dependência `spring-boot-starter-security`, que traz configurações e filtros de segurança padrão. A partir daí, pode-se personalizar as regras de autenticação e autorização através de classes de configuração anotadas com `@EnableWebSecurity`, definindo quais endpoints devem ser protegidos e como os usuários serão autenticados (por exemplo, via um `UserDetailsService`).

### Como você gerencia logs em uma aplicação Spring Boot e quais práticas recomendadas utiliza para configurá-los?

O Spring Boot utiliza, por padrão, o Logback para logging, mas também suporta outros frameworks como o Log4j2. Recomenda-se:

- Definir níveis de log apropriados para diferentes pacotes.
- Configurar logs distintos para ambientes de desenvolvimento e produção.
- Integrar com sistemas de gerenciamento centralizado de logs para facilitar monitoramento e análise.

### Qual a abordagem do Spring Boot para trabalhar com persistência de dados, por exemplo, usando Spring Data JPA e Hibernate?

Ao incluir a dependência `spring-boot-starter-data-jpa`, o Spring Boot configura automaticamente o EntityManager, o datasource e outras dependências necessárias. Isso permite que o desenvolvedor defina entidades (com a anotação `@Entity`) e utilize interfaces que estendem `JpaRepository` para realizar operações CRUD sem a necessidade de implementar cada método manualmente.

### De que forma o Spring Boot implementa a injeção de dependências e quais são as principais anotações utilizadas, como `@Autowired`, `@Component`, `@Service` e `@Repository`?

O Spring Boot utiliza o contêiner de Inversão de Controle (IoC) do Spring para implementar a injeção de dependências. Classes anotadas com `@Component`, `@Service`, `@Repository` ou `@Controller` são automaticamente registradas como _beans_. A anotação `@Autowired` permite que o Spring injete essas dependências automaticamente em outras classes, promovendo um baixo acoplamento e facilitando a manutenção e os testes da aplicação.

### O que é o framework Spring? E o Spring Boot?

O **framework Spring** é uma plataforma open-source para desenvolvimento de aplicações corporativas em Java, focada na Inversão de Controle (IoC) e Injeção de Dependências, o que ajuda a criar sistemas modulares e testáveis.  
O **Spring Boot** é uma extensão do Spring que simplifica o processo de configuração e deploy, permitindo a criação de aplicações standalone com configurações mínimas e rápidas.

---

_Para mais detalhes ou contribuições, sinta-se à vontade para abrir issues ou enviar pull requests!_
