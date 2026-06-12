---
title: "USB support for VirtualBox"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by OllieGab on 2009-08-16
Have VirtualBox installed, with XP. Also the Guest Additions but there seems to be no USB support.
Someone (here) suggested to check in VB settings, under USB....but I have no USB mentioned in settings!

Any suggestions?

Ollie

---

### Post by PureLoneWolf on 2009-08-16
You need to make sure that you installed the PUEL edition from the website, not the standard version in the repositories.  Then you will have USB support.  Until then, USB will be greyed out to you.

---

### Post by OllieGab on 2009-08-16
Installed the version from the web site and XP was still there (thought I might loose it in the process and have to re-install!).

However, neither XP itself or iTunes can "see" the device.
I chose the iPod filter in the VB settings section.

Ollie

---

### Post by HermanAB on 2009-08-16
Howdy,

Each virtualizer has its strengths and weaknesses.  In my experience VMware is better with USB support than Virtualbox.  (Just stay away from the dreadful VMware 2.x).

---

### Post by lkraemer on 2009-08-17
Olliegab,
First you MUST have the PUEL Version installed, and it sounds as
if that is the case since you downloaded directly from VirtualBox.

As always there is a good manual on VirtualBox located at their
website.  Basically what it tells you to do is create a Filter
for the USB Device you will use. (It must be Active, Enabled,
and some Code must be UN-COMMENTED too!)

So, Start VirtualBox.  Scroll Down the Opening window and see what
is listed for USB  DEVICE FILTERS:   ......Yours most likely states
0 (0 Active).....It must be at lease 1 (1 Active)

So click on USB, ENABLE USB CONTROLLER, ENABLE USB 2.0 and add a Filter.
(Now this must be done after you have edited the file in Ubuntu that
UN-COMMENTS the code that actually ENABLES the USB.  You probably
missed that also.....  Back again to reading the install Information,
or searching the forum for HOWTO: or INSTALL VirtualBox.  Someone has
always done it before, and posted HELP for others to save you time,
but you must do a little searching.)

And there is lots of information at the VirtualBox website on the FAQ
also.  Don't forget to go there and read the FAQ information.
Also if you're running a Linux HOST, and have a Windows GUEST OS,
then install the Guest Additions in VirtualBox.

VirtualBox runs good and you will enjoy it.  It just is a bit of a 
learning curve to get it all working if you haven't done it before.

I used this guide:  (I hope it is still an active link)
[http://ohioloco.ubuntuforums.org/showthread.php?t=770745](http://ohioloco.ubuntuforums.org/showthread.php?t=770745)

If there was an Ubuntu Kernel Upgrade:

Run the command "sudo /etc/init.d/vboxdrv setup"

lkraemer

---

