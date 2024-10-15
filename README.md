
## 架构图

![image](https://github.com/user-attachments/assets/987e4351-131f-4a32-b1e8-4866f54fd36d)

## 项目需求

**目标**：明确项目目标和需求，确保项目方向正确。

**项目概述**：
- **行业**：互联网的大数据平台。
- **项目**：加油站服务商数据运营管理平台（油海数据港）。
- **需求**：分析设备维护数据，提升服务质量，优化成本管理。

## 业务流程

**目标**：掌握加油站设备维护的业务流程，为数据流程设计提供依据。

**流程简述**：
 - step1：加油站服务商联系呼叫中心，**申请服务**：安装/巡检/维修/改造加油机
 - step2：呼叫中心联系对应服务站点，**分派工单**：联系站点主管，站点主管分配服务人员
 - step3：服务人员**确认工单**和加油站点信息
 - step4：服务人员在指定日期到达加油站，进行**设备检修**
 - step5：如果为安装或者巡检服务，安装或者巡检成功，则服务完成
 - step6：如果为维修或者改造服务，需要向服务站点**申请物料**，物料到达，实施结束，则**服务完成**
 - step7：服务完成，与加油站站点服务商确认服务结束，完成**订单核验**
 - step8：工程师**报销**过程中产生的费用
 - step9：呼叫中心会定期对该工单中的工程师的服务做**回访**


## 技术选型

**实施细则**：
- **数据源**：Oracle数据库，存储核心业务数据。
- **数据采集**：使用Sqoop进行数据库离线数据采集。
- **数据存储**：Hive on HDFS，作为离线数据仓库解决方案。
- **数据处理**：
  - SparkCore：面向对象和函数处理非结构化数据。
  - SparkSQL：支持SQL和DSL，处理结构化数据，适用于统计分析。
  - ThriftServer：提供SparkSQL服务端接口。
- **数据应用**：
  - MySQL：存储处理结果，供应用层使用。
  - Grafana：进行数据可视化展示。
- **监控与调度**：
  - Prometheus：监控服务器性能。
  - AirFlow：负责任务调度。

## 分层设计

- **ODS**：原始数据层，存储未经处理的原始数据。
- **DWD**：明细数据层，进行数据清洗和扁平化处理。
- **DWB**：基础数据层，实现数据的轻度聚合。
- **ST**：数据应用层，提供报表分析所需的聚合数据。
- **DM**：数据集市层，按部门需求存储数据。
- **DWS**：维度数据层，存储维度信息，如日期、地区等。

## 业务系统结构

**实施要点**：
- **数据来源**：ERP、CISS、呼叫中心系统。
- **业务流程**：涵盖服务申请、工单分派、服务执行、物料申请、订单核验、费用报销和回访。

## 业务主题划分

- 划分为服务、客户、仓储、服务商、运营和市场等多个主题域，每个域下细分具体业务主题。

## 业务维度设计

设计详细的业务维度，支持多角度数据分析。

**实施内容**：
- 包括时间、地区、网点、油站、组织机构等关键维度。

## 事实主题指标划分


**实施方法**：
- 设计包括呼叫中心、油站、工单、安装、维修、回访、费用和物料等关键事实指标。


## ST层设计

设计数据应用层，以支持报表和分析需求。

- **功能**：提供报表数据。
- **数据来源**：聚合DWB层事实数据与DWS层维度数据。


## 贡献指南

我们欢迎任何形式的贡献，包括但不限于提交问题报告、功能请求、代码改进等。

## 版权信息
任何转载或使用，请注明出处。

## 联系我们

如有任何疑问或需要进一步的帮助，请联系我们：

- 邮箱：xianggeng00@gmail.com

---

感谢您的关注和支持，我们期待与您的合作！

