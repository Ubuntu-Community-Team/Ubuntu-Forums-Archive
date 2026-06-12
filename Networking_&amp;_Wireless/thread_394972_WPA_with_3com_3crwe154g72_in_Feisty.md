---
title: "WPA with 3com 3crwe154g72 in Feisty"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by elsieboy on 2007-03-27
Hi there,

Just installed feisty beta, loving it. Wireless works right outta the box except, I need WPA.  Out of the box gnome network manager won't let me use WPA, so I've disabled network security on our router. Housemates have given me till the end of the week to get WPA working, or it's back to Windows - we refuse to use no security or WEP.

I have a 3com 3crwe154g72 PCMCIA card. Do I need to use ndiswrapper and whatnot or will the drivers included with feisty do the trick?

I really want to get this working, but not at the cost of an insecure AP.

Cheers,
elsie

---

### Post by elsieboy on 2007-03-27
Some more info:

I installed ndiswrapper, and got the driver from the disk that came with the card (but this disk seems to be a copy): shouldn't it say 'hardware present' or something?

luke@luke-laptop:~$ ndiswrapper -l
3c154g72 : driver installed

elsie

---

### Post by itsagas2 on 2007-03-28
I'm curious if your problem is similar to mine. Would you try this.

Enable you wireless security in the Ubuntu Administrator / Network application.

Next reboot you computer.

If your wireless card isn't connected, do this.

From a terminal screen issue this command:

sudo ifdown ra0

next after this completes issue this next command,

sudo ifup ra0

See if your wireless card is working and connects to the internet / router.

---

### Post by jogege on 2007-04-01
> **elsieboy said:**
> Hi there,

Just installed feisty beta, loving it. Wireless works right outta the box except, I need WPA.  Out of the box gnome network manager won't let me use WPA, so I've disabled network security on our router. Housemates have given me till the end of the week to get WPA working, or it's back to Windows - we refuse to use no security or WEP.

I have a 3com 3crwe154g72 PCMCIA card. Do I need to use ndiswrapper and whatnot or will the drivers included with feisty do the trick?

I really want to get this working, but not at the cost of an insecure AP.

Cheers,
elsie

For what its worth,I have this exact same card myself and have never been able to get the native drivers to work. With Ndiswrapper though, it works without any problem especially in Dapper and Edgy.

In Fesity, Ndiswrapper works and I have been able to get WPA working with network manager. 

However, and this is the puzzling part, whenever I upgrade and the kernel is upgraded past 2.6.20.9 if my memory serves me( I hosed my system yesterday so I cant check), it doesnt connect. It shows everything fine but somehow, network manager just doesnt connect. I am puzzled and really dont know what to do again.

I have tried disabling ndiswrapper and using prism54pci and prism54common which comes with fesity but still no joy.

---

### Post by jogege on 2007-04-01
I just installed the 2.6.20-12-386 thru synaptic and yeah the card is connecting now. So obviously something in the newer kernels is not right.

I have gotten it to connect thru network manager to my wireless network so you might give that a try.

---

### Post by zvbxrpl on 2007-04-25
Is your card version 1 or version 2 (it shold be printed on the card?)

Version 1 uses 'hardmac' firmware and should be workable under prism54.  Version 2 uses 'softmac' firmware (the MAC address has to be uploaded to the card upon insert) and needs ndiswrapper.

---

### Post by jogege on 2007-04-25
Oh...that makes sense. Mine is Version 2.0

---

