---
title: "Turning my ubuntu laptop into a wireless hotspot"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by shabs on 2008-10-14
Hi, 
I'm running ubuntu 8.04 and I have a built-in wireless card. I would like to let my friend (running vista) access internet from my laptop. I'm connected to a wired connection. How can I do that?
In netowrk manager there is an option that says "Create New Wireless Network", when clicked it asks me to enter a network name and gives me options for wireless security. Once thats entered I network manager icon starts revolving around like its trying to connect to a network and then nothing happens. My friend still does not see my network in his list of wireless networks. Roaming mode is enabled.

---

### Post by ScottHW on 2008-12-06
Sorry to say, but I don't think this is going to go like you'd hoped.

I do know that years ago, I used two WinXP computers, wired together, to "Share an internet connection".

Perhaps you are trying to create an "Ad-hoc network"...?
Here's a summary (Windows specific)
[http://www.dslreports.com/forum/remark,13301334](http://www.dslreports.com/forum/remark,13301334)

If more completely describe your physical hardware and connections situation, perhaps someone might be able to help you accomplish what you want.

---

### Post by shabs on 2008-12-22
Hey Scott,
I was infact trying to create an 'Ad-hoc network' which I have not been successful with yet. I'm posting the output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Does this help?

---

### Post by iponeverything on 2008-12-22
Its pretty strait forward to setup an ad-hoc network and share it:

If your wireless interface is eth1

For:
/etc/network/interfaces

```

auto eth1

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
wireless-essid Home
wireless-mode Ad-Hoc

```


for:
/etc/rc.local

```

iptables -t nat -A POSTROUTING -s  192.168.1.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
exit 0

```

Staticly IP the XP machine on a 192.168.1.x address with a 255.255.255.0 netmask a 192.168.1.1 gateway. You have the XP machine use the opendns servers. Or setup a dhcp server on the linux machine.

---

