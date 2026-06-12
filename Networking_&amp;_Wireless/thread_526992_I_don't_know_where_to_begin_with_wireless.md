---
title: "I don't know where to begin with wireless"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by tk03759 on 2007-08-16
I'm completely new on installing wireless cards. I'm trying to get my wireless card working. I'm using Fiesty. The biggest issue I'm having is figuring out where my issue is. I *think* the card is being detected, but I'm not positive. I tried something from a tutorial that I've lost now to get information:

```
lspci -v | less
...
00:10.0 Network controller: National Datacom Corp Unknown  device 0131 (rev 01)
             Subsystem: National Datacom Corp Unknown  device 0131
             Flags: stepping, medium devsel, IRQ 9
             I/O ports at 1070 [size=16]
             I/O ports at 1000 [size=64]
...
```

I'm assuming that means that it's being detected by Ubuntu. From there I'm really lost at where to go. Most guides ask you to connect to the internet, but the computer I'm trying to hook up has no connection other than it's wireless one, which isn't connecting.

I have the windows driver/software installation cd around somewhere if that's useful. The software is called Net Blaster II, which is also on the wireless antenna.

Any help would be greatly appreciated.

---

### Post by bmartin on 2007-08-16
Well... [this]("http://linux-wless.passys.nl/query_chipset.php?chipset=TI") is what I could dig up. According to it, sourceforge.net has [the drivers that should work for you]("http://acx100.sourceforge.net/"), but they're under inactive development; the lastest snapshot I could find is from [2007-01-01]("http://www.cmartin.tk/acx/acx-20070101.tar.bz2"). If you don't feel like putting up a strong fight with potentially impossible results, just skip down to the ============= below.

To compile the source code and install the module, you'll need the linux-headers package for your kernel, as well as build-essential. You could either figure out **every** DEB you need and transfer it or somehow get a wired connection to your machine. I was able to compile/install the module with the following commands:
```
make -C /lib/modules/`uname -r`/build M=`pwd`
make -C /lib/modules/`uname -r`/build M=`pwd` modules_install
```
Unfortunately, installing that module will overwrite the existing kernel module.

Sadly, it's more complicated than that. If you use the route, you need firmware for your chipset, and I'm not sure which one it is. The firmware page can be found [here]("http://acx100.sourceforge.net/wiki/Firmware"). It appears you can extract the firmware using a program found in the script/firmware/ directory (requires compilation of a single file). I imagine you could do that using your existing Windows driver.
================
There's also an acx kernel module. It might work if you simply type **sudo modprobe acx** into a terminal... but hardware detection should've picked that up automatically. If that works, it's much easier than trying to compile a kernel module.

You'll probably still need firmware for this method. Do a Google search for **"modprobe acx" firmware**; that should turn up some useful results.

If you try this, I wish you luck. Personally, considering the hassle, I'd try a different card.

---

### Post by tk03759 on 2007-08-17
the modprobe didn't work and google search isn't good for the firmware, so i think i'll go the route of extracting the firmware from the windows driver. i had a guide earlier that gave me instructions and a how to, so i'll probably use that once i find the windows installation cd. i'll post what i did and how/if it worked when i'm done.  thanks for the input.

---

### Post by tk03759 on 2007-08-17
Okay, so I used this [tutorial]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble") to try installing the windows drivers, but it doesn't seem to have worked. Now ndiswrapper won't even open so that I can uninstall the faulty driver and try again with a different version.

The card id was 15e8:0131 and I'm guessing this means it's not gonna happen. If anyone can enlighten me as to what else might work instead, please do so.

___
Edit: I removed the old drivers with "sudo rm -rf /etc/ndiswrapper" and installed a different set of drivers, but in the left panel of ndisgtk,, it says No Hardware Detected where the Installed Drivers are supposed to be displayed.

---

