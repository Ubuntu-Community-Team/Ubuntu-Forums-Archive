---
title: "Vodafone Mobile Connect Issue Hardy"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Lord Paladin on 2008-05-02
G'day
I have been using the VMC linux driver on 64 bit for a couple of months now with no issues, installed the python dependencies and it just worked.
Just did a fresh install of 64 bit Hardy installed all the python dependencies and I can't get VMC to work, it says its starting and thats it. Tried a few different deb packaged versions and even installed one from source still nothing.

Has anyone had success with VMC and Hardy 64bit in particular
Does anyone have any ideas.

Id apprecialte anyhing you've got

Thanks

---

### Post by daka on 2008-05-03
Hi

I too had problems.  I now have it working but have to go through a few hoops:

1. modprobe usbserial vendor=0x12d1 product=0x1003
2. remove (disconnect modem) five seconds and re-connect
3. in a few moments .. sudo modprobe -r ehci_hcd
4. click on Vodafone Connect Card

It should connect as usual after those steps

daka

---

### Post by daka on 2008-05-03
One more thing... for some reason Firefox is put into 'offline' mode and can't connect to pages unless you go to 'File' and unclick 'offline'. Similar problem with Evolution for me, have to force the online status to check emails.

If anyone gets this sorted please let me know

daka

---

### Post by Lord Paladin on 2008-05-03
Thanks alot Daka
You've saved me days of stuffing around, works well.

---

### Post by orawax on 2008-05-07
> **daka said:**
> It should connect as usual after those steps

THANKS, this works.
Do I need to repeat these steps every time I want to connect?

Could it be possible to fix this automagically by adding something to
/etc/modprobe.d/options or /etc/modules ?

---

