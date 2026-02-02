# F040_II  十几万知识图谱vue中医药图谱问答(二代)双推荐算法+大数据集+知识图谱+智能问答+vue+flask+neo4j前后端分离B/S架构|爬虫|图谱生成|全套

> 完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从github来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
> 
关注B站，有好处！

编号: 🌿 F040  II
## 视频讲解
https://www.bilibili.com/video/BV15g4y1N7dx/
## 1 前言
技术架构：Vue+flask+neo4j
数据来源：爬取数据
药材数据可以通过爬取中药相关网站
对药材数据系统可以提供页面进行修正
**这个项目主要特点是有28000个节点和10W+条关系**

## 2 实现思路 & 项目特性
这个项目中比较困难的部分是知识图谱的可视化，因为我们使用vue来开发前端，我们使用也是选中了echarts 和 d3.js 两种不同的实现方式：
## 3 功能设计
- 药材数据的爬取：中药的信息从网上进行爬取；
- 方剂数据导入：以excel方式导入到mysql、neo4j数据库中；
- 智能问答，基于模型的药方中医疾病知识问答；
- 两种推荐算法推荐药方；
- 方剂药材的知识图谱可视化；
- 方剂、药材的关键词分析；
### 3.1 逻辑架构图 && 功能模块图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a6f887b9042342ce9f80f9962a48c928.jpeg)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/6c41c95a1ef646f8a6880e1727ff36b7.jpeg)
### 3.2 设计背景
随着中医药现代化建设的推进，传统中药知识的数字化表达与智能化应用面临重大挑战。当前中药领域存在两大核心问题：
1. **数据孤岛现象严重**：方剂、药材、性味归经等关键信息分散在文献典籍与网络资源中，缺乏统一的结构化整合
2. **知识关联分析薄弱**：传统文献检索难以直观呈现方剂与药材间复杂的"君臣佐使"关系网络，制约了中医药知识的传承与创新应用
为解决上述痛点，本项目设计开发了基于知识图谱的中药知识分析系统。通过：
✔️ 构建结构化中药数据库（整合1200+经典方剂与580+中药材数据）
✔️ 建立多维关系图谱（方剂-药材-功效-症候四维关联模型）
✔️ 开发可视化分析工具（支持动态关系探索与数据挖掘）
实现三大核心价值：
🔍 **知识结构化**：将百度文库获取的原始方剂数据与网络爬取的药材数据，经人工校验后构建标准化知识体系
🌐 **关系可视化**：创新采用双引擎图谱渲染（d3.js力导向图+Echarts关系图），直观展示中药配伍网络
项目响应《"十四五"中医药信息化发展规划》提出的"构建中医药知识服务系统"要求，为临床用药分析、方剂配伍研究、中医药教学提供数字化支撑平台，推动中医药知识从静态文献向动态智能服务的转化。
### 3.3 技术选型
语言与框架: Vue、Python3.8、Flask等
数据库: MySQL5.7、Neo4j3.5   (双数据库)、LTP（智能问答）
关键技术: d3js（知识图谱）、echarts（可视化）、pandas等
开发时间： 
## 4功能实现
### 4.1 中医药数据爬取
1. 读取 http://www.zhongyoo.com/name/ 网中药药材信息;
2. 爬取图片;
3. 选择需要存入数据库的列，然后进行数据清洗，重新设置列名称，存入数据库中。
 Flask端与neo4j的交互，并且给前端提供封装好的数据（模糊搜索查询接口、这里两种知识图谱可视化要求的json数据不同，需要分开开发）默认一次显示50个药方，已实现模糊搜索接口，d3js 力导向图方式的可视化
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2fb59dcc3bcc4775b38f85feaee5c246.png)
### 4.2 知识图谱的构造
利用python代码进行知识图谱的构造：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/bfd2b45f904c4572887d3c7cef0984fb.png)
在neo4j自带的浏览器中进行查看：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7799b71e095b4ac38a6d09a7ed2b67d1.png)
### 4.3 neo4j知识图谱的可视化
Neo4j 按照某个属性来搜索,后台对应不同的方法即可
中药数据可视化与知识图谱
采用d3.js实现的知识图谱
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d4077c43dcc64b62bc2a152469d0bc86.png)
实现对知识图图谱的查询，基于dj.js的知识图谱，支持方剂名称、来源典籍、主治症候 三种类型的模糊查询与可视化：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a4a9cd5acce940c792128e64e1028f9f.png)
### 4.4 主页
主页： 轮播图、中药方剂信息卡片展示
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2862775dce4f4829a41869f7f0534134.png)
### 4.5两种推荐算法药方推荐
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/824fd6b74ac84e50b95a7ae8cf819947.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/923001a2e89a46d59253400eabf75210.png)
### 4.6 搜索药方 和 搜索药材
搜索方剂：模糊搜索方剂，展示信息卡片
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8d6964117f834f2fa91e5bdecdc55b64.png)
药材详情：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/72c64d26312c40d29d3df735f1770758.png)
搜索药材：模糊搜索药材，展示信息卡片
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e02f7fe7b5ef4aafa1f65aebcf98d813.png)

### 4.7 智能问答
实现智能问答，对药方、疾病治疗方法的问答：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a849722256804562a1b6f5c79c07a28d.png)
### 4.8 个人设置
设置功能（修改用户信息、头像）
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/25ef5aed897a4561a9d29b5703e9447b.png)
修改密码
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8e72abd586d54805b689e8131a69961d.png)
登录：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/683d89d93a09423f83854feba96267bd.png)
注册：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d4f8101a1fd941feacd2f4a2624c9a66.png)
## 5 文档截图
高达12000字的详细说明文档，从需求设计、概要设计、数据库设计到详细设计、测试结果无所不包：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e278cef86a8d4442898edd253ff4b599.png)
## 6 程序代码
### 6.1 概要介绍
代码说明：**本中药知识图谱系统基于Vue.js 2.0实现，采用响应式数据驱动设计理念。系统核心包含三个数据模型：方剂、药材和属性，构成知识图谱的核心节点。系统使用计算属性动态构建节点间关系：方剂与药材的组成关系，药材与属性的关联关系。图谱可视化方面，动态计算节点位置关系并自适应生成连接线。组件化开发将界面拆分为方剂列表、知识图谱和详细信息三大模块，实现高内聚低耦合。交互功能包括节点点击查看详情、图谱重新布局等功能。UI设计采用自然和谐的绿色色调，符合中医药传统审美，并通过卡片、节点和动效增强视觉层级。系统兼具知识展示与学习功能，帮助用户直观理解中药材之间的复杂关系网络。**
### 6.2 流程图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/bf99285d34814030b8782a8905ee62f3.png)
### 6.3 代码实例
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>中药方剂与药材知识图谱系统</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Microsoft YaHei', sans-serif;
    }
    
    body {
      background: linear-gradient(135deg, #1a4620, #2d5e2d, #1a4620);
      color: #f0f0f0;
      min-height: 100vh;
      padding: 20px;
    }
    
    .container {
      max-width: 1200px;
      margin: 0 auto;
    }
    
    header {
      text-align: center;
      padding: 30px 0;
      margin-bottom: 20px;
      background: rgba(0, 30, 0, 0.7);
      border-radius: 15px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
      border: 1px solid rgba(80, 120, 80, 0.5);
    }
    
    h1 {
      font-size: 2.8rem;
      margin-bottom: 15px;
      color: #d8e9a0;
      text-shadow: 0 0 10px rgba(216, 233, 160, 0.5);
      letter-spacing: 2px;
    }
    
    .subtitle {
      font-size: 1.1rem;
      color: #c8e080;
      max-width: 800px;
      margin: 0 auto;
      line-height: 1.6;
    }
    
    .main-content {
      display: flex;
      flex-wrap: wrap;
      gap: 25px;
      margin-top: 20px;
      justify-content: center;
    }
    
    .panel {
      background: rgba(0, 20, 0, 0.85);
      border-radius: 15px;
      padding: 25px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.6);
      border: 1px solid rgba(80, 140, 80, 0.4);
      transition: transform 0.3s ease;
      flex: 1;
      min-width: 300px;
      max-width: 600px;
    }
    
    .panel:hover {
      transform: translateY(-5px);
    }
    
    .panel-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 25px;
      padding-bottom: 15px;
      border-bottom: 2px solid rgba(100, 180, 100, 0.4);
    }
    
    .panel-title {
      font-size: 1.6rem;
      color: #aff5d0;
      display: flex;
      align-items: center;
    }
    
    .panel-title i {
      margin-right: 12px;
      color: #70d070;
    }
    
    .tcm-card {
      background: rgba(5, 40, 5, 0.9);
      border-radius: 12px;
      padding: 20px;
      margin-bottom: 18px;
      border: 1px solid rgba(80, 160, 80, 0.3);
      transition: all 0.3s ease;
      cursor: pointer;
    }
    
    .tcm-card:hover {
      background: rgba(10, 60, 10, 0.9);
      transform: translateX(5px);
      border-color: rgba(120, 200, 120, 0.5);
    }
    
    .tcm-card h3 {
      color: #c8f0a0;
      margin-bottom: 10px;
      font-size: 1.4rem;
      display: flex;
      align-items: center;
    }
    
    .tcm-card h3 i {
      margin-right: 10px;
      color: #a0e060;
    }
    
    .tcm-info {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
    }
    
    .info-item {
      background: rgba(10, 50, 10, 0.7);
      padding: 8px 15px;
      border-radius: 20px;
      font-size: 0.9rem;
      color: #e0f0b0;
      display: flex;
      align-items: center;
    }
    
    .info-item i {
      margin-right: 6px;
      color: #80d080;
    }
    
    .kg-component {
      height: 450px;
      background: rgba(0, 20, 0, 0.8);
      border-radius: 15px;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      position: relative;
    }
    
    .kg-header {
      padding: 20px;
      background: rgba(0, 40, 0, 0.7);
      border-bottom: 1px solid rgba(80, 140, 80, 0.4);
      display: flex;
      justify-content: space-between;
    }
    
    .kg-body {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      overflow: hidden;
    }
    
    .graph-container {
      position: relative;
      width: 90%;
      height: 90%;
    }
    
    .graph-info {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(0, 20, 0, 0.9);
      padding: 30px;
      border-radius: 15px;
      border: 2px solid rgba(100, 200, 100, 0.4);
      max-width: 480px;
      text-align: center;
      z-index: 10;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.8);
    }
    
    .legend {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-top: 20px;
      flex-wrap: wrap;
    }
    
    .legend-item {
      display: flex;
      align-items: center;
    }
    
    .legend-color {
      width: 20px;
      height: 20px;
      border-radius: 50%;
      margin-right: 8px;
    }
    
    .legend-formula {
      background: #aabb40;
    }
    
    .legend-herb {
      background: #5a9965;
    }
    
    .legend-property {
      background: #4a7799;
    }
    
    .selected-info {
      margin-top: 25px;
      background: rgba(0, 30, 0, 0.7);
      padding: 25px;
      border-radius: 15px;
    }
    
    .info-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
      margin-top: 15px;
    }
    
    @media (max-width: 768px) {
      .main-content {
        flex-direction: column;
      }
      .panel, .kg-component {
        max-width: 100%;
      }
      h1 {
        font-size: 2.2rem;
      }
    }
    
    .relation-line {
      position: absolute;
      height: 3px;
      background: linear-gradient(90deg, transparent, #80ff80, transparent);
      transform-origin: 0 0;
    }
    
    .node {
      position: absolute;
      width: 100px;
      height: 100px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      font-weight: bold;
      padding: 10px;
      cursor: pointer;
      transition: all 0.4s ease;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.4);
      z-index: 2;
    }
    
    .node:hover {
      transform: scale(1.1);
      z-index: 3;
    }
    
    .formula-node {
      background: radial-gradient(circle, #aabb40, #667a2a);
      color: #1a3000;
    }
    
    .herb-node {
      background: radial-gradient(circle, #5a9965, #3a6340);
      color: #d0f0d0;
    }
    
    .property-node {
      background: radial-gradient(circle, #4a7799, #2a4559);
      color: #e0f0ff;
    }
    
    button {
      background: linear-gradient(to right, #3a6340, #2a4a30);
      color: #e0f0e0;
      border: none;
      padding: 12px 25px;
      border-radius: 30px;
      cursor: pointer;
      font-size: 1rem;
      font-weight: bold;
      margin-top: 15px;
      transition: all 0.3s ease;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    }
    
    button:hover {
      background: linear-gradient(to right, #4a7450, #305a38);
      transform: translateY(-3px);
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4);
    }
    
    .highlight {
      animation: pulse 2s ease-in-out infinite;
      box-shadow: 0 0 15px #aaffaa;
    }
    
    @keyframes pulse {
      0% { box-shadow: 0 0 5px #aaffaa; }
      50% { box-shadow: 0 0 20px #aaffaa; }
      100% { box-shadow: 0 0 5px #aaffaa; }
    }
  </style>
</head>
<body>
  <div id="app">
    <div class="container">
      <header>
        <h1><i class="fas fa-leaf"></i> 中药方剂与药材知识图谱</h1>
        <p class="subtitle">探索中药方剂组成、药材属性及其关系。本知识图谱展示了方剂、药材、药用属性三者之间的复杂关系网络。</p>
      </header>
      
      <div class="main-content">
        <div class="panel">
          <div class="panel-header">
            <h2 class="panel-title"><i class="fas fa-prescription-bottle-alt"></i> 方剂列表</h2>
          </div>
          
          <div class="tcm-card" v-for="formula in formulas" :key="formula.id" 
               @click="selectNode(formula)" :class="{'highlight': selectedNode === formula}">
            <h3><i class="fas fa-file-medical"></i> {{ formula.name }}</h3>
            <div class="tcm-info">
              <div class="info-item"><i class="fas fa-list-alt"></i> {{ formula.category }}</div>
              <div class="info-item"><i class="fas fa-user-md"></i> {{ formula.source }}</div>
              <div class="info-item"><i class="fas fa-seedling"></i> {{ formula.ingredients.length }} 味药材</div>
            </div>
          </div>
        </div>
        
        <div class="kg-component">
          <div class="kg-header">
            <h2 class="panel-title"><i class="fas fa-project-diagram"></i> 知识图谱</h2>
            <button @click="randomLayout">重新排列布局</button>
          </div>
          <div class="kg-body">
            <div class="graph-container">
              <div class="relation-line" v-for="(line, index) in relationLines" :key="index" 
                   :style="lineStyle(line)"></div>
              <div class="node" 
                   v-for="node in allNodes" 
                   :key="node.id" 
                   :class="node.type + '-node highlight'"
                   :style="nodeStyle(node)"
                   @click="selectNode(node)">
                {{ node.shortName || node.name }}
              </div>
              <div v-if="!allNodes.length" class="graph-info">
                <h3><i class="fas fa-info-circle"></i> 知识图谱信息</h3>
                <p>图谱中的节点表示中药方剂、药材及其属性，线条表示它们之间的关系。</p>
                
                <div class="legend">
                  <div class="legend-item">
                    <div class="legend-color legend-formula"></div>
                    <div>方剂</div>
                  </div>
                  <div class="legend-item">
                    <div class="legend-color legend-herb"></div>
                    <div>药材</div>
                  </div>
                  <div class="legend-item">
                    <div class="legend-color legend-property"></div>
                    <div>属性</div>
                  </div>
                </div>
                
                <p style="margin-top: 20px;">点击任意节点查看详细信息</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <div v-if="selectedNode" class="selected-info">
        <h2 class="panel-title"><i class="fas fa-info-circle"></i> {{ selectedNode.name }} 详细信息</h2>
        <div class="info-grid">
          <div class="tcm-card">
            <h3><i class="fas fa-tag"></i> 基本信息</h3>
            <p v-if="selectedNode.category"><strong>分类：</strong> {{ selectedNode.category }}</p>
            <p v-if="selectedNode.source"><strong>来源：</strong> {{ selectedNode.source }}</p>
            <p v-if="selectedNode.effect"><strong>功效：</strong> {{ selectedNode.effect }}</p>
            <p v-if="selectedNode.property"><strong>属性：</strong> {{ selectedNode.property }}</p>
          </div>
          
          <div class="tcm-card" v-if="selectedNode.ingredients">
            <h3><i class="fas fa-seedling"></i> 组成药材</h3>
            <div class="info-item" v-for="(ing, idx) in selectedNode.ingredients" :key="idx">
              <i class="fas fa-cannabis"></i> {{ ing.name }} ({{ ing.part }})
            </div>
          </div>
          
          <div class="tcm-card" v-if="selectedNode.composition">
            <h3><i class="fas fa-flask"></i> 主要化学成分</h3>
            <div class="info-item" v-for="(chem, idx) in selectedNode.composition" :key="idx">
              <i class="fas fa-atom"></i> {{ chem }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    new Vue({
      el: '#app',
      data: {
        formulas: [],
        herbs: [],
        properties: [],
        selectedNode: null,
        nodePositions: {}
      },
      computed: {
        allNodes() {
          return [...this.formulas, ...this.herbs, ...this.properties];
        },
        relationLines() {
          const lines = [];
          
          // 添加方剂 -> 药材的关系
          this.formulas.forEach(formula => {
            formula.ingredients.forEach(ing => {
              const herb = this.herbs.find(h => h.id === ing.id);
              if (herb) {
                lines.push({
                  from: formula,
                  to: herb
                });
              }
            });
          });
          
          // 添加药材 -> 属性的关系
          this.herbs.forEach(herb => {
            if (this.properties.length) {
              const relatedProp = this.properties[Math.floor(Math.random() * this.properties.length)];
              lines.push({
                from: herb,
                to: relatedProp
              });
            }
          });
          
          return lines;
        }
      },
      mounted() {
        this.fetchData();
      },
      methods: {
        fetchData() {
          // 模拟数据获取
          this.formulas = [
            {
              id: 'f1',
              name: '桂枝汤',
              shortName: '桂枝汤',
              type: 'formula',
              category: '解表剂',
              source: '《伤寒论》',
              effect: '解肌发表，调和营卫',
              ingredients: [
                {id: 'h1', name: '桂枝', part: '嫩枝'},
                {id: 'h2', name: '芍药', part: '根'},
                {id: 'h3', name: '甘草', part: '根及根茎'},
                {id: 'h4', name: '生姜', part: '根茎'},
                {id: 'h5', name: '大枣', part: '果实'}
              ]
            },
            {
              id: 'f2',
              name: '四物汤',
              shortName: '四物汤',
              type: 'formula',
              category: '补血剂',
              source: '《太平惠民和剂局方》',
              effect: '补血调血',
              ingredients: [
                {id: 'h6', name: '当归', part: '根'},
                {id: 'h7', name: '川芎', part: '根茎'},
                {id: 'h8', name: '白芍', part: '根'},
                {id: 'h9', name: '熟地黄', part: '块根'}
              ]
            }
          ];
          
          this.herbs = [
            {id: 'h1', name: '桂枝', shortName: '桂枝', type: 'herb', property: '辛、甘，温', effect: '发汗解肌，温通经脉'},
            {id: 'h2', name: '芍药', shortName: '芍药', type: 'herb', property: '苦、酸，微寒', effect: '养血调经，敛阴止汗'},
            {id: 'h3', name: '甘草', shortName: '甘草', type: 'herb', property: '甘，平', effect: '补脾益气，清热解毒'},
            {id: 'h4', name: '生姜', shortName: '生姜', type: 'herb', property: '辛，微温', effect: '解表散寒，温中止呕'},
            {id: 'h5', name: '大枣', shortName: '大枣', type: 'herb', property: '甘，温', effect: '补中益气，养血安神'},
            {id: 'h6', name: '当归', shortName: '当归', type: 'herb', property: '甘、辛，温', effect: '补血活血，调经止痛'},
            {id: 'h7', name: '川芎', shortName: '川芎', type: 'herb', property: '辛，温', effect: '活血行气，祛风止痛'},
            {id: 'h8', name: '白芍', shortName: '白芍', type: 'herb', property: '苦、酸，微寒', effect: '养血调经，平肝止痛'},
            {id: 'h9', name: '熟地黄', shortName: '熟地', type: 'herb', property: '甘，微温', effect: '补血养阴，填精益髓'}
          ];
          
          this.properties = [
            {id: 'p1', name: '辛温解表', shortName: '辛温解表', type: 'property', composition: ['挥发性油', '生物碱']},
            {id: 'p2', name: '养血活血', shortName: '养血活血', type: 'property', composition: ['多糖类', '皂苷类']},
            {id: 'p3', name: '补气健脾', shortName: '补气健脾', type: 'property', composition: ['多糖类', '氨基酸']}
          ];
          
          // 初始化节点位置
          this.randomLayout();
        },
        randomLayout() {
          // 随机生成节点位置
          const positions = {};
          const containerWidth = 800;
          const containerHeight = 300;
          
          // 方剂节点在左侧
          this.formulas.forEach((formula, i) => {
            positions[formula.id] = {
              x: 100,
              y: 100 + i * 100
            };
          });
          
          // 药材节点在中间
          this.herbs.forEach((herb, i) => {
            positions[herb.id] = {
              x: 300 + i%3 * 150,
              y: 100 + Math.floor(i/3) * 150
            };
          });
          
          // 属性节点在右侧
          this.properties.forEach((prop, i) => {
            positions[prop.id] = {
              x: 700,
              y: 150 + i * 100
            };
          });
          
          this.nodePositions = positions;
        },
        nodeStyle(node) {
          const pos = this.nodePositions[node.id] || {x: 0, y: 0};
          return {
            left: `${pos.x}px`,
            top: `${pos.y}px`,
            width: node.shortName ? '100px' : '110px',
            height: node.shortName ? '100px' : '110px',
          };
        },
        lineStyle(line) {
          const from = this.nodePositions[line.from.id] || {x: 0, y: 0};
          const to = this.nodePositions[line.to.id] || {x: 0, y: 0};
          
          const dx = to.x - from.x;
          const dy = to.y - from.y;
          const length = Math.sqrt(dx * dx + dy * dy);
          const angle = Math.atan2(dy, dx) * 180 / Math.PI;
          
          return {
            left: `${from.x + 50}px`,
            top: `${from.y + 50}px`,
            width: `${length}px`,
            transform: `rotate(${angle}deg)`
          };
        },
        selectNode(node) {
          this.selectedNode = node;
        }
      }
    });
  </script>
</body>
</html>
```
