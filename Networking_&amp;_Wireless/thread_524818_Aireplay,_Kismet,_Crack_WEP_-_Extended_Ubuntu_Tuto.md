---
title: "Aireplay, Kismet, Crack WEP - Extended Ubuntu Tutorial"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by wifi-staff on 2007-08-13
Try this extended Ubuntu [hacking tutorial]("http://airdump.net/papers/hacking-wifi-ultimate-ubuntu-guide/").

The reason why I'm posting only the link is that text is very long and there are a lot of pictures too.

---

### Post by ipw on 2007-08-13
wery nice tutorial. you took my hearth :)

i have registered just now to ask:
are there any special dependencies? or what i have to have installed on my computer to get it work?

---

### Post by wifi-staff on 2007-08-14
except aircrack-ng install

sharutils
build-essential
linux-source
linux-headers

---

### Post by ipw on 2007-08-14
cool i get kismet to work with system driver.. ubuntu is cool.. i was trying mandriva before and there doesn't works anything.. now i'm going to patch the driver to try aireplay packet injection

thanks for patience :)

---

### Post by wifi-staff on 2007-08-15
nice but.. beware if you are goung to patch the driver (prism 2.5 chipset). name of the interface will probably change from ethx to wlan0 and kismet will not work with remain config. check it and reconfigure it.

---

### Post by ipw on 2007-08-15
i did patch the driver succesfuly but test in ethereal doesn't shows packet injection. it doesn't seems to be working.  how can I find what is wrong?

---

### Post by wifi-staff on 2007-08-16
did you follow the steps in manual? what kernel do you have?

---

### Post by wieman01 on 2007-08-16
Good one. I have got a Ralink chipset which works well with the Aircrack Suite. Anybody interested in a shorter version of such a guide?

---

### Post by wifi-staff on 2007-08-16
> **wieman01 said:**
> Good one. I have got a Ralink chipset which works well with the Aircrack Suite. Anybody interested in a shorter version of such a guide?

Yes, of course.. Thx

---

### Post by wieman01 on 2007-08-16
> **wifi-staff said:**
> Yes, of course.. Thx
Been thinking about writing another simple HOWTO for a while... I'll get back to you as soon as I have had the time to do so. :-)

---

### Post by wifi-staff on 2007-08-16
Cool. I thing this text can help a lot to people.

---

### Post by ipw on 2007-08-17
I have Linux 2.6.17-11-generic #2 SMP i686 and it still doesn't works

---

### Post by ipw on 2007-08-17
I have Linux 2.6.17-11-generic #2 SMP i686 and it still doesn't work

---

### Post by wieman01 on 2007-08-17
> **ipw said:**
> I have Linux 2.6.17-11-generic #2 SMP i686 and it still doesn't work
You can edit posts easily. See the 'Edit' button?

---

### Post by wifi-staff on 2007-08-17
> **ipw said:**
> I have Linux 2.6.17-11-generic #2 SMP i686 and it still doesn't works

My friend..,

this tutorial works with 2.6.15-26-386, 2.6.15-27-386, 2.6.15-28-386 kernel. The kernels in Ubuntu 6.10 I think works with Atheros chipset based cards (the driver needs to be patched - in Ubuntu 6.06 Atheros works with no patch).

---

### Post by ipw on 2007-08-17
Oh man. Sorry, I'm beggining in this theme. I'll download the older version of ubuntu because I have Prism adapter. I just want packet injection.

---

### Post by wieman01 on 2007-08-17
> **wifi-staff said:**
> Cool. I thing this text can help a lot to people.
I just posted my latest HOWTO and noticed seconds later that a similar thread had been posted 2 weeks earlier. Oh well, mine might get jailed after all. Not sure if it's gonna make it this time. I'll post later if the mods show mercy.

---

### Post by wifi-staff on 2007-08-18
> **ipw said:**
> Oh man. Sorry, I'm beggining in this theme. I'll download the older version of ubuntu because I have Prism adapter. I just want packet injection.

That's ok. it happens. Just ask again if you will need after you reinstall.

---

### Post by ipw on 2007-08-19
I found right source.list and I installed everything. What version of aircrack do you use, or will serve the version from repository?

---

### Post by wieman01 on 2007-08-20
I have created a new (simple) HOWTO for Aircrack-NG (see signature). I'll extend it soon and also cover Aircrack-PTW which makes cracking WEP keys even easier.... Feel free to try it out and send me your comments.

---

### Post by wifi-staff on 2007-08-22
I'm the Atheros card user. But if a have a chance to get Realtek I would try it. I like EW7318USg..

---

### Post by wifi-staff on 2007-08-30
> **ipw said:**
> I found right source.list and I installed everything. What version of aircrack do you use, or will serve the version from repository?

i'm using the last version that i found on aircrack-ng homepage. I think in 6.06 isn't -ng at all. Sorry for late response, I wasn't present.

---

### Post by glopv2 on 2007-12-31
I have Ubuntu Feisty on a Thinkpad t60 with an atheros chipset (I think).

I want to make my computer crack WEP keys. I found this link to the tutorial: [http://airdump.net/papers/hacking-wifi-ultimate-ubuntu-guide](http://airdump.net/papers/hacking-wifi-ultimate-ubuntu-guide)
from the beginning of this thread, but it is for a different version of Ubuntu. Is there a more recent tutorial that I can use?


Thanks!

---

### Post by wifi-staff on 2007-12-31
> **glopv2 said:**
> I have Ubuntu Feisty on a Thinkpad t60 with an atheros chipset (I think).

I want to make my computer crack WEP keys. I found this link to the tutorial: [http://airdump.net/papers/hacking-wifi-ultimate-ubuntu-guide](http://airdump.net/papers/hacking-wifi-ultimate-ubuntu-guide)
from the beginning of this thread, but it is for a different version of Ubuntu. Is there a more recent tutorial that I can use? Thanks!

Is the same for 6.06 -> 7.10. The question is driver, but at airdump.net is how to for (hostap) patching drivers in new version of Ubuntu too. Madwifi-ng still works fine.

---

