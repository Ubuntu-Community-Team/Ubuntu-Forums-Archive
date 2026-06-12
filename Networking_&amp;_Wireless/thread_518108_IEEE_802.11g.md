---
title: "IEEE 802.11g"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by hobojjr on 2007-08-05
I have ubuntu 5.10 installed on an old pc (it's so old that I can't get the latest version of ubuntu on it). It also has IEEE 802.11g wireless card in it. Can someone help me get to the internets with it??? Thanks.

---

### Post by tgm4883 on 2007-08-05
What kind of computer?  I have trouble helping you install a wireless card on an unsupported (discontinued) version of Ubuntu.  You may not even be able to install things on it.

What is this computer that wont install newer versions?  Perhaps we can fix that.

---

### Post by hobojjr on 2007-08-05
well I think it has 1999 mother board (at least thats what it told me when I tried to install the latest ubuntu which has 2000 MB cut off) and a p3 ~500 MHZ cpu.

---

### Post by tgm4883 on 2007-08-05
Was that just a warning?  Is there a bios update for your computer?  There shouldn't be an issue installing Ubuntu on old computers.  

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by hobojjr on 2007-08-06
I'm not sure. It also said acpi = force is required enabled along with the bios age being 1999. I've never dealt with installing linux os. So what this all means is beyond normal human comprehension. Hopefully, you will not tell me to recompile the kernel.

Here is some info from the initial screen at boot time:

ACUS F 38-F ACPI BIOS Revision 1003
Award Plug and Play Bios Extension V1.0A

---

### Post by tgm4883 on 2007-08-06
Were you able to boot into the feisty live cd or not?'

We'll get this thing installed, one way or the other

---

### Post by hobojjr on 2007-08-06
yes it tries to install but then it gets some permission denied errors and some other errors and it dies.

Here are some screen shots of the installation:

[IMG]http://i83.photobucket.com/albums/j305/hobojjr/one.jpg[/IMG]

[IMG]http://i83.photobucket.com/albums/j305/hobojjr/two.jpg[/IMG]

[IMG]http://i83.photobucket.com/albums/j305/hobojjr/three.jpg[/IMG]

Here you can see Bios is 1999 and it wants acpi = force enabled
followed by "permission denied" error
[IMG]http://i83.photobucket.com/albums/j305/hobojjr/four.jpg[/IMG]


And here is the final errors before it dies.

[IMG]http://i83.photobucket.com/albums/j305/hobojjr/five.jpg[/IMG]

---

### Post by tgm4883 on 2007-08-06
First, have you tried the CD on any other computers to make sure the CD works?

Next, what brand/model is your computer?  If it's built, open it up and see if the motherboard has any brand name/model on it

---

### Post by hobojjr on 2007-08-06
Haven't tried the cd on any other pc. Live cd gives the same kind of errors.
The motherboard brand is ASUS P3(8 or B can't tell for sure)-F

---

### Post by tgm4883 on 2007-08-06
its p3b-f

Lets do this first, we need to make sure we have a good cd

So you need to check the iso you downloaded with it's md5sum.  Once that checks out, you can burn the cd (at the lowest speed possible).  Make sure to verify the cd after it is burnt.

Once that is done, pop the cd in and at the boot options screen hit F6 and type acpi=force at the end of the line.

That should allow you to boot up and install.

If you run into the same problems, instead of acpi=force do acpi=off

---

### Post by hobojjr on 2007-08-06
don't have a blank cd right now, but how do you verify the md5 stuff?

---

### Post by tgm4883 on 2007-08-06
[http://www.irnis.net/gloss/md5sum-windows.shtml](http://www.irnis.net/gloss/md5sum-windows.shtml)

Looks like you might be able to verify the cd you burned

---

### Post by hobojjr on 2007-08-06
the standard defect check found some errors in 4 files.... I guess I need to get some new cds... thanks

---

### Post by hobojjr on 2007-08-07
Ok I burned a new disk and installed the latest Ubuntu. It sees my wireless network but for some reason it can't connect to it. I enter the key and all but it just wont connect. The key is correct and there are open slots for it to connect to.

---

### Post by hobojjr on 2007-08-07
Now it appears to be connected as it shows the connection bars at 44% but I still have no internet. When I try to do ping on [http://www.google.com](http://www.google.com) it tells me unknown host and when I try to open firefox it tells me "server not found"

---

### Post by hobojjr on 2007-08-08
Looks like its not getting ip .... wtf?

---

### Post by tgm4883 on 2007-08-08
you can use dhclient to get an ip

---

### Post by hobojjr on 2007-08-08
Ok... frack... it messed up again..

The wireless card blinks some few seconds and I have internet for few seconds but then it dies... no more blinking and no more internet... wtf??

---

### Post by hobojjr on 2007-08-08
So as I said before. I can get an ip if I execute sudo dhclient right after I connect to the network. However, after like half a minute the light on the wireless cards goes away and so does the internet. Any ideas why???

---

### Post by hobojjr on 2007-08-11
hello? Any body?

---

### Post by hobojjr on 2007-08-14
So, I've disabled networking in the networkmanger and then I unchecked the wiredcards in the network manager in system administrator. Then I checked the wireless network and unchecked the roaming mode. After entering the my personal wireless network information the cards seems to be connected to something, or at least the green light on the cards doesn't go away!!!

However, STILL NO INTERNET!!!! :(


Here some longs:

-----------------------------------------

 sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 7520
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:d0:41:f7:b1:58
Sending on   LPF/ra0/00:d0:41:f7:b1:58
Listening on LPF/eth1/00:80:c6:f7:fe:05
Sending on   LPF/eth1/00:80:c6:f7:fe:05
Listening on LPF/eth0/00:48:54:64:a6:3e
Sending on   LPF/eth0/00:48:54:64:a6:3e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


-----------------------------------------

sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 10
       serial: 00:48:54:64:a6:3e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:d000-d0ff iomemory:d5800000-d58000ff irq:5
  *-network:1
       description: Ethernet interface
       product: MX987x5
       vendor: Macronix, Inc. [MXIC]
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 20
       serial: 00:80:c6:f7:fe:05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: ioport:b000-b0ff iomemory:d4800000-d48000ff irq:9
  *-network:2
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: c
       bus info: pci@00:0c.0
       logical name: ra0
       version: 01
       serial: 00:d0:41:f7:b1:58
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=32 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:d4000000-d4001fff irq:11
user@user-desktop:~$ clear

user@user-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 10
       serial: 00:48:54:64:a6:3e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:d000-d0ff iomemory:d5800000-d58000ff irq:5
  *-network:1
       description: Ethernet interface
       product: MX987x5
       vendor: Macronix, Inc. [MXIC]
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 20
       serial: 00:80:c6:f7:fe:05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: ioport:b000-b0ff iomemory:d4800000-d48000ff irq:9
  *-network:2
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: c
       bus info: pci@00:0c.0
       logical name: ra0
       version: 01
       serial: 00:d0:41:f7:b1:58
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=32 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:d4000000-d4001fff irq:11


-----------------------------------------

 lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 02)
00:0b.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 20)
00:0c.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

-----------------------------------------

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"ghome"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:12:17:26:D2:2D   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=59/100  Signal level=-59 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



-----------------------------------------

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:48:54:64:A6:3E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:80:C6:F7:FE:05  
          inet6 addr: fe80::280:c6ff:fef7:fe05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:233 dropped:0 overruns:0 carrier:233
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xb000 

eth0:avah Link encap:Ethernet  HWaddr 00:48:54:64:A6:3E  
          inet addr:169.254.5.235  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0xc000 

eth1:avah Link encap:Ethernet  HWaddr 00:80:C6:F7:FE:05  
          inet addr:169.254.9.3  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36993 (36.1 KiB)  TX bytes:36993 (36.1 KiB)

ra0       Link encap:Ethernet  HWaddr 00:D0:41:F7:B1:58  
          inet6 addr: fe80::2d0:41ff:fef7:b158/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43606 errors:1 dropped:1 overruns:0 carrier:0
          collisions:19 txqueuelen:1000 
          RX bytes:10432 (10.1 KiB)  TX bytes:1787584 (1.7 MiB)
          Interrupt:11 Base address:0x4000 

ra0:avahi Link encap:Ethernet  HWaddr 00:D0:41:F7:B1:58  
          inet addr:169.254.8.180  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x4000 



-----------------------------------------

---

### Post by hobojjr on 2007-08-14
Ok, I've rebooted and it seems to be working!

In fact,  I posted it from ubuntu!!! Horay!!!

Randomness for the win!

---

