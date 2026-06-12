---
title: "No chance for my bcm4318 with feisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by hellboy195 on 2007-04-21
I tried everything. And when I say everything I mean everything.
I tried the cafugo packages, packages posted in this forum. Scripts, Ndiswrapper from the repo, The newest version (1.42) self compiled. Nothing is working. Always the card is recognized and I can see my wlan but I can´t connect.  In no case :(

Please help

---

### Post by turbopeppe on 2007-04-21
same as you...desperate

---

### Post by Kobalt on 2007-04-21
What does these command return : 
```
sudo ndiswrapper -l
iwconfig
```

---

### Post by hellboy195 on 2007-04-21
> **Kobalt said:**
> What does these command return : 
```
sudo ndiswrapper -l
iwconfig
```

Actually I haven't installed ndiswrapper now cause I've tried something different. What should I try first? The version from the repository or the self-compiled version (newest 1.42)?

Edit: And what version of bcmwl5.inf ? The one from dell,hp or acer or no matter?

---

### Post by ziadoz on 2007-04-21
I have exactly the same problem. Its driving me nuts. I really hope they fix this issue soon, it seems to be happening to plenty of people.

---

### Post by Kobalt on 2007-04-21
One easy way to install your card is to open Synaptic package manager in System > Admin. menu. Then search for a package named *ndisgtk*. Install it. 
After that, go to System > Admin. > Windows Wireless Drivers : you will access ndiswrapper in a graphical mode, from there you'll be able to install the drivers for your card really easily. If you have an HP computer, pick the ones from HP website, if you have a Dell one, pick them from Dell's website, etc. You can also take them from your Windows partition (should be in c:/windows/system32 if I remember correctly) or your manufacturer computer drivers CD or restoration disk, etc...
Then you can use Network-Manager to configure/access your wireless network pretty easily.

The broadcom cards can be installed pretty easily now under Feisty, you must have missed a step somewhere in what you read/tried...

---

### Post by hellboy195 on 2007-04-21
> **Kobalt said:**
> One easy way to install your card is to open Synaptic package manager in System > Admin. menu. Then search for a package named *ndisgtk*. Install it. 
After that, go to System > Admin. > Windows Wireless Drivers : you will access ndiswrapper in a graphical mode, from there you'll be able to install the drivers for your card really easily. If you have an HP computer, pick the ones from HP website, if you have a Dell one, pick them from Dell's website, etc. You can also take them from your Windows partition (should be in c:/windows/system32 if I remember correctly) or your manufacturer computer drivers CD or restoration disk, etc...
Then you can use Network-Manager to configure/access your wireless network pretty easily.

The broadcom cards can be installed pretty easily now under Feisty, you must have missed a step somewhere in what you read/tried...

Ah thx for your answer. But I use Ubuntu since dapper and I think I don't need a graphical way for ndiswrapper ;)
I know that the new Network-Manager is really nice but how I told you I can't connect. WEP shouldn't be the problem? And I'm Ubuntu only so I have to use the cd ;) And I only tried the bcmwl5.inf from other vendors because someone told me that his bcm4318 is working with the dell driver and he has a hp laptop.

---

