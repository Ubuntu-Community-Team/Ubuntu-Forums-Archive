---
title: "Belkin (BroadCom) wifi card not functioning"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by BlueNoteMKVI on 2005-11-02
I have a Belkin PCMCIA wifi card (model number F5D7011) that I'm trying to get working in my Toshiba Sattelite laptop.  It's giving me fits.  This card has the Broadcom chipset.  I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=25683&highlight=pcmcia](http://ubuntuforums.org/showthread.php?t=25683&highlight=pcmcia)

But no luck.

NDISWrapper installs fine.  The CD that comes with the card has two drivers, bcmwl5.inf and bcmwl5s.inf.  If I install the bcmwl5.inf driver, ndiswrapper -l shows "bad driver" or something like that.  With bcmwl5a.inf I get "driver present, hardware present."  Obviously this is the correct choice.  The output from lspci shows the card and recognizes it properly as a Broadcom network controller.  However, the lights on the card itself do not come on and I cannot get it to connect to my access point.  The PCMCIA slots both show up as empty in the KDE control panel.  Inserting the card does make messages appear in dmesg and changes the output of lspci.  I have tried both PCMCIA slots with the same results in either one.

This card worked fine yesterday under Xandros, but I dumped Xandros in favor of Ubuntu (got tired of dealing with it).  I seem to remember that Xandros was using NDISWrapper as well, but I couldn't swear to that.  It's been a while since I set it up.

What am I doing wrong here?

---

### Post by spd106 on 2005-11-02
Try **lsmod** to see if the ndiswrapper modules is loaded. If not then **sudo modprobe ndiswapper**.
Have you tried changing the radiostate in the driver config file?
Maybe download the latest driver files from the belkin website.

This isn't the prefered solution but as a last resort you could compile ndiswrapper from source. It's up to version 1.5 now, Hoary and Breezy seem to use v1.1. Though I could be wrong. 

Follow the guide in the [wiki]("https://wiki.ubuntu.com/SetupNdiswrapperHowto"). Perhaps a look around the ndiswrapper hardware [list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") would be useful.

---

### Post by BlueNoteMKVI on 2005-11-02
I eventually got it working with a different version of the driver, which I found here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

After installing the new driver I had to:
```
rmmod ndiswrapper
modprobe ndiswrapper
```

Now it works fine, I rebooted and everything came up great.

---

