---
title: "ndiswrapper with a Dell 1450.."
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by dfrandin on 2007-06-30
Having a heck of a time getting ndiswrapper to work with Feisty and a Dell 1450 minipci card. I've tracked down the bcmwl5a.sys and bcmwl5a.inf from my windows install on for the machine containing the 1450 card.. I've blacklisted the built-in bcm43xx driver in the /etc/modprobe.d/blacklist file, restarted the machine, ran ndiswrapper -i bcmwl5a.inf and still get the following:

root@i2200:/home/dave/Desktop# ndiswrapper -i bcmwl5a.inf
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
root@i2200:/home/dave/Desktop# ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4324) present (alternate driver: bcm43xx)

The docs at ndiswrapper say if you see the (alternate driver) line that you need to blacklist the bcm43xx driver.. I thought I'd already done that!!
Needless to say, I cant get on the net with this... To get on the net under Ubuntu, I'm forced to use a clunky old pcmcia orinaco card... Help!!!

Dave

---

### Post by kevdog on 2007-06-30
Ok, lets just check a few things before providing possible resolutions:

Can you post the following:
lshw -C network
lspci
Cut and paste the file /etc/network/interfaces
Cut and paste file /etc/iftab
ifconfig
ndiswrapper -v

Thanks

---

### Post by dfrandin on 2007-07-01
Thanks.. The info below is collected with the Dell 1450 minipci card in the system, but am using the onboard wired ethernet for net access as the old orinaco pcmcia card I use does not work with my wpa2 access point...  Judging from the info I've seen on the ndiswrapper howto, my install *should* be working, but for the
-for some reason- still-loaded bcm43xx kernel driver that is entered into the end of the /etc/modprobe.d/blacklist file...

...last lines of blacklist...

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

(I entered everything below this line...)
# Don't want to load the bogus broadcomm 4300 driver
# trying to use ndiswrapper with bcmwl5.sys/bcmwl5.inf

blacklist bcm43xx

----------------------------------------------------------------------------------------------------------------

root@i2200:~# lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:dfdfe000-dfdfffff irq:1
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth1
       version: 03
       serial: 00:14:22:b9:02:0c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.100.101 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
---------------------------------------------------------------------------------------------------------------------------
root@i2200:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
---------------------------------------------------------------------------------------------------------------------------
/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth2 inet dhcp
wireless-essid Panera Bread
iface eth1 inet dhcp
iface eth0 inet dhcp
wireless-essid CoffeeBean

auto eth0
auto eth2
auto eth1
-------------------------------------------------------------------------------------------------------------------------
root@i2200:/etc# cat iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0b:7d:28:99:e5 arp 1
eth1 mac 00:14:22:b9:02:0c arp 1

-------------------------------------------------------------------------------------------------------------------------
root@i2200:/etc# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:14:22:B9:02:0C  
          inet addr:192.168.100.101  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feb9:20c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1225133 (1.1 MiB)  TX bytes:236108 (230.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
-------------------------------------------------------------------------------------------------------------------------
root@i2200:/home/dave/Desktop# ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by kevdog on 2007-07-01
I dont think the bcm43xx driver is still loading given the info you just presented.  You could issue command:

lsmod | grep bcm

and if nothing shows then the module definitely isnt loaded.

Look at the output you gave me.  ndiswrapper is not installed correctly.  There is a utils error.  This means you need to remove your installation via:

sudo rm -R /etc/ndiswrapper *
Use synaptic to remove ndiswrapper

Then reinstall synaptice from source. These are the instruction on how to do this:

Lets do some setup work first (Skip to #4 if you have a working wired connection that works to download files)
1. Stick ubuntu cd-rom into driver and wait to become ready
2. At command line type: sudo apt-cdrom add
3. Then: sudo aptitude update
4. Then: sudo aptitude install build-essential

At command line, do the following:
cd ~
mkdir ndiswrapper

Download the ndiswrapper source files and place in the ~/ndiswrapper directory:
[http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)

cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

Ok great, now lets check ndiswrapper installation to see if it correct:
ndiswrapper -v

You should see no errors!

Ill stop right now to let you catch up!
__________________

---

### Post by dfrandin on 2007-07-01
Thanks again... Here's what ndiswrapper -v says
after uninstalling the packaged one I got from apt-get and
compiled from  source...  I assume this means I've got pieces of the
old install still lurking on the system... And of course, if I run ndiswrapper -i bcmwl5a.inf
I get the same warning that the bcm43xx is loaded...

-------------------------------------------------

root@i2200:~# ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

---

### Post by kevdog on 2007-07-01
I dont know why you keep getting that error.  But it said you had the utils version installed once.  

What does
ndiswrapper -l
report now??


I think we can keep going at this step if the above states no errors!

Do the following also,

gksu gedit /etc/modprobe.d/blacklist

If the following is not contained in this file add this at the bottom:
blacklist bcm43xx

Save the file.  

Here is what my ndiswrapper -l states (note that the bcm43xx driver is blacklisted so that it doesnt get loaded)

lsbcmnds : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

---

