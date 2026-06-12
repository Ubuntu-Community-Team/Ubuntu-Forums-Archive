---
title: "Help! I can't connect through ethernet!"
date: 2016-09-26
forum: Networking &amp; Wireless
---

### Post by mzshaidu on 2016-09-26
Hi, I am completely new to ubuntu. I installed it yesterday on a relatively old computer and have it installed with linux alone. When first installing it the installation could not connect to the internet even though i am connected by an ethernet cord. After some attempts at troubleshooting I have not found an answer. I have tried inputing the dns manually and after doing so the little icon at the top right now says im connected, but i still don't have internet access. Please help.

---

### Post by jeremy31 on 2016-09-26
*Thread moved to **Networking & Wireless**.*
I guess you could start by posting the info from terminal for ```
lspci -nnk | grep -iA2 net
```

Welcome to the forums

---

### Post by mzshaidu on 2016-09-26
```
00:07.0 Bridge [0680]: NIVIDIA corporation MCP61 Ethernet [10de:03ef] (rev a2)
           Subsystem: Acer Incorporated [ALI] MCP61 Ethernet [1025:0181]
           Kernel driver in use: forcedeth
           Kernel modules: forcedeth
```

Is this what you wanted?

---

### Post by jeremy31 on 2016-09-26
Yes
See if this command works
```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/force.conf
```

Reboot

---

### Post by mzshaidu on 2016-09-26
after typing it in it says
```
options forcedeth msi=0 msix=0
```
after rebooting still no connection

---

