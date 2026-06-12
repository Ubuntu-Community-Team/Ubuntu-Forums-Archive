---
title: "Help plz.....:("
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by Newbie29 on 2007-03-02
Hi, 
Ok, this is the provlem, I have installed ndiswrapper and my wireless cards driver, and if I type in :

ndiswrapper -l

in the terminal, I get that both my driver and the hardware is present....*whew* finally.....ok, then I went to applications, system, networking, and saw that the card had been picked up, so, I opened the properties to activate it, I selected enable this network, then i selected  the network name from a drop down list ("speedstream") and left the key type on plain (ASCII), added no WEP Key (cause I don't know what that is and I don't think I have one) and selected configuration as DHCP, and pressed ok, Now when I pressed OK, immediately, although I hadn't clicked on Activat yet, the "link" light on my wireless began to blink, and the light indicating a wireless connection on my router flashed on as well. And yet, I had not clicked on activate in the network window yet, and in the network window it was written under the wireless icon that the connection is still not active, I still clicked ok, and opened Mozilla, but nothing happened (i.e. it didn't go to any site), so I opened the networking manager again and there instead of saying that the wireless connection was not aactive as it had said when I clicked ok before, it said that the connection was active......and if I try to click on deactivate and then activate, this window pops up which says activating ra0 interface, and then nothing happens, i.e. the card doesn't connect to my router......

Pleas help me, I am a newbie, plz....thank you.

by the way, I am using Xubuntu 6.06, and the wireless card's model is DWL-G630_E1 and I am using ndiswrapper-1.8.

p.s.:what exactly does "ra0" mean?
Thanks in advance.

---

### Post by Newbie29 on 2007-03-02
. bump, sorry to bump, but, I really need the soulution to this problem....

---

### Post by chili555 on 2007-03-02
How about letting us see the output of sudo iwlist ra0 scan as well as sudo iwconfig ra0. Thanks. 

We'll get it going!

---

### Post by nyinge on 2007-03-02
Ok.  We'll have to troubleshoot step by step.  :)

Have you blacklisted bcm43xx driver?  Sometimes it may cause conflicts.  Append the following line to the file /etc/modprobe.d/blacklist:
```
  sudo echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist  
```

Now, reboot.  Then, post the output of the following 2 commands:
```
  iwconfig  
```
and
```
  ifconfig  
```

---

