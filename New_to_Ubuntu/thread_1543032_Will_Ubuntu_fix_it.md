---
title: "Will Ubuntu fix it"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by viking350 on 2010-07-31
Hey guys I just wanted to ask if you know if Linux is going to fix the problem with Ubuntu it will not work on my hard drive Ubuntu 1.04 lucid lynx and i just want to know are they going to fix the graphics problem because thats the only reason it wont work and i want to know will 10.10 be like this i am currently running 9.04 but I really want to upgrade I do not have a old computer its a Dell Dimension 2400 (2005 model) with a Intel processor and currently running gnome as my desktop environment so I just want to know the word on the street about 10.10

---

### Post by cwwilson721 on 2010-07-31
> **viking350 said:**
> Hey guys I just wanted to ask if you know if Linux is going to fix the problem with Ubuntu it will not work on my hard drive Ubuntu 1.04 lucid lynx and i just want to know are they going to fix the graphics problem because thats the only reason it wont work and i want to know will 10.10 be like this i am currently running 9.04 but I really want to upgrade I do not have a old computer its a Dell Dimension 2400 (2005 model) with a Intel processor and currently running gnome as my desktop environment so I just want to know the word on the street about 10.10That hurt to read. Try a PERIOD every once in awhile.

And, what do you want fixed? I'm thinking graphics issue. But what is the actual problem?

---

### Post by viking350 on 2010-07-31
well every time I try to go higher than 9.10 to install, as soon as its done and I reboot my screen just keeps flashing and I want to know if the Graphics will be different with this version.

---

### Post by fancypiper on 2010-07-31
You didn't mention what video chipset your box has.  Some video chip makers have no interest in releasing drivers for Linux. For Linux, I have read that nVidia and ATI are better than intel.

Open a terminal and command:

sudo lshw|less

Scroll down and look for something like this:
```
        *-display
             description: VGA compatible controller
             product: G70 [GeForce 7800 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:fb000000-fbffffff memory:d0000000-dfffffff(prefetchable) memory:fc000000-fcffffff ioport:6c00(size=128) memory:fd000000-fd01ffff(prefetchable)
```

---

### Post by howefield on 2010-07-31
> **viking350 said:**
> i just want to know are they going to fix the graphics problem

What make/model of graphic card are you using, what problem are you referring to ?

> i want to know will 10.10 be like this


Hang out in the Maverick forum for a while, you might even ask the question there.

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

> I do not have a old computer its a Dell Dimension 2400 (2005 model)

I'd say that is old. Technology ages real fast ;-)

---

### Post by viking350 on 2010-07-31
description: Space-saving Computer
    product: Dimension 2400
    vendor: Dell Computer Corporation
    serial: 137CM81
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=space-saving cpus=1 power-on_password=enabled uuid=44454C4C-3300-1037-8043-B1C04F4D3831
  *-core
       description: Motherboard
       product: 0F5949
       vendor: Dell Computer Corp.
       physical id: 0
       version: A01
       serial: ..CN70821592515F.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05 (12/02/2003)
          size: 64KiB
          capacity: 448KiB

---

### Post by QIII on 2010-07-31
According to specs I found on the web, that has Intel Extreme Integrated Graphics.  

The X server has changed since Jaunty.  Many older drivers will no longer work.  That is not something that Canonical can fix.  Drivers are written and maintained by the OEMs, not by those who produce OSes.  It may be that we can get you running on the open source drivers.

Try to run the LiveCD in a Live session.  If you are not able to, I suspect your graphics driver is not compatible with X.

---

### Post by -kg- on 2010-07-31
From the [Dell Documentation Page]("http://support.dell.com/support/edocs/SYSTEMS/dim2400/en/sm_en/specs.htm") for the Dimension 2400:

> Video controller
	

integrated Intel 3D Extreme Graphics

Not real helpful as far as what kind of video controller chipset it uses.  [Wikipedia]("http://en.wikipedia.org/wiki/Dell_Dimension") was a bit more helpful:

> 845GV chip set

This is listed under the "Video Controller" column.  Of course, that's what's listed for the Motherboard chipset, as well.

Remember, Google is your friend!
Since this is a Dell computer, you might find more information in the Dell Support sub-forum on this site.

---

### Post by sandyd on 2010-07-31
have you tried running with "nomodeset" or using the graphics drivers from either the xorg-updates ppa or the xorg crack pushers ppa? (try the xorg -updates ppa first before x crack...). Just add the ppa, and go to update-manager and upgrade everything.

---

### Post by Rubi1200 on 2010-07-31
Post the output of
```
 
lspci | grep VGA

```
 
If you have an i8xx Intel chipset then you need to boot using the i915.modeset=1 parameter.

---

### Post by Kay The Bantu on 2010-07-31
> **Rubi1200 said:**
> Post the output of
```
 
lspci | grep VGA

```
 
If you have an i8xx Intel chipset then you need to boot using the i915.modeset=1 parameter.

I had the same problem, also my X used to crash when I tried to play videos etc, I added the following ppa [HTML]http://ppa.launchpad.net/glasen/intel-driver/ubuntu[/HTML] and the issues i had are all but gone:D

---

