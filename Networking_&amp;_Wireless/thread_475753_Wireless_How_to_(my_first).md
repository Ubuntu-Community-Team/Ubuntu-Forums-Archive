---
title: "Wireless How to (my first)"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by matoxxx on 2007-06-16
Hi everyone, who s having headache with setting up your wireless right.
After some researches i have set up a way i can use wireless in every release of ubuntu.
If it can help you, you are welcome...

[SIZE="4"]1.Your wifi card must be detected by ubuntu ...[/SIZE]
```
lspci
```
mine 
```
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```

[SIZE="4"]2.Your card has the right drivers ?[/SIZE]
```
sudo lshw -class network
``` (thanks to spd106)
mine 
```
matoxxx@matoxxx-desktop:~$ sudo lshw -class network
Password:
  *-network               
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@02:02.0
      ** logical name: eth0**
       version: 01
       serial: 00:60:b3:64:6d:9f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=orinoco driverversion=0.15** firmware=Intersil 1.7.4 ip=192.168.1.113 latency=128 link=yes multicast=yes wireless=IEEE 802.11b

```
if not install them ..(you can find tons of howto s in forums for almost every kind of card)
after installation blacklist all other unnecessary drivers that might interact with your card in /etc/modprobe.d/blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```
in my case i had to blacklist hostap // hostap_pci // prism2_pci //
to get orinoco_pci drivers work

dont forget to remember the logical name of your card (bold) you will need it in next step

[SIZE="4"]3. Edit /etc/iftab for your network interfaces (just for sure , if its set up right)[/SIZE]
```
sudo gedit /etc/iftab
```
check if logical name of your wireless card is shown there with your MAC address
like mine 
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

**eth0** mac 00:60:B3:64:6D:9F arp 1
```
if not fill it with your values ...(thanks to dbott67)

[SIZE="4"]4. Edit /etc/network/interfaces[/SIZE] to fill information about network and WEP keys to the right logical name of your wireless card in my case eth0
```
auto eth0
iface eth0 inet static
address *your_ip*
netmask *255.255.255.0*
gateway *your_gateway*
wireless-essid *your_essid*
wireless-key/1,2,3,4/ *your_key*
wireless-defaultkey /1,2,3,4/
```

the wireless-key/xyz/ entry is a small hack, if you are using other WEP key index than the default first one (thanks to dulljeff)

[SIZE="4"]5. Set up your DNS server or fill the DNS entry and weee, internet is working :p[/SIZE]

I hope i wrote it as briefly as i could ... have networking fun ;)

PS: Please post comments if i made everything right ...

---

### Post by Paris Heng on 2008-04-06
Greats!

---

### Post by kevdog on 2008-04-06
There is no iftab file any longer for Gusty or Hardy.  This part of the tutorial will not be accurate for much longer since 6.06 will no longer be supported once Hardy -- the new LTS is released.

---

### Post by matoxxx on 2008-05-06
Uh, ok then, if iftab isnt to be working just assign wireless configuration to every interface in /etc/network/interfaces and the system will choose the right working one :)

i know its not the clean way, but still with this workaround i have no problems with wireless networking:popcorn:

---

