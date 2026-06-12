---
title: "Wifi issues on all linux machines, Dell Mini 9, Acer 3680, and Dell vostro 1500"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by Leprechaun7 on 2015-03-06
I have an ATT router that is B/G/N and an AP (running DD WRT) that is only G. The DD WRT AP has a stronger signal, which is part of the reason I want to connect to. I also don't like this problem to be lingering. Only the linux machines have wifi issues which are all running 14.10, the Vostro has KDE the other two are vanilla Ubuntu. The Vostro has B/G/N the other two computers have B/G. All of my windows machines and android devices connect fine to both wifi networks. All three linux machines connect fine to the ATT router but not to the DD WRT AP. Any thoughts? All machines have very different wifi cards, they're all internal.

---

### Post by Hadaka on 2015-03-06
Hi, there may be a common denominator, please do..
for each machine. Dell mini.del Vostro,acer in that
order please.
```
lspci -n | grep 0280 | awk '{print $3}'
```
and
```
lsmod | grep bcma| awk '{print $4}'
```
thanks

---

### Post by Leprechaun7 on 2015-03-06
lspci -n | grep 0280 | awk '{print $3}'

Mini
14e4:4315

Vostro
14e4:4328

Acer
no output



lsmod | grep bcma| awk '{print $4}'

Mini
no output

Vostro
b43

Acer
no output

---

### Post by Hadaka on 2015-03-06
please do..
Mini:
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

Vostro:
```
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install --reinstall firmware-b43-installer
sudo modprobe -rf b43
sudo mosprobe b43
```

Acer:
```
lspci -nnk | grep -iA2 net
```
reboot all three
any changes?

---

### Post by Leprechaun7 on 2015-03-07
I didn't think much of it but the linux machines seemed to lose connection to the ATT router more often in the past week or so.

mini 
no change, same problem

Vostro
no change, same problem

acer

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
	Subsystem: Acer Incorporated [ALI] Device [1025:0110]
	Kernel driver in use: sky2
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC [1468:0428]
	Kernel driver in use: ath5k

---

### Post by Hadaka on 2015-03-07
I dont think the problem is with the network configuration of the machines,
you mentioned trying to increase sgnal strength with using the dd wrt router
instead of the att. Access point distance seems to be the biggest problem.
check that your modem is not configure for TKIP if so please change it to
wpa2.

---

### Post by Leprechaun7 on 2015-03-07
First, thank you very much for your help.

So I simplified the situation, this is my parents hotel that I setup the wireles. It's and ATT router/modem conectec to DD WRT as an AP/router which is connected to three other 3com APs (all G only) connected to the DDWRT, the network on the ATT router and the APs are all no encryption. It's just so strange that all other devices, android, iphone and window connect to either network fine. All 3 linux systems don't, and they did when they had windows on them (the mini 9 was always ubuntu). It's a real shame trying to switch my folks over to linux and they're like, well windows worked fine why don't you put that back on.

---

