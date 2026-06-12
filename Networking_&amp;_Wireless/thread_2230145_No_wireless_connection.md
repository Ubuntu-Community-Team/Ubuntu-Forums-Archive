---
title: "No wireless connection"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by Antonio_Carlos_.. on 2014-06-17
Hello! I have an old notebook wich I just installed Lubuntu on it. The main purpose is to give It to my father so he can watch vídeos on youtube.
Well, after the Lubuntu's installation, there is no option nor icon to search or connect to my home wi fi. Cable works fine.

Thanks.

---

### Post by chili555 on 2014-06-17
Please check here: [http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing)

---

### Post by Antonio_Carlos_.. on 2014-06-17
Hi! Thanks for helping! The problem is the wireless connection. The icon appears and when I click on it, just give me the option related to my cable connection (I don't know if it's the appropiate word in english) but nothing about my wi-fi.

---

### Post by chili555 on 2014-06-17
Sorry I misunderstood when you said:> Well, after the Lubuntu's installation, **there is no option nor icon** to search or connect to my home wi fi. Please open a terminal and run and post:```
lspci -nn | grep 0280
```

---

### Post by Antonio_Carlos_.. on 2014-06-17
Sorry. My fault. When I installed de OS, the icon was there. After updating the distro, it had disappeared. I did what you said and managed to get It back. Still, no wireless. When I put the code you asked in the terminal, It gives me no response. I tried with "sudo" before and I still got nothing. What am I doing wrong?

---

### Post by chili555 on 2014-06-17
Two possibilities exist; first, that there is no wireless card in the machine at all or else, it is one of the rare devices that is attached to an internal USB bus. Let's see:```
lspci -nn
lsusb
```

---

### Post by Antonio_Carlos_.. on 2014-06-17
Ok! Now it worked. I copied and pasted and I got this:

edgar@edgar-Positivo-Mobile:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671]
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 IDE Controller [1039:5513] (rev 01)
00:03.0 USB controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 03)
00:06.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a]
00:07.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a]
00:0f.0 Audio device [0403]: Silicon Integrated Systems [SiS] Azalia Audio Controller [1039:7502]
00:1f.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:0004]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
03:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
03:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
03:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
03:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2014-06-17
I'm sorry, I see no wireless adapter at all.

---

### Post by Antonio_Carlos_.. on 2014-06-17
Well, thank you very much anyway. Unfortunately, I'll have the XP installation back. =(

---

### Post by chili555 on 2014-06-17
> **Antonio_Carlos_.. said:**
> Well, thank you very much anyway. Unfortunately, I'll have the XP installation back. =(Are you saying that XP sees the wireless adapter and Ubuntu doesn't??

---

