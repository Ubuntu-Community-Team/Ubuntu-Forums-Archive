---
title: "D-Link DSL-G604T"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by schmikes on 2007-04-20
Anyone knows how to setup wireless connection in Ubuntu?

---

### Post by khanhnt on 2007-05-16
First of all, you access in your modem by address 192.168.1.1 (or 10.0.0.1). Then, you configures parameters in the session Wireless and Lan Setup (it is simple). 
The importance which you must configure in sessions WAN SETUP. In this session, you creates a new connection with: 
                  Name: the name of your connection 
                  **Type** is **Bridge**
                  VPI: 8 
                  VCI: 35 
                nothing to do for another parameter 
Then you applies them. After that, you run **sudo pppoeconf**, in your terminal. And register of information like: your account, password... that ISP provides you.

---

