---
title: "network printing on shared windows printers"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Zoomy on 2010-12-31
Pretty much a newbie, but I am having fun experimenting with Ubuntu.  Just bought a new HP laptop g62, and loaded Ubuntu 10.04 LTS - the Lucid Lynx in a dual boot configuration.  Ubuntu had no trouble with drivers, but sound card doesn't play through internal speakers, however works fine with external jack.  Not especially concerned, but would like to know how to fix it.

The biggest mystery is network printing.  To my delight, ubuntu found the windows network just fine.  Also, when browsing network printer, it found the shared printers with the browse button, and allowed me to find and load the correct drivers (laserjet 1018 and canon pixma 6600).  However, print jobs don't materialize, they just vanish to the ether.

Otherwise, impressed.  Ubuntu loves the i3 cpu and everything is nice and quick.

---

### Post by cariboo on 2010-12-31
> Pretty much a newbie, but I am having fun experimenting with Ubuntu. Just bought a new HP laptop g62, and loaded Ubuntu 10.04 LTS - the Lucid Lynx in a dual boot configuration. Ubuntu had no trouble with drivers, but sound card doesn't play through internal speakers, however works fine with external jack. Not especially concerned, but would like to know how to fix it.

Right-click on the sound icon in the upper panel and select Sound Preferences, when the window open up, select the Output tab, and make sure Analog Speakers is selected in the Connector. Then click the Hardware tab and click the Test Speakers buttun to make sure you have mad the right selection.

> The biggest mystery is network printing. To my delight, ubuntu found the windows network just fine. Also, when browsing network printer, it found the shared printers with the browse button, and allowed me to find and load the correct drivers (laserjet 1018 and canon pixma 6600). However, print jobs don't materialize, they just vanish to the ether.

Sharing supported printers is fairly simple, Canon printers aren't very well supported, so you may have to search for a driver for yours. The HP printer should work without any problems, you may have to use hplip, it's in the repositories, or you can also get it from HP's web site.

---

### Post by Zoomy on 2010-12-31
Thanks for  your suggestions, HPLIP is already installed, and the printer driver appeared to install correctly, however issuing a printer test page still yields nothing.  The print queue shows a status of "processing"

As for the built in speakers, tried your suggestions but still no joy.  Any new suggestions?

---

