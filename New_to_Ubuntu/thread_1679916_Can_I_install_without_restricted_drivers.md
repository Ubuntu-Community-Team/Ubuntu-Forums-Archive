---
title: "Can I install without restricted drivers"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by rrmerkov on 2011-02-01
Hi all,  Complete newbie here.  I have an Acer Extensa 5420-5687 with ATI Radeon Xpress 1250 graphics.  When putting the Lucid Lynx 10.04 CD in my drive to try out Ubuntu I get the message that begins with "Restricted Drivers Available" and ends with "enable drivers which are not free software."  I am not sure exactly what a driver is, but I really do not want to pay for drivers.  Can I install Ubuntu on my hard drive without buying restricted drivers?

Thanks,
merk

---

### Post by Darkness Des on 2011-02-01
By free, they mean not open source. They are absolutely 100% free (as in cost), but it's made by companies which do not release the source code. In short, it costs no money.

---

### Post by davidmohammed on 2011-02-01
...

restricted drivers mean that they are not open-source drivers - they have been created usually by the manufacturer.

No you dont need to pay for these - and you dont need to install them either.

Some find that the video drivers direct from the manufacturer has better performance than the open-source that comes with the distro.  There is a proviso though - sometimes they can also make a mess of your system.  I would suggest you have a backup before you install if you want to try them out.

---

### Post by Frogs Hair on 2011-02-01
Some applications such as docks and Compiz effects require proprietary divers , but you will decide weather you want those things or not.

---

### Post by clhsharky on 2011-02-01
rrmerkov

There are no restricted video drivers for your video chip(ATI Radeon Xpress 1250 graphics)to use on 10.04 release.
Its most likely a restricted WIFI drivers.


Sharky

---

### Post by Zill on 2011-02-01
> **rrmerkov said:**
> ..."enable drivers which are not free software."  I am not sure exactly what a driver is, but I really do not want to pay for drivers...
The GNU [Free Software Definition]("http://www.gnu.org/philosophy/free-sw.html") might help clarify things:
> “Free software” is a matter of liberty, not price. To understand the concept, you should think of “free” as in “free speech,” not as in “free beer.”

---

### Post by SeijiSensei on 2011-02-01
> **Darkness Des said:**
> By free, they mean not open source. They are absolutely 100% free (as in cost), but it's made by companies which do not release the source code. In short, it costs no money.

There's another class of restricted drivers, those that can't be redistributed into certain jurisdictions because they conflict with copyrights or patents.  Ubuntu cannot ship globally a version that includes software to enable MP3 or DVD playback because it would be illegal to ship those items to the United States and some other countries with [strong intellectual property laws]("http://www.chillingeffects.org/anticircumvention/").  Instead Ubuntu puts these into ubuntu-restricted-extras and lets the user decide whether to download them or not.

The [source code for libdvdcss2]("http://www.videolan.org/developers/libdvdcss.html") (DVD decryption) is entirely open, but Ubuntu cannot ship a copy of the libdvdcss2 binary into the US.  Whether they can send you a copy of the source code and let you compile your own version is a more complicated legal question that I don't think has ever really been resolved in the US courts.

---

### Post by rrmerkov on 2011-02-03
Many thanks to all who have responded.  It turns out that the restricted driver was for the wireless modem.  I have installed Ubuntu as well as the restricted drivers, and after playing with it for about an hour, it seems to be working fine.

regards,
merk

---

### Post by Hindol on 2011-02-03
> **clhsharky said:**
> rrmerkov

*There are no restricted video drivers for your video chip(ATI Radeon Xpress 1250 graphics)to use on 10.04 release.*
Its most likely a restricted WIFI drivers.


Sharky

Always good to know new stuff, :). Thanks buddy.

---

