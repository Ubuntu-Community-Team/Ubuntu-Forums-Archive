---
title: "Will Ubuntu 8.10 have better wifi support?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by duksandfish on 2008-08-09
Well, i would love to use ubuntu on my laptop, i installed it with wubi, and had some fun messing around with it, until I found my wifi card wasnt supported, I found a few fixes, one of which worked, but then stopped after a few days. Anyway, had the wifi worked, i frobably would have gone for a full install, when I got some more cd-rs/ the free one comes

My Wifi is the Atheros AR5007EG (as it is called in vista device manager) 

So, the question I am asking is, since there is a fix avaliable, which works for some but not others (possibly not for me because of Wubi), is it likely there be "out of the box" support for my card in ubuntu 8.10 (Intrepid Ibex I believe)

Thanks 

duksandfish

[EDIT:Accidentally put it as [all variants] should be in ubuntu]

---

### Post by scottro on 2008-09-14
Well, it was working out of the box with kernel 2.6.27-2.  However, 2.6.27-3 seems to have broken that, at least for me.  

By the time I get a chance to deeply troubleshoot this, hopefully, it will be confirmed or corrected. 

NOTE!  I don't know yet if this is a Just Me(TM) issue or consistent.  I'm sure if it's affecting everyone, we'll be hearing more about it.  :)

---

### Post by kirsch92 on 2008-09-14
Have you tried this:
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)

Your 5007EG will report as a 242, and this will work although I don't if it will in WUBI.

---

### Post by GepettoBR on 2008-09-14
One of the main goals stated by Shuttleworth when he announced the opening of the 8.10 development cycle was mobility - aka better wireless network support and several laptop-related improvements. I think we can expect a great leap in wireless support (Hardy already recognizes many more cards than Gutsy) especially since Intrepid Ibex uses a much newer kernel than the one currently available for Hardy through the repos.

---

### Post by scottro on 2008-09-14
My completely uninformed guess is that it's a temporary glitch.  Fedora isn't having the same problem in their later kernels--I don't know how the two versions compare.  It's already been mentioned on a launchpad bug about the card.  

The howto posted above is similar to my own howto about it, but I haven't even bothered to try on this latest Ibex build.  (I know that at one point, the latest snapshots weren't building on the 2.6.27 kernel, but by that point, the kernels were supporting the card through the ath5k module.)

Hopefully, this one will be fixed shortly.  

It's always difficult to support the wireless cards because the majority of manufacturers don't want to release the specs.

---

