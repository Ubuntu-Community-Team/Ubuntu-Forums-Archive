---
title: "CPU Temp Not displayed in Conky"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by guv999 on 2011-02-10
Hi 
I am quite new to Conky, and have one issue I cannot seem to be able to resolve.   
I cannot get the CPU Temp to display in Conky
I have lm-sensors downloaded, and when I launch the panel-sensor applet it is able to monitor the temperatures.  So I a least know that they can be measured.
Is there anything I need to be doing direct to Conky? I any additional information is needed I will be happy to supply it.

---

### Post by rcayea on 2011-02-10
Maybe this link will help. It is a similar issue. 

[http://art.ubuntuforums.org/showthread.php?p=8393551](http://art.ubuntuforums.org/showthread.php?p=8393551)

---

### Post by cchhrriiss121212 on 2011-02-10
It depends on your sensors output, but this should work for most people:
${hwmon temp 1}

If not, then post what you get from sensors in a terminal.

---

### Post by guv999 on 2011-02-10
> **cchhrriiss121212 said:**
> It depends on your sensors output, but this should work for most people:
${hwmon temp 1}

If not, then post what you get from sensors in a terminal.

Works perfectly - thanks for your help

---

