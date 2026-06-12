---
title: "[SOLVED] can't reconnect &amp;amp; renew IP lease after reboot"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Kvark on 2008-01-11
Ubuntu 7.10 can't connect to the wired network when rebooting from Ubuntu or from Windows XP without doing "ipconfig /release". On the other hand it connects flawlessly when the computer has been off for longer than the IP lease time or rebooting from Windows after doing "ipconfig /release". Windows can always connect without problems.

When Ubuntu connects during boot it can also reconnect with "sudo /etc/init.d/networking restart" or "sudo ifdown eth0 && sudo ifup eth0". When it didn't connect during boot those commands get the following errors:
```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Doing "sudo ifdown" or "sudo /etc/init.d/networking stop" before rebooting from Ubuntu didn't make any difference. The same with switching between roaming and DHCP mode. Uncommenting the reboot line in /etc/dhcp3/dhclient.conf made it keep it's previous public IP address after reboot instead of switching to a private/local address but it still couldn't connect. The only way I've found to reboot from Ubuntu to Ubuntu is to reboot to Windows to do "ipconfig /release" then reboot back to Ubuntu.

The computer is connected directly to an RJ45 outlet in the wall with a network cable. It receives a public IP address from the  ISP's DHCP server and then it's connected to the Internet. The network card is a Realtek RTL 8111C chip integrated into a Gigabyte GA-G31M-S2L motherboard, HAL Device Manager detects it as an RTL8111/8168B PCI Express Gigabit Ethernet controller.

---

### Post by spd106 on 2008-01-12
Going by the dhclient man page, it doesn't send a dhcp release by default. Instead you have to use the -r switch.

So that might be worth a try.

---

### Post by Kvark on 2008-01-12
That sounds like what I need but I still have the IP address after trying it so the command doesn't seem to do what the man page says. i tried "sudo dhclient -r eth0" too with the same result as below. Still can't connect after doing this and rebooting.
```
$sudo dhclient -r
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:7d:a2:c7:1c
Sending on   LPF/eth0/00:1d:7d:a2:c7:1c
Sending on   Socket/fallback
$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:A2:C7:1C  
          inet addr:85.228.72.120  Bcast:85.228.72.255  Mask:255.255.255.0
```
BTW, this makes me wonder, is the reason for not releasing the lease to reuse the same lease next time and if so why doesn't it manage to do that and why can Windows connect when Ubuntu hasn't released its lease?

---

### Post by Sandbox on 2008-01-15
I just cooked up a box with a gigabyte ga945gcm-2sl which has the 8111 chip. The sucker boots between ubuntu and XP. In XP it sees the NIC but in Ubuntu....I'm gettin exactly the same grief as you are. I tried rolling back to an older driver but the "makes" chucked up all over the place with errs. It's been a looooong time since I did stuff with U/X. That aside has anyone cracked this problem yet?
 Oh and another thing (slap me down like a cheap toilet seat if I'm out of order) I notice that the LED indicator lights don't come up on at either the host or the router......Soooo I dont reckon doing anything with DHCP will help.

---

### Post by Kvark on 2008-01-15
> **Sandbox said:**
> Oh and another thing (slap me down like a cheap toilet seat if I'm out of order) I notice that the LED indicator lights don't come up on at either the host or the router......Soooo I dont reckon doing anything with DHCP will help.
The network LED does flash for me even when I can't get a proper IP address, the device manager does list the network card and Ubuntu connects just fine when there is no currently active IP address lease so I think the out of the box network drivers work for me but are buggy. I put in a generic PCI network card and that one works perfectly all the time.

---

### Post by Sandbox on 2008-01-23
I've given up on the 8111c realtec NIC and chucked in an extra NIC. This ones uses the 8139 chipset. That works fine. Not the most elegant work round, but it does the job

---

