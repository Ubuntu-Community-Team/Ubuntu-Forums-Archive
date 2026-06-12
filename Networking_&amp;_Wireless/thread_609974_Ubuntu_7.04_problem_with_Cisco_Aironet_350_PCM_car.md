---
title: "Ubuntu 7.04 problem with Cisco Aironet 350 PCM card"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by kill4killin on 2007-11-11
Hello everyone,
I have here a Thinkpad T23 with a Cisco Aironet 350 PCM card in it. I just installed Ubuntu 7.04 (7.10 was giving me troubles with the partitioning, it wouldn't partition the hard drive for some reason) on this laptop and was initially impressed, I thought that the wireless card was supported with the pre-installed drivers that came with Ubuntu, but then I noticed something strange. When I click the networking Icon in the top right of the screen, it shows all of the wireless networks in range, but then when I try to connect to mine (with encryption off) it says unable to connect. When I just hover over the icon, it says no networks connected. However, if I do ```
iwconfig eth1
``` it shows that I am connected to my network...why is it that the GUI network manager cannot connect to the networks and when I try doing ```
iwconfig eth1 essid /mynetwork/
``` it doesn't connect, but right at boot time it finds the first unencrypted network and connects just fine?

```
sudo lshw -C network
```
revealed that it saw the network card and knew what it was.

Anyone have any suggestions to solve this. If the laptop was going to be staying with me, just using /etc/network/interfaces would not be a very big deal, but this is going to someone else who isn't terribly good at command line stuff or linux in general so I'm trying to make this feel as easy and comfortable as I can for her.

---

### Post by kill4killin on 2007-11-11
Ok, nevermind, the problem was solved with an release upgrade to 7.10.

---

### Post by Bushido89 on 2007-11-11
Would I have a reformat my Hdd to upgrade? :s.

---

