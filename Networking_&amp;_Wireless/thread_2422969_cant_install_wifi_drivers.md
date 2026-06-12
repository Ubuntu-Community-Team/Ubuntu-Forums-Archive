---
title: "cant install wifi drivers"
date: 2019-07-15
forum: Networking &amp; Wireless
---

### Post by shawnee32 on 2019-07-15
Hi, I've just installed ubuntu on dual boot. What is the way to install wifi drivers without ethernet cable?
I've already tried downloading driver manually then moving it to USB and to desktop. I dpkged it and used "sudo modprobe -r b43 && sudo modprobe b43" but it is still not working. 
I went to software &updates and tried to turn on the option "using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source" but when I hit "Apply Changes" it is stuck on applying and nothing happens. What do I do?

---

### Post by jeremy31 on 2019-07-15
Moved to Networking & Wireless, can you post results for ```
lspci -nnk | grep -iA3 net
```

---

### Post by oksanareynuk on 2019-07-16
Take a screenshot of the LAN equipment team, wrote jeremy31. First you need to figure out, maybe the driver is just installed and there may be a problem in something else.

---

### Post by shawnee32 on 2019-07-16
Here it is

```
06:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: bcma
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:0655]
	Kernel driver in use: r8169
	Kernel modules: r8169
08:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)



```

---

### Post by oksanareynuk on 2019-07-16
&#1069;&#1090;&#1080; Broadcom &#1085;&#1077; &#1080;&#1079; &#1101;&#1090;&#1086;&#1075;&#1086; &#1084;&#1080;&#1088;&#1072; &#1074;&#1086;&#1086;&#1073;&#1097;&#1077;. 
[COLOR=#000000][FONT=&amp]modprobe -c | grep -i 14e4 | grep -i 4315[/FONT][/COLOR] &#1080;&#1085;&#1090;&#1077;&#1088;&#1077;&#1089;&#1085;&#1086;

---

### Post by shawnee32 on 2019-07-16
```
alias pci:v000014E4d00004315sv*sd*bc*sc*i* ssb


```

After trying 'apt-get' command it tells me to insert disc with Yakkety Yak

---

### Post by oksanareynuk on 2019-07-16
[COLOR=#000000][FONT=&quot]sudo modprobe -r wl && sleep2 && sudo modprobe wl[/FONT][/COLOR]

---

### Post by oksanareynuk on 2019-07-19
It would be great if the author of the question answered whether he was able to solve the problem or not, since other people may need it ...

---

### Post by chili555 on 2019-07-19
> **shawnee32 said:**
> Hi, I've just installed ubuntu on dual boot. What is the way to install wifi drivers without ethernet cable?
I've already tried downloading driver manually then moving it to USB and to desktop. I dpkged it and used "sudo modprobe -r b43 && sudo modprobe b43" but it is still not working. 
I went to software &updates and tried to turn on the option "using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source" but when I hit "Apply Changes" it is stuck on applying and nothing happens. What do I do?The correct driver for your device is bcmwl-kernel-source. While it is tempting to simply find the package at packages.ubuntu.com and transfer it on a USB key, this won't work as it has many dependencies and depencies of dependencies.

Do you have the disk or USB from which you originally installed Ubuntu? All of the requirements are on it. Please see: [https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949](https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949)

---

