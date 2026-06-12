---
title: "Cant connect to internet with a wired Realtek 8139 nic card"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by connel on 2008-09-12
hi i have an old laptop that i have installed xbuntu on. However i cant connect to the internet.

Here are my results for lspci:

```
jiggah@jannah-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
02:09.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:09.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)

```

Here are my results from ifconfig:
```
jiggah@jannah-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:e2:7e:3c:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11140 (10.8 KB)  TX bytes:11140 (10.8KB)
```

Here is the network section of the results for

$sudo lshw -html > your-file-name.html:

```
id: network 
description:  Ethernet interface 
product:  RTL-8139/8139C/8139C+ 
vendor:  Realtek Semiconductor Co., Ltd. 
physical id:  5 
bus info:  pci@0000:02:05.0 
logical name:  eth0 
version:  10 
serial:  00:00:e2:7e:3c:23 
size:  100MB/s 
capacity:  100MB/s 
width:  32 bits 
clock:  33MHz 
capabilities:  pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation = on 
broadcast = yes 
driver = 8139too 
driverversion = 0.9.28 
duplex = full 
latency = 66 
link = no 
maxlatency = 64 
mingnt = 32 
module = 8139too 
multicast = yes 
port = MII 
speed = 100MB/s
```


pleaaase help me :)

---

### Post by pytheas22 on 2008-09-12
Try running:
```

sudo rmmod 8139cp
sudo modprobe 8139too
sudo dhclient eth0
```

If it's successful, you will be assigned an IP address and be able to connect to the Internet.

If that doesn't work, what about:
```

sudo rmmod 8139too
sudo modprobe 8139cp
sudo dhclient eth0
```

Please let me know if the above helps.  If not, please post the output of:
```

lspci -nn | grep -i ethernet
dmesg | grep -e 8139 -e eth0
```

---

### Post by connel on 2008-09-12
hi thanks for such a quick response :)

erm heres what i got when i tried the commands in your previous post:

```
jiggah@jannah-laptop:~$ sudo rmmod 8139cp
jiggah@jannah-laptop:~$ sudo modprobe 8139too
jiggah@jannah-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:00:e2:7e:3c:23
Sending on   LPF/eth0/00:00:e2:7e:3c:23
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jiggah@jannah-laptop:~$ sudo rmmod 8139too
jiggah@jannah-laptop:~$ sudo modprobe 8139cp
jiggah@jannah-laptop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 5940
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
jiggah@jannah-laptop:~$ lspci -nn | grep -i ethernet
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
jiggah@jannah-laptop:~$ dmesg | grep -e 8139 -e eth0
[   21.732321] 8139too Fast Ethernet driver 0.9.28
[   21.734823] eth0: RealTek RTL8139 at 0x7000, 00:00:e2:7e:3c:23, IRQ 10
[   21.734827] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   21.776427] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   82.297379] eth0: link down
[  122.071214] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1054.659466] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 1054.660315] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[ 1054.660323] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
jiggah@jannah-laptop:~$ dmesg | grep -e 8139too -e eth0
[   21.732321] 8139too Fast Ethernet driver 0.9.28
[   21.734823] eth0: RealTek RTL8139 at 0x7000, 00:00:e2:7e:3c:23, IRQ 10
[   21.734827] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   82.297379] eth0: link down
[  122.071214] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1054.660323] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
jiggah@jannah-laptop:~$ 

```
thanks again

---

### Post by pytheas22 on 2008-09-12
There seems to be some issues with the drivers.  What does this do:
```

echo 'blacklist 8139cp' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod 8139too
sudo rmmod 8139cp
sudo modprobe 8139too media=0x01
sudo dhclient eth0
```

If that doesn't work, you can try adding the acpi=off option to your boot menu ([this thread]("http://ubuntuforums.org/showthread.php?t=91746") says that that fixes the issue).  To do that, first open up your grub menu by typing:

```
mousepad gedit /boot/grub/menu.lst
```

Scroll down through the file until you find a section that looks similar to this:

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

(There may be several sections, depending on how many kernels you have installed on your system. Each entry corresponds to a different line in the grub boot menu that you see when you first start your computer.)

Add the "acpi=off" option to the end of the "kernel" line as below:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash **acpi=off**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Then you can save and close the file. Reboot your computer, and make sure you select the kernel entry at the grub boot menu that corresponds to the one that you just changed (probably the one at the top of the list).

Please let me know if this helps.

---

### Post by connel on 2008-09-13
hi thanks again for the quick reply. the laptop is actually my girl friends and i was jus trying to get it to connect to my own network at home before i gave it back to her. how ever when i brought it round hers today the card seemed to work fine :S

how ever i have a new problem :) lol

she has a BTHomeHub and it is sayin the wired network is proected and i dont no what to write as the password. i have tired using the wireless key to no availe. if the forums admin would prefer i will create a new thread for this problem

thanks inadvance

---

### Post by pytheas22 on 2008-09-13
I'm glad the first issue is solved.  I don't know anything about encrypting wired connections so I'm not sure what to tell you for the second problem.  I know that if you click on the Network Manager icon, you have an option to "Connect to 802.1X Protected Wired Network," so I suppose that's where you have to enter the configuration information.  But I think you need more than just a password--it looks like you need a certificate and stuff, which is a lot more complicated than just connecting to a normal home WEP or WPA-secured wireless network.  The only advice I can give you is to look at how the computer is configured in Windows and/or the instructions on how to configure it in Windows, if available; probably the certificates and stuff that you need will be there somewhere.

You should also probably start a new thread so that you'll get more attention for your new problem from people who can help better than I.

---

### Post by connel on 2008-09-13
kk thanks for your help

---

### Post by caddict on 2008-09-17
hi pytheas (or anyone)

i have a similar problem. I've tried all your suggestions (plus a hundred others) with no luck. 

this is a fresh install of 8.04 onto a new hdd dual booting with xp on another hdd. i connect to the internet through a d-link dsl-504g router. all works perfectly on this computer with windows and on my other computer with windows and a 8.04 upgrade.

i seem to have 2 problems
  some issue with the 8139 card / driver
  not knowing what settings to use in etc/network/interfaces

lspci -nn | grep -i ethernet shows the realtek rtl 8139/8139c/8139c+ card

dmesg | grep -p 8139 -e eth0 seems to find both the cp and the too driver even though i have blacklisted the cp driver

i have set acpi=off as you described...still nothing.

any ideas?

---

### Post by pytheas22 on 2008-09-18
> hi pytheas (or anyone)

i have a similar problem. I've tried all your suggestions (plus a hundred others) with no luck.

this is a fresh install of 8.04 onto a new hdd dual booting with xp on another hdd. i connect to the internet through a d-link dsl-504g router. all works perfectly on this computer with windows and on my other computer with windows and a 8.04 upgrade.

i seem to have 2 problems
some issue with the 8139 card / driver
not knowing what settings to use in etc/network/interfaces

lspci -nn | grep -i ethernet shows the realtek rtl 8139/8139c/8139c+ card

dmesg | grep -p 8139 -e eth0 seems to find both the cp and the too driver even though i have blacklisted the cp driver

i have set acpi=off as you described...still nothing.

any ideas?

What is the 'lspci -nn | grep -i ethernet' output for your card?  Maybe if we google it we'll come up with something.  Also did you look at the output of:
```

dmesg | grep -e 8139 -e eth0
```

It might provide useful information (like tell you whether you need to use 8139cp or 8139too for your card).

---

### Post by caddict on 2008-09-18
Thanks pytheas

here is the output you asked for.

```
steve@foxy:~$ sudo lspci -nn | grep -i ethernet
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

steve@foxy:~$ sudo dmesg | grep -e 8139 -e eth0
[   17.038246] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.531992] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   17.531998] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
[   17.535380] 8139too Fast Ethernet driver 0.9.28
[   18.547421] eth0: RealTek RTL8139 at 0xa000, 00:00:00:00:00:00, IRQ 23
[   18.547424] eth0:  Identified 8139 chip type 'RTL-8101'
[  209.631215] 8139too Fast Ethernet driver 0.9.28
[  209.633002] eth0: RealTek RTL8139 at 0xa000, 00:00:00:00:00:00, IRQ 23
[  209.633007] eth0:  Identified 8139 chip type 'RTL-8101'
```

lsmod shows the 8139too driver to be present but not 8139cp.

Also, since posting first I have upgraded to the latest windows realtek driver and enabled "wake on LAN"

Strangely though, since doing that I no longer see a light on the router (port 4) when ubuntu is running. It is there when windows is running. 

I've read so many threads on this topic that I'm pretty confused now!

---

### Post by pytheas22 on 2008-09-18
It looks like the ethernet interface is being brought up with a bogus MAC address (00:00:00:00:00:00).  I've seen this once before, and spoofing to a more legitimate MAC solved the problem.  What happens if you type (please post all output):
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up hw ether 01:23:45:67:89:01
sudo dhclient eth0
dmesg | tail
ifconfig
```

If this gets you connected, we can make the solution permanent.

---

### Post by kbubuntu on 2008-09-18
caddict i don't know that it will help you but i just solved a similar issue with winxp dual boot and realtek 8139 -- see thread:

[http://ubuntuforums.org/showthread.php?t=922873](http://ubuntuforums.org/showthread.php?t=922873)

also, this might be helpful if not dual booting but replacing previous winxp install:

[http://gentoo-wiki.com/Wake_on_lan](http://gentoo-wiki.com/Wake_on_lan)

---

### Post by caddict on 2008-09-19
A stroke of genius there, Pytheas!

It didn't look good at first, but it worked! Sorry, the commands are not in the order you gave...

```
steve@foxy:~$ sudo ifconfig eth0 up hw ether 01:23:45:67:89:01
SIOCSIFFLAGS: Invalid argument
SIOCSIFHWADDR: Cannot assign requested address
steve@foxy:~$ sudo ifconfig eth0 up hw ether 00:00:00:00:00
SIOCSIFFLAGS: Invalid argument
steve@foxy:~$ sudo ifconfig eth0 up hw ether 01:23:45:67:89:01
SIOCSIFHWADDR: Device or resource busy - you may need to down the interface
steve@foxy:~$ sudo ifconfig eth0 down
sudo: timestamp too far in the future: Sep 20 05:56:02 2008
[sudo] password for steve: 
steve@foxy:~$ sudo ifconfig eth0 up hw ether 01:23:45:67:89:01
SIOCSIFHWADDR: Device or resource busy - you may need to down the interface
steve@foxy:~$ sudo ifconfig eth0 down
steve@foxy:~$ sudo ifconfig eth0 up hw ether 01:23:45:67:89:01
SIOCSIFHWADDR: Device or resource busy - you may need to down the interface
steve@foxy:~$ dmesg | tail
[   56.014599] NET: Registered protocol family 10
[   56.014854] lo: Disabled Privacy Extensions
[  287.885770] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  290.010894] NET: Registered protocol family 17
[  304.003158] eth0: no IPv6 routers present
[  329.210873] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  346.326468] eth0: no IPv6 routers present
[  352.377757] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  371.861062] eth0: no IPv6 routers present
[  614.380737] eth0: no IPv6 routers present
steve@foxy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:bf  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:478376 (467.1 KB)  TX bytes:78303 (76.4 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42200 (41.2 KB)  TX bytes:42200 (41.2 KB)
steve@foxy:~$ sudo dhclient eth0
[sudo] password for steve: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:00:00:00:00:bf
Sending on   LPF/eth0/00:00:00:00:00:bf
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 10.1.1.4 from 10.1.1.1
DHCPREQUEST of 10.1.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.1.1.4 from 10.1.1.1
bound to 10.1.1.4 -- renewal in 1636 seconds.
steve@foxy:~$ 
```

how do we make this permanent?

---

### Post by caddict on 2008-09-19
Yes KT, I had also seen that thread on gentoo which is really important for people with 8139 cards (maybe other realtek cards also). In my case I had to upgrade to the latest windows driver because my old driver didn't have that option. On the driver I have now, the option is worded "shutdown wake-on-lan" which needs to be **enabled** (a bit confusing!)

Anyway it is still only part of my problem. Without Pytheas' great trick I still cannot connect statically or with dhcp. But I've been connected once so there is light after all

And another thing, in this case, should acpi be on or off?

---

### Post by caddict on 2008-09-19
This may be useful

If I enter

```
steve@foxy:~$ sudo ifconfig eth0 up hw ether 01:23:45:67:89:01
```
i get 
```
SIOCSIFFLAGS: Invalid argument
SIOCSIFHWADDR: Cannot assign requested address
```
then
```
steve@foxy:~$ sudo dhclient eth0
```
has no success

but if i then add the line

```
steve@foxy:~$ sudo ifconfig eth0 up hw ether 00:00:00:00:00
```
i get
```
SIOCSIFFLAGS: Invalid argument
```
and i have a connection!

happens every time

---

### Post by pytheas22 on 2008-09-19
That's weird...it doesn't seem to be spoofing the MAC to the one you try to set (instead it goes to 00:00:00:00:00:bf, have no idea where it comes up with that), but at least it works.  To make it permanent, you can write a boot script.  First open up a blank file:

```
sudo gedit /etc/init.d/ethernet-fix.sh
```

(if you're using KDE or Xubuntu, replace 'gedit' with 'kate' or 'mousepad')

Add to the file these lines:

```
#!/bin/bash
#this script spoofs the MAC address of eth0 to something that works

ifconfig eth0 down
ifconfig eth0 up hw ether 01:23:45:67:89:01
dhclient eth0
ifconfig eth0 up hw ether 00:00:00:00:00
dhclient eth0
```

Then save and close the file.  Finally, run these commands so that the script will be run automatically at boot:
```

cd /etc/init.d
sudo -s
chmod +x ethernet-fix.sh
update-rc.d ethernet-fix.sh defaults
```

Then try rebooting and see if you're connected automatically by the time you log in to your desktop.  We may need to play with the script a little bit to get it to work, but hopefully the stuff above will do it.

---

### Post by caddict on 2008-09-19
OK I've managed to simplify the process even further. All that is required is
```
ifconfig eth0 up hw ether 00:00:00:00:00

```
and then the same again
```
ifconfig eth0 up hw ether 00:00:00:00:00
```
and i'm in.

I've tried a few variations of the script, starting from what you wrote and ending with the above, but no go. It works every time from the terminal. Maybe the script is being executed too soon?

---

### Post by pytheas22 on 2008-09-19
The script shouldn't be getting executed too soon...it should be waiting till the rest of the system is pretty much up.  You could try making a script that runs each time you log into Gnome, though--go to System>Preferences>Sessions and add a startup program with the command:
```

gksudo ifconfig eth0 up hw ether 00:00:00:00:00; gksudo ifconfig eth0 up hw ether 00:00:00:00:00
```

Then the next time you login to Gnome, you'll be prompted for your password, and after you enter it, the commands needed to make the Internet work should be run.  Unfortunately I don't know of any way to do it without you having to enter your password (you could probably play with the permissions of 'ifconfig' but it's probably not a good idea).

By the way, if you're not using Gnome, let me know.

---

### Post by kbubuntu on 2008-09-19
caddict in my case acpi remains on

---

### Post by caddict on 2008-09-20
ok thanks kt I think I'll turn mine back on again

---

### Post by caddict on 2008-09-20
Pytheas, weirdly enough, the script doesn't work. I get prompted for my password, but when gnome appears, the network is not up.

Maybe I could write a little script that could be executed from the desktop?

Seems like a crazy workaround!

PS I have deleted the ill-fated ethernet-fix.sh from init.d. What about the rc.d files that were updated? Does anything need to be done?

---

### Post by caddict on 2008-09-21
I've placed a small script on the desktop which does the deed. The commands are now

```
gksudo ifconfig eth0 up hw ether 00:00:00:00:00
gksudo /etc/init.d/networking restart
```
That'll do for now. Still have to enter pswd of course.

I've also deleted all links to previous ethernet-fix.sh in the rc#.d files.
Pytheas, thanks for helping me make some sense of this. Much appreciated

---

### Post by pytheas22 on 2008-09-21
Sorry, I must have missed your post from yesterday.

Don't worry about the rc.d stuff...it shouldn't hurt anything if the scripts are not there.

I'm glad things are fixed now.  Let me know if you need any more help; otherwise, enjoy Ubuntu!

---

### Post by caddict on 2008-09-22
thanks again
Ubuntu is great!

---

