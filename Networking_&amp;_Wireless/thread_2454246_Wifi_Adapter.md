---
title: "Wifi Adapter"
date: 2020-11-25
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2020-11-25
I've been using Ubuntu for about 5 years.  I've now upgraded to Ubuntu 20.04.2 :TS.  I have this [USB WiFi Adapter 1750Mbps,USB 3.0 Wireless Network WiFi Dongle with Dual 5dBi Antenna, 802.11ac Dual Band 2.4GHz/5.8GHz]("https://www.newegg.com/p/0XM-015B-00002?Item=9SIAJPZ97T0026") that is plug and play on Windows 10 Pro, but I can't get it going on Ubuntu.  It came with a disk that has a folder called :LINUX".  In the folder are two other folders and a file called install.sh .  I take it I just change directly to the disc and write in terminal, [COLOR=#000000]sudo ./install.sh ?[/COLOR]

---

### Post by jeremy31 on 2020-11-26
Please post results from terminal for ```
lsusb
```
Chances are that the drivers on the disk are made for an ancient kernel

---

### Post by shane_faulkinbury2 on 2020-11-26
Okay, I ran lsusb and here is what I got.```
[COLOR=#4E9A06]**none@none-OptiPlex-3020**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ lsusbBus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 0bda:8813 Realtek Semiconductor Corp. RTL8814AU 802.11a/b/g/n/ac Wireless Adapter
Bus 003 Device 003: ID 046d:c33c Logitech, Inc. G513 RGB MECHANICAL GAMING KEYBOARD
Bus 003 Device 008: ID 1050:0407 Yubico.com Yubikey 4 OTP+U2F+CCID
Bus 003 Device 002: ID 04f9:02e9 Brother Industries, Ltd MFC-J475DW
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [COLOR=#4E9A06]**none@none-OptiPlex-3020**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ 
```

---

### Post by CelticWarrior on 2020-11-26
[https://askubuntu.com/a/1185986](https://askubuntu.com/a/1185986)

---

### Post by shane_faulkinbury2 on 2020-11-26
Much appreciated CelticWarrior, that worked perfectly.  I'm using wifi now!

---

### Post by CelticWarrior on 2020-11-26
Don't thank me me, thank Jeremy31, it's his answer.
But please use the thread tools to mark it solved.

---

### Post by shane_faulkinbury2 on 2021-01-24
Hey all, I know this thread is Solved, but I do a lot of reinstalls and now I get this.  Any solutions?

```
OptiPlex-3020:~/rtl8812au$ sudo ./dkms-install.shsudo: ./dkms-install.sh: command not found



```

---

### Post by jeremy31 on 2021-01-24
Shane, they changed the code on the github, try ```
sudo make dkms_install
```

---

### Post by shane_faulkinbury2 on 2021-01-24
Never mind, I solved it with this.  
```
[FONT=Consolas]sudo make dkms_install[/FONT]
```

---

