---
title: "Apply &quot;Extra&quot; visual effects"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by ghettoman962 on 2009-10-11
I'm trying to apply the "extra" visual effects, for wobbly windows and such, but it says "searching for a drivers" or something like that, and then says "Desktop effects could not be enabled" what do I do to get it to work? Do I need to install a driver or something? I'm really new to Ubuntu. thanks

---

### Post by OpenGuard on 2009-10-11
[COLOR=DimGray]System / Administration / Hardware drivers

[/COLOR]Do you see any available drivers listed there ?[COLOR=DimGray]
[/COLOR]

---

### Post by tuxxy on 2009-10-11
If no drivers are listed then post your video card model

---

### Post by ghettoman962 on 2009-10-11
I've never put any card in my computer, and I don't know how to check, sorry I don't know all this stuff yet. how do you do it

---

### Post by Alex566 on 2009-10-11
Go to System>Administration>Hardware Drivers and see if there are any. If so, install/activate them. Then your effects *should* work.

---

### Post by wojox on 2009-10-11
What does this output from a terminal:

```
lspci | grep VGA
```

---

### Post by tuxxy on 2009-10-11
You can run the following command in terminal or use the system monitor to identify your video card
```

lspci | grep VGA
```

---

### Post by ghettoman962 on 2009-10-11
well... sorry but this is what it came up with...

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)


I have no clue what any of that means but hope it helps

---

### Post by sandyd on 2009-10-11
there are currently not really any drivers for your card.
however, it seems to work in hardy....
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/56791](https://answers.launchpad.net/ubuntu/+source/xorg/+question/56791)

also
[http://ubuntuforums.org/archive/index.php/t-675870.html](http://ubuntuforums.org/archive/index.php/t-675870.html)

---

### Post by ghettoman962 on 2009-10-11
i just typed in "sudo lshw -C display" and got:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

what does it mean and does it help?
I'm thinking I need to Install a driver or something, how do I do that?

---

