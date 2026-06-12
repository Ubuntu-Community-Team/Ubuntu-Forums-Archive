---
title: "Wireless Networking Issues (ACX111)"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by Nuker on 2007-04-18
I've been trying to get my Wireless working since 6.xx. I've tried a lot of things. All without any succes, so I decided to try the latest beta version; Feisty Fawn. I was suprised, it found my network! horay! Yet, it doesn't want to connect to it. It just tries to connect, but it fails after waiting a minute or two. There is nothing wrong with the network settings, I tried the same settings on my other computer and it worked fine. I'm almost sure the problem is the acx111 chipset.   

I tried dmesg, and I noticed it kept repeating these errors:
> [  281.029146] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  284.980565] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  285.053467] wlan0: duplicate address detected!

I have no idea how to fix this. So I request your help!

edit: please note, I'm kinda new to linux :|
edit2: I'm using an OvisLink WL-8000 PCI

---

### Post by Nuker on 2007-04-18
bring up my post! :(

---

### Post by shaydee on 2007-04-20
Hi Nuker,

I've got the same problem with Feisty. lspci identifies my cards chip as "Texas Instruments ACX 111", and I get the very same messages in my syslog. My cards manufacturer is D-Link, but I suppose the chip is the same. 
On Dapper I managed to get the card running using ndiswrapper. But after each kernel update some manual adjustments were required in order to bring the networking up again. And since I am configuring Feisty for a person who is unable to do such things on her own, ndiswrapper is not really an option here. :/
Any hints on how this problem can be solved on the long run (other than buying a different wifi card ;) ) are greatly appreciated. :)

---

### Post by stijngysemans on 2007-04-21
I have the same problem.
And I also have a D-link adapter. (g650+)
What can we do 'bout it to make it connect to our network.

---

