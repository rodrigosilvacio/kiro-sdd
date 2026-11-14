# Curso de Spec-Driven Development

Curso gratuito, em português, sobre Spec-Driven Development (SDD) e sete ferramentas que aplicam essa abordagem. O site é estático e roda no GitHub Pages, sem servidor nem banco de dados.

**Site publicado:** https://rodrigosilvacio.github.io/Kiro-sdd/

## Conteúdo

O curso tem 9 módulos e carga horária de 24 h:

| Módulo | Conteúdo |
|---|---|
| 01 Fundamentos | O que é SDD e o projeto de exemplo (Lista de Tarefas) |
| 02 OpenSpec | Tutorial, exercício e quiz |
| 03 GitHub Spec Kit | Tutorial, exercício e quiz |
| 04 BMAD Method | Tutorial, exercício e quiz |
| 05 AWS Kiro | Tutorial, exercício e quiz |
| 06 GSD | Tutorial, exercício e quiz |
| 07 Spec Kitty | Tutorial, exercício e quiz |
| 08 SpecWeave | Tutorial, exercício e quiz |
| 09 Complementares | Produtos relacionados ao Spec Kitty e ao SpecWeave |

Além dos módulos, o site tem:

- **Comparador** (`comparador.html`): compara de 2 a 4 ferramentas em tabela e gráfico radar e recomenda ferramentas a partir do perfil do projeto. As notas do gráfico são avaliação editorial do curso.
- **Certificado** (`certificado.html`): liberado quando todas as lições, exercícios e quizzes estão concluídos. Pode ser impresso, salvo em PDF ou baixado em PNG. É um certificado de participação autodeclarado, sem validade oficial.

Os dados das ferramentas vêm das fontes oficiais consultadas em 14/11/2026. Cada tutorial mostra a fonte e a data de consulta.

## Progresso

O progresso fica no `localStorage` do navegador, na chave `curso-sdd:progresso:v1`. Nada é enviado para servidor. Se o armazenamento estiver indisponível, o site funciona em memória e avisa que o progresso não será salvo. A página inicial tem um botão para reiniciar o progresso.

## Estrutura

```
index.html, 404.html          Página inicial e página de erro
comparador.html               Comparador de ferramentas
certificado.html              Emissão do certificado
modulos/NN-<modulo>/          Páginas de cada módulo
assets/css/                   Tokens, layout, visuais, comparador e impressão
assets/data/                  Dados: ferramentas, catálogo, quizzes, critérios
assets/js/core/               Lógica pura (progresso, quiz, comparador, gráfico, certificado)
assets/js/ui/                 Componentes de interface, carregados por data-componente
assets/svg/                   Ícones das ferramentas
tools/                        Verificadores de conteúdo, links e orçamento
tests/                        Testes de propriedade e de unidade
```

Para alterar o conteúdo de uma ferramenta, edite `assets/data/ferramentas.js` e a página do tutorial correspondente. O verificador de conteúdo acusa divergência entre os dois, por exemplo um número de etapas diferente.

## Rodar localmente

As páginas usam módulos JavaScript, que não carregam por `file://`. Sirva a pasta por HTTP:

```sh
python3 -m http.server 8000
```

e abra http://localhost:8000.

## Testes e verificações

Precisa de Node.js (testado na versão 26). As dependências são só de desenvolvimento.

```sh
npm install
npm test                    # testes de propriedade (fast-check) e de unidade (linkedom)
npm run lint:conteudo       # idioma, acessibilidade, blocos de texto, contraste, Botão Concluir
npm run lint:orcamento      # limite de 50 KB de JS visual e 150 KB no total por página
npm run lint:links          # links internos quebrados e URLs com utm_source
npm run lint:links:externos # também consulta links externos (usa rede)
```

## Publicação

O GitHub Pages publica a branch `main`, na raiz. O arquivo `.nojekyll` desativa o Jekyll. O `404.html` calcula o link de volta para o início a partir do caminho `/kiro-sdd/`; se o repositório mudar de nome, atualize esse trecho.

## Pendência

A URL oficial do GSD (`https://github.com/open-gsd/gsd-core`) foi publicada sem confirmação do mantenedor. O repositório antigo (`gsd-build/get-shit-done`) aparece como fonte adicional.
