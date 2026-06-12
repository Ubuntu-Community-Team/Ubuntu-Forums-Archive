---
title: "My Wireless Experience"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by slikwill on 2007-10-29
All the recommended documentation notwithstanding, The following is working very well on 7.04:
Wireless card is a Dell Truemobile 1300 with the Broadcom 4306 chipset.
Based on the documentation at ndiswrapper wiki I downloaded R115321.EXE, unpzipped it, went to directory AR and did 
sudo ndiswrapper bcmwl5.inf
Inserting my wireless card got no light on, but about 24 hours later inserting it and the light came on.
Then the wireless was functional.  BLACK MAGIC!
The link to fwcutter does not work (acknowledged in some documentation), so could not remove bcm43xx.
Doing the following:  ndiswrapper -l

yeilds:
bcmwl5 : driver installed

        device (14E4:4320) present (alternate driver: bcm43xx)

So the prevailing documentation is telling me I am running the bcm43xx driver not the bcmwl5 driver.
BUT
if I type in:  sudo ndiswrapper -r bcmwl5
this driver goes away and my wireless card quits working.  Reinstalling bcmwl5.inf  again made it work.

The point of my story is to request insights to the wireless card functioning on version 7.10.  I get the impression that this might function automatically in 7.10 and I won't have to do the ndiswrapper bit.  Any help is greatly appreciated.  My UNIX experience ended in 1994.  We need to teach this old dog new tricks.

---

### Post by scrooge_74 on 2007-10-29
My opinion is you either run a virtual machine or make space in your drive to have 7.10 along with your current install in case something goes wrong or is to much of a problem to resolve

---

### Post by Supertonic on 2007-10-29
Let me see if I can help you out here.

If I understand you correctly, you already have the appropriate driver installed with ndiswrapper which is the bcmwl5.inf.

What you need to do is blacklist the native bcm43xx that comes with ubuntu so there are no conflicts with the bcmwl5 driver.  The procedure for that is as follows:

```
 gksu gedit /etc/modprobe.d/blacklist
```
At the bottom of the list add:*blacklist bcm43xx*   Save and exit.

Next you want type the command:
```
 ndiswrapper -m 
```   if you haven't already.

Next you need to edit the modules file in order to make ndiswrapper run each time you boot up ubuntu.  
Type
```
 gksu gedit /etc/modules
```
At the bottom of the text file add * ndiswrapper *  Save and exit.

Reboot and you should be in good shape.

---

### Post by kevdog on 2007-10-29
Confused about the point you are trying to make or the question you have.  In 7.10 ndiswrapper is still needed, the bcm43xx drivers are available with an internet connection, but they seem to be somewhat unstable for many.  Not much has changed in my opinion with 7.04 vs 7.10 for the broadcom chipsets except for the ability to download the bcm43xx driver -- although I still think at least as it stands right now the ndiswrapper approach is the more stable and better performing option.

---

