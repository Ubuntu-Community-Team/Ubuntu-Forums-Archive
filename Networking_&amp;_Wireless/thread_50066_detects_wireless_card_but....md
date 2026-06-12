---
title: "detects wireless card but..."
date: 2005-07-18
forum: Networking &amp; Wireless
---

### Post by sinisterSupreme on 2005-07-18
i have a dell inspiron 5100 with both a internal mini-pci dell 1450 802.11 a/b/g wireless card (not detected) and a pcmcia linksys wpc54g ver 2 802.11 wireless-g (detected)

in system >> admin >> network the pcmcia card is detected and is configured with WEP and everything. but there isnt a connection. even after configing, activating it switches over to idle. I know i dont need ndiswrapper for this card since it is already detected and is active but i'm at a loss for why its not hearing the router.

the only thing i can think of is that it really isnt powered. i get this feeling because the led lights aren't on even after plugging it in. this could be a problem with the kernel but i'm at a loss.

any ideas?
thanks
me

---

### Post by ProNoblem on 2005-07-19
Hi Sinister,

I think that I've had the same problem, my link light also didn't came up when I was configuring my wireless card (although I did everything correct through the howto's/man pages)

The solution for me was to manually edit the ndiswrapper conf files with gedit.
In these files there is an entry "RadioState" with the value 0. If you change this value in 1 ([COLOR=Navy]sudo gedit /etc/ndiswrapper/<driver>/<conffile.conf>[/COLOR]) , save the files and then do:
[color=Navy]rmmod ndiswrapper
modprobe ndiswrapper[/color] (or just reboot if you've already added ndiswrapper to init.d)

It'll use the freshly editted conf files now, and your wireless card will be active.

---

