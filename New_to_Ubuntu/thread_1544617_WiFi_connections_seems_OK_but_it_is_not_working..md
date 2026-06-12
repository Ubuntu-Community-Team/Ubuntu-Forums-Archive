---
title: "WiFi connections seems OK but it is not working."
date: 2010-08-02
forum: New to Ubuntu
---

### Post by GuildedMason on 2010-08-02
So my WiFi connection seems to be up - the Wireless Network Connection tool shows that.
It reads that the connection is Active and 100%.

Under 'Connection Information' I can see an IP Address, Broadcast Address, Subnet Mask, Default Route, Primary and Secondary DNS values.

It also shows a HW Address, the driver (b43), and that security is WPA.

I've noticed the speed is really slow 12Mb/s while my MAC is running at 54Mb/s.

When I do System/Network Tools - select the 'Wireless Interface' and I try to Ping my access point Network Address - I get nothing back.


I've checked the forums and Google - but I am fairly certain the connection is set up properly. So no dice.


It seems as if my WiFi connection is connected correctly - yet it is unable to do anything.


Any ideas/pointers?

---

### Post by TheNerdAL on 2010-08-02
Did you try another browser? What are you trying to do again?

---

### Post by GuildedMason on 2010-08-02
I tried Opera ... but nothing.
I basically have no Wifi activity - other than it seems to be connected ok.

I am just trying to get anything running over Wifi (this is on a netbook - so there is no wired connection).

I am coming to the conclusion that my problem is with the driver.

The netbook has a BCM4312 device in it ... and I guess I must have not installed the driver properly.

---

### Post by TheNerdAL on 2010-08-02
Give us the output of this: 
```
lspci -v | less

```

---

### Post by kerry_s on 2010-08-02
> **GuildedMason said:**
> I tried Opera ... but nothing.
I basically have no Wifi activity - other than it seems to be connected ok.

I am just trying to get anything running over Wifi (this is on a netbook - so there is no wired connection).

I am coming to the conclusion that my problem is with the driver.

The netbook has a BCM4312 device in it ... and I guess I must have not installed the driver properly.

connect to the internet & install "bcmwl-kernel-source" using  synaptic.

---

### Post by GuildedMason on 2010-08-02
Here it goes ...

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)                                  
        Subsystem: Hewlett-Packard Company Device 361a                                                                       
        Flags: bus master, fast devsel, latency 0                                                                            
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 361a
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc80 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fe940000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 361a
        Flags: bus master, fast devsel, latency 0
        Memory at fe880000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 361a
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe938000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
:

---

### Post by GuildedMason on 2010-08-02
I can't connect to the net - the netbook has no wired connector.

I have downloaded the bcmwl-kernel-source file - but it will not install.
The error reads - 

Error: Dependency is not satisfiable: dkms

---

### Post by beew on 2010-08-02
Did you also install the b43-fwcutter? You need to extract the firmware from the card before the b43 drivers in the bcmwl- kernel-source- file can install.

---

### Post by GuildedMason on 2010-08-03
Yeah - did all that and no luck.

I finally downloaded the HP MIE Linux Image - then reinstalled that - and hey presto, it is all working as expected now.

I don't really like the User Interface - but I guess I'll get used to it - and well, this way it works.

Thanks for all the tips.

---

