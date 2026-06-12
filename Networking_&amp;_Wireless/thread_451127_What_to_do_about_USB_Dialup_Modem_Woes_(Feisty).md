---
title: "What to do about USB Dialup Modem Woes? (Feisty)"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by strangerep on 2007-05-22
Hi, first-time post here, but I've been a lurker for a while...

Does anyone know of any external USB dialup hardware modem
that Ubuntu (Feisty) will even recognize??

I've spent quite a lot of time trawling previous posts about the
nightmare of USB dialup modems on Linux, and looked at quite a
few other Linux related sites. (I have 20 years experience as
a Unix programmer, though not much on Linux.)

I recently decided to splurge on a new machine, choosing all the
components myself. I chose a Gigabyte GA-965G-DS4 motherboard,
with many USB ports (but no RS-232 serial).  Silly me. I just
assumed that USB would be fine for everything these days and
didn't bother checking, although I spent much time researching
most of my other component choices.

I got a Netcomm AM5055 Roadster V.92 USB modem, thinking that
it would be a full hardware external modem. This model takes
its power from the USB bus, and was recognized ok under Vista
after I installed the Windows drivers supplied by Netcomm. Then I
got rid of Vista and installed Feisty. A curious thing happened:
the "power" LED on the modem came on for a few secs, then went
off, and continued slowly cycling on/off in this way. However,
this didn't happen under Vista, and also *doesn't* happen when I
plug the modem into another much older Gateway GP6 PC running
Ubuntu 6.10 (Edgy). But even on Edgy, I can't get the Netcomm
modem to respond to "AT" commands, so I'm guessing it's really a
softmodem inside an external case, and needs a Linux driver
(which Netcomm doesn't support).

In contrast, the old computer running Edgy happily talks to a
Dynalink 56K E-modem II (external serial H/W modem). I was able
configure PPP in Edgy on that machine without too much trouble.

QUESTION: Over on linux-usb.org, there's a page on USB modems
which talks about how a "USB Modem (CDC ACM) support" kernel
option is necessary. How do I find out whether or not this is in Feisty's
kernel? (Linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC
2006 i686 GNU/Linux.) I've tried "lsmod" but the output contained
nothing involving either of the phrases "cdc" or "acm".

Anyway... since ADSL/Broadband is not an acceptable option for me,
I need to figure out what to do to get dialup working on my
new machine running Feisty. My options appear to be:

1) Buy a different external USB dialup modem (certified for use
in Australia) which is indeed an external hardware modem,
requiring no driver. QUESTION: do any even exist? (I searched in
many places, but failed to find one.)

2) Buy a simple PCI serial card which can plug into the Gigabyte
motherboard's PCI slot, and then use my Dynalink modem (or
some other serial H/W modem). QUESTION: Is this a sensible idea?
If so, can anyone recommend a suitable card/manufacturer?  I'm not 
too fussed about price, as I want ease, reliability, and quality.

3) Are there other (non-ADSL/BB) options that I don't know about?

Thanks in advance for any help/suggestions/comments.

---

### Post by rapattack1 on 2007-05-28
Yes I have been tackling this issue since January being the first time I ued Linux. The easiest option I found to get Ubuntu on the net was to put in a pcmcia card and I installed gnome-ppp. Have you got pcmcia slots? I have tried to get so many serial modems working after many hours have managed to do it with two desktops but the laptop just refused to do it. I was looking at the usb possibility but I found out that that was going to be problematic. I am also in Sydney and have seen some pcmcia cards over at 'Reverse garbage' and I am sure they are ultra cheap but of unknown condition. They also do not have the little cable that runs off it but I did find one this week for another friends laptop that I have installed Debian on. I am going to get one of those pcmcia cards and see if it works on the laptop with Debian as easily as the laptop with Ubuntu. Anyway let me know if I am have been helpful at all and if you have come up with any miracles. Carla

---

### Post by strangerep on 2007-06-18
> **rapattack1 said:**
> The easiest option I found to get Ubuntu on the net was to put in a pcmcia card and I installed gnome-ppp. Have you got pcmcia slots? [...]
Hi Carla,
Thanks for your reply, and apologies for not noticing it sooner. I had become
depressed with the deafening volume of cries for help around here, and abandoned
Ubuntu Forums for a while. But I've now realized I can subscribe to particular
threads and get notified by email.

Anyway... I don't have pcmcia slots, just pci and pci express. I bought a PCI serial
card (Sunix 4079T) which Feisty seemed to recognize ok. I configured PPP
easily enough, but then a weird thing happened...

Everything initially works fine. I can configure PPP and connect to
my ISP. The first web page loads fine at the usual dialup speed
I'm used to on my older machine running Edgy (with the same external
serial modem). But then something seems to go wrong on the new machine.
Hardly any data gets through (the SD/RD lights on the modem only light up
occasionally, even though I'm still trying to download other webpages).
After a while, PPP shuts it down, and the PPP log says "serial link appears
to be disconnected. No response after 4 echo requests". After a short pause,
it re-dials, re-connects ok, the first page loads ok as before, but subsequent
ones have the same problem. And so it continues. This never happens with
exactly the same modem using Edgy on my older PC. I'm wondering whether
there's something wrong with the Sunix PCI serial card. (?)

I'm willing to try a different tack with a USB-to-Serial dongle that someone
else mentioned, but I need to figure out exactly what to buy. I'm not too
worried about saving pennies - I just want something that works. (sigh)
I'm even thinking about gambling some more money on a different
PCI serial card to see if there's a difference.

> I have tried to get so many serial modems working after many hours
have managed to do it with two desktops but the laptop just refused
to do it.
I've been able to get my Dynalink e-modem-II external serial hardware
modem to work flawlessly (and fairly easily) on my older PC. I did have to
muck around with the various /etc/ppp files though (which was ok, since
I have a background in unix systems programming). But this new
problem on the newer machine has me stumped.

---

### Post by rapattack1 on 2007-06-18
Sorry to say I am having more problems with dialup and Linux. Well the laptop is fine with Ubuntu 6 but the desktop is not ok so I not much help. I have another laptop that I am trying to get on the net too but to no avail. Even with a pcmcia card like the other laptop. It is frustrating when there is little support/knowledge offered on these things. I won't be getting a faster connection anytime soon.
Yep I know what you mean by the lack of replies too and I haven't visited here since I posted that reply to you! I have also joined some laptop group and a couple of others. Ultimately I am waiting for my Linux friend to come over and wave his magic wand. I hope it is soon! He also has a past with Unix or still is in it. 
Hope it all works soon for you!

---

### Post by strangerep on 2007-06-18
> **rapattack1 said:**
>  [...] the laptop is fine with Ubuntu 6 but the desktop
is not ok so I not much help.
I'm writing this post on a desktop running Edgy via serial dialup modem. If you
tell me more about what's wrong with your desktop, I'll try and help (assuming
it's a unix/linux config problem rather than hardware issues).

---

### Post by strangerep on 2007-06-23
Just in case anyone else was following this thread...

My result is this: I bought an ATEN UC-232A usb<->serial adapter.
It works **perfectly **out of the box. No hardware problems whatsoever.
Although its CDROM comes with driver source code for Linux, you
don't need it because the relevant pl2303 driver is already
included in modern linux kernels.

I then tried the Sunix PCI serial I/O card again, just to make sure.
It still fails in the same way I described earlier. Data starts to flow
ok, then dries up to nothing. The Sunix card will now be thrown in
the bin, and I won't be buying their products again.

---

