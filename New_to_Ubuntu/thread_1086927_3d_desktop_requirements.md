---
title: "3d desktop requirements"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by parce7 on 2009-03-04
I just installed Ubuntu on a pretty old pc, HP dc7600.  Im looking to get familiar with it and try a few things to later make the switch permanently from Windows.  I am having a hard time figuring out how to get the 3D desktop started.  Im have not even been able to figure out if this PC will be able to support this.  I was able to get some info about the graphic controller from looking at other post and this is what I came out with:

*-display UNCLAIMED
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0


VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


How can i be sure this will support 3D desktop and if so what would be a good start to setting this up?

Thanks for your help

---

### Post by Kevbert on 2009-03-04
Welcome to Ubuntu.
Regarding the 3D desktop - I assume you mean the 3D cube. What you need is the Compiz Configuration Settings Manager. Just go to Applications-Add/Remove and search for ccsm. Tick the box and apply. Once installed it will be under System-Preferences-Advanced Desktop Effects Settings.

---

### Post by civillian on 2009-03-04
I don't think compiz/beryl/compizfusion (whatever it's called these days) will work with that GPU, because of it's low video memoery size. (It's unlikely that intergrated graphics cards will work (if it's on a desktop computer), and if you want it its probably worth investing in a graphics card (a card like the nVidia 7200 can be bought for peanuts these days and will support the 3D desktop, once drivers are installed which can be quite painless with tools like envy).

Hope this helps.

---

### Post by Kevbert on 2009-03-05
Compiz should work fine. If you have any problems, run ```
compiz
``` in terminal,and install [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") and post back the outputs from them.
Compiz will run on most Intel, Nvidia and ATI cards.

---

### Post by skymera on 2009-03-05
I was able to run Compiz on an Intel G965 graphics chip.
So i think it'll work on yours (945chip?)

---

