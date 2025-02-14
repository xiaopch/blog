## OpenAI 的 Swarm多智能体框架

![](image.webp)

OpenAI最近开源了一个名为Swarm的多智能体框架，这是一个实验性质的工具，旨在简化多智能体系统的构建、编排和部署工作。以下是Swarm框架的一些关键特性和信息：

### Swarm框架概述

Swarm被设计为一个轻量级、易于使用且高度可定制的多智能体编排框架。它通过智能体（Agent）和交接（Handoff）的概念来简化多智能体系统的工作流程。每个Agent包含一组指令和工具，并能够在任何时刻将对话交接给另一个Agent。

### 主要特性

- **多智能体协调**：Swarm支持多个智能体协同工作，处理复杂的任务和对话。
- **任务和对话的移交（Handoff）**：智能体在需要时可以将任务或对话移交给另一个智能体，以适应不同的场景和需求。
- **轻量级和高度可定制**：Swarm设计轻量，易于扩展和定制，适应不同的应用场景。
- **易于测试**：提供易于测试的环境，开发者能快速迭代和优化智能体的行为。
- **完全透明和细粒度控制**：开发者完全控制智能体的上下文、步骤和工具调用，提供对智能体行为的深入洞察。

### 安装与使用

安装Swarm框架非常简单，只需一条命令：

```bash
pip install git+ssh://git@github.com/openai/swarm.git
```

通过简单的Python脚本来定义智能体并指定它们的行为：

```python
from swarm import Swarm, Agent
client = Swarm()
def transfer_to_agent_b():
    return agent_b
agent_a = Agent(
    name="Agent A",
    instructions="You are a helpful agent.",
    functions=[transfer_to_agent_b],
)
agent_b = Agent(
    name="Agent B",
    instructions="Only speak in Haikus."
)
response = client.run(
    agent=agent_a,
    messages=[{"role": "user", "content": "I want to talk to agent B."}],
)
print(response.messages[-1]["content"])
```

输出消息将展示Agent B的回应，以Haiku的形式。

### 许可

Swarm是开源的，根据MIT许可证授权，这意味着开发者可以自由地使用、修改和分发这个框架。

Swarm的开源标志着OpenAI在多智能体研究领域的一个重要进展，为开发者提供了一个强大的工具来构建和管理复杂的多智能体系统。