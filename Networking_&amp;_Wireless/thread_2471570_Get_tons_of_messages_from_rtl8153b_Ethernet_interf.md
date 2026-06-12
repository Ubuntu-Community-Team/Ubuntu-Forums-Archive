---
title: "Get tons of messages from rtl8153b Ethernet interface"
date: 2022-02-03
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2022-02-03
Hello Guys,
I own a Chinese Thunderbolt dock. It contains (among other things ) a Gigabit Ethernet interface :
```
Bus 002 Device 006: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
```
The Lenovo ThinkBook native interface is : 
```
0000:2c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
```
Sometimes, I get a huge amount of the following messages in the logs
```
11398.196525] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[11401.528645] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[11407.548340] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[11413.596465] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[11419.616561] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[11425.668489] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[11431.696500] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12241.324457] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12244.975656] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12250.995740] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12257.564601] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12263.147727] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12269.123793] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12275.151749] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12278.645407] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12284.295778] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12290.271832] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12296.283850] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12299.812779] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12305.791865] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12311.408013] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12317.416027] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12323.832453] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12407.008284] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12411.049833] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12416.688352] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12422.712325] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12429.233448] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12437.844351] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12443.824583] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12450.300919] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12455.996533] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12461.972483] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12467.994996] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12473.800728] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12479.456579] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12485.484592] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12491.924803] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12497.632714] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12503.588711] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
[12509.628700] r8152 2-2.4.1:1.0: load rtl8153b-2 v1 10/23/19 successfully
```
But sometimes no problem at all. I seldom use Ethernet interfaces (only when I've huge amount of data to transfer) and often use the Thunderbolt hub one because the ThinkBook has a folding Ethernet plug which is a pita to use.
Both interfaces run perfectly when plugged and get the correct speed and duplex from the switch, so apart from the messages, I'm satisfied by the behavior of this computer.
Could you please help me find what is wrong ? And correct it ? 
Many thanks in advance for your time and help. 
Have a nice day!

---

