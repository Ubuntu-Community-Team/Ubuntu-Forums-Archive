---
title: "belkin f5d7051 usb adaptor (again!)"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by salut on 2007-11-04
Hello,

I'm trying to get a broadcom chipset Belkin usb adaptor (one of the troublesome 050d:7051 / F5D7051 type ones...) to work in Feisty (7.04) and having limited success. So far I've done the following:

1. updated ndiswrapper to version 1.38

2. tried to install drivers provided on belkin installation cd. This gave an invalid driver message. I used to have a belkin pci card in my system, which I had the old drivers lying around for, so I also reinstalled these in ndiswrapper, so at this point I had both (invalid) drivers for the usb device (bcmrndis.inf) and drivers for the (not installed) pci card (bcmwl5) loaded. I then copied the .conf files beginning 050D:7051...F.conf into the /etc/ndiswrapper/bcmwl5 directory and finally removed the ndiswrapper entry for the invalid drivers. The next time I tried ndiswrapper -l I got:

bcmwl5 : driver installed
        device (050D:7051) present (alternate driver: rt2570)

and the usb device now wakes up and twinkles at me when I startup, which I hope is a good sign :-) I should possibly mention that I didn't really know what I was doing here!!

I'm now a bit stuck, though, as my system doesn't seem to have anything wireless registered. When I do iwconfig I get:

lo        no wireless extensions.
eth0      no wireless extensions.

and lshw -C network just lists my ethernet card

I've read the wiki / searched previous posts. The main consensus seems to be "buy a new adaptor", but I'd be hugely grateful for any help. (I've also tried the alternate rndis driver mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=128975&page=2]("http://ubuntuforums.org/showthread.php?t=128975&page=2") 
but to no avail...) I'm running kernel 2.6.20-12

Cheers!
Mouse

---

