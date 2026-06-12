---
title: "ndiswrapper"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by seismicmike on 2005-10-27
:mad: 

had ndiswrapper working great under hoary, now i come over to breezy and i try to install ndiswrapper, but it doesn't work....

oh it says it works, but it says my driver is invalid

IT'S THE SAME DRIVER I USED UNDER HOARY!!!

what am I doing wrong????

---

### Post by az on 2005-10-27
You cannot always use the same driver with ndiswrapper since they develop it using the most recent version of the inf file.  Look on the wiki for a link to the ndiswrapper list of driver downloads.

Also, if you did not remove and then reinstall the inf driver, try that.  They sometimes change the format of the configuration.

---

### Post by seismicmike on 2005-10-27
well... i'm using the same driver i use under windows... does that matter?

---

### Post by jackmacokc on 2005-10-27
[QUOTE=seismicmike]well... i'm using the same driver i use under windows... does that matter?[/QUOTE]

probably not, but you might get the latest from the vendor website just to eliminate that as a problem.

---

### Post by az on 2005-10-27
[QUOTE=seismicmike]well... i'm using the same driver i use under windows... does that matter?[/QUOTE]
Yes, because ndiswrapper is developed using usually the latest windows driver.  You often need to use the same version the developers used for your chipset.
Check the wiki.

---

### Post by indymcse on 2005-10-27
okay, I have gotten ndiswrapper installed with my wifi card driver.  No errors or anything.  I can enable the card and activate it, but not use it.  It never gets an IP address from my AP.  I'm using a Linksys AP plugged into my network and my DHCP server is just my Netopia DSL modem/router.  The Linksys is just acting as a "passthrough" to my home network.  I don't have WEP enabled.  I am using MAC filtering and the MAC of my laptop is already in the allow list as I was using it with WinXP till yesterday.

Any help would be greatly appreciated.  Thank you.

---

### Post by mxyzptlk on 2005-10-27
go to your breezzy installation cd
open it
open pool folder
in letter n find ndiswrapper tools
paste to your desktop
open a terminal and type this
cd /desktop
$ sudo dkpg -i <filename.deb>

maybe it will ask your password

thats it

---

### Post by az on 2005-10-27
[QUOTE=mxyzptlk]go to your breezzy installation cd
open it
open pool folder
in letter n find ndiswrapper tools
paste to your desktop
open a terminal and type this
cd /desktop
$ sudo dkpg -i <filename.deb>

maybe it will ask your password

thats it[/QUOTE]

Or just do it the easy way.  Use synaptic, aptitude, apt or dselect.  They do all the work for you.

---

### Post by seismicmike on 2005-10-27
Guys, ndiswrapper is just flat out not working for me...

i've downloaded the latest driver from Broadcom's site, and it just won't work... :(

HELP!!!!

it installs....

```

sudo -s
# ndiswrapper -i <driver>.inf
# ndiswrapper -l
<driver> driver installed
# ndiswrapper -m
# modprobe ndiswrapper

```

and yet, it doesn't work!!!!!!  :mad: :mad: :mad: :mad: :mad: :mad:

---

### Post by MattiViljanen on 2005-11-03
OK, what card do you have? Brand and model, I mean.

---

### Post by Zelut on 2005-11-03
I also have the issue wherein a driver that worked under Hoary will not work under Breezy.  I figured something was changed (intentionally/un-intentionally) that is conflicting with ndiswrapper.  I'm getting the latest drivers as suggested on the ndiswrapper wiki.  We'll see how it goes.. I've got 3 machines that I need wifi working on again since Breezy...

---

### Post by seismicmike on 2005-11-09
I got it to work by following the directions here:

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

