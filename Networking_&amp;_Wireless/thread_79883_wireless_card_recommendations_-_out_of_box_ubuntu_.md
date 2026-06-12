---
title: "wireless card recommendations - out of box ubuntu support"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by bionnaki on 2005-10-21
what cards do you guys recommend that would work out of the box in ubuntu (i.e. no ndiswrapper/windows drivers)? I have a linksys wrt54g router, if that matters.

thanks!

---

### Post by mohaham on 2005-10-21
Intel BG2200 is well supported

---

### Post by bionnaki on 2005-10-21
which cards have that chipset? would it work with my router?

---

### Post by Chuckaluphagus on 2005-10-21
[QUOTE=bionnaki]which cards have that chipset? would it work with my router?[/QUOTE]

That's the wireless card built into some Centrino notebooks; it's what I have in my notebook, and it works flawlessly with my router (the exact same model you have).

I don't know that you can get it as a PCI network card for a desktop, but I gather Linksys wireless cards for desktops are well-supported.  Haven't tried one myself, just what I've read.  Good luck.

---

### Post by bionnaki on 2005-10-21
thanks.

yeah, I have a linksys wmp54g pci card that can work with ndiswrapper, but I have found it be rather unstable at times. I'd rather have a card that is supported in ubuntu/linux without having to use ndiswrapper - hopefully that would be more reliable.

anyone know of such cards?

---

### Post by jhong on 2005-10-21
[QUOTE=bionnaki]thanks.

yeah, I have a linksys wmp54g pci card that can work with ndiswrapper, but I have found it be rather unstable at times. I'd rather have a card that is supported in ubuntu/linux without having to use ndiswrapper - hopefully that would be more reliable.

anyone know of such cards?[/QUOTE]

Breezy supports wmp54g out of box, and it even works perfectly with WPA without installing wpa_supplicant. :D 

Yes, ndiswrapper isn't so stable, i used to use it on hoary.

---

### Post by bionnaki on 2005-10-21
wait, are you serious? how do I get it working then?

on a fresh install (or before install ndiswrapper), my ESSID does not show up in network settings ra0 properties...so I never even put in my static IP & other information. I figured the wireless card was not supported like it wasnt supported in horary & required ndiswrapper.

do I just manually enter my ESSID?

I currently have ndiswrapper + windows drivers installed, and I have no idea how to get back breezy's original state other than ndiswrapper -e rt2500 (uninstalling the driver). how would I get ra0 to show up instead of wlan0 (which the wireless connection alias is called after install ndiswrapper + drivers)?

I guess I could just do a fresh install...

---

### Post by jhong on 2005-10-21
here's how i made it work: [http://ubuntuforums.org/showthread.php?t=78250]("http://ubuntuforums.org/showthread.php?t=78250")

remove ndiswrapper and reboot, ra0 might come back...

---

### Post by bionnaki on 2005-10-22
thanks for the reply. I'll see if uninstalling the driver & ndiswrapper brings ra0 back. if not, then I'll do just a fresh installation & await your HOW-TO.

---

### Post by Red Sand on 2006-01-08
[QUOTE=jhong]Breezy supports wmp54g out of box, and it even works perfectly with WPA without installing wpa_supplicant. :D 

Yes, ndiswrapper isn't so stable, i used to use it on hoary.[/QUOTE]


Out-of-the-box, means crash when used often. :( 
When I start downloading or browsing more then a minute my system hangs, not when I use my wiredlan....
Any thoughts?

---

### Post by Czar on 2006-01-08
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

I have not found a "plug and play" wi-fi card yet for Ubuntu. With a couple commands, and NDISWrapper[1], I have found both the Belkin Wireless G Notebook Card (F5D7010 v4)[2] and the Belkin Wireless G USB[3] to be solid networking adapters (as good as I would expect any other wi-fi device to).
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQFDweVTDOEqJEQ8QqYRAmw+AJ4oANQBB7EUc5FLDuP0wBGKK5X5jACfbxvk
Q3GPvdDq84Jp3Lna0ldzhas=
=zrLB
-----END PGP SIGNATURE-----

[1] [http://packages.ubuntu.com/ndiswrapper-utils](http://packages.ubuntu.com/ndiswrapper-utils)
[2] [http://czarism.com/ubuntu-debian-wpa-wi-fi-w-belkin-adapter](http://czarism.com/ubuntu-debian-wpa-wi-fi-w-belkin-adapter)
[3] [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

---

### Post by Red Sand on 2006-01-09
My wmp54g ended up being out-of-the box. It was an IRQ conflict. USB IRQ reservations, was enabled in my BIOS. Disabled it, working like a charm :D

---

