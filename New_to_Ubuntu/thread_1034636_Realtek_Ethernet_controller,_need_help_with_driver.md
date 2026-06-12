---
title: "Realtek Ethernet controller, need help with driver in Ubuntu 8.10"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Ronok on 2009-01-08
Hi this is my first post :)
glad to be here

I have a 100% Ubuntu computer, new... 
(MB = asus p5gc-mx 1333, duo core 3ghz, Ubuntu 8.10)

should be fast...but when I get on line (dsl) useing the "on-bord (motherboard) Ethernet rj45" it is slow !

_so I would like to use my new:_

[B]Gigabit PCI Ethernet Adapter Enlga-1320
made by Realtek / Encore electronic[/B]s

I put it in the PCI slot, put the Ethernet jack in before boot, 
and then... no connection ?, 
(I know it needs a Linux / Ubuntu **driver**, right ?)

it came with a CD and has some "Linux" files on it
but:
1) I could not find the "TarBall" or .zip   and
2) the rest of their vague instructions are Way over my head

maybe there is a "packit" that will just do the trick ? 
(but I looked and did not find any)

or

a little cleared **step by step** of 
what to put in the root / sudo
or where to navigate to to make the changes, additions

ok **Thanks** for your help 
Ronok, Seattle

ok I hope this is not too long of a post, 
here is what their linux "README" file in the CD said:
"
<Linux device driver for Realtek Ethernet controllers>

  This is the Linux device driver released for RealTek Ethernet controllers, which are listed as following.
	1. RTL8169S/SB/SC (Gigabit Ethernet with PCI interface)
	2. RTL8168B (Gigabit Ethernet with PCI-Express interface)
	3. RTL8101E (Fast Ethernet with PCI-Express interface)

<Requirements>

  - kernel source tree (supported versions 2.4.x or 2.6.x)
  - compiler/binutils for kernel compilation



<Quick install with proper kernel settings>

  Unpack the tarball :
	unzip r1000_linuxdrv_vxx.zip

  Change to the directory:
	cd r1000

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a




<Force Media Speed>

 The media can be forced to one of the 5 modes as follows.

        Cmd: "insmod r1000 media = SET_MEDIA"
        For example:
         "insmod r1000 media = 0x04" will force PHY to operate in 100Mpbs Half-duplex.

         SET_MEDIA can be:
                _10_Half        = 0x01
                _10_Full        = 0x02
                _100_Half       = 0x04
                _100_Full       = 0x08
                _1000_Full      = 0x10


   Force media type for multiple cards could be performed as:

         "insmod r1000 media=0x04,0x10"

   which force PHY to operate at 100Mbps half-duplex and 1000Mbps full-duplex.



<Advanced feature>

  - Supports Jumbo Frame
  - Hardware Tx/Rx flow control
"

---

### Post by wolfen69 on 2009-01-08
[Here]("http://www.encore-usa.com/download/driver/ENLGA-1320.zip") is the zip file containing the linux driver. just right click it and "extract here". there is a text file in the linux folder with instructions. take your time with it.

---

### Post by Ronok on 2009-01-24
**Thanks** "wolfen69" for your help

I _am **now** able_ to _get on line_ with the:
"Gigabit PCI Ethernet Adapter Enlga-1320"

_but:_
a) loading web pages seems _slow_ ?   &
b) the "system> administration> Hardware Testing"
   says: " running test Internet... **NO Internet Connection**"

I have Quest DSL at 1.5Mbps
speakeasy speed test Now says 1350 Kbps
so that is more or less correct, 
and has been fast over the last few years 
(under W-XP, Before I made 100% switch, to Ubuntu)

BUT loading google> search:"dogs"> any-dog-page> click_home(=google)
each of these 4 transitions takes about 12 Seconds... Grrrrr

I will never go back to MSFT ! but this is a slow irritation
and I know it can be made fast again
I just dont know how
Thanks 

Below is the output of lshw -c network
if that is any help


root@LuoDianNao:/home/ronok# lshw -c network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:22:15:8b:19:e6
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.4 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 10
       serial: 00:06:4f:64:1c:ae
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:42:da:90:ac:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

