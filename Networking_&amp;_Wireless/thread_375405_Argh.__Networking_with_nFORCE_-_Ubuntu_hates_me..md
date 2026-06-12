---
title: "Argh.  Networking with nFORCE - Ubuntu hates me."
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by kargath64 on 2007-03-03
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

---

### Post by MetalMusicAddict on 2007-03-03
Sorry I cant directly answer your question.

I would _REALLY_ use Edgy or even Feisty. I have the same chipset and things work swimmingly. Please do take that because Dapper is LTS it means its a better choice. Edgy works great and Feisty is shaping up nice.

---

### Post by RandomJoe on 2007-03-03
Will the 'forcedeth' driver not work for you?  I have an nForce4 board as well, ASUS P5N32-SLI SE Deluxe, and use it without any trouble.  As a bonus, I didn't have to install extra drivers, they were already there.  I don't recall having to do anything special to get it to work, but I'll go check my notes when I get a chance...

I'm using Dapper as well, no need for Edgy/Feisty unless you just want it.

---

### Post by kargath64 on 2007-03-04
RandomJoe: So how do I set forcedeth to be used then?

MMA:  You mean you have the same mobo or just an nforce 4?

---

### Post by RandomJoe on 2007-03-04
I checked the notes I made, and I didn't do anything special - it Just Worked...  You could try loading the module and see if the interface comes up manually - run 'sudo modprobe forcedeth', then if it loads 'ifconfig eth0' should show you the interface.  It won't have an IP and all that but it would tell you if the module is seeing the hardware and working.

If that works, and for some reason Ubuntu just isn't detecting the chipset properly, you could just add 'forcedeth' to /etc/modules so it would load that module at boot each time.  Reboot, and see if the interface gets configured then.

Hm, I just checked your mobo specs on Newegg, and it says the chipset is an nForce 430B, not nForce 4.  I'm not well-versed on the nForce models, but I think that may be where the difference is.  I can find plenty of search results regarding nForce 4 support in the kernel, but nothing about nForce 430B...

---

### Post by kargath64 on 2007-03-07
I took a look at my old posts and it seems that the last thread I left ( [http://www.ubuntuforums.org/showthread.php?t=231330](http://www.ubuntuforums.org/showthread.php?t=231330) ) got a lot more replies than I knew.  I'll keep my posts to there from now on and request this be locked.

---

