---
title: "Ethernet adapter problems"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by kingbabi on 2007-08-16
Hey, I recently installed Ubuntu on an older PIII with 256 MB RAM to use as a Bittorrent box. It is dual booting with Windows 98 (which I am using to type this post). It has a Wired ethernet card installed, a CNET PRO200WL PCI Fast Ethernet Adapter ([http://www.cnetusa.com/product/specs/nics_pro200wl.htm](http://www.cnetusa.com/product/specs/nics_pro200wl.htm)). This works fine on 98, but when I go into Ubuntu it seems not to work. Should I get a driver for it? I don't know my way around Ubuntu that well so I can't be sure if it is even recognized. When I ask the networking monitor to connect to the wired network, it tries to connect for a while, then it says I am connected to the wired network, but it does not connect to the internet. At first I took this as a sign that it was working partially, but when I disconnected the ehternet cable and tried again, it did the same thing, disproving my theory.
What should I do? 
Thanks in advance for your help.

---

### Post by tbfr on 2007-08-16
I don't know this card but the first thing I would check is whether the kernel recognized the card. Just type **dmesg | grep eth** to see if an ethernet card was found during boot.

The output of **lspci** migth be interesting too as well as the output of **lsmod**.

Searching the forum for PRO200WL shows quite a few threads, you might want to start with [http://ubuntuforums.org/showthread.php?t=54886]("http://ubuntuforums.org/showthread.php?t=54886")

---

