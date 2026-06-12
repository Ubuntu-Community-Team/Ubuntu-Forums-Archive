---
title: "Cannot connect to LAN"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by thangola on 2008-07-30
I have a strange error with my network connection, and after a day of trying to fix it, I've come here.

I use 2 OS on my PC, Ubuntu 8.04 and Windows XP. With WinXP, nothing happens and I can connect to both my network and the Internet. But with Ubuntu 8.04, there is a problem. I can't connect to my local network when I use static address. When I ping 127.0.0.1 or my LAN address, it's okie, but when I tried to ping my router (192.168.1.1), I received the error message: **Destination Host Unreachable**. DHCP also failed.

My NIC: Realtek RTL8139 10/100.

The /etc/network/interfaces file:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.1.219
  netmask 255.255.255.0
  broadcast 192.168.1.255
  gateway 192.168.1.1

What should I do to fix this problem?
Thanks for reading.

---

### Post by chili555 on 2008-07-30
> I use 2 OS on my PC, Ubuntu 8.04 and Windows XP.I suspect Windows is shutting down your ethernet card. Please check here: [http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/)

---

### Post by thangola on 2008-07-30
> **chili555 said:**
> I suspect Windows is shutting down your ethernet card. Please check here: [http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/)
Thanks. But I removed my Windows 2 days ago >.< . So what I should do for enabling the feature "Wake-on-lan after shutdown"?

---

### Post by chili555 on 2008-07-31
Please post the result of these commands:```
sudo lshw -C network
sudo ethtool eth0
```When you say you removed Windows, did you re-format and do a re-install?

---

### Post by mythms on 2008-08-03
I spent all of my free time for the past week chasing this problem down.  Ultimately the last thing that I changed to make it work was to place 'noapic' at the end of the kernel line in /boot/grub/menu.1st.  

As so...
```
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=82f63a28-3d98-4397-a3d1-be3f562314af ro quiet splash acpi=off noapic

```

I am fairly certain that I tried this earlier this week so the solution could involve some of the other things that I tried.  Another post had suggested that kernel parameter 'pci=noapic' was the solution.  Inspection of dmesg revealed that the kernel does not recognize 'pci=noapic'.  

Also notice that my kernel line has acpi=off.  There are several posts which suggest that acpi=off or noacpi will fix this problem.  It didn't help me network problem.  However, this parameter resolved several errors in my dmesg so I left it in.  (If I learned anything this week it is to address all errors in dmesg, first!)  I did go back and comment it out to see if it affected my network connection in any way.  My RTL8139 worked with and without the acpi=off parameter.

Some people are having trouble with the RTL8139 due to the Windows wake-on-lan driver setting.  At one point I installed WinXp on this machine and went in and modified the driver settings under 'Power Management' (Didn't actually find a 'Wake-on-Lan' check box in my WinXP driver dialog, but found something similar).  Also activated wake-on-lan in BIOS.  (It was called 'wol S4' with no explanation). Did these steps help?  Don't know.  Most of the posts regarding wake-on-lan sounded like the link lights were not lit up on the NIC.  My link lights were always on.  ethtool always reported that I had a link and 'arp' on another slackware10 server frequently would list my ip address and my hardware address.  Even with this level of connection is still could not ping from 192.168.2.6 to 192.168.2.5.

This change too might have helped:

sudo ethtool -s eth0 wol p


Other things I tried with no success:
[LIST]
[*] echo "blacklist 8139cp" >> /etc/modprobe.d/blacklist
[*] [INDENT]/etc/init.d/networking stop
   rmmod 8139too
   rmmod 8139cp
   modprobe 8139cp
   /etc/init.d/networking start][/INDENT]
[*] blacklisting ipv6 see [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/")
[*] all manner of edits to /etc/network/interfaces.  (What I ended up with is shown below)
[*] cycle power on all switches, routers and computers
[*] pre-up line in /etc/network/interfaces (I left it commented out in my final 'interfaces' file since I thought it might come in useful someday)
[*] adding a bogus 'eth1' section in /etc/networks/interfaces
[*] different cables
[*] different hub ports
[*] different hubs
[*] simplified network (mythbuntu<hub>winxp)
( Full network is: 3x winxp, 3x linux (slack10, ubuntu 7.10, mythbuntu 8.04), 1x w2k, 1x nokia770, 3xhubs, wireless router dsl modem combo on full network)
[/LIST]


My final /etc/network/interfaces (both static and dhcp now work, static is currently commented out):

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#  address 192.168.2.5
##  pre-up /usr/sbin/ethtool -s eth0 autoneg off wol p
#  netmask 255.255.255.0
#  gateway 192.168.2.1

```

My most difficult problems to are those for which there are multiple, overlapping causes.  I think that is the case here.

---

### Post by cariboo on 2008-08-03
Wake-on-lan is usually setup in the BIOS. the RTL8139 is a really old chip set I've had them working since Redhat 6.0 I beieve they use the ne module. I'll have to see if I've still got one in my junk box and see if I can get it running.

Jim

---

### Post by chili555 on 2008-08-03
> **cariboo907 said:**
> Wake-on-lan is usually setup in the BIOS. the RTL8139 is a really old chip set I've had them working since Redhat 6.0 I beieve they use the ne module. I'll have to see if I've still got one in my junk box and see if I can get it running.

JimIn fact, it works with the module *8139too*. Here is my wife's machine:>  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       ---snip---
       logical name: eth0
       ---snip---
       driver=8139too driverversion=0.9.28 
       ---snip---Works beautifully here, but we specialize in old things!

---

### Post by thangola on 2008-08-10
I did as in this TUT and the problem was solved. Thanks to all for help.

---

