---
title: "how to recover wifi free drivers?"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by zibi on 2008-10-30
I have a dwl g630 card d link card that makes my laptop crash if the incoming traffic is too large (e.g. downloading big files).

I followed the instruction in the wiki for nfiswrapper. But the driever even if correctly installed doesn't work with the WPA2 encryption (I can't change the encryption of the wi-fi lan to which I should connect).

So I wanted to restore the free drivers and I undid the changes I made to /etc/modprobe.d/blacklist

But then the system didn't recognized anymore the card.

So I had to make a fresh install :mad:

Now I would like to try again with the ndiswrapper, this time together with the wpa_supplicant package to see if it works . But I 'm afraid that
1) it won't 
and 2) I will not to able to restore the original free drivers.

Could you tell me how to recover the free drivers?
Thanks
Luca

---

### Post by Ayuthia on 2008-10-30
> **zibi said:**
> I have a dwl g630 card d link card that makes my laptop crash if the incoming traffic is too large (e.g. downloading big files).

I followed the instruction in the wiki for nfiswrapper. But the driever even if correctly installed doesn't work with the WPA2 encryption (I can't change the encryption of the wi-fi lan to which I should connect).

So I wanted to restore the free drivers and I undid the changes I made to /etc/modprobe.d/blacklist

But then the system didn't recognized anymore the card.

So I had to make a fresh install :mad:

Now I would like to try again with the ndiswrapper, this time together with the wpa_supplicant package to see if it works . But I 'm afraid that
1) it won't 
and 2) I will not to able to restore the original free drivers.

Could you tell me how to recover the free drivers?
Thanks
Luca

Usually if you want to use the original drivers again, you will have to blacklist ndiswrapper (and remove the original drivers).  Sometimes you might even have to load the original drivers by adding them to /etc/modules (and remove ndiswrapper).

---

