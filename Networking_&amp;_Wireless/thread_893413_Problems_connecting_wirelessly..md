---
title: "Problems connecting wirelessly."
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Matchu24 on 2008-08-18
Hey, I installed Ubuntu last night and didn't run into any problems. The little icon in the top right told me when networks were available and I could connect fine. But seemingly overnight everything has disappeared, when I booted up this morning there's no longer an icon in the top right and I can find no way to connect wirelessly. I've tried following the steps available in the help file to no avail. Any help appreciated, also here's some info that may/may not be useful:


  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:e5:e0:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by Matchu24 on 2008-08-18
Sorry to bump but I really need some help.

---

### Post by Matchu24 on 2008-08-19
Anyone?

---

### Post by shinkaide on 2008-08-20
I know, man, It's got a thing about it that'll just disappear on ya. 

Try typing this in a terminal (or just do alt-F2 and then type it):

```
 nm-applet 
```

Also... go to **System > Preferences > Sessions**. In the "Startup Programs", see if "Network Manager" is checked or available. If it's not, just add it (using the command above for the launcher).

Hope that helps. :)

---

