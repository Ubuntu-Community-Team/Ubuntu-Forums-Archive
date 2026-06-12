---
title: "Printer Driver Install Help Needed"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Longtrain on 2011-01-07
I am a newbie, I love Ubuntu and have converted my PC requirements to this OS.  I am trying to install a quality print driver for my Epson 1400.  I found a driver from GutenPrint for this printer. I downloaded the appropriate, (I think) DEB file and started the install with the Ubutu Software Manager, following the install, I get a reinstall button at the right of the screen, and not the usual "Remove" button, which I guess means a good install. 

I don't believe the install worked...

Any help is appreciated.

Thanks,

Tony
Longtrain

---

### Post by JKyleOKC on 2011-01-07
Open your web browser and go to [http://localhost:631](http://localhost:631) (which is a port on your own machine, not an actual outside internet address) to access the CUPS (Common Unix Printing System) interface. Select the "Printers" tab to see whether your printer is installed. If it is, you can modify its settings from the resulting display. If not, select the "Administration" tab and then click on "Add printer" to start the setup.

If you don't get the CUPS display, but instead get an error message, you need to install CUPS by using the Software Center or Synaptic Package Manager. I believe, though, that it's installed automatically when you install Ubuntu -- I know it was on my own systems.

---

### Post by Longtrain on 2011-01-07
Thanks, CUPS is there and the driver version is up to date.  Thanks again...

Tony

---

