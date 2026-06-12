---
title: "Network is broken after upgrade to Gutsy, need help"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Pietro Pizzi on 2007-11-14
Hello,

I have a big Problem. Yesterday i upgraded from Kubuntu Edgy over Feisty to Gutsy. And now my network is broaken and i can't fix it.

My Sys: Asus P5B with 2 onboard Gbit Marvell NICs (88E8001 PCI and 88E8056 PCIe) and a P965 Intel Chipset.

On Edgy the kernel 2.6.17 doesn't support it so i installed the sk98lin ver. 8.4x module from the the Marvell homepage. Now on Gutsy the kernel 2.6.22-14 loads the newer sky2 module for it. But i can't ping my router. So i installed the old sk98lin modul. Then i tryed a new sk98lin ver. 10.22.4.3 from the Marvell homepage. I also tryed the skge module with both NICs and i have always only one card on and turned the other one off in the bios to minimize fault possibilitiies. Now i finaly check an old PCI Realtek card with a RTL8139C chipset.

With the Realtek card and the Marvells with the sky2 or the new sk98lin modules the output from 'sudo lshw -C network', 'ifconfig', 'route', 'lsmod | grep sk' and 'dmesg' look like it should, i think. I have no IP Tables script running. Also the graphikal network tools in KDE shows no problems. But no combination works.

Becouse not even the old Realtek gives me an net access i think the problem could be on another point. I althogh checkt the router, he respond on pings and gives me net access with my laptop. Now i run out of ideas. If anyone can help me i can support u with any sys output u need.

I hope anyone have an idea what i can do now!
Thanks, Pietro.

---

### Post by kickus on 2007-11-18
So you can probably confirm my problem: [http://ubuntuforums.org/showthread.php?p=3744491](http://ubuntuforums.org/showthread.php?p=3744491)

I downloaded old working kernel packages (2.6.20-16-386). 

The 2.6.22 kernel packages shipped with gutsy are broken. I compiled a 2.6.23.1, and it seemed to be broken as well. If you can pin the problem further down, I'd like to hear about it. My own postings were ignored.. 

Good luck

/Kristian

---

