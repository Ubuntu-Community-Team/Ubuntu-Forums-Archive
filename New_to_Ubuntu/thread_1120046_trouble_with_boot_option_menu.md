---
title: "trouble with boot option menu"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by gulmer on 2009-04-08
Here's the situation, I installed ubuntu on to a friends computer, replacing his slow running XP os.The install worked flawlessly, ubuntu ran without any hang ups, even connected wireless to his modem and recognized his printer using the wireless card, he loved it. Then he wanted me to buy and install another hard drive and install his Windows XP os on it. I did this without any trouble. He now has 2 operating systems on 2 different hard drives, now for the problems that came about after. When we first turned on the computer, it booted to ubuntu immediately, without a boot menu. I searched the forum for a fix, to get a boot menu running and found that I needed to install the "start-up manager" to get the menu, did that, menu can up and no xp in list, under the list of linux kernels, then I found this on the forum:                            title XP
root  (hd1,0)
savedefault
makeactive
map   (hd0) (hd1)
map   (hd1) (hd0)
chainloader    +1  

 entered this and now xp is in list, but the keyboard arrows wont scroll to select which os to choose, could not get into xp again, then I really messed it up when I chose xp as the default os in the start-up manager, now all we can get is xp and no scrolling to get back to ubuntu.
What can I do to get ubuntu back and get the keyboard arrows to work on the boot menu? 

 Thanks for all answers.

---

### Post by kansasnoob on 2009-04-08
Is that a usb keyboard?

---

### Post by gulmer on 2009-04-08
yes, and I tried a different usb port without any luck.

---

### Post by kansasnoob on 2009-04-08
Read here:

[http://www.intel.com/support/peripherals/sb/cs-011939.htm](http://www.intel.com/support/peripherals/sb/cs-011939.htm)

Those are pretty good instructions (as good as any I could write).

As it says you'll need to temporarily use a PS/2 keyboard and the puter **MUST be shutdown when plugging it in!**

You may have to do some googling to find specific BIOS info for that computer.

---

### Post by presence1960 on 2009-04-08
> **kansasnoob said:**
> Read here:

[http://www.intel.com/support/peripherals/sb/cs-011939.htm](http://www.intel.com/support/peripherals/sb/cs-011939.htm)

Those are pretty good instructions (as good as any I could write).

As it says you'll need to temporarily use a PS/2 keyboard and the puter **MUST be shutdown when plugging it in!**

You may have to do some googling to find specific BIOS info for that computer.

Yep, I remember a thread that was so long not too long ago with the same issue. After about 50-60 more posts after the suggestion was made the OP finally realized he never checked in his BIOS to enable that option. When he finally did that everything went fine.

---

