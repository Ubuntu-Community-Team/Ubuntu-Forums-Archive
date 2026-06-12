---
title: "Slow Ethernet"
date: 2019-04-23
forum: Networking &amp; Wireless
---

### Post by jeanmarc-louviaux on 2019-04-23
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I got an issue since 19.04 using kernel 5.0, it's ok with 4.18 though [/COLOR]#-o

[COLOR=#000000][I]jeanmarc@astrolabe:~$ sudo lshw -class [COLOR=#417394]network[/COLOR] *-network 
description: Ethernet interface
produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
fabriquant: Realtek Semiconductor Co., Ltd.
identifiant matériel: 0
information bus: pci@0000:03:00.0
nom logique: enp3s0
version: 16
numéro de série: e0:d5:5e:a7:59:ec
taille: 1Gbit/s
capacité: 1Gbit/s
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.0.26 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
ressources: irq:16 portE/S:3000(taille=256) mémoire:a3204000-a3204fff mémoire:a3200000-a3203fff
[/I]
[/COLOR]
[COLOR=#000000]Any tips ?
Thanks[/COLOR]

---

### Post by praseodym on 2019-04-23
Update the driver via
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/35/15/3005217-r8168-dkms-8.047.01.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.047.01.tar.gz -C /usr/src
sudo dkms add -m r8168 -v 8.047.01
sudo dkms build -m r8168 -v 8.047.01
sudo dkms install -m r8168 -v 8.047.01
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by jeanmarc-louviaux on 2019-04-24
Hi,
Sorry for late reply. I tried without sucess 8-[
I use a Realtek 8118.
thanks for your help, it is appreciated

---

### Post by jeanmarc-louviaux on 2019-04-26
hmm.. i got 22Mbps down on speedtest @1000 (i can reach up to 400Mbps)
If i **sudo ethtool -s enp3s0 speed 100 duplex full **i get ~92Mbps
What's wrong with my card ? :-s

---

