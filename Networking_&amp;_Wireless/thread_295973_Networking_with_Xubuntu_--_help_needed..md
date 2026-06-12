---
title: "Networking with Xubuntu -- help needed."
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Micro$oftWinblows on 2006-11-08
I've two computers, one is dual booting Ubuntu and Windows and the other is booting Debian and acts as a gateway for the internet via an ethernet adsl modem.

The friend who set Debian up years ago did a full install and so it's cluttered with crap which is slowing it down considering that particular computer is a Pentium II.

I booted up the Debian machine with Xubuntu and manage to connect to the internet using pppoeconf without any problems. 
However, the Ubuntu/Windows machine could talk to the Debian machine and vice versa, and so couldn't connect to the net. I tried to fiddle with the network settings while in Xubuntu but to no avail.

Windows/Ubuntu machine has the correct settings as follows:

eth0      Link encap:Ethernet  HWaddr 00:50:BF:4D:E9:FF  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe4d:e9ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5657 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2579788 (2.4 MiB)  TX bytes:681563 (665.5 KiB)
          Interrupt:10 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5866 (5.7 KiB)  TX bytes:5866 (5.7 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


The Debian machine which has the correct settings here, reads this:


eth0      Link encap:Ethernet  HWaddr 00:0E:2E:09:2D:40

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1570 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1615 errors:0 dropped:0 overruns:0 carrier:0

          collisions:6 txqueuelen:1000

          RX bytes:763700 (745.8 KiB)  TX bytes:220435 (215.2 KiB)

          Interrupt:10 Base address:0x1000


eth1      Link encap:Ethernet  HWaddr 00:50:BA:1D:D1:20

          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1471 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3457 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:197742 (193.1 KiB)  TX bytes:818191 (799.0 KiB)

          Interrupt:11 Base address:0x1400


lo        Link encap:Local Loopback

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:526 errors:0 dropped:0 overruns:0 frame:0

          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0

          RX bytes:29196 (28.5 KiB)  TX bytes:29196 (28.5 KiB)


ppp0      Link encap:Point-to-Point Protocol
 inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx Mask:255.255.255.255

          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1

          RX packets:1482 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1530 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:3

          RX bytes:724500 (707.5 KiB)  TX bytes:181321 (177.0 KiB)



As I mentioned before, when I boot up in Xubuntu on the Debian machine, I can connect to the internet fine with pppoeconf, but my two computers can't talk to each other and thus the Ubuntu/Windows computer has no internet.

In the network settings of Xubuntu there are eth0 and eth1, but what should their settings be? I can't just use DHCP because for some reason, it has never worked -- I've no idea why but that doesn't bother me and isn't a problem.

Help is much appreciated.

Thanks.

---

### Post by dermotti on 2006-11-10
Set your Xubuntu machine to the same network setting as your Debian  Machine


inet addr:192.168.0.1 Bcast:192.168.0.255 Mask:255.255.255.0

---

### Post by hans796 on 2006-11-11
I've got a computer running Xubuntu-desktop from Brezy Badger. This one is connected to the internet via ADSL and DHCP.

My second computer is running WinXP and is connected via my second ethernet card in the Xubuntu machine.

When I've done, i must get my second ethernet card running, cause it's not configured by default.

I go to /etc/network/interfaces sudo gedit /etc/network/interfaces 

And when i'm done it looks like this:

# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
	map eth1

# The primary network interface
iface eth0 inet dhcp

# The secondary network interface
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

After that i need to reboot.

After that i download firestarter (which is a firewall with built in internet connection sharing)

Run firestarter, config it..

Then i install samba

edit /etc/samba/smb.conf sudo gedit /etc/samba/smb.conf

Under Global Setting i check that workgroup are: MSHOME (or that both machine uses the same name)

Under Share Definitions i make these lines uncommented:

[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

Last i make a samba password:

sudo smbpasswd -a hans (write sudo passwrd than new samba password twice.

I always have the same username on both machines it really helps.

Then In WinXP

I make my useraccount password (same as samba)

The configure my Internet connection on XP:

IP: 198.168.0.2
Netmask: 255.255.255.0
Gateway:19.168.0.1
DNS: 195.67.199.18
DNS2: 195.67.199.19

Through trial and error and searching ubuntu forums i've got it working.

My Xubuntu machine shares it's internet connection with XP machine.
I can shuffle files back and forth.

Hope this might give you a clue, though i understand your problem is slight different.

Good Luck

---

### Post by hans796 on 2006-11-11
Sorry i  was in a hurry, noticed that XP Machine setting was wrong, should be:

IP: 192.168.0.2
Netmask: 255.255.255.0
Gateway:192.168.0.1
DNS: 195.67.199.18
DNS2: 195.67.199.19

Sorry..

---

