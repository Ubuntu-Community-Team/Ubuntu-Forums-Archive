---
title: "Wireless not found"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by savvasgr on 2008-08-21
hello to all

I have the exist problem in my Network settings I haven't Wireless connection to choose or to configure. How can I appear the wireless network. My Wired network works perfect.



lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 13
       serial: 00:11:2f:a3:10:52
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A ip=192.168.0.4 latency=64 maxlatency=31 mingnt=23 module=skge multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=28 m

---

### Post by pytheas22 on 2008-08-21
This card should be supported by madwifi.  Which version of Ubuntu are you using (8.04 or something older)?

Please post the output of these commands (in this order) so that we can figure out why the card isn't being recognized:

```
lspci -nn | grep -i atheros
lsmod | grep ath
sudo modprobe ath_pci
iwlist scan
modinfo ath_pci | grep version
uname -m
```

With that information we can tell you a solution.

---

### Post by savvasgr on 2008-08-22
Hello i'm using Ubuntu 8.04
                
when I'm give your commands.

savvas@savvas-desktop:~$ lspci -nn |grep -i atheros
02:0a.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
savvas@savvas-desktop:~$ lsmod |grep ath
savvas@savvas-desktop:~$ sudo modprob ath_pci
[sudo] password for savvas: 
sudo: modprob: command not found
savvas@savvas-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

savvas@savvas-desktop:~$ modinfo ath_pci |grep version
modinfo: could not find module ath_pci
savvas@savvas-desktop:~$ uname -m
i686
savvas@savvas-desktop:~$

---

### Post by savvasgr on 2008-08-22
Finally I reinstalled the umbutu and the problem fixed.

---

