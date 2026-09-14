# 📊 Simulador Tributário para Serviços de TI (Reforma Tributária - EC 132/2023)

Aplicação web moderna, responsiva e de alta precisão contábil projetada para planejamento tributário de empresas de **Tecnologia da Informação e Software**, comparando **Simples Nacional (Anexos III e V)**, **Simples Híbrido**, **Lucro Presumido** e **Lucro Real** durante todo o período de transição da Reforma Tributária (**2027 a 2032**).

---

## 🚀 Principais Funcionalidades

### 1. 🟣 Regime do Lucro Real Integrado
- **Demonstrativo do Resultado do Exercício (DRE Fiscal):** Apuração contábil efetiva mês a mês e no trimestre:
  $$\text{Lucro Real (LAIR)} = \text{Receita Bruta} - (\text{Folha} + \text{INSS Patronal} + \text{Compras} + \text{Despesas de Nuvem} + \text{Tributos s/ Faturamento})$$
- **Cálculo Real da Renda:**
  - **IRPJ:** 15% básico + Adicional de 10% sobre o lucro excedente a R$ 20.000,00/mês.
  - **CSLL:** 9% sobre a base apurada.
  - Se a empresa operar com prejuízo fiscal ou margem estreita, o imposto sobre a renda é reduzido proporcionalmente ou zerado.
- **Não-Cumulatividade Plena:** Apropriação integral de créditos de CBS e IBS sobre despesas de servidores em nuvem (AWS, Azure, GCP), SaaS e licenças.

### 2. ⚙️ Alíquotas de CBS e IBS Editáveis
- Como as alíquotas definitivas ainda dependem de regulamentação do Senado Federal:
  - **Alíquota CBS de Referência:** Editável (Padrão: `8,80%`).
  - **Alíquota IBS Plena de Referência:** Editável (Padrão: `17,70%`).
  - **Alíquota ISS Municipal:** Editável (Padrão: `5,00%`).
  - **Indicador do IVA Dual Total:** Atualizado dinamicamente (`CBS + IBS = 26,50%`).
  - **Ajuste Automático da Transição:** O simulador recalcula automaticamente as alíquotas vigentes do ano selecionado.

### 3. ⚖️ Rigor Fiscal na Reforma Tributária (EC 132/2023)
- **Simples Nacional Tradicional sem Distorções:** No Simples comum (Anexo III e V), as compras e despesas **não abatem** créditos do DAS.
- **Simples Híbrido da Reforma:** Simulação da opção legal onde a empresa recolhe CBS/IBS fora do DAS (com créditos integrais) e mantém IRPJ, CSLL e CPP no DAS.
- **Transição Dinâmica (2027 a 2032):**
  - **2027-2028:** CBS plena em vigor; ISS a 100%; IBS teste (0,10%).
  - **2029:** Redução de 10% no ISS; IBS a 10% da referência.
  - **2030:** Redução de 20% no ISS; IBS a 20% da referência.
  - **2031:** Redução de 30% no ISS; IBS a 30% da referência.
  - **2032:** Redução de 40% no ISS; IBS a 40% da referência.
- **RBT12 Integrado:** O histórico de 12 meses alimenta a alíquota efetiva do DAS, com botão de conveniência para **"Projetar RBT12 do Trimestre"**.

### 4. 🎨 Experiência do Usuário (UX/UI Moderna)
- **Máscaras de Moeda Automáticas:** Digitação fluida em formato real `R$ 0,00` em todos os campos numéricos.
- **Navegação em Abas (*Tabs*):**
  1. `🏆 Comparativo Executivo:` Resumo do regime vencedor, economia frente ao 2º colocado, cards dos regimes e tabela consolidada lado a lado.
  2. `📊 Gráficos Interativos (Chart.js):` Custos totais, composição de tributos e carga tributária efetiva (%).
  3. `🟣 Lucro Real:` DRE trimestral e memória de cálculo contábil.
  4. `🔴 Lucro Presumido:` Detalhamento da presunção de 32% e transição de tributos.
  5. `💚 Simples Nacional & Fator R:` Termômetro interativo com sugestão de ajuste de pró-labore e tabela oficial de partilha (Res. CGSN 140/2018).
  6. `🏢 Créditos & B2B:` Demonstração dos créditos tomados e do crédito transferido aos clientes tomadores (vantagem comercial).
- **Persistência Local (LocalStorage):** Não perde os valores digitados ao recarregar a página (`F5`).
- **Exportação para PDF / Impressão:** Folha de estilos `@media print` para impressão executiva em A4.

---

## 📁 Estrutura do Projeto

```text
simulador-tributario/
│
├── index.html      # Aplicação completa e autônoma (HTML5, CSS3, JS ES6+, Chart.js)
└── README.md       # Documentação detalhada do projeto e regras fiscais
```

---

## 💻 Como Executar Localmente

Como a aplicação é **100% autônoma** (não requer Node.js, compilação ou banco de dados), basta abrir o arquivo no seu navegador:

1. Acesse a pasta:
   ```bash
   cd "c:\Users\VMF CONTABILIDADE\Downloads\RASCUNHO\simulador-tributario"
   ```
2. Dê dois cliques no arquivo `index.html` ou execute via linha de comando:
   ```powershell
   Start-Process "index.html"
   ```

---

## 🌐 Como Publicar no GitHub Pages

Para disponibilizar o simulador online gratuitamente para seus clientes e equipe:

1. Crie um repositório no GitHub (ex: `simulador-tributario-ti`).
2. Copie o arquivo `index.html` e `README.md` para o repositório.
3. No GitHub, vá em **Settings** > **Pages**.
4. Em **Branch**, selecione `main` e a pasta `/ (root)`, depois clique em **Save**.
5. O link público estará disponível em instantes:
   `https://<seu-usuario>.github.io/<nome-do-repositorio>/`

---

## 📐 Resumo dos Critérios de Cálculo

| Regime | Tributação sobre Consumo | Tributação sobre a Renda | INSS Patronal |
| :--- | :--- | :--- | :--- |
| **Simples Nacional (Anexo V)** | Embutido no DAS (CBS/ISS/IBS) | Embutido no DAS (IRPJ/CSLL) | Embutido no DAS (CPP) |
| **Simples Nacional (Anexo III)** | Embutido no DAS (se Fator R $\ge$ 28%) | Embutido no DAS | Embutido no DAS (CPP) |
| **Simples Híbrido** | CBS e IBS pagos por fora com créditos integrais | IRPJ e CSLL dentro do DAS | Embutido no DAS |
| **Lucro Presumido** | CBS e IBS com créditos + ISS em transição | IRPJ (15% + 10%) e CSLL (9%) s/ 32% da receita | 20% sobre a folha |
| **Lucro Real** | CBS e IBS com créditos + ISS em transição | IRPJ e CSLL sobre o Lucro Líquido contábil apurado na DRE | 20% sobre a folha |

---

## 📄 Licença e Uso

Desenvolvido para uso contábil, consultoria e planejamento tributário em conformidade com as diretrizes da **Emenda Constitucional nº 132/2023** e **Resolução CGSN nº 140/2018**.
