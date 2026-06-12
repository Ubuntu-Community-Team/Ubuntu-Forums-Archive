---
title: "Can't get ip address!"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by doggy123 on 2007-01-13
I believe that I have installed my usb wireless pen correctly with ndiswrapper.

$ ndiswrapper -l

rt2500usb                 driver present, hardware present

but 'route' gives me nothing in the routing table

my network interfaces are:

auto lo
iface lo inet loopback

iface rausb1 inet dhcp
wireless-essid ************
wireless-key ************

auto rausb1


iwconfig seems to be ok and so does 'iwlist rausb1 scan' bringing back the mac address of my router.

I just can't ping anything or get my own ip address my router is set up correctly as the same machine running windows connects fine.

Can any one help?

Cheers,

Dan

---

### Post by mojoman on 2007-01-13
Could it be a driver issue and do you need ndiswrapper? Ralink are, I think, one of the manufacturers of wireless that actually release their source code. I've used rt2500 both for laptop and desktop, and in Ubuntu it worked out of the box (though I never used the usb-variant). However, for Debian it was a little bit harder (failed with sarge but got it working on Etch at first try) but you could give this a go:

[http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto)

The package rt2500-source is available in the Ubuntu repositories and so is everything needed to autocompile it according to this howto. That said, I've only used it on Debian Sarge and Etch myself but it might be worth a try.

/Mojoman

---

### Post by chili555 on 2007-01-13
If he can scan and see his router, doesn't that suggest the driver is loaded and working fine?

Please be sure the essid and key match your router exactly. Also, is the encryption method in your router set to Auto or Shared Key? If Shared Key, please amend your wireless-key ************ to wireless-key ************ restricted.

What is the output of sudo dhclient rausb1?

---

### Post by mojoman on 2007-01-14
> **chili555 said:**
> If he can scan and see his router, doesn't that suggest the driver is loaded and working fine?

It does, and it at least proves that the drivers work for this purpose. My point was mainly that there drivers compiled specifivally for that chip are available in the repos, and that this might be a driver-specific problem. I have encountered stranger things in the world of computers...
/Mojoman

---

