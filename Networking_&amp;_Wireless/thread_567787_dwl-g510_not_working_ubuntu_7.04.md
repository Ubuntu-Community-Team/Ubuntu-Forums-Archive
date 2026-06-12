---
title: "dwl-g510 not working ubuntu 7.04"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by Ituxlinux on 2007-10-05
Hi there! 

I just installed Ubuntu 7.04 on my Desktop PC; and I can't get connected to internet using my wireless card D-Link DWL -G510 (Marvell chip I guess).  This device is NOT present at the Network Manager, but if I use 

 sudo lshw -C network       

*-network:0
      description: Ethernet Interface
      product: 88E8001 Gigabit Ethernet Controller
      vendor: Marvell Technology Group Ltd.
      physical id: a
      bus info: pci@00:0a.0
      logical name: eth0
      version: 13
      serial:00:11:2f:60:4c:14
      capacity: 1GB/s
      width: 32 bits
      clock:  66Mhz
      capabilities: bus_master cap_list ethernet physical tp 10bt 10bt- fd 100bt 100be -fd 1000bt 1000bt -fd autonegotiation
      configuration:autonegatiatio=on broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: iomemory:f7c0000 - f7c03fff ioport:cc00-ccff irq:16

*-network:1 UNCLAIMED
        description: Ethernet controller
        product: Marvell W8300 802.11 adapter
        vendor:Marvell Technology Group Ltd.
        physical id: c
        bus info: pci@00:0c.0
        version: 07
       width: 32 bits
       clock: 66Mhz
       capabilities: bus_master cap_list
       configuration:latency=64
       resources: iomemory :f7e00000 - f7e0ffff  iomemory: f7d00000 - f7d0ffff irq:5

So I'm guessing it's the chip or the driver that is not working, and I can not get any update.

The card is working OK in win xp (I'm using it right  now).

Any help Please!!!!

---

### Post by Lambert on 2007-10-05
> **Ituxlinux said:**
> Hi there! 

I just installed Ubuntu 7.04 on my Desktop PC; and I can't get connected to internet using my wireless card D-Link DWL -G510 (Marvell chip I guess).  This device is NOT present at the Network Manager, but if I use 

 sudo lshw -C network       

*-network:0
      description: Ethernet Interface
      product: 88E8001 Gigabit Ethernet Controller
      vendor: Marvell Technology Group Ltd.
      physical id: a
      bus info: pci@00:0a.0
      logical name: eth0
      version: 13
      serial:00:11:2f:60:4c:14
      capacity: 1GB/s
      width: 32 bits
      clock:  66Mhz
      capabilities: bus_master cap_list ethernet physical tp 10bt 10bt- fd 100bt 100be -fd 1000bt 1000bt -fd autonegotiation
      configuration:autonegatiatio=on broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: iomemory:f7c0000 - f7c03fff ioport:cc00-ccff irq:16

*-network:1 UNCLAIMED
        description: Ethernet controller
        product: Marvell W8300 802.11 adapter
        vendor:Marvell Technology Group Ltd.
        physical id: c
        bus info: pci@00:0c.0
        version: 07
       width: 32 bits
       clock: 66Mhz
       capabilities: bus_master cap_list
       configuration:latency=64
       resources: iomemory :f7e00000 - f7e0ffff  iomemory: f7d00000 - f7d0ffff irq:5

So I'm guessing it's the chip or the driver that is not working, and I can not get any update.

The card is working OK in win xp (I'm using it right  now).

Any help Please!!!!

There is no native driver for this chipset. You will need to use the winxp drivers and a linux app called ndiswrapper. Lots of information can be found here on ndiswrapper. You can search the forums and wiki.ubuntu.com

---

### Post by Ituxlinux on 2007-10-05
I got the wireless card to work following[ [COLOR="Blue"]this[/COLOR]]("http://i-eat-noobs.blogspot.com/"), actually I got internet connection for only 2 minutes, and right now I can see, from my PC, that there are two wireless networks in my area, 

I'm using my notebook to connect to one of them,  but my PC does not connect.

So I guess I have something misplaced in the setup of the wireless card, because I'm looking at the "Connection Information" of both computers and they look very different.

.....................................The PC:......................................notebook
Inteface:.................... Wireless Ethernet (wlan0).....Wireless Ethernet (eth1)
Speed:........................11 Mb/s......................................48 Mb/s
Driver:.........................ndiswrapper..............................ipw3945
IP Address..................111.222.3.444..........................111.222.3.456
Broadcast Address:..0.0.0.0........................................111.222.3333
Subnet Mask:.............0.0.0.0........................................111.111.111.1
Default Route:...........0.0.0.0........................................111.222.3.4
Primary DNS:.............0.0.0.0........................................11.222.33.44
Secondary DNS:........0.0.0.0.......................................11.222.33.44

By comparing this two tables I'm, almost, sure I'm missing something.

Any additional help is more than welcome.
Itux

---

### Post by Ituxlinux on 2007-10-06
Hi there;

I almost solved the connection problem using Ndiswrapper, and the howto I linked in my previous post.

Now the next issue is that anytime I login, my wireless card seems to be inactive, but it tries to connect.  I see the gray circles with the arrows.  in order to get connected I have to repeat the process.  From a directory with the following files I have to do:

sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils-1.9_*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper

After doing this, I see the circles now turning green and I get connected.

So It is anyway to change it and make it more automatic?
Itux

---

### Post by kevdog on 2007-10-06
Just make the ndiswrapper module load at startup:

echo ndiswrapper | sudo tee -a /etc/modules

You should be good to go then without having to type anything.

---

### Post by Ituxlinux on 2007-10-06
Hi there;

Actually I did introduce that module 
I did add "ndiswrapper" to the /etc/modules file.
gksudo gedit /etc/modules

But still I have to repeat the process.

Thanks for the hint anyway.
Itux

---

### Post by kevdog on 2007-10-06
So what doesnt work at startup?? Im kind of confused.

If you boot and then check
lsmod | grep ndiswrapper

This will tell you the module is loaded.  Is this the part that isnt working?? Or is it something else.

---

### Post by Ituxlinux on 2007-10-06
{This will tell you the module is loaded. Is this the part that isnt working?? Or is it something else.}

Well, when  logging in, the module is loaded, the green light in the wireless card is on, it is possible to see what wireless networks are available,  but it is NOT possible to get  connection to the modem until I repeat  the instruction.  I have done this several times in the last two days, and I just wanted it to be more automatic so other users don't have problems.

Any idea?

Thanks

---

