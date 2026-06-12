---
title: "Network Notification Bubble Garbage"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by erilidon on 2009-11-14
After upgrading to 9.10 the network notification bubble that pops up after a successful connection to a wireless network is garbage on my wife's laptops. It is fine on my desktop so I am not sure what could be causing this... I have attached a screen shot

Could someone tell me how to fix this? Thanks.

---

### Post by Paqman on 2009-11-15
Is it just for network notifications, or for others as well?

---

### Post by erilidon on 2009-11-15
I have only noticed it on the network notification

---

### Post by erilidon on 2009-12-02
anyone??

---

### Post by LowSky on 2009-12-02
are you running compiz? Do you have the propretary driver installed?

only things I can think of

---

### Post by erilidon on 2009-12-02
> **LowSky said:**
> are you running compiz? Do you have the propretary driver installed?

only things I can think of

as I don't know what compiz is I am going to go with no. I didn't have to insall a properity driver either. It worked without issues until I upgraded.

Can anyone tell me perhaps how to uninstall and reinstall the network manager without having an internet connection for the reinstall?

Thanks..

---

### Post by dkruidhof on 2009-12-02
To see if you have compiz running (and turn it off if you like) go to System -> Preferences -> Appearance. Then the Visual Effects tab. Selecting None will turn it off and may fix your problem.

---

### Post by mgmiller on 2009-12-02
There is a known bug in the xorg drivers for ati video cards that causes this problem.  I have an old dell laptop with radeon m6 ly graphics that suffers from this problem.  Ati graphics cards that have low memory (mine has 16 mb) seem to have the worst time with this.  You can enable exa instead of xaa in xorg.conf, but window refresh rates get really slow.  Here is a link to the bug report with some various work arounds:
[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/429251](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/429251)

---

### Post by erilidon on 2009-12-03
Thanks for the replies. I always turn the visual effects off, just didn't know it was call compiz, I am just not much for the pretty things, just want things to work. So that wasn't it.

As for the ATI video card issue it is great to know that I am not the only one. However it states its just when compiz is enabled, It wasn't and as a further measure I have now uninstalled it and it is still garbled.

Also I am not interested in the purposed fix as I do not wish to have slower refresh rates, we use her laptop a lot to watch streaming video, wouldn't that slow that down and possibly make it choppy?

Also I never had this issue before upgrading, everything worked just fine. Is there a way to just turn off bubble notifications? This would suite me! Thanks again!

---

### Post by wilee-nilee on 2009-12-03
I had the same problem with a ati radeon with Karmic I found a script on the forums that fixed it, I will look on that computer now and see if I can find it. Can't find it sorry, removing the notification I think is possible, but if we can find the script it will probably serve you all best

---

### Post by mgmiller on 2009-12-04
> As for the ATI video card issue it is great to know that I am not the only one. However it states its just when compiz is enabled,

The compiz thing only fixes it for some ATI cards.  In my cases, I have the ATI m6 ly card and compiz is not enabled and I still have the problem.  Only the EXA change fixes it for me, but the performance is so degraded that I don't bother and just live with the problem for now.  Hopefully it will be fixed soon.

I would love to know what the script wilee-nilee found does.

---

### Post by erilidon on 2009-12-05
> **mgmiller said:**
> I would love to know what the script wilee-nilee found does.


As would I... however I just got bored and booted the laptop in question with a ubuntu 9.10 live cd and the bubble notification work, no garbage mess...

So that makes me think that something has messed it up.. whether it was my wife messing around or an update I am not sure.

But I think that I am going to reload the OS and go from there and try to see what if anything messes it up again.

---

### Post by wmMarshall on 2009-12-05
Hi everybody,

I had the same problem: notifications windows were blank with odd vertical & horizontal lines.  Also, OpenOffice opening selection screens were showing giberish, and the System Monitor program was unusable.  There's a fix over at:

[https://bugs.launchpad.net/ubuntu/+bug/466066](https://bugs.launchpad.net/ubuntu/+bug/466066)

Checkout posts 5 and 6 from user techneeq; those fixed the problem for me (although I had to reboot before the problem was fixed).  Looks like the main problem is to get the ATI card configured in xorg.

(I'm running a Dell Inspiron 5100 with a Radeon Mobility 7500 and Ubuntu 9.10.)

Good luck!  Hope this helps.

---

### Post by erilidon on 2009-12-06
> **wmMarshall said:**
> Hi everybody,

I had the same problem: notifications windows were blank with odd vertical & horizontal lines.  Also, OpenOffice opening selection screens were showing giberish, and the System Monitor program was unusable.  There's a fix over at:

[https://bugs.launchpad.net/ubuntu/+bug/466066](https://bugs.launchpad.net/ubuntu/+bug/466066)

Checkout posts 5 and 6 from user techneeq; those fixed the problem for me (although I had to reboot before the problem was fixed).  Looks like the main problem is to get the ATI card configured in xorg.

(I'm running a Dell Inspiron 5100 with a Radeon Mobility 7500 and Ubuntu 9.10.)

Good luck!  Hope this helps.

Yes, we were already aware of the "EXA" work around, just don't like the results.

As I had stated I was going to, I reloaded my wife's computer and the bubble notifications worked. Updated it and everything and they are still good!

However, I just went and checked the "Visual Effects" tab by right clicking on the desktop and selecting "Change Background" and there was nothing selected. When I selected "None" it killed the bubbles, they are garbage again.

However when I set it to "Normal" they work.. So it appears that compiz is required to be running for the bubble notifications not to be garbage... This seems to be contrary to all the other reports of the issue. But none the less my laptop is fixed now and I am all good. Thanks for all the help!

---

### Post by twowheeler on 2009-12-08
I'm just letting folks know that my old Dell suffered from the same malady as described earlier, but when I apply the "EXA" workaround everything is good.  There is no noticable slowdown, so I will stick with it.  Thanks to all for the tip.

---

