---
title: "I desperately need to fix ethernet in Ubuntu (nFORCE 4) ..."
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by kargath64 on 2006-08-07
... or move to another distribution.  It's gotten to that stage.  Since internet access is so central to Ubuntu and its packages system, I cannot continue to work without it (I use an ADSL modem).  

My comp specs:
PIONEER 110D DVD+-RW burner
AMD64 3800+ dual core cpu
ASUS A8N-VM-CSM motherboard (integrated sound, *ethernet*) (nforce based)
Dual booting with windows XP Home
NVIDIA GeForce 6600GT graphics card  (Gigabit brand board)
Dapper AMD64 edition

I have tried installing the NVIDIA-blabla64.run package - which gloriously killed my system and X server.  I have read that there is an OSS clone of the driver called 'forcedeth', but their offical page says that it's part of the kernel now, and it only seems to support nforce 3 and less.  

Also, the network monitor widget in GNOME complains that there is 'no such device'.

Does anyone know of how I can get the nforce ethernet working, and therefore let me upgrade my system from "basic compile and OO.org" to something approaching normal functionality?

Or, if Ubuntu cannot support my hardware, can anyone recommend me another distribution which can?

Your help would be much appreciated with this.

---

### Post by AndrewShugg on 2006-08-13
It doesn't look to be for the faint of heart, but this HOWTO may help you get the official Nvidia drivers working, which in turn will hopefully bring the nForce 4 ethernet controller along with it.

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

I have an nforce4 based system myself where the eth0 is recognised by Ubuntu 6.06 using the 'forcedeth' driver, but nothing can actually go in or out the interface.  If I get it working I will reply here.

Andrew S.

---

### Post by AndrewShugg on 2006-08-13
The following wiki page may also be helpful to get the official Nvidia drivers installed for your Nforce 4 controller.

[https://help.ubuntu.com/community/NvNetInstallation](https://help.ubuntu.com/community/NvNetInstallation)

Andrew S.

---

### Post by azmrb on 2006-08-13
I have the same MB and nvidia 7600 video card.  Dapper64 installed the forcedeth driver during installation but it didn't work because of the documented problem on dual-boot machines where windoze leaves the ethernet card in an unusable state.  I had to shutdown, disconnect the power, unplug the ethernet cord and wait a few minutes, then reconnect and boot straight into dapper64.  
Then I could download updates and that updated forcedeth from the default version 0.48 to 0.54 which reinitializes the ethernet card.

I did NOT have to install the nforce drivers from nvidia.  I only installed the video drivers from nvidia.

---

### Post by RichardSchollar on 2006-08-13
My motherboard uses the NForce 430 chipset and I dual boot using XP and Ubuntu.  I was completely unable to connect to the internet thru Ubuntu until I installed a separate ethernet card (just a cheap one - 3Com approx US$17).  I subsequently found that after I installed all the latest updates following achieving internet access using my new 3com adapter, I was able to connect to the internet using my original NForce 430 adapter.  A right royal pain...

Richard

---

### Post by AndrewShugg on 2006-08-14
> **azmrb said:**
> I have the same MB and nvidia 7600 video card.  Dapper64 installed the forcedeth driver during installation but it didn't work because of the documented problem on dual-boot machines where windoze leaves the ethernet card in an unusable state.  I had to shutdown, disconnect the power, unplug the ethernet cord and wait a few minutes, then reconnect and boot straight into dapper64.  
Then I could download updates and that updated forcedeth from the default version 0.48 to 0.54 which reinitializes the ethernet card.

I did NOT have to install the nforce drivers from nvidia.  I only installed the video drivers from nvidia.

What documented problem is this?  I haven't heard of it before, can you point me to it?

I'm not sure if that was the (only) problem I was experiencing, because I booted my PC from a cold start with the Dapper live/install CD.  At least I'm pretty sure that's what I did ... I'll have to do it again tomorrow and see if it works, including power & ethernet cables disconnected first.

Andrew S.

---

### Post by azmrb on 2006-08-14
> **AndrewShugg said:**
> What documented problem is this?  I haven't heard of it before, can you point me to it?

I'm not sure if that was the (only) problem I was experiencing, because I booted my PC from a cold start with the Dapper live/install CD.  At least I'm pretty sure that's what I did ... I'll have to do it again tomorrow and see if it works, including power & ethernet cables disconnected first.

Andrew S.

I found it here..
[http://www.ubuntuforums.org/archive/index.php/t-186848.html](http://www.ubuntuforums.org/archive/index.php/t-186848.html)

My problem went away when I got the first big batch updates from security
that updated forcedeth from version 0.48 to 0.54 which is the 2 versions mentioned in this post.

---

### Post by AndrewShugg on 2006-08-17
> **azmrb said:**
> I found it here..
[http://www.ubuntuforums.org/archive/index.php/t-186848.html](http://www.ubuntuforums.org/archive/index.php/t-186848.html)

My problem went away when I got the first big batch updates from security
that updated forcedeth from version 0.48 to 0.54 which is the 2 versions mentioned in this post.

Brilliant, I've booted the box up from cold and eth0 came online. Hot dog. Thanks for the pointer.

Andrew S.

---

### Post by zoro on 2006-08-18
I've been having this exact problem - I'll give it a go later on if I can be bothered to go back to Ubuntu.
It's an endless stream of problems ... :/

---

### Post by azmrb on 2006-08-18
> **zoro said:**
> I've been having this exact problem - I'll give it a go later on if I can be bothered to go back to Ubuntu.
It's an endless stream of problems ... :/

zoro, I urge you to give this a try and give Ubuntu a fair evaluation.  I am more and more pleased as I use it.

---

### Post by zoro on 2006-08-19
Ah I know it's good, don't worry.

Myself and linux have a bit of a love hate relationship you see - I love it, but it hates me :)

---

### Post by droogy on 2006-08-19
How do you tell if you are using the forcedeth drivers?  I have an nforce4 board and have never had a problem w/ ethernet other than some slow speeds.  Would forcedeth improve speeds?

---

### Post by spd106 on 2006-08-19
As said earlier, forcedeth is integrated with the kernel. This will show you if forcedeth is currently loaded```
 lsmod | grep forcedeth
``` and this will show you which version you have ```
dmesg | grep forcedeth
```

---

### Post by zoro on 2006-09-07
Just by way of an update - it would appear that this particular problem didnt exist in 64 bit Ubuntu Dapper (6.06, and 6.06.1)
And it has been fixed in the latest 32 bit Dapper (6.06.1) - I have my nforce4 motherboard (MSI K9N) running happily with both Ethernet ports up after a clean install

In case someone has this problem in future!

---

### Post by kargath64 on 2007-03-07
Crossposted from my other obsolete topic:

Hi there!

I recently re-installed Ubuntu Dapper Drake onto my machine (dual-booting), and I decided to have another go at trying to get my internet working, but despite my best efforts, I have been unable to get it to work.  

I have installed the nFORCE nvnet driver from the nVIDIA site using the .run package.  I have attempted to edit my config file at /etc/modprobe.d/ to configure linux to use nvnet.  (I edited the aliases file.)  Yet still nothing happens.

```
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
alias net-pf-10 ipv6
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

#CUSTOMISED SECTION
alias eth0 nvnet
alias forcedeth off

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore


```
That's my edited aliases file, with the two lines I was told to add by the nVIDIA readme.

> Configuration

The installer does not update configuration files.  After installing the drivers, configure the system to use the drivers by using the distribution's built-in configuration mechanisms for networking and sound, or edit the required files manually.
Module Configuration File Location

Module configuration files are different for 2.4 and 2.6 series kernels. The various Linux distributions also differ in how they handle module configuration.

    * For distributions based on a 2.4 series kernel, the module configuration file is typically called /etc/modules.conf.

    * For distributions based on a 2.6 series kernel, the module configuration file is typically called /etc/modprobe.conf. Some distributions use a subdirectory, /etc/modprobe.d/ , to hold individual configuration files for sound modules, etc. 

> Other distributions
If the distribution you are using provides a configuration mechanism for network drivers, use it to select the nvnet driver module for use with the nForce ethernet device, and to set the networking parameters (IP address, etc.) for the interface. Otherwise, manually edit the module configuration file.

If your configuration file already contains an entry for the forcedeth driver (an open-source network driver that supports the nForce network controller), that entry needs to be commented out with a # or removed:

# alias eth0 forcedeth

Add the following lines to the configuration file:

alias eth0 nvnet
alias forcedeth off

If your system has multiple ethernet interfaces, you may need to use 'eth1'  or higher in place of 'eth0'.
That's the relevant sections of the readme.


My computer specs are as follows.
ASUS A8N-VM-CSM mobo (NFORCE4 based, with inbuilt ethernet and sound)
AMD64 3800+ dual core CPU
160GB HDD
NVIDIA 6600GT graphics card
I also dual-boot with WinXP Home.

I connect to the internet via an ADSL modem.  It's a D-Link DSL-502T, and it connects to my computer via the ethernet port.  When I plug it in in Windows, it assigns me an address via DHCP (I do not use static IPs).  The IP of the modem itself is 10.1.1.1 .

```
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 10.1.1.2
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        Default Gateway . . . . . . . . . : 10.1.1.1
```
That's the output of ipconfig in Windows.

The network monitor traylet in Ubuntu, when set to eth0, consistently shows 0 packets sent and recieved, even though it detects plugging and unplugging.

I really, REALLY would appreciate help with this.  Not being able to use Synaptic or go on the Internet is really frustrating.

-------------------------------------

OK, since I posted that, I tried the "disconnect power" trick, and managed to get packets on eth0, and even my standard DHCP address appeared after trying "ifconfig eth0".  
ping [www.google.com](www.google.com) 
worked, and noticably caused traffic on the network monitor gizmotraylet, and definitely caused activity on my ADSL modem.  However, links, synaptic and Firefox are still unable to access outside.  Firefox just comes up with an error page instantly.  Any suggestions?

(Also, I tried a burnt downloaded version of Feisty, but the situation was the same there.)

:frown:

---

### Post by zoro on 2007-03-07
The problem disappeared in Edgy for me ...

---

### Post by Mr. C. on 2007-03-07
What is your ipconfig info?

ipconfig -a

---

### Post by zoro on 2007-03-07
I'll post it later if you want, but basically, I have network connectivity and everything is fine and dandy

---

### Post by kargath64 on 2007-03-09
I wish I was that lucky, zoro. :/


```


The below lines are dmesg output when fed to grep using search strings "nvnet" and "forcedeth"
[   30.989962] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
[   31.502951] eth0: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:14.0
[   39.541605] nvnet: module license 'NVIDIA' taints kernel.


The below lines are lsmod output when fed to grep using search strings "nvnet" and "forcedeth"
nvnet                  78632  0 
forcedeth              27908  0 

The below lines are output of ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:F2:01:55:63  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::215:f2ff:fe01:5563/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12842 (12.5 KiB)  TX bytes:13909 (13.5 KiB)
          Interrupt:225 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



The following is the excerpt of a truncated ping session, proving ping goes through:

PING www.google.com (66.102.7.99) 56(84) bytes of data.
64 bytes from www.google.com (66.102.7.99): icmp_seq=1 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=2 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=3 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=4 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=5 ttl=242 time=213 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=6 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=7 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=8 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=9 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=10 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=11 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=12 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=13 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=14 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=15 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=16 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=17 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=18 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=19 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=20 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=21 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=22 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=23 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=24 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=25 ttl=242 time=213 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=26 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=27 ttl=242 time=230 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=28 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=29 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=30 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=31 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=32 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=33 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=34 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=35 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=36 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=37 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=38 ttl=242 time=220 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=39 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=40 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=41 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=42 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=43 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=45 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=46 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=47 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=48 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=49 ttl=242 time=223 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=50 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=51 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=52 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=53 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=54 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=55 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=56 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=57 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=58 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=59 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=60 ttl=242 time=215 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=61 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=62 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=63 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=64 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=65 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=66 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=67 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=68 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=69 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=70 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=71 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=72 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=73 ttl=242 time=212 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=74 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=75 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=76 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=77 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=78 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=79 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=80 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=81 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=82 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=83 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=84 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=85 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=86 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=87 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=88 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=89 ttl=242 time=212 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=90 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=91 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=92 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=93 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=94 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=95 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=96 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=97 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=98 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=99 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=101 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=102 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=103 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=104 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=105 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=106 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=107 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=108 ttl=242 time=204 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=109 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=110 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=111 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=112 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=113 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=114 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=115 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=116 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=117 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=118 ttl=242 time=204 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=119 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=120 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=121 ttl=242 time=211 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=122 ttl=242 time=210 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=123 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=124 ttl=242 time=209 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=125 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=126 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=127 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=128 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=129 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=130 ttl=242 time=208 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=131 ttl=242 time=217 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=132 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=133 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=134 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=135 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=136 ttl=242 time=205 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=137 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=138 ttl=242 time=206 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=139 ttl=242 time=207 ms
64 bytes from www.google.com (66.102.7.99): icmp_seq=140 ttl=242 time=207 ms
64 bytes from mc-in-f99.google.com (66.102.7.99): icmp_seq=141 ttl=242 time=208 ms
64 bytes from mc (66.102.7.99): icmp_seq=142 ttl=242 time=204 ms
64 bytes from mc (66.102.7.99): icmp_seq=143 ttl=242 time=206 ms
64 bytes from mc (66.102.7.99): icmp_seq=144 ttl=242 time=212 ms
64 bytes from mc (66.102.7.99): icmp_seq=145 ttl=242 time=216 ms
64 bytes from mc (66.102.7.99): icmp_seq=146 ttl=242 time=210 ms
64 bytes from mc (66.102.7.99): icmp_seq=147 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=148 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=149 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=150 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=151 ttl=242 time=211 ms
64 bytes from mc (66.102.7.99): icmp_seq=152 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=153 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=154 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=155 ttl=242 time=209 ms
64 bytes from mc (66.102.7.99): icmp_seq=156 ttl=242 time=212 ms
64 bytes from mc (66.102.7.99): icmp_seq=157 ttl=242 time=211 ms
64 bytes from mc (66.102.7.99): icmp_seq=158 ttl=242 time=210 ms
64 bytes from mc (66.102.7.99): icmp_seq=159 ttl=242 time=211 ms
64 bytes from mc (66.102.7.99): icmp_seq=160 ttl=242 time=210 ms
64 bytes from mc (66.102.7.99): icmp_seq=161 ttl=242 time=212 ms

--- www.google.com ping statistics ---
161 packets transmitted, 159 received, 1% packet loss, time 160078ms
rtt min/avg/max/mdev = 204.651/209.311/230.403/3.178 ms


The following is the current contents of my aliases file in:

# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
alias net-pf-10 ipv6
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

#CUSTOMISED SECTION
#alias eth0 nvnet
#alias forcedeth off

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore



And the following is my blacklist file:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


#CUSTOM
#blacklist forcedeth


The following is the results of seaching for and trying to run "ipconfig"
kargath64@KIARAC:/usr/lib/klibc/bin$ ./ipconfig
./ipconfig: no devices to configure
kargath64@KIARAC:/usr/lib/klibc/bin$ ./ipconfig -a
./ipconfig: invalid option -a


```

---

### Post by Mr. C. on 2007-03-09
kargath64, I'm confused about where you are now.  You seem to have packets flowing (albeit, with some pretty high latency), so is the only trouble you're having DNS lookups (no name->IP translations) ?

If so, this is no longer a NIC/driver issue, rather its a DNS configuration issue.

Please let me know if this is a current assessment.

MrC

---

### Post by kargath64 on 2007-03-09
Well I can only get pings working if I disconnect power from my comp for 5min and then reconnect and boot straight into Dapper.
DNS appears to be working for ping, since [www.google.com](www.google.com) gets translated into an IP address of some sort (see previous post).

I really have no idea what is wrong with everything else except ping.  Firefox complains it cannot make a connection to [INSERTSITENAME], and links and Synaptic complain similarly. :confused: 

If there's any more diagnostics you need me to run, please tell me.

---

### Post by Mr. C. on 2007-03-09
Let's clear up some things by using the low-level tools.  Ignore the browsers, mail clients, etc.  If the stuff below doesn't work, they cannot either.

1) If ping'ing an IP address work reliably, your network is reliable enough to go to the next step.

2)  Now onto DNS lookups.  If the command:

```
  nslookup *somehostname.com yourDNSserverIP*
```
works and translates the somehostname.com into an IP address, like :

```
Non-authoritative answer:
Name:   apple.com
Address: 17.254.3.183
```
Then you know that DNS server is responding.  Try several other names, and try ALL of the IP addresses you were given by your ISP.

3)  Exaxmine the file /etc/resolv.conf.  There should be 1 to 3 lines that say 

 ```
nameserver *yourDNSServerIP*
```
again, where those IPs match what we just discussed.

If DNS is not configured, hostname -> IP address translation cannot occur, and every application that uses some hostname will fail.

Let me know where we are.
MrC

---

### Post by kargath64 on 2007-03-09
Well, I was never provided with a list of DNS addresses from my ISP.  Is there any way to get that information from Windows?

I'll just re-boot into Dapper right now and try as much as I can of your diagnostics.  Thanks so much for helping so far.

---

### Post by kargath64 on 2007-03-09
kargath64@KIARAC:~$ nslookup google.com
Server:         10.1.1.1
Address:        10.1.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.187.99

kargath64@KIARAC:~$ nslookup deviantart.com
Server:         10.1.1.1
Address:        10.1.1.1#53

Non-authoritative answer:
Name:   deviantart.com
Address: 69.28.181.43

kargath64@KIARAC:~$ nslookup deviantart.com
Server:         10.1.1.1
Address:        10.1.1.1#53

Non-authoritative answer:
Name:   deviantart.com
Address: 69.28.181.43

kargath64@KIARAC:~$ nslookup yahoo.com
Server:         10.1.1.1
Address:        10.1.1.1#53

Non-authoritative answer:
Name:   yahoo.com
Address: 216.109.112.135
Name:   yahoo.com
Address: 66.94.234.13

kargath64@KIARAC:~$ cat /etc/resolv.conf
nameserver 10.1.1.1


Please note: 10.1.1.1 is the default address of my modem itself.  I do not have a router.  I know that my modem functions as a DHCP server... it might be working as a DNS server too.  Is that even possible?

---

### Post by zoro on 2007-03-09
Set your network card to dynamic - allow your modem to give you the settings that it knows are correct.

---

### Post by kargath64 on 2007-03-09
So how do I do that in Ubuntu?

---

### Post by zoro on 2007-03-09
Did you try google? :)

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

> Configuring DHCP address for your network card

If you want to configure DHCP address you need to edit the /etc/network/interfaces and you need to enter the following lines replace eth0 with your network interface card

sudo vi /etc/network/interfaces

# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp


try that

---

### Post by kargath64 on 2007-03-09
Thanks for the link mate, I'm rebooting to try that out right now. :)

---

### Post by kargath64 on 2007-03-09
OK, that's weird.  The lines were already there ... now what can I try?

Contents of /etc/network/interfaces ...
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



```

---

### Post by Mr. C. on 2007-03-09
kargath64,

It is good that you ran the nslookup commands, however they told us what you already knew - that DNS is configured to come from your modem, and this is what you *do not* want. 

There's no need to google-this and google-that; some of the responders here to do not understand the problem, and are sending you on a wild-goose chase.

You need a DNS server that works with your system consistently.  It is clear that using the DNS of modem  (10.1.1.1) works sometimes; however, these freebie modems have poor and unreliable DNS support.  Go to your ISPs website, find their help and support area, and lookup the DNS servers to use.  If you cannot find it, contact them, and they will give you these server IPs.  Once you have those, configure them in the Networking panel, and this problem will be solved.

Its in your hands now,
MrC

---

### Post by kargath64 on 2007-03-10
THANK YOU SO MUCH EVERYONE - it works now!   I might wikify the process if I have the time.

---

### Post by Mr. C. on 2007-03-10
That's great news; and thanks for updating us.

Best of luck,
MrC

---

