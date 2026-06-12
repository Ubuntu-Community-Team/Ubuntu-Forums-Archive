---
title: "Realtek RTL8139 not detected"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by richardi on 2007-04-12
I recently installed dapper to dual boot with XP and would like to use it all the time but for no network connection. Tried and failed with exisiting USB modem and lots of mucking about with eciadsl. Then gave up and bought a Realtek RTL8139 Family PCI fast Ethernet NIC and a voyager 220V router adsl modem. Works out of the box with XP but not Ubuntu.
In the Graphical Networking admin tool I just have a dialup modem listed - not configured and am stuck. It would appear that the card is not recognised but the realtek website says that the driver is included in the Linux Kernel. Official Ubuntu book and Ubuntuguide are no help- any ideas for a total noob?
Thanks
Richard
ps. this is reposted from a reply to a thread that I just realised was about 6 months old and was buried. Sorry if this is poor form.

---

### Post by renzokuken on 2007-04-12
the rtl driver included in the kernel is buggy and doesnt work for all rtl cards. you need the realtek  WINDOWS drivers for your card and use them together with ndiswrapper. you may have to blacklist the rtl modules too......

there are loads of threads about ndiswrapper and realtek in the forums here, just search

---

### Post by dbott67 on 2007-04-12
Can you post the output of the following commands:
```
dbott@feisty:~$ [COLOR=Red]**sudo lshw -C network**[/COLOR]
           *-network      
                description: Ethernet interface
                [COLOR=Blue]product: RTL8139 Ethernet[/COLOR]
                vendor: D-Link System Inc
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth0
                version: 10
                serial: 00:50:ba:c0:a7:55
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes [COLOR=Blue]driver=8139too[/COLOR] [COLOR=Blue]driverversion=0.9.28[/COLOR] duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:16
```

Also, can you post the output of **lsmod | grep 8139**:
```
dbott@feisty:~$ [COLOR=Red]**lsmod | grep 8139**[/COLOR]
8139too                26112  0 
mii                     5632  1 8139too

```And lastly:
```
dbott@feisty:~$ [COLOR=Red]**lspci | grep Ethernet**[/COLOR]
02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

```-Dave

---

### Post by leshaussebons on 2007-04-12
hey , I have the same kind of network card ( RTL8139) , it is working fine, except that I have really slow transfert rates in SFTP protocol ...

FTP is working fine.

ubuntu version 6.06 server - i386 ( I have a 6.10 server on another box, exactly the same hardware, and I experience the same slowdowns in SFTP )

I was told to look for some new drivers, must I change the ones from the kernel too, or this wont change anything ?

```
pierre@cthulbuntu:/var/log$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:50:fc:47:12:31
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1000-10ff iomemory:40000000-400000ff irq:177
```

```
pierre@cthulbuntu:/var/log$ lsmod | grep 8139
8139cp                 24960  0
8139too                29696  0
mii                     7040  2 8139cp,8139too
```



```
pierre@cthulbuntu:/var/log$ lspci | grep Ethernet
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

thank you !!

---

### Post by richardi on 2007-04-12
Thanks both for your replies and apologies for the delay - I have to log off ubuntu and restart in XP and vice versa to try things out and get back on the internet again.

I entered commands as suggested and post the outputs in one go below:

> richard@richard-desktop:~$ sudo lshw | grep network
Password:
        *-network UNCLAIMED
richard@richard-desktop:~$

richard@richard-desktop:~$ sudo lshw | grep -A 15 network
        *-network UNCLAIMED
             description: Ethernet controller
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:d8001000-d80010ff ioport:e400-e4ff irq:11



richard@richard-desktop:~$ lsmod | grep 8139



richard@richard-desktop:~$ lspci | grep Ethernet
0000:00:0a.0 Ethernet controller: Unknown device 1904:2031 (rev 01)
richard@richard-desktop:~$




hopefully this will make some sense to you!

---

### Post by dbott67 on 2007-04-12
@richardi: As you point out, the driver is not being loaded for the card.  You could try loading it via the command line:
```
sudo modprobe 8139too
```
Check to see if it's loaded:
```
lsmod | grep 8139
```
And check to see if the network card is detected:
```
sudo lshw -C network
```
It should return something similar to:
```
dbott@feisty:~$ [COLOR=Red]**sudo lshw -C network**[/COLOR]
           *-network      
                description: Ethernet interface
                [COLOR=Blue]product: RTL8139 Ethernet[/COLOR]
                vendor: D-Link System Inc
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth0
                version: 10
                serial: 00:50:ba:c0:a7:55
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes [COLOR=Blue]driver=8139too[/COLOR] [COLOR=Blue]driverversion=0.9.28[/COLOR] duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:16
```

If this does not work there are a few folks that have compiled a custom kernel in PIO mode (as opposed to MMIO mode, which is the default).  If all of this is making your head spin, you may just want to try to exchange the NIC for a D-Link or something else fairly common.

-Dave

---

### Post by richardi on 2007-04-15
Thanks Dave,
I tried this and it didn't do anything so I looked up d-link pci cards and found this one for sale:
		
	
D-Link DFE-530TX pci ethernet network card

but it seems to use the same RTL8139 chipset as the realtek. Does this mean that it is just as unlikely to be detected or will the fact that it is from a different manufacturer make a difference?

I see from the supported hardware list that both of these pci cards are supposed to work but also find threads from people saying that they don't. 
I'm happy to buy one new card but not half a dozen. What do you think is my safest bet before I make the purchase?

Thanks
Richard

---

### Post by dbott67 on 2007-04-15
HI Richard,

I've got a D-Link DFE-538TX that uses the Realtek 8139 & it has never given me any trouble, so if you can find one of those you may be okay.
```
02:0b.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)
        Subsystem: [COLOR=Red]D-Link System Inc DFE-538TX 10/100 Ethernet Adapter[/COLOR] [1186:1300]
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at b000 [size=256]
        Memory at be800000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

```I also checked out the Hardware page ([here for those that might be interested]("https://wiki.ubuntu.com/HardwareSupport")) and see that some of the more popular ones can be hit & miss.  Give the D-Link a try, and if it doesn't work we'll have to go the ndiswrapper route as Renzokuken suggests.

-Dave

---

### Post by richardi on 2007-04-18
Thanks Dave,
Just installed the D-link card as suggested and hey presto - straight online in Ubuntu to post this!
If it hadn't worked I might have given up but thankfully here we are.
All the best
Richard

---

### Post by stalkingwolf on 2007-06-05
I have the D-Link 530TX in all my desktops and several that I have built for others.  I have yet to have
it not work "out of the box" with any Linux system I have tried.

---

### Post by Robsteranium on 2007-06-10
I followed your suggestions but when I reached the following step nothing was returned:
```
sudo lshw -C network
```
Where might I find better drivers (I'm using an old RTL8139 that only does 10Mbs)?  Is a win/ndiswrapper really the only way?!

---

