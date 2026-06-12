---
title: "no wifi network after installation of ubuntu 14.04 dell inspiron 1520"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by marc49 on 2015-02-24
peace be with you all brothers and sisters'

im an absolute newbie and knew little about the ubuntu OS but i tried this inspite having a little knowledge about it. my problem is after installing ubuntu 14.04 there is no wifi network only the ethernet cable is working but after several reboot the ethernet was also gone i've tried some solutions found on the thread but it didnt works for me.

here is what i've done so far;

ive enter this command 
[COLOR=#000000][FONT=SmartGothic]lspci -nnk | grep -iA2 net 
and here is the results
marc@marc-Inspiron-1520:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01f1]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge
marc@marc-Inspiron-1520:~$ 
i hope these info will help thanks you all 
[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-02-24
It should work after```
sudo apt-get install firmware-b43-installer
``` and a reboot

---

### Post by marc49 on 2015-02-24
Hi' Jeremy31 the Ethernet network is also gone and the wifi didn't work as well'

---

### Post by jeremy31 on 2015-02-24
Did you happen to install a driver from the driver manager?

---

### Post by marc49 on 2015-02-24
Is that the driver found on software and updates?

---

### Post by jeremy31 on 2015-02-24
> **marc49 said:**
> Is that the driver found on software and updates?

Yes and if you installed it```
sudo apt-get purge bcmwl-kernel-source
``` and reboot as it blacklists the drivers your wifi and wired needs

---

### Post by marc49 on 2015-02-24
Yes' there's a message on the screen that it cannot be installed' I don't know why?

---

### Post by jeremy31 on 2015-02-24
> **marc49 said:**
> Yes' there's a message on the screen that it cannot be installed' I don't know why?

You don't need or want the driver in software and updates

---

### Post by marc49 on 2015-02-24
Hi Jeremy31 I'm sorry if I ask a very silly question I hope you will understand me as I am really a newbie here. What I did was input your code into a terminal extract it on the terminal itself and after that I typed exit.

---

### Post by jeremy31 on 2015-02-24
> **marc49 said:**
> Hi Jeremy31 I'm sorry if I ask a very silly question I hope you will understand me as I am really a newbie here. What I did was input your code into a terminal extract it on the terminal itself and after that I typed exit.

Ok, lets see if there is a blacklist file ```
cat /etc/modprobe.d/* | grep bcma
``` and ```
ls /etc/modprobe.d/
```

---

### Post by marc49 on 2015-02-24
[Solved][]hi' jeremy31 thank you very much for your help my wifi and ethernet are now both working after some reboot and after this code
sudo apt-get purge bcmwl-kernel-source thank and god bless

how can i mark this a solved?

---

### Post by jeremy31 on 2015-02-24
Thread tools is near the top of the page and it will let you mark as solved

---

