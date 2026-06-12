---
title: "Network was working, changed for WiFi, how do I tel Ubuntu ?"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by bleakcabal on 2006-11-13
Hi, when I first installed Ubuntu I was using a wired connection. Everything was auto-detected and ran fine. 

Now I removed my old ethernet card and put a DLink wifi card since my home network is now WiFi.

I can't make networking/connecting to the internet work. 

I assume I must do something to tell Ubuntu ( Kubuntu in my case ) to detect my new card and new network setting and all.

Is there a command or program to run to acomplish this ?

Thanks in advance for your help.

---

### Post by jpkotta on 2006-11-13
```
sudo network-manager
```
If you know a bit about networking, then you should be able to get it working, assuming the drivers work.  See the [wiki]("https://help.ubuntu.com/community/NetworkDevices") for more general help.

---

