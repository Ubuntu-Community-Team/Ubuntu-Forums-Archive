---
title: "keyboard doesn't work at grub page"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by chaddiesel on 2009-03-16
I just bought a new keyboard that is USB instead of PS2. I don't have an adapter to the PS2 port but I know there is a way to configure the keyboard to work in grub. 

The good thing is I use ubuntu 90 percent of the time but I still need access to windoze. Is this a BIOS fix or a ubuntu x-server fix?:D

---

### Post by iaculallad on 2009-03-16
I had experienced that once, I had to buy a USB-to-PS2 keyboard adapter for me to access boot settings. 
I even can't access the BIOS settings page through the Del key.

*Buy an adapter or use a PS2 keyboard*

EDIT: Trying to base my suggestion on my current motherboard.

---

### Post by chaddiesel on 2009-03-16
Dang, what is weird is I can get to bios but can't get it to work on grub.  I didn't poke around enough to find what I was looking for. I'll give it another shot and see what happens. 

Thanks for the quick reply.

---

### Post by Weidbrewer on 2009-03-16
Just to cover the bases, it isn't always "del" that enters BIOS...double check as the computer is booting up.

Once in BIOS, there should be something that says "USB Startup driver," or possibly under "Keyboards."  There will then be an "Enable/Disable" option.

Now, this is assuming your motherboard allows it.  Some older ones don't have the capability to enable USB ports on boot.


I hope this helps.

---

### Post by chaddiesel on 2009-03-16
I got it to work from the bios settings. 

Thanks alot everyone. :D

---

### Post by presence1960 on 2009-03-16
> **chaddiesel said:**
> I just bought a new keyboard that is USB instead of PS2. I don't have an adapter to the PS2 port but I know there is a way to configure the keyboard to work in grub. 

The good thing is I use ubuntu 90 percent of the time but I still need access to windoze. Is this a BIOS fix or a ubuntu x-server fix?:D

Look in your BIOS and see if you have a setting for USB keyboard or Legacy.

We just had this problem with someone. Check out post #39 on this page : [http://ubuntuforums.org/showthread.php?t=1095619&page=4](http://ubuntuforums.org/showthread.php?t=1095619&page=4)

Hope this helps.

---

