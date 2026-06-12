---
title: "Wireless worked with 7.10, doesn't with 8.04"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by lesliek on 2008-06-05
I've got two laptops.

One runs Ubuntu 8.04 and currently connects wirelessly to my access point with no difficulty. (In other words, there's nothing wrong with the access point.)

One runs Xubuntu 8.04 and doesn't connect wirelessly to my access point anymore, though it did with no difficulty when running Xubuntu 7.10.

The wireless card is a Netgear WG511v2. I use the Windows XP driver with ndiswrapper, just like I did when running Xubuntu 7.10 (except that it's a newer version of ndiswrapper).

When I try to connect to the access point, I'm asked to enter the password (or whatever it's called) to get to the access point. I do. The little circular whirring thing keeps going round, though neither of the two lights turns green. I see the lights on my wireless card indicating an attempt to connect. After a bit, up pops again the box asking me to enter the password. I do. Same result. I can go through the routine three or four times, but no connection occurs. Then, when I've had enough, I click "cancel" when asked to enter the password again. Immediately, the two lights turn green for a moment and then the two lights turn back into the two computer icons and I have no wireless connection.

Can anyone tell me what I'm doing wrong?

Thanks for reading this,

Leslie

---

### Post by cdtech on 2008-06-05
If your using the ndiswrapper:

Try modprobe -r ndiswrapper and modprobe -r b43 then reload ndiswrapper and b43 in that order and see if it comes back.

Let me know...

---

### Post by lesliek on 2008-06-05
But I don't have a Broadcom chipset, nor does the b43 module load at startup, at least not according to the result of lsmod.

EDIT: I'm sorry, I don't know why I should have thought you a mindreader or why I should have wanted to keep it such a secret--I should've said from the outset that my card uses a Marvell chipset.

---

