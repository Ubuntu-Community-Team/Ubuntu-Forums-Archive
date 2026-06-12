---
title: "Resolution a little too big"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by zer010 on 2009-09-04
I have installed ubuntu 9.04 on my dad's comp.  everything work fine except that the resolution is a little too big.  It's an AMD 1.3Ghz, but NO graphics card.  The resolution is a little big.  The desktop doesn't  quite reach the sides of the monitor.  when I open up a large sized menu, I can't see the bottom of the menu.  I can't scroll down the menu either.  Is there any way I can contain the menus to fit the desktop?  Some help would greatly be appreciated!!!  Right now the resolution is set at 845X625 (i think...running Win, blah).  Thanks!!!

---

### Post by QIII on 2009-09-04
You may not have a "card" because the graphics are integrated on the motherboard.

Could you go to the terminal and type

```
lspci
```

and post the results?

---

### Post by bacardiandwatermelon on 2009-09-04
What resolutions can you choose in the display properties?

---

### Post by zer010 on 2009-09-04
I know i'm running mobo graphics.  I coulgn't put in agraphics card because I don't see anywhere to put one, unless it's a really old on I guess.  I ALWAYS run PCs "naked"(no cover). Only because they're nothing big/new.

---

### Post by QIII on 2009-09-04
lspci will tell us what graphics chipset is being used.

And watermelon has a good question.

---

### Post by zer010 on 2009-09-05
Ok, by request, lspci:

desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8361 [KLE133] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8361 [KLE133] AGP Bridge
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1
=========================================================
Display resolution options are:
832x624 (4:3),  800x600 (4:3),  700x525 (4:3),  640x512 (5:4),  720x450 (16:10),  640x480 (4:3),  and the resolution just keeps goin down to, 320x175 (9:5)

Hope this helps.

---

### Post by CatKiller on 2009-09-05
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by zer010 on 2009-09-05
This problem appears no matter what monitor I hook it up to.  I will say that the only monitors I hook it up to are CRT not LCD.  From the lspci data I provided, is it possible to install some kind of graphics card?  If possible, might that solve the problem, so as I'm not running off mobo graphics chipset?

---

