---
title: "NDISwrapper"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by paulroberts20 on 2008-01-23
I;m quite new to Linux, but so far I love ubuntu!

Been having trouble with ndiswrapper and ndisgtk

(i've got an ASUS 138g V2 PCI wireless card)


I've downloaded these files onto a USB drive using a PCLinuxOS live cd :

ndiswrapper-common_1.43-1ubuntu2_all.deb.deb
ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb.deb
ndisgtk_0.7.2-1ubuntu1_i386.deb.deb

i've installed all of these in that order, and then went System>Admin>Windows Wireless...
and loaded the WinXP driver from ASUS website. It said the hardware was detected, but when I entered my network SSID, Encryption type and Passphrase etc it wasn't connected.

I haven't had any error messages, but I can't figure out where i've gone wrong...

I know there's a few similar threads, but none of them helped much, apart from telling me where to get these files from (packages.ubuntu.com/gutsy ...)


Can anyone help me please?

---

### Post by Hightide on 2008-01-23
> **paulroberts20 said:**
> I;m quite new to Linux, but so far I love ubuntu!

Been having trouble with ndiswrapper and ndisgtk

(i've got an ASUS 138g V2 PCI wireless card)


I've downloaded these files onto a USB drive using a PCLinuxOS live cd :

ndiswrapper-common_1.43-1ubuntu2_all.deb.deb
ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb.deb
ndisgtk_0.7.2-1ubuntu1_i386.deb.deb

i've installed all of these in that order, and then went System>Admin>Windows Wireless...
and loaded the WinXP driver from ASUS website. It said the hardware was detected, but when I entered my network SSID, Encryption type and Passphrase etc it wasn't connected.

I haven't had any error messages, but I can't figure out where i've gone wrong...

I know there's a few similar threads, but none of them helped much, apart from telling me where to get these files from (packages.ubuntu.com/gutsy ...)


Can anyone help me please?


Hi

have you had a look at Kevdogs's ndiswrapper guide?. It may be useful.

[http://ubuntuforums.org/showthread.php?t=574501&highlight=kevdog](http://ubuntuforums.org/showthread.php?t=574501&highlight=kevdog)

:)

---

### Post by rustybronco on 2008-01-23
> **paulroberts20 said:**
> (i've got an ASUS 138g V2 PCI wireless card)
I know there's a few similar threads, but none of them helped much, apart from telling me where to get these files from (packages.ubuntu.com/gutsy ...)
Can anyone help me please?asus 138g v2?, bcm4318 rev2 chipset.
[http://www.linuxquestions.org/hcl/showproduct.php/product/3811/cat/myprod](http://www.linuxquestions.org/hcl/showproduct.php/product/3811/cat/myprod)

spin up a 7.10 live cd and try... [http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)
you'll loose not a thing trying it.
> but when I entered my network SSID, Encryption type and Passphrase are you sure the passphrase was the same either hex or ascII?
if so try connecting from the command line in the link hightide just gave you.

---

### Post by paulroberts20 on 2008-01-24
Thanks guys.

Never thought to use the last method.
(d'oh!)


I should just be able to take my PC downstairs and temp. connect direct to the modem.. Forgot there were restricted drivers available for my card..


Thanks again!     :D

---

