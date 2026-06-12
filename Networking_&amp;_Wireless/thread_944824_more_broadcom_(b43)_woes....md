---
title: "more broadcom (b43) woes..."
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by stormcrow_wolf on 2008-10-11
Let me start at the beginning.  I've had this Dell laptop for a while now, and it has a Broadcom 4318 mini-pci (Dell wlan mini-pci card model 1350) wlan card in it.  At first I had Ubuntu 8.04 on it and everything worked moderately well... wireless had terrible range but it at least worked with both open and WPA protected APs, but for various reasons I had to switch it back to Windows for a while.  I recently moved back to 8.04 and did the full update and all, installed the b43 firmware again after the update (which included a new kernel although it's still listed as 2.6.24-19 generic) and suddenly wireless no longer would scan, associate, or anything else whether the radio was active or not.  In /var/log/messages i would get these messages:  "wlan0:  interface is not ready" and wpa would not work.  Setting up WPA manually from the command line would give me errors "ioctl: operation not supported" and while wpa_supplicant would still run, the interface would not associate with any access point. 

So I tried other kernels and distributions, and the same problems kept cropping up, slackware 12.1 with a new 2.6.27 kernel, the proper firmware and wpa_supplicant (v 0.5.10) would error out.  It would scan APs fine and show all the ones within easy reach, but no joy on WPA protected APs.  The module would give the same error each time "wlan0: interface is not ready" and nothing would happen or it would try to associate with a neighbor's open ap.

Can anyone confirm this is an upstream issue and I'm not the only one having problems with the b43 module both with the upgraded 8.04 kernel and the newly released vanilla kernels or is it just me?  I've googled around, and while I've seen similar errors with wpa_supplicant, but nothing that matched my problem.

I'm currently back to Ubuntu 8.04 using the initial kernel without an update because I'm afraid if I do, the card will again stop working.  Anyone have suggestions?

---

### Post by Ayuthia on 2008-10-11
This is probably not the best answer, but you might try using ndiswrapper.  I think that I saw that you tried it once before, but you are using 64-bit.  This [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") has an option for your card.  Some bcmwl5 drivers come with the 64-bit driver which will work with ndiswrapper.  As for needing the b44 driver, you should be able to use ndiswrapper with it with the workaround that is labeled as "Hardy Bug Fix".  It will remove all the possible wireless drivers along with the b44 driver, load ndiswrapper, and then load the b44 driver back.  The ssb driver needs to be loaded after ndiswrapper or else it will take over the wireless card before ndiswrapper can get to it.

Hope this helps.

Here is the link that is the help thread for the link above:
[http://ubuntuforums.org/showthread.php?t=870086](http://ubuntuforums.org/showthread.php?t=870086)

---

### Post by stormcrow_wolf on 2008-10-11
No, the laptop is i386, but the reason I can't use NDISwrapper is because I need native Linux functionality that's not included in NDISwrapper.   I think you're getting my post confused with the other person's thread using a broadcom card in an x86-64 computer.

Basicly what i need to know is where and what exactly changed between initial 8.04's kernel and the most recent one that broke the native b43 kernel module for us with a 4318 chipset.

---

### Post by Ayuthia on 2008-10-11
> **stormcrow_wolf said:**
> No, the laptop is i386, but the reason I can't use NDISwrapper is 2 fold.  One, NDISwrapper requires me to remove the ssb module which eliminates b44 module as well. b44 is dependent on ssb and that's my wired ethernet port, strike one.  Secondly, NDISwrapper removes functionality I need, so that's strike two and three.  

Unless someone figures out where the problem is and there's a fix or at least a valid workaround suggested (no, NDISwrapper isn't valid for me for the above reasons), I have to stick with the older kernel or I have to try to find someone with a verified Atheros or Ralink chipset minipci card to sell.

My post was in another thread regaurding his computer which using the Ubuntu AMD64 version. Using NDISwrapper with the AMD64 kernel which is generally a no-no.  You can't use a 32 bit windows driver with NDISwrapper in a AMD64 linux kernel.
I have a 4311 card that is able to use NDISwrapper in 64-bit mode (with an AMD64) without any problems.  I also had a 4306 rev 03 card with a b44 ethernet card that worked with ndiswrapper without any problems.  I will agree with you that you cannot use a 32-bit windows driver with a 64-bit kernel though.

Going back to your issue with the b44 card, you need to load the b44 module after ndiswrapper is loaded.  As long as you do this, both the ndiswrapper driver and the b44 driver will work.   However, I do not know what functionality you are missing with NDISwrapper so I cannot help you there.

---

### Post by stormcrow_wolf on 2008-10-11
> **Ayuthia said:**
> I have a 4311 card that is able to use NDISwrapper in 64-bit mode (with an AMD64) without any problems.  I also had a 4306 rev 03 card with a b44 ethernet card that worked with ndiswrapper without any problems.  I will agree with you that you cannot use a 32-bit windows driver with a 64-bit kernel though.

Going back to your issue with the b44 card, you need to load the b44 module after ndiswrapper is loaded.  As long as you do this, both the ndiswrapper driver and the b44 driver will work.   However, I do not know what functionality you are missing with NDISwrapper so I cannot help you there.

Heh, sorry, I reread your post and edited mine to be less annoying.  My apologies.  However, I'm still back to the problem that NDIS drivers can't address, they lack functionality I currently need in the native linux drivers.  May just be easier to just order a new card *shakes a fist at Broadcom* WITHOUT a broadcom chip in it.

---

### Post by Ayuthia on 2008-10-11
> **stormcrow_wolf said:**
> 
Basicly what i need to know is where and what exactly changed between initial 8.04's kernel and the most recent one that broke the native b43 kernel module for us with a 4318 chipset.

Can you post the results of:
```
dpkg -l linux-image-2.6.24-19-generic
```
This will help us see what the current version that you are using for the kernel.  From there, we can see if we can find the updates that were done for that version.

---

### Post by Ayuthia on 2008-10-11
> **stormcrow_wolf said:**
> Heh, sorry, I reread your post and edited mine to be less annoying.  My apologies.  However, I'm still back to the problem that NDIS drivers can't address, they lack functionality I currently need in the native linux drivers.  May just be easier to just order a new card *shakes a fist at Broadcom* WITHOUT a broadcom chip in it.

No need to apologize.  I can understand your frustration.

Broadcom is getting better though, unfortunately, it has not been for your card.

---

### Post by stormcrow_wolf on 2008-10-11
> **Ayuthia said:**
> Can you post the results of:
```
dpkg -l linux-image-2.6.24-19-generic
```
This will help us see what the current version that you are using for the kernel.  From there, we can see if we can find the updates that were done for that version.

It says:

linux-image-2.6.24-19-generic version: 2.6.24-19.34

That's the version that is currently working, which I've not updated since the most recent installation (the 8.04.1 ISO image).

---

### Post by Ayuthia on 2008-10-11
> **stormcrow_wolf said:**
> It says:

linux-image-2.6.24-19-generic version: 2.6.24-19.34

That's the version that is currently working, which I've not updated since the most recent installation (the 8.04.1 ISO image).

I did not find much, but here is a link to the linux updates for Hardy and Intrepid.  It does have some stuff for the b43 card, but I did not see anything that was significant.

[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

### Post by stormcrow_wolf on 2008-10-11
> **Ayuthia said:**
> I did not find much, but here is a link to the linux updates for Hardy and Intrepid.  It does have some stuff for the b43 card, but I did not see anything that was significant.

[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

And there's nothing obvious there that would break b43 in hardy... since i'm still using 24-19 rather than 24-21 the bluetooth coexistence patch hasn't been integrated.  19-33 has a small patch but that's already in this kernel.  This is very weird, i wonder if something else is going on somewhere not actually in the b43 module?

---

