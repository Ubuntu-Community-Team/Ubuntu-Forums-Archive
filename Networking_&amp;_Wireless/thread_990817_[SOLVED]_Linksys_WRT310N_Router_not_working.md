---
title: "[SOLVED] Linksys WRT310N Router not working"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by lariosa42 on 2008-11-23
Hello,

I could use your help. I just bought a fancy new WRT310N (firmware version v1.00.1) router and have been trying to configure it.  The installation CD would not autorun, even when I tried opening it in wine.  I have been sifting through various forums for hours trying to solve this.

So far, I hooked up the cable from my ethernet connection to the router, then from the router to my computer, and plugged in the power cord.  Then I typed [http://168.192.1.1](http://168.192.1.1) into Firefox and tried to work through the settings. I clicked on Wireless-->Basic Wireless Settings, and it gives me three options for "Wi-Fi Protected Setup."  One of the options says that if I have a WPS button, to (physically) push it and then click a button in the browser, which I did.  Everything seems fine and a little bar starts filling up that says "Searching for your client device..." The bar fills to 99%, then says "Connection Failure.  Refer back to your client device for instructions."  I don't really know what this means.

Can anyone help?  At the very least, does anyone know a good walk-through guide to setting up this kind of router without the CD?

Stats:
-Running Intrepid 8.10 on a Dell Inspiron 1405E
-(from lspci): Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)



Also, I'm new to this stuff, so please go easy on the lingo.

---

### Post by lariosa42 on 2008-11-23
OK, I solved it.  I opened the [http://192.168.1.1](http://192.168.1.1) window as mentioned above (just type [http://192.168.1.1](http://192.168.1.1) into your browser after the ethernet cables are plugged in), clicked on "Wireless" and then clicked "Manual" under "Wireless Configuration" rather than "Wi-Fi Protected Setup."  I typed in a new SSID and set "SSID Broadcast" to "enabled."  From there, I just needed to enter a new passphrase under "Wireless Security," and also chose "WPA2 Personal" for my security mode, since I heard this is a good way to go.  No need to use the button on the router. For a little extra security (from my wifi stealing neighbors) I went to Administration-->Management and changed my "Router Password." After that, my wireless was working fine (amazingly in fact).   To log in to the router, I had to choose the 128 bit password setting when it prompted me, and then  "WPA and WPA2 Personal."  After than, Ubuntu's Network manager remembered the password for me.

It's too bad that such a linux-friendly company as Linksus didn't work "out of the box," but the easy manual setup above worked fine.  I can definitely verify that the following setup:

  3945ABG Intel PRO/Wireless  card (from a Dell Inspiron 1405 E)
+ Ubuntu 8.10 Intepid Ibex
+ Linksus WRT310N

works very, very well after the initial setup.  Beautiful video streaming, here I come!

Anyway, I hope this helps someone out.

---

