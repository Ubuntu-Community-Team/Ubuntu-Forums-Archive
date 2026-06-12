---
title: "Slow wifi [Ubuntu 15.10] [Realtek RTL8821ae]"
date: 2015-12-19
forum: Networking &amp; Wireless
---

### Post by a-safiullin on 2015-12-19
Fresh install of Ubuntu 15.10 on brand new computer. 

Not satisfied with wi-fi quality: 
1) speed is about 2 times slower than if I connect to the same wi-fi spot using USB-tethering through my mobile (onboard wifi - about 600-700KB/s, through USB-tethering 1.2-1.5MB/s)
2) sometimes after suspend wi-fi doesn't work. The only solution to start it again is to reboot.

Computer - acer revo rl85, wifi = realtek rtl8821ae 

Installed fresh drivers from** ppa:hanipouspilot/rtlwifi**, but no much difference.

Please help! Thanks a lot!

---

### Post by Knightwise on 2016-01-04
Hi,

I don't have a driect answer to your question but I did want to ask how the rest of the hardware is supported ? 
Does everything work out of the box ?
Do you have any issues with the wired network interface ? 
Are the video drivers working ?

---

### Post by branislav-kopun on 2016-01-10
Hello, I have the same issue (with ASUS VivoPC UM62).
I'm using ubuntu Mate - Willy and still searching for solution.

---

### Post by cariboo on 2016-01-10
When wifi doesn't work after suspend, I use the following command:

```
sudo service NetworkManager restart
```

---

### Post by Knightwise on 2016-02-11
Hey guys, I'm trying to get Ubuntu installed on my Acer R85L but I'm somehow unable to boot from any other device then the harddrive. I've disabled secure boot in the bios but the device will only start from its internal harddrive running Windows. How did you guys manage to get it booting into Ubuntu ?

---

