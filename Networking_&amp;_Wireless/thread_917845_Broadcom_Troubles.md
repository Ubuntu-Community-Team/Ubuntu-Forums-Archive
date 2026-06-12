---
title: "Broadcom Troubles"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by nightmarestreet on 2008-09-12
Hi Folks,

Just bought myself one of the new Dell Inspiron Mini 9 umpcs, and so far I'm thinking it's pretty nice -- except for the *BROADCOM* wifi card. Argh.

I've always been lucky enough to have my previous wifi cards work out of the box. So I'm not really sure what my options are. I could really use some pointers!


For the record, here's what I'm looking at:
BCM4310 (rev 01) - 14e4:4315

Now I've read around a fair bit, and as far as I can tell, my options are as follows:

- Use fwcutter to extract the firmware(?) from the Windows drivers ([http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174))

- Use ndiswrapper together with a driver (integrity unknown) which I downloaded from a link on this page ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers))

- Use some combination of the two

What I'd like to know, is what is the preferred method, and will this persist across kernel upgrades?

Is there any chance that this issue will be fixed in the next release of Ubuntu?

I saw this sticky ([http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)) but didn't try it because it didn't mention my specific card.


Would really appreciate some help sorting this out, or just any pointers in general.

Cheers!

---

### Post by TSupra88 on 2008-09-12
try this: [http://tsupra88.blogspot.com](http://tsupra88.blogspot.com)

(I've written a quick, but clear tutorial that will help you install broadcom cards and I've provided links to the necessary drivers/firmware.)

---

### Post by nightmarestreet on 2008-09-12
Okay so you say that fwcutter is more stable than ndiswrapper. I will give it a try.

I see that b43-fwcutter is in the repos, so I'll install it. Would you be able to tell me how I would go about getting wl_apsta.o for myself?

---

### Post by nightmarestreet on 2008-09-12
Just found this: [http://linuxwireless.org/en/users/Drivers/b43#FAQ-Frequentlyaskedquestions](http://linuxwireless.org/en/users/Drivers/b43#FAQ-Frequentlyaskedquestions)

BCM 4310 - This device has an LP PHY. We think that means low power. In any case, previous code does not work. The reverse engineers have translated a great deal of the code and are currently generating specs for the code writers.

Apparently b43-fwcutter does not support my card :(

---

### Post by TSupra88 on 2008-09-12
> **nightmarestreet said:**
> Okay so you say that fwcutter is more stable than ndiswrapper. I will give it a try.

I see that b43-fwcutter is in the repos, so I'll install it. Would you be able to tell me how I would go about getting wl_apsta.o for myself?

wl_apsta.o is included in the b43.zip file on that site.

---

### Post by nightmarestreet on 2008-09-12
WOOO! Wireless is working :D

Thought I'd upgrade my packages before trying anything with ndiswrapper, and after the upgrade the Restricted Hardware Manager picked up the card.

---

