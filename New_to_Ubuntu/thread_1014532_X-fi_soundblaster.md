---
title: "X-fi soundblaster"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by loseby on 2008-12-17
Ok, have just installed 8.10 and graphics for the 4800 series now have drivers that work. 

Also have read Creative labs have made available what was required for the Linux community to get the x-fi sound working. Now I have no idea what 8.10 has detected on my system and when I hover my mouse over the sound icon it shows "Digital-1 100%" but no sound comes out. Now my speakers are digital ( and ttas what works on XP ) so I guess its detecting something.

Anyidea on how to get sound ?

---

### Post by talsemgeest on 2008-12-18
Try going to system>preferences>sound and changing the default mixer tracks to something else similar to your card. Then right click on the sound icon and go to the volume manager (sorry, Im on windows right now so I cant give you the exact name, it is the second one down from memory,) and make sure the master volume is right up. If it is, try a different mixer track in the sound preferences and try again.

Hope this helps :)

---

### Post by theamber on 2008-12-18
Do you have Pulse Audio installed?

---

### Post by loseby on 2008-12-19
> **talsemgeest said:**
> Try going to system>preferences>sound and changing the default mixer tracks to something else similar to your card. Then right click on the sound icon and go to the volume manager (sorry, Im on windows right now so I cant give you the exact name, it is the second one down from memory,) and make sure the master volume is right up. If it is, try a different mixer track in the sound preferences and try again.

Hope this helps :)

No sound, in sound preferences I try the test and get an error message " failed to connect stream"

---

### Post by JavonR on 2008-12-19
As I just finished installing my x-fi sound card in 8.10, I can be of some assistance :)

You need to go to the following site:[http://support.creative.com/Products/Products.aspx?catid=1&catName=Sound+Blaster](http://support.creative.com/Products/Products.aspx?catid=1&catName=Sound+Blaster)

and download the appropriate linux driver for your exact model of sound card. The readme includes very straight forward instructions on how to install it. Then, all you gotta do is reboot and you're good to go.

Good luck.

---

### Post by JavonR on 2008-12-19
Oh, also as stated above, once the driver is installed go to System>Preferences>Sound and make sure Creative X-Fi (ALSA Mixer) is selected for everything.

---

### Post by loseby on 2008-12-21
> **JavonR said:**
> As I just finished installing my x-fi sound card in 8.10, I can be of some assistance :)

You need to go to the following site:[http://support.creative.com/Products/Products.aspx?catid=1&catName=Sound+Blaster](http://support.creative.com/Products/Products.aspx?catid=1&catName=Sound+Blaster)

and download the appropriate linux driver for your exact model of sound card. The readme includes very straight forward instructions on how to install it. Then, all you gotta do is reboot and you're good to go.

Good luck.

Straight foward if you know how to use the terminal window

Ok, its uncompressed ( untarballed )in my Documents
and I will see if I can figure out what to do

---

