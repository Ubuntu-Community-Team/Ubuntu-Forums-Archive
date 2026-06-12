---
title: "Ubuntu 16.04 LTS + TL-WN8200ND wifi card"
date: 2016-12-30
forum: Networking &amp; Wireless
---

### Post by srap100 on 2016-12-30
Hello,

I am a new Ubuntu user and since I installed it I am trying to connect to the internet via wifi because my router is in another floor. My wifi card is TL-WN8200ND. It is recognised by Ubuntu and it finds a lot of networks including mine but i can not connect to it, it keeps asking for my password. As i was searching to find a solution I found this thread: 

[https://ubuntuforums.org/showthread.php?t=2315376](https://ubuntuforums.org/showthread.php?t=2315376)

I did take my PC to the floor where the router is, connected via ethernet and followed the steps stated it that thread. When i finished i unplugged the ethernet cable, restarted my PC and connected the wifi card(my router was next to my PC and my wifi card). It connected to the internet but when i took my computer to the other floor it did not connect again. Today i placed it again next to my router and it connected but the problem is that i can not leave my PC permanently there.

Is there any solution to fix this issue? 

PS: My PC is dual boot with windows. In windows the wifi card works fine.

Thanks.

---

### Post by praseodym on 2016-12-30
Please show the outputs of these commands:

```
lspci -nnk | grep -iA2 net
lsusb
```
Does LAN work?

---

### Post by srap100 on 2016-12-30
```
vasilis@vasilis-desktop:~$ lspci -nnk | grep -iA2 net00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
	Subsystem: ASRock Incorporation Ethernet Connection (2) I219-V [1849:15b8]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
vasilis@vasilis-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 003: ID 2357:0100  
Bus 001 Device 002: ID 045e:07b9 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by praseodym on 2016-12-30
Change the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
sudo git clone https://github.com/vincent-t/rt8192cu_dkms /usr/src/8192cu-4.0.2.9000.20130911
sudo dkms add -m 8192cu -v 4.0.2.9000.20130911
sudo dkms build -m 8192cu -v 4.0.2.9000.20130911
sudo dkms install -m 8192cu -v 4.0.2.9000.20130911 
echo -e "blacklist rtl8192cu\nblacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot

---

### Post by srap100 on 2016-12-30
I just did it. Nothing changed, it still does not connect.

---

### Post by praseodym on 2016-12-30
Please check if the MAC address filter is "on" in your router and turn it off, if applicable

---

### Post by srap100 on 2016-12-30
It is not applicable. There are not any mac addresses in the filter in case that helps.

---

### Post by samigina on 2017-04-23
I have the same card and the same problem (but Ubuntu 17.04), shows the networks in the area but never connects, just ask for the password again and again.

Wireless script result:
[ATTACH]274740[/ATTACH]

---

