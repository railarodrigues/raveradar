# ◈ RaveRadar

**Encontre sua próxima frequência.** Um planner de raves que transforma a organização do rolê em uma experiência simples e visual.

Projeto de portfólio de [Raila Rodrigues](https://github.com/railarodrigues), desenvolvido com assistência de IA. Une um tema pessoal a funcionalidades de frontend: filtros, estado, persistência, validação e cálculos.

## O que você pode fazer

- Explorar três eventos **fictícios**, filtrando por estilo musical, nome ou cidade.
- Favoritar eventos e selecionar um deles para o plano.
- Calcular orçamento por pessoa e total do grupo.
- Marcar oito itens de preparação no checklist.
- Reabrir a página com favoritos, orçamento e checklist preservados no navegador.
- Exportar o plano como JSON.

**Não é uma agenda real nem uma plataforma de venda de ingressos.** Eventos, preços e datas são demonstrativos. Os dados ficam somente no navegador, sem conta, backend ou sincronização entre dispositivos. Limpar os dados do navegador apaga o plano. O arquivo exportado é uma cópia para consulta; esta versão não importa planos.

## Ver sem instalar nada

Abra `ABRIR-RAVE-RADAR.html` no navegador. É uma versão autossuficiente para experimentar a interface. Alguns navegadores limitam o salvamento em arquivos locais; para persistência consistente e desenvolvimento, use o servidor abaixo. Essa cópia foi gerada a partir do código modular e precisa ser regenerada após alterações.

## Rodar em dois passos

Instale Node.js 20 ou superior, abra um terminal na pasta do projeto e execute:

```bash
npm start
```

Depois abra **http://localhost:3000**. Não precisa de `npm install`: este projeto usa apenas os recursos nativos do Node.js e do navegador. Abrir o HTML diretamente por `file://` pode bloquear os módulos JavaScript; use o servidor.

```bash
npm test
```

Os testes verificam cálculo, valores inválidos, busca com acentos e recuperação de dados corrompidos.

## Como o orçamento funciona

Ingresso e alimentação são individuais. Transporte e extras são despesas compartilhadas.

```text
Por pessoa = ingresso + alimentação + (transporte + extras) / pessoas
Total = (ingresso + alimentação) × pessoas + transporte + extras
```

Exemplo: ingresso R$ 180, alimentação R$ 70, transporte R$ 160 e extras R$ 40 para duas pessoas → **R$ 350 por pessoa e R$ 700 no grupo**. O resultado é uma estimativa; os valores exibidos são arredondados a centavos.

## Tecnologias e organização

HTML semântico, CSS responsivo, JavaScript com módulos ES e `localStorage`. Servidor e testes com Node.js, sem dependências de produção.

| Arquivo | Responsabilidade |
| --- | --- |
| `index.html` | Estrutura e controles acessíveis |
| `style.css` | Identidade visual, breakpoints e preferência por movimento reduzido |
| `src/core.js` | Eventos, filtros, cálculo e validação do estado |
| `src/app.js` | Interface, interações, persistência e exportação |
| `server.js` | Servidor local para desenvolvimento |
| `tests/core.test.js` | Testes da lógica de negócio |
| `docs/GUIA.md` | Guia para entender e apresentar o projeto |

O servidor é para uso local de desenvolvimento. O frontend pode ser hospedado como arquivos estáticos; não depende dele em produção.

## Próximas evoluções possíveis

Importação de planos, eventos inseridos pelo usuário e integração com uma agenda real podem ser incrementos futuros. Esta versão não promete essas funções.
