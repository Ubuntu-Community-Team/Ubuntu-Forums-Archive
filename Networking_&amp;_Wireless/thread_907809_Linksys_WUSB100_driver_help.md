---
title: "Linksys WUSB100 driver help"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by meteora184 on 2008-09-01
I am a complete noob when it comes to ubuntu, and it would be appreciated if anyone could help me figure out how to get my Linksys WUSB100 driver working.

I do have ndiswrapper installed, but i have no clue how to use it.
My computer is dual booting with windows xp, and that is why i can access the internet right now.
So how would i get this to work, again sorry but i am a complete noob.i tried ndiswrapper to install the rt2870.inf driver file using ndiswrapper -i "asdfjkf" and that it said i believe error on like 97 although i'm not too sure which line it is. I can double check if necessary.
I have some more information, idk if this is helpfull but i was searching this forum and i saw that people asked for it:


lspci -nn
```

00:00.0 Host bridge [0600]: 
Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 
PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:01.0 Modem [0703]: 
Intel Corporation FA82537EP 56K V.92
Data/Fax Modem PCI [8086:1080] (rev 04)
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)

```




lshw -C Network
```

  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:1a:7c:fc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

lsub:
```
Bus 004 Device 004: ID 1737:0070  
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by meteora184 on 2008-09-02
can anyone help me?

---

### Post by milanvora2 on 2008-09-05
wusb100 uses the ralink rt2870 drivers.
install them and you don't need ndiswrapper.
i did it yesterday and it worked very easily. if you need help give me a shout

---

### Post by Douglas Selph on 2008-09-30
I got the linux driver source: 2008_0718_RT2870_Linux_STA_v1.3.1.0.tar.bz2

I successfully compiled it on my Ubuntu system.

Following the installation instructions in README_STA I successfully did step #5 and the first part of step#6:

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

But the last ifconfig step I am completely stuck. I keep getting this error:

linux # /sbin/ifconfig ra0 inet 192.168.0.144 up
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device

I also tried the same procedure on a mandriva linux and the same thing happened. I don't know to make it so that the USB linksys device is registered as an ra0. If I do lsusb I see it on bus007, device 002.

linux # lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 1737:0070  
Bus 007 Device 001: ID 0000:0000  
...

I am logged in as root. Any clues or help would be appreciated. Thanks!
Doug

---

### Post by carronhero on 2009-03-24
I had the same problem with a Linksys WUSB100. The above instructions are right, but not enough. Before compiling by running make you should edit the include/rt2870.h file and add the USB device ID, i.e.:

```

#define RT2870_USB_DEVICES      \
{       \
        {USB_DEVICE(0x1737,0x0070)}, /* Linksys */              \
...

```

for the lsusb output 
```

Bus 001 Device 004: ID 1737:0070 Linksys

```

Then, make and make install as usual.

Hope it works for you.

---

### Post by bradpurvis on 2009-07-11
could someone plz make an easy howto for this?

---

### Post by s7er01ds on 2009-10-11
Don't Know If You Already Have Taken Care Of Your Problem, But Here Is A Tutorial So To Say On How To Do This, You Were Just In The Wrong Forum xD

[http://ubuntuforums.org/showthread.php?p=8086015#post8086015](http://ubuntuforums.org/showthread.php?p=8086015#post8086015)

---

