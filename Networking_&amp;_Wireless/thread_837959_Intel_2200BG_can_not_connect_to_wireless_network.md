---
title: "Intel 2200BG can not connect to wireless network"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by VeeArrSix on 2008-06-23
Hi, recently I installed Ubuntu 8.04 on my Dell Inspiron 9200. For some time now I have been trying to connect to my wireless network. I have followed the instructions on this website [here.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") I have installed my driver in Ndiswrapper and I still am not able to connect to my wireless. HELP!!! Thanks in advance.

---

### Post by lisati on 2008-06-23
> **VeeArrSix said:**
> Hi, recently I installed Ubuntu 8.04 on my Dell Inspiron 9200. For some time now I have been trying to connect to my wireless network. I have followed the instructions on this website [here.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") I have installed my driver in Ndiswrapper and I still am not able to connect to my wireless. HELP!!! Thanks in advance.

This *might* help: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---

### Post by VeeArrSix on 2008-06-23
> **lisati said:**
> This *might* help: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

I will try this and let you know. Thanks!

---

### Post by VeeArrSix on 2008-06-23
No..this didn't work. It will connect to a wired network fine, but it doesn't even find any wireless networks.

---

### Post by VeeArrSix on 2008-06-23
I just was able to have the wireless networks show up in the Network Manager, now I click my network and I enter my WPA and click connect and it says "Waiting for network key" and never connects :confused:

---

### Post by VeeArrSix on 2008-06-23
still haven't fixed it yet

---

### Post by lswb on 2008-06-23
The native linux driver for the IPW 2200 works very well, ndiswrapper whould not be required. I installed an IPW2200 mini-pci card in my laptop using hardy and it loaded the correct driver (module name is ipw2200) and everything worked on the first boot. Could you try uninstalling or disabling ndiswrapper?

---

### Post by arh1 on 2008-08-01
fwiw, i was struggling with the "waiting for network key" issue for one wireless network i use, and the solution was to simply change to a different "wireless security" setting in the wireless network dialog.  the one that worked in my specific case was "WEP 64/128-bit ASCII".

---

