---
title: "nvidia or ATI ?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by anatak on 2009-02-08
I am looking to convert an XP box to a Ubuntu system.
wanting to upgrade the graphics card I wonder which has the best support ? ATI or Nvidia ?
I am looking for a graphics card that has 2 HDMI out ports preferable as silent as possible (eg EAH3650 Silent would be perfect).
On my laptop my ATI IGP 9000 does not support TV out using the S-video under Ubuntu. Can anybody tell me if they have the  EAH3650 Silent working under Ubuntu with dual display ?
Or any other recommendations ? I am not into playing games I would mostly like to watch DVD's and divx/mkv/mpeg4 files.

thank you
anatak

---

### Post by jimv on 2009-02-08
Nvidia's probably the way to go.  I've never had any huge issues with any of my Nvidia cards.  I have heard about headaches with ATI cards though.

Oh, and for more than one HDMI output, they have cables that will covert a DVI connector to HDMI:
[http://www.google.com/products/catalog?q=dvi+to+hdmi&oe=utf-8&cid=4362525598946032433&sa=title#ps-sellers](http://www.google.com/products/catalog?q=dvi+to+hdmi&oe=utf-8&cid=4362525598946032433&sa=title#ps-sellers)
So any card with two DVI outputs should work fine.

---

### Post by carml on 2009-02-08
Go for Nvidia,at the moment as a better support by the manufacturer i.e. more support with native drivers.

---

### Post by billgoldberg on 2009-02-08
But that might change in the future.

ATI has released driver specifications for their cards, meaning they will start working better than de Nvidia ones in the future.

--

I'm using ATI and everything works great btw.

---

### Post by zipperback on 2009-02-08
I have an acer aspire laptop with an ati radeon 1100 video and I have been very happy with it. I have no complaints about it.

ATI and Nvidia are both well in the Linux community.

- zipperback
:popcorn:

---

### Post by carml on 2009-02-08
Me too,I have an ATI but with the proprietary version of the drivers installed,I suggested to go for an Nvidia because,as I know,at the moment there are open-source driver for Nvidia.I have an ATI Mobility Radeon X2300.

---

### Post by madverb on 2009-02-08
Nvidia's Linux drivers aren't Open Source but they work very well.

---

### Post by carml on 2009-02-08
Sorry for being wrong.

---

### Post by philinux on 2009-02-08
My nVidia card works really well with the dvi cable. It has two dvi outputs. This is fine for me as sound is output to labtec system.

---

### Post by soxs on 2009-02-08
> **billgoldberg said:**
> But that might change in the future.

ATI has released driver specifications for their cards, meaning they will start working better than de Nvidia ones in the future.

--

I'm using ATI and everything works great btw.

I am using ATI aswell, and I must admit that 9.1 drivers helped a lot for video issues, but the proprietary drivers of nvidia are still A LOT better, rom opengl to wine compatibility.

The OSS driver approach from ati will take some more years to get to a really "playable" level of 3D/video acceleration.

I'd suggest you to buy an nvidea one, just for your next step. If you then decide in 1 to 5 years about a new one, this may have changed.. but atm nvidea is the way to go (especially since GPU accelerated video decoding, quite open source, and it works, in spite of atis closed f*** approach without x264 decoding support and still NO player supports that, this means either you have an Core2Quad/Core2Duo 3GHz+ or 1080p videos will lag, I have an phenom, and it lags like hell on my amd box)

---

### Post by Whoo on 2009-02-08
Hello,

Ma première carte fonctionnait bien avec le driver Mach64. Mais depuis RivaTNT2, Nvidia permet d'avoir une configuration qui fonctionne à 99% et rapidement.

Le seul problème est que le driver propriétaire n'est pas mis à jour aussi rapidement que le kernel, il faut donc attendre quelques jours pour utiliser Nvidia avec le dernier kernel linux.

/!\: Quand Nvidia ne voudra plus faire l'opensource... cela posera un grave problème: l'avantage des drivers propriétaires.

---

### Post by theozzlives on 2009-02-08
My oldest computer on the network has an ATI 3D Rage Pro (old I know). Works fine, I've also had luck with Intel.

---

### Post by soxs on 2009-02-08
> **Whoo said:**
> Hello,

Ma première carte fonctionnait bien avec le driver Mach64. Mais depuis RivaTNT2, Nvidia permet d'avoir une configuration qui fonctionne à 99% et rapidement.

Le seul problème est que le driver propriétaire n'est pas mis à jour aussi rapidement que le kernel, il faut donc attendre quelques jours pour utiliser Nvidia avec le dernier kernel linux.

/!\: Quand Nvidia ne voudra plus faire l'opensource... cela posera un grave problème: l'avantage des drivers propriétaires.

english man, englisch!

btw: rage 3D is SO old, the OOS suppport is quite complete.

---

### Post by linux_tech on 2009-02-08
There is usually better overall linux support, drivers, etc for nvidia
(not for all cards, but likely more than ATI)

---

### Post by jimv on 2009-02-08
>ATI has released driver specifications for their cards, meaning they will start working better than de Nvidia ones in the future.


I don't really know how you can work better than working perfectly already.  Perhaps you mean "as good as".

---

### Post by RomeReactor on 2009-02-08
> **jimv said:**
> I don't really know how you can work better than working perfectly already.  Perhaps you mean "as good as".

While nVidia drivers are good, they're not perfect. Currently I have a GeForce 6200 and a bug in the 180 series driver kept showing the cursor in Eve Online as a square cloud of dots, and no amount of reading posts or tweaking options changed that; so back to 177 it was.

I'm waiting for an ATI x1650 pro to arrive; I like what AMD is doing, and I plan on supporting them from now on.

---

### Post by Kellemora on 2009-02-08
Hi Anatak

Not that my 2 bits is worth much anymore these days, hi hi.......

I prefer the Nvidia cards on Ubuntu only machines!

But on the Doze boxes and on dual boot, while in Doze ATI has features I really like and use often that Nvidia does not have.
These ATI features are not available in the Linux drivers.
So on Linux machines, the Nvidia is slightly better than the ATI cards and neither have the feature that ATI does when in the Doze.

TTUL
Gary

---

