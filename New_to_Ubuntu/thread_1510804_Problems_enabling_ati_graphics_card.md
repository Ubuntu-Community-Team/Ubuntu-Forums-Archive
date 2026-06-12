---
title: "Problems enabling ati graphics card"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by wigglestix on 2010-06-16
I did a fresh install of ubuntu lucid lynx on my laptop today and i ran into a problem with my ati graphic card.  I have installed ubuntu and many other linux distrobutions in the past with no problems. When i try to enable my graphics card with the hardware drivers utility i get an error saying the installation of the drivers failed.


Her is the last few lines of jockey.log...i can include the whole file if needed.

2010-06-15 22:25:12,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2010-06-15 22:25:12,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2010-06-15 22:25:12,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2010-06-15 22:25:12,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-15 22:25:12,613 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-15 22:25:12,613 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-15 22:25:12,613 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2010-06-15 22:25:12,613 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2903290> about HardwareID('modalias', 'acpi:TOS1900:')
2010-06-15 22:25:12,835 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-15 22:25:13,061 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-15 22:25:13,277 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-15 22:25:16,347 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-15 22:25:19,722 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-15 22:25:19,723 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-06-15 22:25:19,724 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-06-15 22:25:29,227 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-15 22:25:29,398 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches

---

### Post by anewguy on 2010-06-16
I noticed it said it can't find the fglrx module.  If you open Synaptics Package Manager you will fglrx there and can install it.  Perhaps that will solve your problem.

If you can't get to graphics mode, try ctrl/alt and pressing F1 to get a terminal log on.  Once logged on, do the following:

sudo apt-get install fglrx <press enter>

That's all I can think of right now.

Dave ;)

---

### Post by wigglestix on 2010-06-16
> **anewguy said:**
> I noticed it said it can't find the fglrx module.  If you open Synaptics Package Manager you will fglrx there and can install it.  Perhaps that will solve your problem.

If you can't get to graphics mode, try ctrl/alt and pressing F1 to get a terminal log on.  Once logged on, do the following:

sudo apt-get install fglrx <press enter>

That's all I can think of right now.

Dave ;)


I figured this out just moments after i posted this but thanks anyway Dave.


For anybody reading this to enable the driver i installed all the packages that had to do with fglrx and then uninstalled and reinstalled fglrx with apt-get and configured it by running "aticonfig --initial" and reboted.

---

