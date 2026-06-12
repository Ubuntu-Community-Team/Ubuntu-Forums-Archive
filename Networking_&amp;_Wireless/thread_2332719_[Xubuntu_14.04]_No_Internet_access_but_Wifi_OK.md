---
title: "[Xubuntu 14.04] No Internet access but Wifi OK"
date: 2016-08-03
forum: Networking &amp; Wireless
---

### Post by waouh2 on 2016-08-03
Hello,

Today, my Xubuntu 14.04 has frozen. So, I pressed Alt+Syst+B to reboot the system. Since then, I no longer have Internet access. Here are the tests I did to track the issue:

- I succeed to ping my router and my roommate computer. So, I am indeed connected to the wifi network.
- I am able to access the Internet through my roommate computer thanks to a proxy connection via the ssh command and the -D option.
- If I use my smartphone as a hotspot, the problem remains: I can establish the connection, but the Internet is still unreachable.
- I have a dual boot with Windows 8 and Internet works fine.
- It does not change anything if I connect my computer to the router with an ethernet wire (still connected to the local network, including my roommate computer, but still no Internet connection.)

In order to affirm that Internet is not reachable, I just ping 8.8.8.8 (and it fails.)

According to these tests, it appears that the problem comes from the OS itself since it works on Windows and connecting to another wifi access point does not change anything. What confuses me is that I am able to communicate with the different devices on the local network, but the packets I send to the Internet seem to be lost.

My knowledge in this area are limited to what I did and I don't know what else to do to track the issue. Do you have any other tests I could run?

Thanks a lot

---

### Post by chronomus on 2016-08-03
hello greetings from Venezuela
1: try acualizar your controller
2: go and upgrade software or additional driver
3: use the command sudo apt-get purge bcmwl-kernel-source
4: sudo apt- get install bcmwl-kernel-source
5: sudo apt- get install firmware-b43-installer

sudo apt-get update

sudo modprobe -rv b43 

sudo modprobe b43

your internet ready it should work !

---

### Post by Keith_Helms on 2016-08-04
Sounds like a DNS related problem to me.  What do the following commands show?
```
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

