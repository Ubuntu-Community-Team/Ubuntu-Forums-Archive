---
title: "Invalid wireless driver"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by Radovitch on 2007-02-24
Hi,
I have a wireless speedtouch 121g adapter on my PC. I've installed ndiswrapper-utils and copied the Speedtouch driver file, via the Speedtouch link posted on the ndiswrapper site, to my home folder. However when I try to install it with the ndiswrapper -i command it gives me a 'couldn't copy line 135' error. When I then run the  -l command it says 'invalid driver'. I have even tried using the ndisgtk wireless frontend to install the driver with the good old point and click method. Anybody have any suggestions? I'm using Dapper Drake.
Thanx

---

### Post by Metaljaz on 2007-02-24
Run the below command from the terminal window and check under network controller for the name and chipset of your card. Once you have the chipset then if using ndiswrapper get the windows driver and install it.  

lspci

the line displayed should look something like this:

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Then try the below thread:
[http://www.ubuntuforums.org/showthread.php?t=245651&highlight=speedtouch+121g](http://www.ubuntuforums.org/showthread.php?t=245651&highlight=speedtouch+121g)

---

### Post by Radovitch on 2007-02-26
Thanks for your reply. Unfortunately the lspci command does not show any wireless controllers, only ethernet. The link you provided was the one I'd already used to try to configure the initial setup. The whole thing would be a lot easier if I could just use the apt-get command but without the internet connection in the first place...

---

### Post by Metaljaz on 2007-02-26
When you followed the link that was sent to you what was the problem that you ran into?
Your device is pci and not usb, right?

---

### Post by Radovitch on 2007-02-28
Sorry for the delay.  I have a usb adapter. The snag I hit on that link was with the sudo indiswrapper -i drivername command. Entering this gave me the invalid couldn't copy line 135 error.

---

### Post by Metaljaz on 2007-02-28
try this command:

lsusb

which will list your usb devices. Then look for the speedtouch and the chipset.

---

### Post by nabdan on 2007-03-27
Hi there,

here you should find how to, just take care to drivers as example is based on ST121G.

you also have an how to WPA ;)

[http://network.wiki.xs4all.nl/index.php?title=Linux_/_Ubuntu:_ST121G_wireless_adapter](http://network.wiki.xs4all.nl/index.php?title=Linux_/_Ubuntu:_ST121G_wireless_adapter)

I wish you best of luck !

---

### Post by littletinman on 2008-02-13
I have a good driver and a bad driver installed but the invalid one won't delete. what should i do. Here's a screenshot of what i have.

---

