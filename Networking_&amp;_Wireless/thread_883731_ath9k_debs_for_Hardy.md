---
title: "ath9k debs for Hardy"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by cyberdork33 on 2008-08-08
Ubuntuforums user, volanin, has kindly backported the wireless-testing portion of the kernel and bundled it with the new ath9k driver for Atheros cards in a deb and posted it in the Apple Users forum. Now hardy users with 802.11n Atheros cards should be able to enjoy a completely free driver! Here is the relevant post. Enjoy

[http://ubuntuforums.org/showpost.php?p=5545069&postcount=5](http://ubuntuforums.org/showpost.php?p=5545069&postcount=5)

---

### Post by TDragon on 2008-08-11
[**madwifi**]("http://madwifi.org/") achieves this as well.

---

### Post by NullHead on 2008-08-12
This is odd that you guys are saying it's wireless N ... I compiled a brand new kernel with ath9k built in the kernel, and it only got me 1mbps with wireless G ... this is depressing. The kernel worked wonderfully, but the problem is that the speeds only got me 27kbps VS. my usual 550kbps and 6mbps through my LAN. 

Perhaps I simply failed, but I was excited to try this driver. Perhaps I'll try that deb ... 

If any of you are interested, it's a 2.6.27-rc2 AMD64 kernel. I have the debs handy if anyone is interested.

---

### Post by cyberdork33 on 2008-08-13
> **TDragon said:**
> [**madwifi**]("http://madwifi.org/") achieves this as well.
This IS madwifi... at least what will replace madwifi...

madwifi has not supported the Atheros cards in the Intel Macs for a long time (had to compile code from svn). 
> **http://madwifi.org/wiki/Releases/0.9.4]This also means that v0.9.4 still has no support for AR5007 (EeePC) and AR5008 (MacBook) chipsets. An experimental patch that adds AR5007 support at least for i386 (32bit) is attached to [ticket #1679]("http://madwifi.org/ticket/1679"), while legacy AR5008 support for all platforms that MadWifi runs on is available in trunk. [/quote]

[quote=NullHead said:**
> This is odd that you guys are saying it's wireless N ... I compiled a brand new kernel with ath9k built in the kernel, and it only got me 1mbps with wireless G ... this is depressing. The kernel worked wonderfully, but the problem is that the speeds only got me 27kbps VS. my usual 550kbps and 6mbps through my LAN. 

Perhaps I simply failed, but I was excited to try this driver. Perhaps I'll try that deb ... 

If any of you are interested, it's a 2.6.27-rc2 AMD64 kernel. I have the debs handy if anyone is interested.
It supported Atheros' n-series cards. ath9k 'will' support 802.11n eventually if it doesn't already. the 1mbps reported connection is a known bug (and is not your real connection speed), although it doesn't sound like you have slow throughput for some reason.

---

### Post by ktechman on 2008-08-16
Is this thread Mac specific?

---

### Post by highlandsun on 2008-08-23
Hmm, I wish I had found this forum sooner. Anyway, my HP dv5z has an Atheros AR5009 a/b/g/n wifi card which apparently uses an AR9280 chipset, and I found the ath9k source and compiled it myself. I installed Ubuntu 8.04LTS then compiled a 2.6.26.3 kernel, then grabbed the compat tarball from here
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Then I used git to retrieve the wireless-testing tree and get the ath9k source, since it's not currently included in the compat source. After copying the ath9k source into the compat tree, a few files failed to compile because they were using some functions that were newly added to the 2.7 <linux/list.h> header. I copied the missing functions into my 2.6 <linux/list.h> and now I have a working driver. I haven't had any problems with it at all, in 802.11g mode with a Linksys WRT. I don't actually have any 802.11n gear yet, so no idea how well that works.

---

### Post by highlandsun on 2008-09-04
If you're running a 2.6.27 kernel (which is included in ubuntu 8.10) then the ath9k driver is already present, so none of this work is needed. I posted my patches for ath9k support to the linux-wireless mailing list [http://marc.info/?l=linux-wireless&m=121990907531656&w=2](http://marc.info/?l=linux-wireless&m=121990907531656&w=2) and they've already been integrated into the compat package.

So now all you have to do is follow the instructions on this page [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) and use the compat-wireless-2.6-old tarball.

---

### Post by NullHead on 2008-09-04
I can't wait for the next alpha of ubuntu to release :D 

I really wana test this out. I've never had out of the box wifi support before :mrgreen:

---

### Post by ktechman on 2008-09-04
NullHead,

     Just installed alpha 4 and could not get wireless working "out of the box".  I also applied several updates but it did not help.  It did however "see" my wireless network but it failed to connect.  Back to Hardy.

---

### Post by highlandsun on 2008-09-04
alpha4 also ships with a new NetworkManager 0.7, which also has quite a few bugs. I posted a fix for my connection issues here [http://mail.gnome.org/archives/networkmanager-list/2008-August/msg00224.html](http://mail.gnome.org/archives/networkmanager-list/2008-August/msg00224.html) but you may be seeing others. Regardless, the ath9k driver connects fine for me on 802.11g; if your kernel didn't have multiqueue support configured in it may not work on 802.11n.

---

### Post by NullHead on 2008-09-04
What's this!! Alpha5 isn't out yet :| 

[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)
>     *  Alpha 4 - Released August 14th, 2008
    * Alpha 3 - Released July 24th, 2008
    * Alpha 2 - Released July 11th, 2008
    * Alpha 1 - Released June 27th, 2008

Note the lack of Alpha 5s in that list.

---

### Post by ktechman on 2008-09-05
NullHead,  

     Is there any way to get the ath9k driver to function on the AR9281 chipset with Ndiswrapper and preserve my present wired driver or are they joined at the hip?  Thank you  for your reply, Ktechman

---

### Post by NullHead on 2008-09-05
I would suspect that is possible. 

I guess I'm not understanding your question correctly. 

So you want ath9k, ndiswrapper, and the driver for your wired device to all dwell on the same machine at the same time? 

*That* is possible with the modprobe command + the module you want to modprobe. To unload a driver, e.g. ndiswrapper, sudo rmmod ndiswrapper. 

For this particular setup, on my laptop it has ndiswrapper, b43legacy, ssb, b44 all modprobed at the same time. This will cause ndiswrapper to fail and not work properly. So I have to rmmod b44, b43, b43legacy and ssb before I can load ndiswrapper. 

I'd check your lsmod, list of loaded modules, and look for the modules that you want to load and unload.

---

### Post by ktechman on 2008-09-05
Thank you for your reply, seeing that once again this is way over my head I guess my alternative is to wait for a how-to.  I thought the "big" news was that Atheros deployed a couple of very capable people to provide a driver for this chipset.  All I have seen so far is work on the ath5k driver even the new releases dated 2008-09-05 only show support for the ath5k driver.

---

### Post by NullHead on 2008-09-05
Well I'm excited that the new atheros direct [FOSS](http://en.wikipedia.org/wiki/Free_and_open_source_software) driver, ath9k, will/should be in the next ubuntu kernel, which should give out of the box support for almost every atheros card made.

---

### Post by ktechman on 2008-09-05
Will there be any way to implement it into Hardy?

---

### Post by NullHead on 2008-09-05
You can try this thread: [http://ubuntuforums.org/showpost.php?p=5545069&postcount=5](http://ubuntuforums.org/showpost.php?p=5545069&postcount=5)

I've never tried it, but I did actually get ath9k in hardy before with a custom kernel. 

I'd drop my connection almost every 20 min.

---

### Post by ktechman on 2008-09-05
I tried that and had very little success.  Sigh... I guess that I will be waiting for the Intrepid release + a month or so for all of the bugs to be worked out.  Thank you for your response to my questions.  Ktechman

---

### Post by NullHead on 2008-09-06
You could always try using the alpha5 that was released yesterday. That had the new ath9k in the kernel included. 

It "should" just work out of the box.

---

