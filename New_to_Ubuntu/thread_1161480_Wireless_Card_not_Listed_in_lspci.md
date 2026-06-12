---
title: "Wireless Card not Listed in lspci"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Warpnow on 2009-05-16
I installed a wireless card. The lights on it light up on the back. But lspci doesn't list it, and Ndiswrapper says the hardware is not installed, any idea why ubuntu wouldn't recognize that the hardware has been installed?

---

### Post by paradigm2 on 2009-05-16
> **Warpnow said:**
> I installed a wireless card. The lights on it light up on the back. But lspci doesn't list it, and Ndiswrapper says the hardware is not installed, any idea why ubuntu wouldn't recognize that the hardware has been installed?

Hmm. Do you happen to know what kind of card /maker/model # it is?

Generally where possible in my opinion it is best not to use ndiswrapper anymore, instead it is better usually to opt for native linux drivers.

---

### Post by Warpnow on 2009-05-16
Its an airlink AWLH6070.

But the real issue seems to be that linux doesn't even recognize that the hardware is installed.

---

### Post by pastalavista on 2009-05-16
Try this in terminal ```
sudo lshw | grep pci
```

---

### Post by sandyd on 2009-05-16
is it a.... usb card

```

lsusb

```

---

### Post by albinootje on 2009-05-16
> **Warpnow said:**
> But lspci doesn't list it, and Ndiswrapper says the hardware is not installed

Did you use the right driver in Ndiswrapper ?
Please post the output of this :
```

lsusb
dmesg
ndiswrapper -l

```

Does the card have some on/off button somehow ?

And I assume that you're following this howto :
[http://ubuntuforums.org/showthread.php?t=885987](http://ubuntuforums.org/showthread.php?t=885987)

There's a very slight chance that the vendor has put a different chipset on the same card. I've seen this a few years ago where SMC was shipping pci based wifi cards which worked fine in Linux, but later they sold the same type of cards with a completely different chipset (which didn't work natively in Linux at that time), perhaps that's the reason you're not seeing it properly in lspci ?

---

### Post by Warpnow on 2009-05-16
> **pastalavista said:**
> Try this in terminal ```
sudo lshw | grep pci
```

> chase@chase-desktop:~$ sudo lshw | grep pci
[sudo] password for chase: 
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-pci
          bus info: pci@0000:00:00.0
        *-pci:0
             bus info: pci@0000:00:01.0
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
                bus info: pci@0000:01:00.0
                capabilities: pm msi pciexpress bus_master cap_list
             bus info: pci@0000:00:1b.0
             capabilities: pm msi pciexpress bus_master cap_list
        *-pci:1
             bus info: pci@0000:00:1c.0
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
                bus info: pci@0000:02:00.0
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             bus info: pci@0000:00:1d.0
             bus info: pci@0000:00:1d.1
             bus info: pci@0000:00:1d.2
             bus info: pci@0000:00:1d.3
             bus info: pci@0000:00:1d.7
        *-pci:2
             bus info: pci@0000:00:1e.0
             capabilities: pci bus_master cap_list
                bus info: pci@0000:03:01.0
             bus info: pci@0000:00:1f.0
             bus info: pci@0000:00:1f.1
             bus info: pci@0000:00:1f.2
             bus info: pci@0000:00:1f.3
chase@chase-desktop:~$ 


Its not a USB card. I am pretty sure I used the right driver in ndiswrapper.

---

### Post by sandyd on 2009-05-16
> **Warpnow said:**
> Its not a USB card. I am pretty sure I used the right driver in ndiswrapper.
heres the extremely obvious question.....
are you EXTREMELY 100% sure you have seated the card right.
pull it out and install it again. The power might be on, but that doesn't meen all the contacts are touching

---

### Post by Warpnow on 2009-05-16
> **carlee said:**
> heres the extremely obvious question.....
are you EXTREMELY 100% sure you have seated the card right.
pull it out and install it again. The power might be on, but that doesn't meen all the contacts are touching

I tried this, and then tried moving it to a different PCI slot. None changed the end result.

It really has me baffled. I had this card working in a windows machine.

---

### Post by Warpnow on 2009-05-16
I just switched back to my old Airlink card, which is Atheros, and very easy to install with madwifi.

Wireless N is not worth this much effort. :-p

---

### Post by albinootje on 2009-05-16
> **Warpnow said:**
> I tried this, and then tried moving it to a different PCI slot. None changed the end result.
It really has me baffled. I had this card working in a windows machine.
And which driver was used ? 
And what chipset did the .inf file talk about ?

It is still not clear to me whether lspci showed some unknown device instead of what you expected to see (from lspci) from that howto. .. Just curious whether the company changed the chipset.

And the command "sudo lshw | grep pci" is perhaps useful when you need some specific info, but for a device that is perhaps not recognised properly by the kernel simply "lspci" would have been so much better.

---

### Post by Warpnow on 2009-05-16
> **albinootje said:**
> And which driver was used ? 
And what chipset did the .inf file talk about ?

It is still not clear to me whether lspci showed some unknown device instead of what you expected to see (from lspci) from that howto. .. Just curious whether the company changed the chipset.

And the command "sudo lshw | grep pci" is perhaps useful when you need some specific info, but for a device that is perhaps not recognised properly by the kernel simply "lspci" would have been so much better.

lspci listed no different device when the card was inserted than when it was not. In short, the card's existance was seemingly unrecognized. Why this happened, I have no idea.

---

