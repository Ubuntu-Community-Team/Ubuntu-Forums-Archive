---
title: "[PROBLEM] static ip on wifi connection freezes the pc"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by skann3r on 2015-05-08
Hi guys, a couple of days ago I've bought a pci express wifi card, an asus pce-ac68 based on Broadcom BCM4360 chipset, everything works good using dhcp but if I try to set a static ip address my pc freezes,  mouse won't responde and scroll/num lock leds on the keyboard starts blinking so i have to hard reset the computer, do you have any idea? Thanks so much!

---

### Post by SeijiSensei on 2015-05-08
1)  Make sure some other machine doesn't already have that address.

2)  Choose an address that is outside the range of addresses the router manages with DHCP.  For instance, if the router hands out addresses between 10.10.10.10 and 10.10.10.100, choose a static address < .10 or > .100.

---

### Post by skann3r on 2015-05-08
> **SeijiSensei said:**
> 1)  Make sure some other machine doesn't already have that address.

2)  Choose an address that is outside the range of addresses the router manages with DHCP.  For instance, if the router hands out addresses between 10.10.10.10 and 10.10.10.100, choose a static address < .10 or > .100.

No ip collisions and tried changing the range of the dhcp excluding my desired ip, nothing changes.
 I've also tried disabling network-manager and configuring manually the ip in /etc/network/interfaces, still freezes.
The only workaround i've found is to tie the mac address of my wifi card with my desired ip address in the dhcp pool table on my router...

---

### Post by SeijiSensei on 2015-05-08
Does it freeze the GUI interface or the whole machine?  Can you ping the machine from another on the network while frozen?  If the machine has openssh-server installed, can you connect with SSH from another machine even if your machine appears frozen?

Do you see any errors in /var/log/syslog when the network comes up?

I assume you have the correct netmask and broadcast address in /etc/network/interfaces.

---

### Post by skann3r on 2015-05-11
> **SeijiSensei said:**
> Does it freeze the GUI interface or the whole machine?  Can you ping the machine from another on the network while frozen?  If the machine has openssh-server installed, can you connect with SSH from another machine even if your machine appears frozen?

Do you see any errors in /var/log/syslog when the network comes up?

I assume you have the correct netmask and broadcast address in /etc/network/interfaces.

It seems the machine totally freezes, can't ping nor ssh it!

in /var/log/syslog i found no particular errors before it shows (in red)
```
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```
then it report a system startup (i think all that 00\ appears on crash, then i force the system off/on)

I have the correct configuration in /etc/network/interfaces or in network_manager, i've tried both way, i really can't see a solution because of few to none information from the system for the reason of a total freeze, i've never freezed an ubuntu machine like this before!

---

### Post by ftp30 on 2015-05-22
I have the same exact prob with Apple Macbook pro Retina mid 2014.  Same drivers, same configuration, with static IP it freezes, with DHCP it works...

---

### Post by Nikhil_Verma on 2015-09-08
Even I have the same problem since I upgraded to 15.04. I use a BCM43142 chipset with bcmwl-kernel-source. Whenever I connect to the network using a static ip, my Ubuntu crashes. The only way out is a hard reset. Please help.

---

### Post by jaseem2 on 2015-10-30
Please help me too. Static ip is freezing my Dell Inspiron 1536 with Broadcom 802.11n network adapter in both 15.04 and 4.04 LTS versions. Please help

---

