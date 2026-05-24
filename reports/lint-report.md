# Wiki 知识库 Lint 报告

> 检查日期：2026-05-09
> 检查范围：wiki/ 下全部 7 个页面

---

## 第一轮检查

### A. 信息矛盾

#### A1. product-catalog.md 钻石珑系列标题型号前缀与示例不符

- **位置**：`wiki/product-catalog.md:135`
- **问题**：标题写 "(JT7xx，玻璃基材)"，但所有示例型号（JT6201、JT6301、JT6101、JT6501 等）均为 JT6xxx 前缀，与编码规则表（JT6xx=钻石/高纯）也不一致。
- **严重程度**：高 — 可能导致读者对型号前缀产生错误认知。
- **修复**：`(JT7xx，玻璃基材)` → `(JT6xx，玻璃基材)`

#### A2. company-overview.md 编码规则表缺失 JT4xx

- **位置**：`wiki/company-overview.md:78-86`
- **问题**：型号命名规则列举了 JT1xx→JT3xx，然后直接跳到 JT5xx，缺少 JT4xx（着色系列）。而 product-catalog.md 和 faq.md 均有 JT4xx。
- **严重程度**：中 — 新员工参考此表会遗漏着色系列的存在。
- **修复**：在 JT3xx 与 JT5xx 之间插入 `JT4xx — 着色系列（溶剂型二次上色，上百个品种）`

#### A3. faq.md 编码规则表 JT6xx/JT7xx 条目不清晰

- **位置**：`wiki/faq.md:42`
- **问题**：原条目 `JT6xx/JT7xx | 钻石珑/高纯` 将两个不同前缀混在一起，没有清晰区分各前缀对应的系列名称。与 product-catalog.md 编码规则表（JT6xx=钻石/高纯，JT7xx=钻石珑分别列出）不一致。
- **严重程度**：中 — 编码规则在不同页面表述不一致，容易混淆。
- **修复**：拆分为两行（JT6xx、JT7xx 各一行），分别标注系列名称和基材。

#### A4. product-parameters.md 化妆品推荐与 pricing-guide.md 不一致

- **位置**：`wiki/product-parameters.md:130-136` vs `wiki/pricing-guide.md:24`
- **问题**：product-parameters.md 化妆品章节仅推荐"银白系列（JT110、JT110M）+ 幻彩系列"，而 pricing-guide.md 推荐"银白（细粒径）+ 高纯"（首选）、"水晶系列"（备选），多出了高纯和水晶两个推荐系列。
- **严重程度**：低 — 两处从不同角度选型，但不一致会让读者困惑哪个更权威。
- **修复**：在 product-parameters.md 化妆品章节补充高纯系列和水晶系列作为推荐选项。

---

### B. 孤立页面检查

| 页面 | 被链入情况 |
|------|-----------|
| home.md | company-overview, product-catalog, product-parameters, industry-knowledge, pricing-guide, faq（共 6 处） |
| company-overview.md | home, product-catalog, product-parameters, industry-knowledge, pricing-guide, faq（共 6 处） |
| product-catalog.md | home, company-overview, product-parameters, industry-knowledge, pricing-guide, faq（共 6 处） |
| product-parameters.md | home, company-overview, product-catalog, industry-knowledge, pricing-guide, faq（共 6 处） |
| industry-knowledge.md | home, company-overview, product-catalog, product-parameters, pricing-guide, faq（共 6 处） |
| pricing-guide.md | home, company-overview, product-catalog, product-parameters, industry-knowledge, faq（共 6 处） |
| faq.md | home, company-overview, product-catalog, product-parameters, industry-knowledge, pricing-guide（共 6 处） |

**结论：无孤立页面。** 所有页面在"相关链接"中均相互引用，形成闭环。

---

### C. 结构与完整性检查

#### C1. 产品系列数量统计差异

- **位置**：`wiki/home.md:39-41`、`wiki/product-catalog.md:7`
- **问题**：product-catalog.md 介绍"11 大核心系列"，但其中第 7 节（合成云母系列）与第 11 节（水晶系列）实际指向同组产品（第 11 节标注"见第 7 节"），严格计数为 10 个独立系列。home.md 速览列出了 10 个系列名称（未单独列出水晶系列），反而是准确的。建议在 product-catalog.md 中明确水晶系列为合成云母的子分支而非独立第 11 系列，或保持 11 个计数但说明从属关系。
- **严重程度**：低 — 不影响理解，但"11 大"的计数不够精确。
- **修复建议**：建议在后续更新中调整 product-catalog.md 的系列计数为 10 或明确水晶系列的从属定位。

#### C2. 文件结构完整性

CLAUDE.md 推荐的 7 个骨架页面全部存在：
- [x] `wiki/home.md`
- [x] `wiki/company-overview.md`
- [x] `wiki/product-catalog.md`
- [x] `wiki/product-parameters.md`
- [x] `wiki/industry-knowledge.md`
- [x] `wiki/pricing-guide.md`
- [x] `wiki/faq.md`

**结论：结构完整，无缺失页面。**

---

## 第一轮修复汇总

| # | 文件 | 修复内容 |
|---|------|---------|
| A1 | `wiki/product-catalog.md:135` | 钻石珑标题 `(JT7xx)` → `(JT6xx)` |
| A2 | `wiki/company-overview.md:81` | 补充缺失的 JT4xx 着色系列条目 |
| A3 | `wiki/faq.md:42-43` | 拆分 JT6xx/JT7xx 为两行，与编码规则表一致 |
| A4 | `wiki/product-parameters.md:133-136` | 化妆品章节补充高纯系列与水晶系列推荐 |

---

## 第二轮检查

### 修复验证

| # | 修复内容 | 验证结果 |
|---|---------|---------|
| A1 | 钻石珑标题 `(JT7xx)` → `(JT6xx)` | ✅ 已修正，与示例型号一致 |
| A2 | 补充 JT4xx 着色系列 | ✅ 已插入 JT3xx 与 JT5xx 之间 |
| A3 | 拆分 JT6xx/JT7xx 条目 | ✅ 拆分为两行，明确各自对应关系 |
| A4 | 化妆品章节补充推荐 | ✅ 已增加高纯系列、水晶系列项 |

### 二次检查发现的补充问题

#### A5. company-overview.md 编码规则表 JT6xx/JT8xx 描述需调整

- **位置**：`wiki/company-overview.md:83-85`
- **问题**：原表述 `JT6xx/JT8xx — 高纯系列` 未体现 JT6xx 也用于钻石珑产品，与 product-catalog.md 编码表（JT6xx=钻石/高纯）不一致。
- **严重程度**：中
- **修复**：拆分为三行，明确 JT6xx=钻石珑/高纯（玻璃基）、JT7xx=钻石珑（玻璃基）、JT8xx=水晶/高纯（合成云母基）
- **验证**：✅ 已修正

### 二次检查最终状态

| 检查项 | 状态 |
|--------|------|
| 信息矛盾 | ✅ 5 处全部修复 |
| 孤立页面 | ✅ 0 处（无需处理） |
| 结构缺失 | ✅ 无缺失页面（C1 为低优先级建议） |
| 编码规则跨页一致性 | ✅ 3 个页面（product-catalog / company-overview / faq）现已一致 |
| 化妆品推荐跨页一致性 | ✅ product-parameters 与 pricing-guide 推荐系列已对齐 |

---

## 后续建议

1. **系列计数统一**：考虑将 product-catalog.md 的"11 大核心系列"调整为"10 大核心系列"，或将水晶系列明确标注为合成云母的子分支。
2. **钻石珑/JT6xx/JT7xx 命名梳理**：当前编码规则中 JT6xx 既属于钻石珑又属于高纯，JT7xx 在编码表中标注为钻石珑但实际示例较少，建议内部确认后统一表述。
3. **定期检查**：如新增产品系列，建议同步更新所有页面的编码规则表和产品系列速览。
