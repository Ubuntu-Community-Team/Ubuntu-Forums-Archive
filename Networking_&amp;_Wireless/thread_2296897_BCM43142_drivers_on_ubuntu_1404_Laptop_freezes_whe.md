---
title: "BCM43142 drivers on ubuntu 14:04: Laptop freezes whenever it is using Wi-Fi"
date: 2015-09-29
forum: Networking &amp; Wireless
---

### Post by jmcarcell on 2015-09-29
Hello,
I'm running a fresh installed ubuntu 14.04 on a brand new Asus F555L laptop but the driver that was provided for my network card isn't working. Whenever I use the internet the computer freezes completely and the only thing I can do is to turn it off using the power button.
I've tried follow what I've found in
[http://ubuntuforums.org/showthread.php?t=2214110]("http://ubuntuforums.org/showthread.php?t=2214110")
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

to no avail. I have purged and reinstalled the  bcmwl-kernel-source (even b43 and more...) and nothing works. I don't know what to do nor why this is happenning since my network card should work with the sta drivers as it listed in the posts I've linked before.
Output for
```
lspci -vvnn | grep -A 9 Network 
```
is
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6675]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at f7100000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: wl

```



Any help would be highly appreciated.

Many thanks.

---

### Post by jeremy31 on 2015-09-30
Show ```
uname -r; dpkg -l | grep -i broadcom
```

---

### Post by jmcarcell on 2015-10-01
```
3.19.0-30-generic
ii  b43-fwcutter                                          1:018-2                                             amd64        utility for extracting Broadcom 43xx firmware
ii  bcmwl-kernel-source                                   6.30.223.248+bdcom-0ubuntu0.1                       amd64        Broadcom 802.11 Linux STA wireless driver source
ii  broadcom-sta-dkms                                     6.30.223.141-1                                      all          dkms source for the Broadcom STA Wireless driver
rc  wireless-bcm43142-oneiric-dkms                        6.20.55.19~bdcom0602.0400.1000.0400-0somerville1    amd64        Broadcom 802.11 Linux STA wireless driver source


```

Thanks for the help.

---

### Post by jeremy31 on 2015-10-01
I would ```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-dkms wireless-bcm43142-oneiric-dkms
sudo apt-get install bcmwl-kernel-source
```

Reboot

---

### Post by jmcarcell on 2015-10-01
I did what you said and tested it at my college campus with success; it worked flawlessly (I don't know whether it worked before there or not). However, when I came back home and connected to the Wi-Fi it froze is usual. The biggest difference between the Wi-Fi at the campus and mine's is that they use dynamic IP while I use static IP. I changed static to dynamic at home and voilá, now it works.
I can solve this temporarily changing it to be dynamic but it would be better if there was a solution that allowed me to use static IP. 

Output for ```
dpkg -l | grep -i broadcom
```

now is

```

ii  b43-fwcutter                                          1:018-2                                             amd64        utility for extracting Broadcom 43xx firmware
ii  bcmwl-kernel-source                                   6.30.223.248+bdcom-0ubuntu0.1                       amd64        Broadcom 802.11 Linux STA wireless driver source
```

---

### Post by jeremy31 on 2015-10-02
How do you set the static IP for your home network, through Network Manager or through the wifi access point?

---

### Post by jmcarcell on 2015-10-04
Through the wifi access point. Even it is dynamic IP through the wifi access point but I have static IP through the Network Manager it will freeze too. The only way that works for me is dynamic IP at the router and at my computer.

---

### Post by Graham_Mitchell on 2015-10-12
I've seen this issue as well. I think it might be down to the Network Manager not changing the settings correctly. Have you tried configuring the static IP settings through the command line interface instead?

---

