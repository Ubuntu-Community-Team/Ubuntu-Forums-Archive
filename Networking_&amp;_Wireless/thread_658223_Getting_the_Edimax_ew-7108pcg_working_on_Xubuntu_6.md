---
title: "Getting the Edimax ew-7108pcg working on Xubuntu 6.06 LTS"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by ghostis on 2008-01-04
I found this card on newegg.com for cheap money and the company
claimed Linux support, so I got it.  So far, I have it working on a
WEP test network, but the driver package does come with WPA-supplicant
bits.  I assume that works as well.  Folks online claim it works out
of the box on Ubuntu 7.10, but my laptop didn't do well with the newer
Xubuntus, so I had to make do with 6.06 LTS.  Note, out-of-the-box, the rt61 driver
provided by Xubuntu 6.06 LTS throws a stack trace and can wedge your
system.  I found that you need to build the Edimax's rt61 driver.

Note, I didn't know this card used RT* chipset up front, or I would have probably used the NDIS wrapper instructions folks have helpfully written elsewhere on this site.  I may try them, if the WPA-supplicant support does not work out.

Here was my procedure for 6.06 LTS:

1) Install gcc and friends,if you haven't already.
2) Update to the latest kernel packages.
3) Install the linux-header packages for your platform (I used the 386
packages).
4) Download the driver zip for the ew-7108pcg from the Edimax
website's support area, unpack it, and the unpack the tar ball inside.
5) cd into the IS_Linux_STA_6x_D_1.1.1.0 directory
6) run make
7) Ignore all the compiler warnings ;)
9) run sudo make install
10) Add "alias ra0 rt61" to /etc/modules.conf or into your preferred
location in /etc/modules.d if it wasn't automatically added.
11) Add correct bits to /etc/network/interfaces

So, that being said (I am typing this email via the card now):

1) On boot, the card comes up, but does not go online.  Ifconfig has
configured the interface, but iwconfig shows no essid or key
configured.

2) I opened the Applications->System->Networking tool.  The tool shows
the interface as active.  I can "activate/deactivate", but likewise
iwconfig shows no configuration.

I can only bring the interface up via running iwconfig and then dhclient on the command line after boot.  I have the card stanza in /etc/network/interfaces, but unlike my other wireless machine, the stanza seems to do nothing except activate the card, hardware-wise... :-/.

Does anyone have any ideas about what plumbing I am missing to get
automatic configuration at boot (or better, on eject/insert)?

Thanks!

-Adam

---

