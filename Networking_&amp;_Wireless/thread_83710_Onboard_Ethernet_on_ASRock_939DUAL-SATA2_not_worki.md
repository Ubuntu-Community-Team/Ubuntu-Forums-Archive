---
title: "Onboard Ethernet on ASRock 939DUAL-SATA2 not working!"
date: 2005-10-29
forum: Networking &amp; Wireless
---

### Post by Erwin123 on 2005-10-29
Hello,

I've set up an Ubuntu Breezy machine - it works very nice. I've a working ISDN card. Now, I wanted to upgrade to DSL and access a Barricade 4-port router. However, I can't even ping that router!

>ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.114 icmp_seq=1 Destination Host Unreachable

>ifconfig -v
eth0      Link encap:Ethernet  HWaddr 00:13:8F:37:4B:B7
          inet addr:192.168.2.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe37:4bb7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe400

A strange thing is the missing RUNNING, but even worse are the transmission errors!

My board is a ASRock 939DUAL-SATA2 with ULi 1695 chip set. (ULi was formerly ALi).

>sudo lspci -v
0000:00:11.0 Ethernet controller: ALi Corporation: Unknown device 5263 (rev 40)
        Subsystem: Unknown device 1849:5263
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e400 [size=256]
        Memory at febfec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

>sudo ethtool -i eth0
driver: tulip
version: 1.1.13
firmware-version:
bus-info: 0000:00:11.0

There is a kernel module "tulip" running, but I'm not sure whether it is the correct driver.
If I reload the module
>sudo rmmod tulip && sudo modprobe tulip
ifconfig tells the device is RUNNING! But after ifdown/ifup this feature is lost again...

The router acts as a DHCP server assigning IPs in the range 192.168.2.100-200, its own IP is 192.168.2.1. I could connect successfully with a Windows machine, the resulting gateway is 192.168.2.254. Since I can't use DHCP, I've set up the ethernet adaptor as follows:

>relevant part of /etc/network/interfaces:
 iface eth0 inet static
 address 192.168.2.114
 netmask 255.255.255.0
 # gateway 192.168.2.254  -- doesn't change anything

>route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0

If you need anything else, please ask.
I would appreciate very much any helpful advice!

THANX!
Erwin

---

### Post by Erwin123 on 2005-10-29
Maybe some more information helps, this is the output from

>sudo dmesg
Linux Tulip driver version 1.1.13 (May 11, 2002)
ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 17 (level, low) -> IRQ 17
tulip0:  EEPROM default media type Autosense.
tulip0:  Index #0 - Media MII (#11) described by a 21140 MII PHY (1) block.
tulip0:  Index #1 - Media 10baseT (#0) described by a <unknown> (128) block.
tulip0:  Index #2 - Media 10baseT (#0) described by a 21140 non-MII (0) block.
tulip0:  Index #3 - Media 10base2 (#1) described by a 21140 non-MII (0) block.
tulip0:  Index #4 - Media 10baseT-FDX (#4) described by a 21140 non-MII (0) block.
tulip0:  Index #5 - Media 100baseTx-FDX (#5) described by a 21140 non-MII (0) block.
tulip0:  MII transceiver #1 config 3100 status 7869 advertising 01e1.
eth0: ULi M5261/M5263 rev 64 at 000000000001e400, 00:13:8F:37:4B:B7, IRQ 17.
eth0:  Invalid media table selection 128.
eth0: no IPv6 routers present
eth0:  Invalid media table selection 128.
eth0: no IPv6 routers present

I have no ideaa what the media tables are...

Greets,
Erwin

---

### Post by mips on 2005-10-29
try and hard code the speed/duplex settings on both ends and see what gives...

---

### Post by Erwin123 on 2005-10-29
mpis, thank you for the reply.

I don't know how to set these parameters directly, can you give me some hint? How can I see, which speed is set?

The router is a little black box, it should auto-detect the network card. There is a little green light shining for 100MBit/s (there would be another light for 10MBit/s).

Thanks!
Erwin

P.S: The following does not work:
>sudo ethtool -s eth0 speed 10
Cannot get current device settings: Operation not supported
  not setting speed

It seems that all options of ethtool except for -i don't work.

---

### Post by Erwin123 on 2005-10-29
OK, I found another tool, mii-diag, it tells that the connection is ok, isn't it?

I'm still at the end of any ideas and hope for any ideas from you!
Greets,
Erwin


>sudo mii-diag -v
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 1 (BMCR 0x3100).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #1 transceiver registers:
   3100 786d 0000 8201 01e1 45e1 0001 0000
   0000 0000 0000 0000 0000 0000 0000 0000
   000c 01c0 0086 0000 0000 0000 0000 0000
   0000 00f9 0000 0000 0000 0000 0000 0000.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 Basic mode status register 0x786d ... 786d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Vendor ID is 00:00:20:--:--:--, model 32 rev. 1.
   No specific information is known about this transceiver type.
 I'm advertising 01e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation  completed.

---

### Post by janne5011 on 2005-10-29
hm. If i understand this ok so your card works-right?
then go and check this file 
etc/resolve.conf.
check if there is :

nameserver 192.168.2.1

remove everyting  else

then
go to etc/networks/interfaces
here is my interfacefile:
-----------------------------------------------------------------------------
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

iface eth0 inet dhcp




auto eth0
-----------------------------------------------------------------------------
check it out so it looks reasoble for your setup-
iface eth0 inet dhcp <----assume this is the importanty part
then if there was errors in files do:
sudo /etc/init.d/networking restart
I dont no if this one helps you anyting Im a n00b but I have a similar setup and 
notice if there is connection errors often thoose 2 files is the first things  to look up.

good luck!

---

### Post by greenway on 2005-10-30
Hey, 

in your first post, you posted:

>ifconfig -v
eth0 Link encap:Ethernet HWaddr 00:13:8F:37:4B:B7
inet addr:192.168.2.114 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::213:8fff:fe37:4bb7/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:3 dropped:0 overruns:0 carrier:3
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0xe400

The carrier errors are caused by the NIC loosing its's connection to the router.

You said the link light on your router was on right? This usually indicates that the duplex and speeds have been negatiated. So the duplex shouldn't be the problem. 

Can you try ethtool -S to get a more detailed error report? To me it really sounds like either a bad NIC or bad cables.

Another tool to check your NIC status is mii-tool, try this and print the output, as well as the output from the ethtool -S error report (if possible)

---

### Post by Erwin123 on 2005-10-30
Thanks for the reply,

I'm afraid that the output of these tools is not so instructive:

>sudo ethtool -S eth0
no stats available

>sudo mii-tool -v eth0
eth0: negotiated 100baseTx-FD, link ok
  product info: vendor 00:00:20, model 32 rev 1
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

The only strange thing is the line with "product info", the output of lspci was a little bit different. But I'm not sure what it means anyway.

One thing, I've noticed: after reloading the "tulip" module, the interface is running for a moment (ifconfig output), after a few seconds, "RUNNING" disappears and I have these transmission errors.

Is it possible, that I'm using the wrong driver? I find it very strange, that all the diagnostics with ethtool etc. don't work. How can I check the interplay between network card and driver?

Greets,
Erwin

---

### Post by Erwin123 on 2005-10-30
Hi guys,

under
[http://individual.utoronto.ca/chant/asrock.html](http://individual.utoronto.ca/chant/asrock.html)
I found something interesting describing exactly my problem:

> It appears the onboard ethernet chip (ULI M5263) doesn't work as-is with the tulip driver. I believe the patch tulip-fixes-for-uli5261.patch will fix it, but I have yet to figure out how to compile a custom-module for debian-installer.
Without this patch, you'll currently get 
eth0: Invalid media table
selection 128

and you own't be able to connect to any HTTP or FTP servers. ifconfig will likely show 10 or so RX packets, and 2 TX errors w/ no TX packets. I'll update as soon as I've figured out the next step, likely tonight.

It sounds that I just need to get this patch for the tulip driver. I will look, whether it is already in Ubuntu. If not, can somebody tell me how to get such a patch the Debian-way, e.g. with apt-get?

Thanks that there are people outside who take care of somebody else's problems!

Greets,
Erwin

---

### Post by marsian on 2005-10-30
Hi Erwin,
sorry this is not an answer, but just to say I'm facing exactly the same problem.
The router seems to see the PC (corresponding LED is on), but no way to ping anything over the network... 
Everything you described (lspci, ...) give the same results for me. Is there anybody with the same motherboard and with a running eth0 ?

---

### Post by marsian on 2005-10-31
The source for the driver can be downloaded from here:
[http://www.uli.com.tw/eng/support/drivers.php](http://www.uli.com.tw/eng/support/drivers.php)
Product category=M1695
OS=Linux Kernel 2.6.x
The downloaded archive (directory LAN_M5263) explains how to compile the driver (as a module, with make menuconfig or make xconfig)... which seems to be quite easy but the problem for me is that I don't have the libraries needed to run make xconfig or make menuconfig... and without a running network on the PC, I wonder how to get them ?!...:( 
Is there somewhere a ISO of all what is needed to re-build a kernel ? 
or is it possible to build a module on another PC (my working PC is Intel-P4 whereas the new PC with the ASRock 939DUAL-SATA2 is AMD-64: is it an issue ?)
Manu

---

### Post by marsian on 2005-10-31
Finally, I managed to compile the driver (i386 achitecture) on another PC and to import it.
This is a way I used (hope it could help):
1. copy the attached uli526x.ko file (after unzip)  into /lib/modules/2.6.12-9-386/kernel/drivers/net/tulip/uli526x.ko
2. add the following line in /lib/modules/2.6.12-9-386/modules.dep:
[FONT="Courier New"]/lib/modules/2.6.12-9-386/kernel/drivers/net/tulip/uli526x.ko:[/FONT]
(":" at the end of line must not be forgotten)
3. [FONT="Courier New"]sudo rmmod tulip[/FONT]
4. [FONT="Courier New"]sudo modprobe uli526x[/FONT]

Last unresolved problem is: how to load automatically the uli526x driver at startup ? Add it in /etc/modules is OK, but how to unload the standard tulip driver at the same time (because with the both loaded, it doesn't work) ?

Manu

---

### Post by Erwin123 on 2005-10-31
Hi marsian,

this sounds really good. When I'm back home, I will try it. Since I have an amd64 architecture, I will need to compile it myself. Will I need kernel sources for the compilation? (kernel-headers probably)

Regarding the tulip driver: there are blacklists in /etc, maybe you can add it there. I'm thinking of /etc/hotplug/blacklist.

Greets,
Erwin

---

### Post by switi on 2005-10-31
Hi!

I got the same Mainboard today and also have the problem. I tried to compile the uli drivers but they also didnt allow me to get an address by DHCP. :( 

Currently I am completely rebuilding the kernel. I hope that helps.

Bye Switi

---

### Post by marsian on 2005-11-01
[QUOTE=Erwin123]

Regarding the tulip driver: there are blacklists in /etc, maybe you can add it there. I'm thinking of /etc/hotplug/blacklist.

Greets,
Erwin[/QUOTE]

Adding tulip in /etc/hotplug/blacklist does not help. Maybe is the NIC driver loaded before the hotplug subsystems ? Can anyone help regarding this issue (ie load a specific network interface driver instead of the standard "tulip")
Thanks
Manu

---

### Post by jjukka on 2005-11-02
Would somebody be sooo nice that submits here an uli526x.ko compiled for AMD 64? Please.

---

### Post by K1M on 2005-11-03
cool :D

---

### Post by marsian on 2005-11-04
Hi all !
Is there a feedback regarding the solution I gave ? 
Because for me it has worked, but now it does not work anymore: when I remove the tulip driver, the eth0 Interface desapears from the Gnome Network Panel and even once the uli526x driver is loaded I can't see any eth0 interface... and I can't figure out what is the difference between now and the (happy) time when it worked :( 
If it works for you, can you explain what you did ?
Thanks
Manu

---

### Post by jjukka on 2005-11-07
[QUOTE=jjukka]Would somebody be sooo nice that submits here an uli526x.ko compiled for AMD 64? Please.[/QUOTE]

Not needed anymore, problem solved.

---

### Post by marsian on 2005-11-07
[QUOTE=jjukka]Not needed anymore, problem solved.[/QUOTE]
Can you explain how you've solved it ?...

---

### Post by Dogers on 2005-11-09
Are there any updates to this?? I'd love to get Ubuntu working fully :)

---

### Post by jjukka on 2005-11-10
[QUOTE=marsian]Can you explain how you've solved it ?...[/QUOTE]
Downloaded the module source from ULi's website, put it into the kernel sources and recompiled the kernel. Good luck!

---

### Post by Erwin123 on 2005-11-11
I have compiled the ULi module for AMD64, it can be loaded but the NIC is still not RUNNING :( 

For people who don't want to get into the kernel business I wanted to attach my version of the module. However, I am to stupid to get the attachment working. Please ask, if you need the module. BTW, the dependency can be adjusted via 
>/sbin/depmod -a

If the module should be loaded at boot time, it may be included in /etc/modules.

Maybe it's some IRQ stuff? I have another strange thing: if I plug in a USB stick in my front USB, the computer reboots... (It does work, however, at the rear panel.)

Greets,
Erwin

>ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:8F:49:E2:F4
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe49:e2f4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe400

>sudo ethtool -i eth0
driver: uli526x
version: 0.9.3
firmware-version:
bus-info: 0000:00:11.0

>sudo ethtool -S eth0
no stats available

---

### Post by Dogers on 2005-11-12
[QUOTE=jjukka]Downloaded the module source from ULi's website, put it into the kernel sources and recompiled the kernel. Good luck![/QUOTE]

Where did you get the Kernel source from?? All I can find on the install CD are the kernel headers - which doesn't have the "tulip" folder the readme mentions! :(

---

### Post by leezer3 on 2005-11-12
Hiya,
I assume you have a working internet connection, as this will involve downloading a fair bit of stuff :p 
Read this wiki page: 
[https://wiki.ubuntu.com/KernelBuildpackageDetailedHowto](https://wiki.ubuntu.com/KernelBuildpackageDetailedHowto)
and this will tell you how to compile your own kernel. The driver source that you downloaded should have some instructions in it, please post these here and I'll be able to help further. (All it should involve is the replacement of a couple of files in the kernel source directory, but I want to be sure!)

Oh, it might be an idea to submit a bug citing the latest driver on thier site as a fix.

Cheers

-Leezer-

---

### Post by Dogers on 2005-11-12
Bleurgh..

The only machine I have with a working net connection is a Windows machine..

It's gonna be a PITA to keep the module updated for every kernel release - maybe I'll just dig out my old Intel network card instead :(

---

### Post by mips on 2005-11-12
Maybe ask the developers to add support for it...

---

### Post by leezer3 on 2005-11-12
Precisely- Submit a bug report :D 
Most network cards are well supported in Ubuntu, even if not a new one can be bought for a few £. Remember to check on the compatibility lists though, or you may end up in the same situation :eek: 

-Leezer-

---

### Post by Dogers on 2005-11-12
There's already a bug report for it, looking at this thread :)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=18673](https://bugzilla.ubuntu.com/show_bug.cgi?id=18673)

---

### Post by leezer3 on 2005-11-12
Good work. :cool: 
If all the people who posted with this problem in this thread post on the bug report, then the more effort the devs will put into solving the problem. 

Don't forget- The devs can only fix something they know about ;) 

Cheers

-Leezer-

---

### Post by jjukka on 2005-11-14
[QUOTE=Dogers]Where did you get the Kernel source from?? All I can find on the install CD are the kernel headers - which doesn't have the "tulip" folder the readme mentions! :([/QUOTE]

I grabbed the kernel from kernel.org, and driver source from  [ftp://www.uli.com.tw/driver/Linux_K2.6.x_Integrated132.zip](ftp://www.uli.com.tw/driver/Linux_K2.6.x_Integrated132.zip)

---

### Post by gyrev on 2005-11-14
[QUOTE=marsian]Finally, I managed to compile the driver (i386 achitecture) on another PC and to import it.
This is a way I used (hope it could help):
[/QUOTE]

Wonderful!!
I had the same problem on a PB EasyNote W3281. now I have lan function ok, things are greatly easier to config, video, sound and wlan cards...
thanx a lot!

---

### Post by vtechstu on 2005-11-14
I am still in need of the 64bit kernel compiled file.  Erwin do you think you could hook me up?  Thanks.

---

### Post by loqshio on 2005-11-15
I'm also having trouble with this issue.  Is it just me, or am I stuck in a loop?  I need the Linux kernel compiled to install the network drivers, but I need the network drivers running to download the files to compile the kernel.  

If anyone has compiled the ethernet driver for Kubuntu AMD64 v5.10, I would appreciate some help!

-Steve
[email]loqshio@yahoo.com[/email]

---

### Post by Erwin123 on 2005-11-18
Hi there, 

I started this thread some weeks ago and I am surprised how many people are in trouble with this board! For me, I can't manage to get the NIC working up to now. My solution was to "dig out" an old network card - and within a minute I had my internet connection :cool: 

Nevertheless, I tried to compile the ULi module for AMD64 (K8 kernel), you find my result appended. But I have no idea how to load the module in such a way that it *works* My installation "procedure" was just copying the file to

>sudo cp uli526x.ko /lib/modules/`uname -r`/kernel/drivers/net/tulip

After reboot, the module is loaded automatically - however, the tulip module is loaded as well. I tried *deleting* the tulip module from the above directory, but it is loaded again :confused:

>lsmod | grep uli
uli526x                15508  0 [permanent]
tulip                  54176  0
sata_uli                8896  4
libata                 56072  1 sata_uli

What does the "permanent" mean? If I remove the tulip driver, eth0 stops to exist. Removing uli526x works only with "rmmod -f", but then I can't reload it again. Maybe we could collect on which machines/kernels the uli526x driver is working?

>uname -r && sudo ethtool -i eth0
2.6.12-9-amd64-k8
driver: tulip
version: 1.1.13
firmware-version:
bus-info: 0000:00:11.0

In the installation steps shipped with the ULi driver, they say to  execute "make mdoule_install" after compilation. I don't want to do that because I don't want to overwrite all the other modules. Has somebody an idea what this command does beyond copying?

One final thing: changing anything in /lib/modules/* (modules.dep etc.) is useless since this list is generated automatically during the boot procedure everytime.

Good luck!
Erwin

---

### Post by gyrev on 2005-11-18
Hi all!

here is how I solved this issue: fortunately, my adsl modem also works with a usb connection, so I downloaded the last 2.6.14.2 kernel sources and compiled it. just mark Uli 526x with M in *menuconfig* .

works fine, now.

---

### Post by Hercynium on 2005-11-18
I'm considering buying this exact same board... would you all consider this problem solved after applying the above-mentioned patch for the tulip kernel module?

---

### Post by raydel on 2005-11-20
I had been following this thread. And using the info that everyone had found.
I tried compiling as a module, copying it over and "tricking" the kernel into using it.
This is esentially what the instructions from ULI have you do.  it works until you reboot. Then it will come up but you will get a network unreachable error until you unload the tulip and reload the uli526x modules. Then every thing works as advertised again.......until you boot.  So I figured I figured I'd give it a shot rolling it in the kernel.  Works great! I installed the tulip and uli526x into the kernel and all the problems are gone.  I pulled the realtek card I had been using and have rebooted it a few times.  YaHoo!

---

### Post by Hercynium on 2005-11-22
Well, then it looks like there are ways to make it work properly. I wouldn't consider the issue 'resolved', but as soon as I get my new system, I'll see what I can do to make a real 'Debian-style' solution... maybe a package that totally disables the tulip driver and installs the correct one (and puts things back after an apt-get remove)

---

### Post by Dogers on 2005-11-22
[QUOTE=raydel]This is esentially what the instructions from ULI have you do.  it works until you reboot. Then it will come up but you will get a network unreachable error until you unload the tulip and reload the uli526x modules. Then every thing works as advertised again.......until you boot.[/QUOTE]

There should be a way of blacklisting the tulip driver and having it load the other automatically.. I know with hotplug you could blacklist drivers, but I don't know how to do it with udev :confused: 

I wonder if aliasing the uli driver as the tulip one would work, too? :)

---

### Post by raydel on 2005-11-22
I don't think you'll be able to black list the tulip module. The kernel config will not let you.  You can't select the uli module without the tulip. It is dependant on it.  Compiling in the code for for those two modules made no real change to the size of the my kernel and the brown splash screen is gone and won't be missed.

---

### Post by Dogers on 2005-11-23
No, not in the kernel config, in the systems that load the modules at boot time :)

---

### Post by Pridkett on 2005-11-25
For folks that are having problems with this network device coming up at boot time, I had to do some brute force fun to get it to work.  Open up /etc/init.d/networking and fine the following line (around line 84):
```
        log_begin_msg "Configuring network interfaces..."
```
Now, add these lines after that line:```

modprobe -r tulip
modprobe -r uli526x
modprobe uli526x
```
This basically forces the driver to unload and reload itself when the networking restarts.  It's a total hack, but it seems to make my network card work just fine.

Here's hoping for inclusion in Dapper Drake.

---

### Post by Dogers on 2005-11-26
Just poking around on Kernel.org, it seems this will certainly be fixed in the next Ubuntu release:
[http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=commit;h=8386aa4e7d74c56eacf8a8ce8b0410d36919fcd1](http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=commit;h=8386aa4e7d74c56eacf8a8ce8b0410d36919fcd1)

Although it may well be fixed in the recent kernel builds anyway, as gyrev seems to be saying!

---

### Post by vtechstu on 2005-11-28
Would someone be so kind as to roll this driver into the current ubuntu kernel, and upload it, or be willing to email/send on a case by case basis?  This would be MUCH appreciated, and the easiest way to solve this.  Thanks

---

### Post by GameManK on 2006-01-03
has anybody here tried doing a fresh install on this board? according to this thread and the bug report the driver should be in dapper, so i tried installing the flight 2 cd and it won't detect the network hardware during install.

I already started a new thread on this in the dapper forum [http://ubuntuforums.org/showthread.php?t=112001](http://ubuntuforums.org/showthread.php?t=112001)

---

### Post by legatodnl on 2006-01-14
I discovered the issue last night. I found this useful thread 5 minutes later :) I tried compiling the module on my 64bit gentoo machine and transfering it to the ubuntu computer, sadly the ubuntu computer is not liking it. Perhaps its bcus the gentoo machine is not socket 939 or could be that i'm running 2.6.14-r2 kernel. if someone e-mails me a compiled module it would be useful and I would make sure its availiable for everyone else. 

Thanks for all the advise so far.

Dan

---

### Post by wolfchri on 2006-02-12
On dapper, the NIC is now perfectly working at least on my 64bit installation, did not try the 32bit dapper. 

However, I have still problems with hotplugging USB drives on this board, on various  
Linux distros including dapper as well as on Windooze XP with all the latest patches. Either the system just freezes (on Dapper, after becoming extremely slow) or it does not recognize 1 of 2 drives, e.g. it sees the USB stick but not the additional USB hard drive.

Also ACPI is an issue - I had Breezy32 bit freezing after the system going idle for 5 minutes, looks to me as if this was related to a power saving function since KDE battery status on PCLinux for example keeps telling me that the system is running low on batterie power and then logs me out, sometimes straight after login.

Also, the BIOS does not detect my SATA-1 drive when I disable SATAII. Looks to me as if the BIOS needs one or two updates....

---

### Post by eeknay on 2006-02-18
Just just need to get the a kernel >=2.6.15 and all the stuff works fine.
Btw, is there a way to easy install the drapper kernel in breezy?

---

### Post by sony102600 on 2006-03-03
Hey all, I am a complete Ubuntu noob, and feel like there should a solution to this problem in there, but I can't quite understand, could anyone spell it out for me?

---

### Post by GameManK on 2006-03-05
[QUOTE=sony102600]Hey all, I am a complete Ubuntu noob, and feel like there should a solution to this problem in there, but I can't quite understand, could anyone spell it out for me?[/QUOTE]
Solution: download and install ubuntu dapper (development version) flight 4

---

### Post by wolfchri on 2006-03-11
Since a few days, the networks needs to be deactivated/activated in order to work in Dapper. Strange. It was working flawlessly, and now this.... well, not a real problem, however a step backwards :-(

---

### Post by Darkshine on 2006-03-12
I can't get this to work on the live CD.  Is DHCP working or do I need to set a static IP?

EDIT: Seems like the device manager detects the device, however when it is enabled it doesn't connect to the network. No idea how to solve this.

>  Solution: download and install ubuntu dapper (development version) flight 4 

I have Ubuntu Dapper Flight 5 and it doesn't work there.

---

### Post by bonnei on 2006-03-22
[QUOTE=Darkshine]I can't get this to work on the live CD.  Is DHCP working or do I need to set a static IP?

EDIT: Seems like the device manager detects the device, however when it is enabled it doesn't connect to the network. No idea how to solve this.



I have Ubuntu Dapper Flight 5 and it doesn't work there.[/QUOTE]
I install the Dapper Flight 5 just now,and the NIC works now.You can activiate it,it maybe work.

---

### Post by Darkshine on 2006-03-22
Well I can activate it, but DHCP still does nothing and I can't ping any other computers on the network.  It works in Win XP....why not here?

---

### Post by ShiftyPowers on 2006-04-12
has anyone tried installing with Flight 6?  I'm just installing now and it doesn't seem to recognize the LAN during install.

---

### Post by ShiftyPowers on 2006-04-12
I'm going to try Suse, this is a pain.

---

### Post by Darkshine on 2006-04-22
Tell me if that works out for you...this problem is really annoying.  However I did email one of the developers ;) hopefully we can get to the bottom of this.

---

### Post by -X- on 2006-04-23
I just tried disabling and enabling the darn thing in Beta 1 but it doesn't seem to like me any more than it likes you.

---

### Post by Darkshine on 2006-04-25
Just tried the beta also...no luck ](*,)

---

### Post by wolfchri on 2006-04-29
On my system, it is now working for 3 weeks or so without any problem, using Dapper x86 and Dapper AMD64. 

Do you have the latest BIOS (1.60 I think?), and no IRQ problems?

---

### Post by nandes on 2006-05-11
wow!

I Just update my deb pacakages, on my dapper, reboot the computer and... vuala! networking now works!

post my dmesg

```
[4294667.296000] Linux version 2.6.15-22-k7 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sun May 7 17:27:47 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[4294667.296000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 262064
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32688 pages, LIFO batch:7
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9be0
[4294667.296000] ACPI: RSDT (v001 A M I  OEMRSDT  0x01000627 MSFT 0x00000097) @ 0x3ffb0000
[4294667.296000] ACPI: FADT (v002 A M I  OEMFACP  0x01000627 MSFT 0x00000097) @ 0x3ffb0200
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x01000627 MSFT 0x00000097) @ 0x3ffb0390
[4294667.296000] ACPI: OEMB (v001 A M I  AMI_OEM  0x01000627 MSFT 0x00000097) @ 0x3ffc0040
[4294667.296000] ACPI: DSDT (v001  939M2 939M2160 0x00000160 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:15 APIC version 16
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec10000] gsi_base[24])
[4294667.296000] IOAPIC[1]: apic_id 2, version 17, address 0xfec10000, GSI 24-39
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf7c0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda7 ro vga=0x31a quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] mapped IOAPIC to ffffb000 (fec10000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2000.007 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour dummy device 80x25
[4294667.609000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.609000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.628000] Memory: 1028392k/1048256k available (2085k kernel code, 19188k reserved, 593k data, 328k init, 130752k highmem)
[4294667.628000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.688000] Calibrating delay using timer specific routine.. 4002.39 BogoMIPS (lpj=2001195)
[4294667.688000] Security Framework v1.0.0 initialized
[4294667.688000] SELinux:  Disabled at boot.
[4294667.688000] Mount-cache hash table entries: 512
[4294667.688000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294667.688000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294667.688000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.688000] CPU: L2 Cache: 512K (64 bytes/line)
[4294667.688000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000010 00000001 00000000 00000001
[4294667.688000] mtrr: v2.0 (20020519)
[4294667.688000] Enabling fast FPU save and restore... done.
[4294667.688000] Enabling unmasked SIMD FPU exception support... done.
[4294667.688000] Checking 'hlt' instruction... OK.
[4294667.692000] SMP alternatives: switching to UP code
[4294667.692000] checking if image is initramfs... it is
[4294668.089000] Freeing initrd memory: 5408k freed
[4294668.093000] ACPI: Looking for DSDT ... not found!
[4294668.095000] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 02
[4294668.095000] Total of 1 processors activated (4002.39 BogoMIPS).
[4294668.095000] ENABLING IO-APIC IRQs
[4294668.095000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294668.206000] Brought up 1 CPUs
[4294668.206000] NET: Registered protocol family 16
[4294668.206000] EISA bus registered
[4294668.206000] ACPI: bus type pci registered
[4294668.206000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[4294668.206000] PCI: Using configuration type 1
[4294668.206000] ACPI: Subsystem revision 20051216
[4294668.210000] ACPI: Interpreter enabled
[4294668.210000] ACPI: Using IOAPIC for interrupt routing
[4294668.211000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.211000] PCI: Probing PCI hardware (bus 00)
[4294668.213000] PCI quirk: region 0800-083f claimed by ali7101 ACPI
[4294668.214000] Boot video device is 0000:03:00.0
[4294668.214000] PCI: Transparent bridge - 0000:00:06.0
[4294668.214000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[4294668.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
[4294668.234000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB1._PRT]
[4294668.234000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB2._PRT]
[4294668.234000] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 12 14 15)
[4294668.235000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.235000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.235000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15), disabled.
[4294668.236000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294668.236000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.236000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294668.236000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[4294668.237000] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.237000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.237000] pnp: PnP ACPI init
[4294668.241000] pnp: PnP ACPI: found 13 devices
[4294668.241000] PnPBIOS: Disabled by ACPI PNP
[4294668.241000] PCI: Using ACPI for IRQ routing
[4294668.241000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.249000] pnp: 00:0b: ioport range 0x290-0x29f has been reserved
[4294668.249000] PCI: Bridge: 0000:00:01.0
[4294668.249000]   IO window: disabled.
[4294668.249000]   MEM window: fa700000-fa7fffff
[4294668.249000]   PREFETCH window: disabled.
[4294668.249000] PCI: Bridge: 0000:00:02.0
[4294668.249000]   IO window: disabled.
[4294668.249000]   MEM window: fa800000-fa8fffff
[4294668.249000]   PREFETCH window: disabled.
[4294668.249000] PCI: Bridge: 0000:00:05.0
[4294668.249000]   IO window: disabled.
[4294668.249000]   MEM window: fa900000-fe9fffff
[4294668.249000]   PREFETCH window: aff00000-cfefffff
[4294668.249000] PCI: Bridge: 0000:00:06.0
[4294668.249000]   IO window: d000-dfff
[4294668.249000]   MEM window: fea00000-feafffff
[4294668.249000]   PREFETCH window: disabled.
[4294668.249000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 29 (level, low) -> IRQ 169
[4294668.249000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294668.249000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 34 (level, low) -> IRQ 177
[4294668.249000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294668.249000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294668.249000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294668.249000] audit: initializing netlink socket (disabled)
[4294668.249000] audit(1147370870.247:1): initialized
[4294668.249000] highmem bounce pool size: 64 pages
[4294668.249000] VFS: Disk quotas dquot_6.5.1
[4294668.250000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.250000] Initializing Cryptographic API
[4294668.250000] io scheduler noop registered
[4294668.250000] io scheduler anticipatory registered
[4294668.250000] io scheduler deadline registered
[4294668.250000] io scheduler cfq registered
[4294668.250000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 29 (level, low) -> IRQ 169
[4294668.250000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294668.250000] assign_interrupt_mode Found MSI capability
[4294668.250000] Allocate Port Service[pcie00]
[4294668.250000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 34 (level, low) -> IRQ 177
[4294668.250000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294668.250000] assign_interrupt_mode Found MSI capability
[4294668.250000] Allocate Port Service[pcie00]
[4294668.250000] isapnp: Scanning for PnP cards...
[4294668.607000] isapnp: No Plug & Play device found
[4294668.617000] PNP: No PS/2 controller found. Probing ports directly.
[4294668.619000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.619000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.619000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294668.619000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.620000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.621000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.621000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294668.621000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294668.621000] mice: PS/2 mouse device common for all mice
[4294668.621000] EISA: Probing bus 0 at eisa.0
[4294668.621000] EISA: Detected 0 cards.
[4294668.621000] NET: Registered protocol family 2
[4294668.631000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.631000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[4294668.633000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[4294668.633000] TCP: Hash tables configured (established 262144 bind 65536)
[4294668.633000] TCP reno registered
[4294668.633000] TCP bic registered
[4294668.633000] NET: Registered protocol family 1
[4294668.633000] NET: Registered protocol family 8
[4294668.633000] NET: Registered protocol family 20
[4294668.633000] Using IPI No-Shortcut mode
[4294668.633000] ACPI wakeup devices:
[4294668.633000]  HTT UAR1 AC97 MC97  LAN USB0 USB1 USB2 UB20 PEB1 PEB2 PEB3
[4294668.633000] ACPI: (supports S0 S1 S3 S4 S5)
[4294668.633000] Freeing unused kernel memory: 328k freed
[4294668.694000] vesafb: framebuffer at 0xb0000000, mapped to 0xf8880000, using 5120k, total 262144k
[4294668.694000] vesafb: mode is 1280x1024x16, linelength=2560, pages=1
[4294668.694000] vesafb: protected mode interface info at c000:ce20
[4294668.694000] vesafb: scrolling: redraw
[4294668.694000] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[4294668.694000] vesafb: Mode is VGA compatible
[4294668.932000] Console: switching to colour frame buffer device 160x64
[4294668.932000] fb0: VESA VGA frame buffer device
[4294670.178000] Capability LSM initialized
[4294670.672000] ALI15X3: IDE controller at PCI slot 0000:00:12.0
[4294670.672000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 209
[4294670.672000] ALI15X3: chipset revision 199
[4294670.672000] ALI15X3: not 100% native mode: will probe irqs later
[4294670.672000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[4294670.672000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[4294670.672000] Probing IDE interface ide0...
[4294670.937000] hda: Maxtor 6E040L0, ATA DISK drive
[4294671.193000] hdb: Maxtor 6Y200P0, ATA DISK drive
[4294671.245000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.245000] Probing IDE interface ide1...
[4294671.918000] hdc: PIONEER DVD-RW DVR-110D, ATAPI CD/DVD-ROM drive
[4294672.531000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.538000] hda: max request size: 128KiB
[4294672.553000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[4294672.554000] hda: cache flushes supported
[4294672.554000]  hda: hda1 hda2 < hda5 hda6 hda7 >
[4294672.596000] hdb: max request size: 1024KiB
[4294672.596000] hdb: 398297088 sectors (203928 MB) w/7936KiB Cache, CHS=24792/255/63, UDMA(133)
[4294672.597000] hdb: cache flushes supported
[4294672.597000]  hdb: hdb1 < hdb5 hdb6 >
[4294672.623000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[4294672.623000] Uniform CD-ROM driver Revision: 3.20
[4294673.081000] usbcore: registered new driver usbfs
[4294673.082000] usbcore: registered new driver hub
[4294673.083000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294673.084000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 20 (level, low) -> IRQ 217
[4294673.084000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[4294673.146000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294673.146000] ohci_hcd 0000:00:13.0: irq 217, io mem 0xfebfd000
[4294673.200000] hub 1-0:1.0: USB hub found
[4294673.200000] hub 1-0:1.0: 3 ports detected
[4294673.301000] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 21 (level, low) -> IRQ 225
[4294673.301000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[4294673.312000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294673.312000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xfebfc000
[4294673.366000] hub 2-0:1.0: USB hub found
[4294673.366000] hub 2-0:1.0: 3 ports detected
[4294673.467000] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 22 (level, low) -> IRQ 233
[4294673.467000] ohci_hcd 0000:00:13.2: OHCI Host Controller
[4294673.478000] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294673.478000] ohci_hcd 0000:00:13.2: irq 233, io mem 0xfebfb000
[4294673.532000] hub 3-0:1.0: USB hub found
[4294673.532000] hub 3-0:1.0: 3 ports detected
[4294673.635000] ACPI: PCI Interrupt 0000:00:13.3[D] -> GSI 23 (level, low) -> IRQ 50
[4294673.635000] ehci_hcd 0000:00:13.3: EHCI Host Controller
[4294673.635000] ehci_hcd 0000:00:13.3: debug port 1
[4294673.656000] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[4294673.657000] ehci_hcd 0000:00:13.3: irq 50, io mem 0xfebfe800
[4294673.657000] ehci_hcd 0000:00:13.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294673.657000] hub 4-0:1.0: USB hub found
[4294673.657000] hub 4-0:1.0: 8 ports detected
[4294673.684000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[4294673.804000] Attempting manual resume
[4294673.818000] kjournald starting.  Commit interval 5 seconds
[4294673.818000] EXT3-fs: mounted filesystem with ordered data mode.
[4294674.477000] usb 2-1: new low speed USB device using ohci_hcd and address 3
[4294674.845000] usb 2-2: new low speed USB device using ohci_hcd and address 4
[4294685.317000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294685.319000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294685.459000] Linux agpgart interface v0.101 (c) Dave Jones
[4294685.460000] agpgart: Unsupported ALi chipset (device id: 1689)
[4294685.571000] agpgart: Detected AGP bridge 20
[4294685.571000] Setting up ULi AGP.
[4294685.574000] agpgart: AGP aperture is 128M @ 0xd8000000
[4294685.946000] nvidia: module license 'NVIDIA' taints kernel.
[4294685.948000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 58
[4294685.948000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8756  Wed Mar 29 14:26:26 PST 2006
[4294686.043000] ali15x3_smbus 0000:00:07.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294686.043000] ali15x3_smbus 0000:00:07.1: ALI15X3 not detected, module not inserted.
[4294686.090000] ali1535_smbus 0000:00:07.1: ALI1535_smb region uninitialized - upgrade BIOS?
[4294686.090000] ali1535_smbus 0000:00:07.1: ALI1535 not detected, module not inserted.
[4294686.206000] 8139too Fast Ethernet driver 0.9.27
[4294686.206000] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 21 (level, low) -> IRQ 225
[4294686.207000] eth0: RealTek RTL8139 at 0xf8deec00, 00:05:1c:13:6b:23, IRQ 225
[4294686.207000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294686.217000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294686.221000] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[4294686.221000] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 17 (level, low) -> IRQ 66
[4294686.248000] eth1: ULi M5263 at pci0000:00:11.0, 00:13:8f:3f:90:0e, irq 66.
[4294686.297000] Real Time Clock Driver v1.12
[4294686.356000] ali1563: SMBus control = 0403
[4294686.356000] ali1563_probe: Returning 0
[4294686.359000] input: PC Speaker as /class/input/input0
[4294686.425000] parport: PnPBIOS parport detected.
[4294686.425000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294686.470000] Floppy drive(s): fd0 is 1.44M
[4294686.485000] FDC 0 is a post-1991 82077
[4294686.610000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 74
[4294686.747000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[4294687.620000] AC'97 1 does not respond - RESET
[4294687.620000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294687.620000] Unable to initialize codec #1
[4294687.672000] intel8x0_measure_ac97_clock: measured 50930 usecs
[4294687.672000] intel8x0: clocking to 48000
[4294687.704000] usbcore: registered new driver hiddev
[4294687.716000] input: Logitech USB Receiver as /class/input/input1
[4294687.716000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.1-1
[4294687.738000] input: Logitech USB Receiver as /class/input/input2
[4294687.738000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1
[4294687.749000] input: Logitech Optical USB Mouse as /class/input/input3
[4294687.749000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-2
[4294687.749000] usbcore: registered new driver usbhid
[4294687.749000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294687.868000] ts: Compaq touchscreen protocol output
[4294688.302000] lp0: using parport0 (interrupt-driven).
[4294688.362000] fuse init (API version 7.3)
[4294688.434000] NET: Registered protocol family 10
[4294688.434000] lo: Disabled Privacy Extensions
[4294688.434000] IPv6 over IPv4 tunneling driver
[4294688.571000] Adding 1542200k swap on /dev/hda6.  Priority:-1 extents:1 across:1542200k
[4294688.684000] EXT3 FS on hda7, internal journal
[4294688.916000] kjournald starting.  Commit interval 5 seconds
[4294688.922000] EXT3 FS on hda5, internal journal
[4294688.922000] EXT3-fs: mounted filesystem with ordered data mode.
[4294689.102000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294689.142000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294689.189000] NTFS volume version 3.1.
[4294690.560000] ACPI: Power Button (FF) [PWRF]
[4294690.560000] ACPI: Power Button (CM) [PWRB]
[4294690.644000] ibm_acpi: ec object not found
[4294690.662000] pcc_acpi: loading...
[4294693.701000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[4294696.701000] uli526x: eth1 NIC Link is Up 10 Mbps Half duplex
[4294696.705000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[4294698.877000] eth0: no IPv6 routers present
[4294699.111000] NET: Registered protocol family 17
[4294699.896000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
[4294699.896000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
[4294699.896000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[4294700.199000] i2c_adapter i2c-1: SMBus Quick command not supported, can't probe for chips
[4294700.199000] i2c_adapter i2c-2: SMBus Quick command not supported, can't probe for chips
[4294700.199000] i2c_adapter i2c-3: SMBus Quick command not supported, can't probe for chips
[4294701.118000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[4294701.118000] apm: overridden by ACPI.
[4294707.218000] eth1: no IPv6 routers present
[4294770.146000] eth1: no IPv6 routers present
[4295071.493000] eth0: link down
[4295071.496000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4295093.168000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[4295279.314000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[4295422.214000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[4295425.211000] uli526x: eth1 NIC Link is Up 10 Mbps Half duplex
[4295425.217000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[4295435.498000] eth1: no IPv6 routers present
[4295486.685000] eth1: no IPv6 routers present

```

---

### Post by nandes on 2006-05-14
in my last boot, networking fails again :???: 

i removed my pci realtek 8139 i modified some BIOS parameters, i left all parameters  like beginning...
finally .... I don't understand, networking works again :-k 
I am scared to lose the network again ](*,)

---

### Post by Rroet on 2006-06-02
I have the same issue, using a Packard Bell Easynote R3400 laptop.

Problem with me is, I can't seem to STOP the boottime loading of the tulip driver.

Is there a way of preventing this driver being loaded during boottime? It severely pisses me off that I have to go back to a shell line, unload both the tulip driver and the uli526x driver (breezy kernel) every time I need to use the network.

Could somebody please help me?


Why am I not using a dapper kernel? Because it has issues with the 8254 Ati Timer which is causing IO-APIC issues and it makes my entire system unstable.

---

### Post by Erwin123 on 2006-06-03
One day, I gave up with Breezy and the onboard NIC and installed a PCI card. Since Dapper is out now, I updated and tried again. After some issues with /etc/iftab (somebody entered a wrong MAC address there which looked similar to the real one!) and many reboots the onboard NIC is working now fine!  :)

Cheers,
Erwin

---

### Post by Erwin123 on 2006-06-07
One more comment on the Cool'n'Quiet feature of this mainboard (its not related to this thread but might be of interest to people dealing with this board).

I figured out that the board doesn't support the "Quiet" part of the feature, i.e. it is impossible to adjust the speed of the CPU fan :-) One solution is Zalmans FanMate, a potentiometer for manual regulation. One can also try to set the voltage of the fan to fixed 5V, but this may be too low for heavy CPU demand. I also recommend a BIOS upgrade (I had the very early 1.10 version) - the voltage for low CPU load is drastically decreased (from 1.3V to 1.1V) which reduces the necessary cooling.

Cheers,
Erwin

---

### Post by lmandrake on 2006-10-17
Any news on this subject?

I just tried the the 6.10 beta with this nic but I had no luck so far. According to syslog the nic is detected and eth0 created

```
eth0: ULi M5263 at pci0000:00:11.0, 00:13:8f:c4:ee:06, irq 58.
```

But I can't use DHCP or setup a static ip adresse

Both /etc/init.d/network restart and ifup eth0 give me 

```
Bind socket to interface: No such device
Failed to bring up eth0
```

And ifconfig just shows me the loopback device. I desperately want to get rid of my pci nic and use the pci slot for something useful ;) Does anybody have some ideas?

---

### Post by Dogers on 2006-10-18
Upgrade to Dapper, it works automatically there. I think we've all given up on Breezy now!

---

### Post by lmandrake on 2006-10-18
As I wrote I'm using the Edgy Beta right now and I don't really want to go back to Dapper. Beside I think whats running with Dapper should also work with Edgy.

---

### Post by Dogers on 2006-10-18
Ah, sorry, you sort of did :)

I think it's to do with a specific kernel version, but I'm not sure which? I would have thought that Eft would have the same or higher version than Dapper? One to log in Bugzilla I think!

---

### Post by GameManK on 2006-10-18
> **lmandrake said:**
> Any news on this subject?[snip]

Hmm... works fine for me in edgy and dapper

have you tried using "sudo dhclient eth0" instead of ifup?

---

### Post by lmandrake on 2006-10-25
It's working now :) For whatever reason the nic is now working as eth1 although only eth0 appears in /var/log/messages. I'll look into this in the next days.

---

### Post by enervation on 2006-11-28
Any updates on how to make this work for a (k)ubuntu/linux noob?

---

### Post by BDNiner on 2007-06-27
I have an ASRock P4vm890 and was having the same problem. it was really frustrating me but this high pitched beep/ring from the computer was annoying me even more. I discovered that the noise was coming from my processor, i replaced the 3.2GHz with a spare 1.8GHz that i had lying around and the noise is gone and my NIC works. Must be ghosts.

---

### Post by Power_Pickle on 2007-12-24
I have the same problem with the 386 Gutsy release with a 939Dual SATA2. AMD64 works fine with the onboard NIC but that won't fly with my Radeon 850XT.

Anyway, I noticed that my switch was showing no connection (layer one thru two,) but I had networking in Windows. I finally scrutinized the Network Tools and noticed it was showing no MAC address for the interface. This is obviously a driver issue.

I'm going back to reviewing this thread to see what I can try.

---

### Post by archimedes1981 on 2008-04-26
everything was already there.
i typed:
sudo rmmod tulip
ERROR: Module tulip does not exist in /proc/modules
sudo apt-get install tulip
it finished ok but then
sudo rmmod tulip
ERROR: Module tulip does not exist in /proc/modules
again

help pls?
btw i want this for my ethernet not SATA drive

---

