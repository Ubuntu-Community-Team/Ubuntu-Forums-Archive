---
title: "eth0 disabled - new install of Ubuntu 14.10"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by joel33 on 2015-02-15
Hi all,

New to Ubuntu

I have recently completed a new install of Ubuntu 14.10 but the eth0 is not working.
An *ifconfig *does not show it **but **an *ifconfig-a *does show it. When i run the *sudo lshw -C network *command, it tells me it is disabled.

I am new to this and have spent days trawling the net looking for the solution...please help!!

Thanks in advance!

---

### Post by chili555 on 2015-02-15
> When i run the *sudo lshw -C network* command, it tells me it is disabled.May we see the exact output, please?

---

### Post by joel33 on 2015-02-16
Hi Chilli555
Thanks for replying...see below

joel@joel-ubuntu:~$ sudo lshw -C network
[sudo] password for joel: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:5e:50:4c:23
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.16.0-23-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:93500000-9350ffff
  [B]*-network DISABLED
       description: Ethernet interface[/B]
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:92500000-9250ffff

---

### Post by chili555 on 2015-02-16
Please plug in a known good ethernet cable, click the Network Manager icon and ask your wireless to disconnect and then run:```
cat /var/log/syslog | grep -e eth0 -e r8169 | tail -n25
```Post the result here:  [http://paste.ubuntu.com](http://paste.ubuntu.com)  and give us the link in your reply. Thanks.

---

### Post by joel33 on 2015-02-17
Sorry for late reply

See link

[http://paste.ubuntu.com/10271052/](http://paste.ubuntu.com/10271052/)

---

### Post by chili555 on 2015-02-17
Verrrry interesting!> device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]Are you running Network Manager or Wicd or (yuck!) both? What is in this file?```
cat /etc/network/interfaces
```I love a mystery. And by 'love' I mean 'hate.'

---

### Post by joel33 on 2015-02-18
haha I would call it a 'love/hate' relationship.

When i run:
```
cat /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by chili555 on 2015-02-18
So far, I see nothing wrong; that is, fixable.> Are you running Network Manager or Wicd or (yuck!) both? Let's see:```
ps aux | grep -i -e wicd -e network
```Thanks.

---

### Post by joel33 on 2015-02-19
I believe I am only running Network Manager, but i could be wrong. Have been many times in the past.

[http://paste.ubuntu.com/10304953/](http://paste.ubuntu.com/10304953/)

---

### Post by chili555 on 2015-02-20
You are running only Network Manager; that's good as no potential conflicts arise. Please run:```
cat /etc/NetworkManager/NetworkManager.conf
```We hope it says:```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=XX:DE:F1:3E:B2:XX,

[ifupdown]
[COLOR="#FF0000"]managed=false[/COLOR]

```If it does not, please do:```
gksudo gedit /etc/NetworkManager/NetworkManager.conf 
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the managed= to read as above. Proofread carefully, save and close the text editor. Restart NM:```
sudo service network-manager restart
```Does it still show as disabled?```
sudo lshw -C network
```If you have a no-auto listing, may we see it?

---

### Post by joel33 on 2015-02-26
Sorry for the long delay. Haven't had a chance to get back to fault finding, although i think i have a oneway ticket to frustration station haha

I ran the 
```
cat /etc/NetworkManager/NetworkManager.conf
```

and received

```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
```

I restarted NM anyway but the eth0 is still disabled.

---

