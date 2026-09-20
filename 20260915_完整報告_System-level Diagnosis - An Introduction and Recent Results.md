---
title: System-level Diagnosis - An Introduction and Recent Results

---

# System-level Diagnosis - An Introduction and Recent Results
*20260915 School of Computing Montclair State University 王大進教授*
## 演講簡介
  本次書報討論由王大進教授主講。開頭，王教授介紹其學校，在一個山坡上，並介紹環境優美，以及介紹學校的人數等簡介。
  
  之後介紹了，由於現今越來越多高速、大規模的多核心系統正在被使用，他們之間需要利用各種拓樸結構的互聯網路來連接各節點，但是隨著系統規模遽增，加上網路攻擊活動猖獗，以及硬體節點故障則是一個不可避免的難題，為了這個難題，王教授設計了一個演算法，來解決此難題。
  
此演算法名稱為 "System-level Diagnosis" ，此演算法利用各點之間互相的檢查，檢查出是否有壞掉的節點，當檢查到壞掉的點則回傳 "1" ，當該節點為正常時則回傳 "0" ，但是如果測試別的節點的那個節點，被測出來是壞掉的話，則其測試的結果是不可靠的。如下圖所示，此圖檢測了4次，每次 $d$ 測試 $c$，以及 $b$ 測試 $c$，都回傳 "1" ，表示c是故障的點，因此c測試的點都不能採信，利用此方法測出哪個點是故障的。

但是以上方法在故障點不多時才能奏效，因此，存在一個關鍵數值t，當故障的節點大於t，則此互相測試的技術失效，$t$ 這個數值就被稱為此系統的 "Diagnosability" 。

如果對故障點的分布做出合理的假設，那麼有很大的機會大幅提升系統診斷度，此方式稱為 "Conditional Diagnosability"。

## 相關技術說明

### 系統背景與可靠度挑戰

1. 大規模互連網路：系統透過如 Hypercube（超立方體）、Star Graph、$k$-ary $n$ -cube 以及 Bubble-sort Graph 等拓樸結構將大量處理器節點連接。
2. 2.可靠度衰減模型：若假設單一處理器的可靠度為 $99.99\%$，當無備援處理器數量擴增至 10,000 個時，系統整體可靠度將暴跌至 $36.79\%$。因此， fault tolerance（容錯）與自動診斷機制不可或缺。

### 網路節點的診斷

 1. 相互測試與限制：節點 $i$ 可對鄰居節點 $j$ 進行測試，判定其為「正常（0）」或「故障（1）」。但若測試者本身即為故障節點，其產生的測試結果將隨機且無效。

### 診斷度（Diagnosability）

1. $t$ -Diagnosability（傳統診斷度）：指系統能容忍並正確診斷的最大壞點數  $t$ ，充分條件：網路 $G=(V, E)$ 需滿足總節點數 $|V| >= 2t + 1$ 且最小度數 $\kappa(G) >= t$。
2. Conditional Diagnosability（條件診斷度）：傳統診斷度假設壞點可任意分佈。若引入一項合理的實際假設——「任何單一節點的所有鄰居不可能同時全部故障」（因機率極低可予排除），即可大幅提升系統的容錯與診斷能力。

## 心得報告
本次聽完王大進教授的演講，讓我對大規模平行與分散式系統底層的「可靠度設計」有了更深刻的認識。過去上課時，沒想過當節點數量達到數千甚至數萬個時，硬體故障率與隨之而來的系統崩潰風險會變大。

教授從最基礎的處理器可靠度數學公式切入，利用簡單的方法講述著，一步一步引導出「系統級診斷」，讓我明白分散式系統不只能依賴外部監控，更可以透過節點之間的「互相測試」來達到自我診斷的效果。特別是「條件診斷度（Conditional Diagnosability）」的概念讓我印象深刻——透過加入合理的假設，便能突破傳統理論的極限，將系統的診斷能力提升好幾倍。這對我未來在從事相關技術時，提供了一個非常重要且具啟發性的思維。

## 關鍵字 
1. 系統級診斷 (System-Level Diagnosis)
2. 容錯與可靠度 (Fault Tolerance & Reliability)
3. 互連網路拓樸 (Interconnection Network Topologies)
4. 診斷度 ($t$ -Diagnosability)
5. 條件診斷度 (Conditional Diagnosability)

## 參考文獻
1. F. P. Preparata, G. Metze, and R. T. Chien, "On the connection assignment problem of diagnosable systems," IEEE Transactions on Computers, vol. C-16, no. 6, pp. 448-454, 1967.
2. H. Lai, J. Leu, and S. Shih, "Conditional diagnosability of hypercubes under the PMC model," Journal of Algorithms, 2005.