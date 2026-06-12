---
title: "Can't find Network Manager icon..."
date: 2011-07-03
forum: New to Ubuntu
---

### Post by mtds on 2011-07-03
I just installed a new wireless router (Netgear WNDR3700v2) in my home. I got my wife's Windows 7 desktop (cabled) and her Vista laptop (wireless) both working fine.
 
HOWEVER, I can't find the Network Manager icon on my Ubuntu-only laptop so I can try to get on our new network. (Gnashing of teeth AND she is mocking me for using Linux.)
 
Help?

---

### Post by pikamoku on 2011-07-03
just plug the wire (rj45) if you have this option. DHCP is default enabled so if router is well configured you'll get network access. Open synaptic and Look if you have   network-manager package installed, if not: install it. Otherwise try to reinstall it to be sure all dependencies are satisfied. 
You can verify if you have cable network access by typing on a terminal: > ifconfig You'll see all network devices detected on you laptop.


And let me add that you have to be more specific about your problem:  Ubuntu version, hardware description, desktop enviroment,etc. You can find it by typing on terminal some commands like lsusb and/or lspci

---

### Post by mtds on 2011-07-03
> **pikamoku said:**
> just plug the wire (rj45) if you have this option. DHCP is default enabled so if router is well configured you'll get network access. Open synaptic and Look if you have network-manager package installed, if not: install it. Otherwise try to reinstall it to be sure all dependencies are satisfied. 
You can verify if you have cable network access by typing on a terminal: You'll see all network devices detected on you laptop.
 
 
And let me add that you have to be more specific about your problem: Ubuntu version, hardware description, desktop enviroment,etc. You can find it by typing on terminal some commands like lsusb and/or lspci
 
pikamoku:
 
Thank you for trying to help me.
 
As you suggested I plugged in the cable and was able to get network access, as you said. I then went to Synaptic Package Manager and seached for "network-manager." Selected the applet file for network manager and agreed to the other suggested packages, selected apply and waited. All seemed to be well, but still no sign of the icon. Repeated the work in Synaptic; same result. Ubuntu Software Center tells me that Network Manager is installed, but I see no icon. I tried uninstalling and reinstalling from the Software Center and still no icon.
 
I am sorry I was not more informative about my problem: Ubuntu 10.04 LTS Gnome 2.30.2 on a Dell Inspirion E1505 with no other OS on-board.

---

### Post by ajgreeny on 2011-07-03
Make sure you have **notification area** and **indicator applet** in your panel.

---

### Post by mtds on 2011-07-03
> **ajgreeny said:**
> Make sure you have **notification area** and **indicator applet** in your panel.
 
ajgreeny:
 
That did the trick. I am connected wirelessly now. Thank you for your help!

---

### Post by ajgreeny on 2011-07-03
> **mtds said:**
> ajgreeny:
 
That did the trick. I am connected wirelessly now. Thank you for your help!
No problem!

They contain other notifications as well as network manager icon, so are worth having on the panel, and I thought were there by default.  Did you remove them?

---

### Post by mtds on 2011-07-03
> **ajgreeny said:**
> No problem!

They contain other notifications as well as network manager icon, so are worth having on the panel, and I thought were there by default.  Did you remove them?

Well, I don't *remember* removing them, but I might have done so while bumbling around exploring.  I can't wait to find out what snares I've left for myself while trying to correct the problem you just solved.  There were many choices in Synaptic Package Manager for network-manager and I have no confidence that I selected the right ones.

---

