---
title: "No wired connection after fresh install of 7.10"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by Chris1091 on 2007-12-20
Hey guys,

I'm a new user to Ubuntu (or any linux system), and I'm having a few problems getting network connectivity.  After a fresh install of gutsy, I'm getting no connectivity to the internet either through wired or wireless.  First things first, I would like to take care of the wired connection.

I ran all the download and disc checks before installing, all passed.  I installed with the ethernet connection plugged in.  I've also disabled IPv6, with the help of some users from the 'absolute beginner' forum.  Here's a copy of some of my commands as they stand now:

> chris@chris-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:08.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
01:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
03:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)




chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:1C:23:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:1C:10:F9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3082732 (2.9 MB)  TX bytes:22231 (21.7 KB)
          Interrupt:20 

eth0:avah Link encap:Ethernet  HWaddr 00:0E:A6:1C:23:26  
          inet addr:169.254.2.249  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21592 (21.0 KB)  TX bytes:21592 (21.0 KB)



chris@chris-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp





chris@chris-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      No scan results




chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  Nickname:"Broadcom 4301"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@chris-desktop:~$ 

I should also mention that the /etc/network/interfaces was modified.  It originally only had the lo portion, and I was advised to modify it in such way.  Also, the ethernet is connected to the Marvell adapter, and is ran hardwired through a Linksys WRT54G.  My other computer is also ran hardwired through this router, and is connected.  

I appreciate the help in advance,
Chris

---

### Post by ajmorris on 2007-12-20
hi,
first, the /etc/network/interfaces file should have all interfaces commented out, apart from lo.
Could you please try sudo ifup eth0, and post any output

then try, sudo dhclient eth0 and post any output.

---

### Post by Chris1091 on 2007-12-20
AJ, thanks for the quick response.  Here are the results from the commands:

> chris@chris-desktop:~$ sudo ifup eth0
[sudo] password for chris:
ifup: interface eth0 already configured



chris@chris-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0e:a6:1c:23:26
Sending on   LPF/eth0/00:0e:a6:1c:23:26
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
chris@chris-desktop:~$ 

---

### Post by tonytux on 2007-12-20
*bump*
my system was an upgrade form feisty to gutsy and am having the exact same problem, I use a lynksys router and have my LAN configured with staticIPs all around.  I believe it occured when the system asked for me to do an upgrade of about 133 pkgs directly after the initial upgrade,  but I'm not sure which one.  I also hae used various commands and config entries to dissable ipv6 with no relief of the problem in any sense

---

### Post by Chris1091 on 2007-12-20
Tony, hopefully someone will be able to chime in and help us out.  I haven't been asked to upgrade any packages.

---

### Post by tonytux on 2007-12-20
I  upgraded my distribution throught the automatic upgrades option on my system tray, and I obiviously still had connectivity when the distribution upgraded because it had me upgrade those 133 packages, and now it's telling me that I can upgrade 3 more packages but when I try to i'm told that I can't download them, which meand the pkg list was upgraded before the LAN's config was changed to the point of no connectivity.
right now I'm using a seperate install of feisty on a different HD on my tower so that I can take care of everything, I know that it isn't my network, cause everything works great here and on my wife's xp laptop and on my xbox-live, just a big no-go in gutsy....

---

### Post by darkrider2k6 on 2007-12-21
> **tonytux said:**
> I  upgraded my distribution throught the automatic upgrades option on my system tray, and I obiviously still had connectivity when the distribution upgraded because it had me upgrade those 133 packages, and now it's telling me that I can upgrade 3 more packages but when I try to i'm told that I can't download them, which meand the pkg list was upgraded before the LAN's config was changed to the point of no connectivity.
right now I'm using a seperate install of feisty on a different HD on my tower so that I can take care of everything, I know that it isn't my network, cause everything works great here and on my wife's xp laptop and on my xbox-live, just a big no-go in gutsy....

Are you having the same problem for both wired and wireless connections? If one works but not the other, it's possible that you might be having a driver issue.

---

### Post by Chris1091 on 2007-12-21
I just got my wireless working following VON_CAPO's instructions in this thread :thumbup:

[http://ubuntuforums.org/showthread.php?t=583052&highlight=enable+firmware+broadcom](http://ubuntuforums.org/showthread.php?t=583052&highlight=enable+firmware+broadcom)

still no wired connection though

---

### Post by darkrider2k6 on 2007-12-21
Since a driver installation fixed your wireless card, I suspect that your Marvell ethernet card might be fixed by a driver update as well. Have you looked around for any such thing?

---

### Post by tonytux on 2007-12-21
i only hvae a wired connection, but I will look for a driver to install for my "ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)" pci card, thank you for the idea...
ok tulip to the rescue, but nothing anywhere about tulip and the 2.6.20.xx kernel...any ideas? the tulip I found is for the 2.4.xx.xx kernel and doesn't compile for cr@p with my 2.6.20.xx
alas it's no use gutsy already has tulip driver

---

### Post by tonytux on 2007-12-21
finally!!

ok, I got it to work, but I had to do a few things, first off I had to reset my network rules as per this thread [http://ubuntuforums.org/showthread.php?t=604897]("http://ubuntuforums.org/showthread.php?t=604897") and then , even though I did it with firefox and through some other way which I can't remember but is easily found on these forms, got rid of IPv6 by black listing it completlely as per this article [http://www.lockergnome.com/linux/2007/10/24/ubuntu-gutsy-internet-help/]("http://www.lockergnome.com/linux/2007/10/24/ubuntu-gutsy-internet-help/")

the same author in that article has another one about how he had to choose between his wired connection and his wireless connection in gutsy...[http://www.lockergnome.com/linux/2007/11/27/ubuntu-wired-networking-woes-read-this-closely/]("http://www.lockergnome.com/linux/2007/11/27/ubuntu-wired-networking-woes-read-this-closely/")

i really thank you all for the input and hope that others could find these links as helpful as I did

---

