---
title: "GRUB wont load Ubuntu 10.10"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by asonJ on 2011-03-28
Hey, 

Got through the install (no other OS, just UBUNTU 10.10 desktop 32bit), restarted (and it kicked out the CD), and just a blank black screen. 

After about 30 minutes i rebooted, GRUB pops up and i choose recovery mode. after 60 seconds it freezes. I choose to load Ubuntu and it just gives a blank screen. 

Where should i start looking? Or what can i show to drill down my issue? 

thanks!

---

### Post by drs305 on 2011-03-28
asonJ,

Welcome to the Ubuntu Forums.

If you are getting a blank screen it probably isn't a Grub2 (bootloader) issue. Grub 2 problems are associated with an error message, so the problem most likely has something to do with the OS.

Do you have a blinking cursor at the top left of the screen, or is the screen completely blank?

---

### Post by asonJ on 2011-03-28
Blinking Cursor

---

### Post by drs305 on 2011-03-28
> **asonJ said:**
> Blinking Cursor

This is often caused by a video problem. 

You can start the boot with a special option which will allow the system to boot, after which you will need to add your video driver.

At the Grub2 menu, press "e" to edit the top entry. If you don't see the menu, hold down the SHIFT key when you start the computer until it appears.

The menuentry will be several lines long, Use the cursor to move to the line that starts with "linux". It may end with "quiet splash".

Use the cursor to move to the end of the line. Remove "quiet splash" if they are there and add **nomodeset**

Next press CTRL-x to boot.

If it boots, select System, Administration, Additional Drivers.

Hopefully Ubuntu will find your video card and you will be able to install it. Then your system should boot normally the next time you restart it.

---

### Post by asonJ on 2011-03-28
Solved...you genius!

---

### Post by drs305 on 2011-03-28
> **asonJ said:**
> Solved...

Great. You can help us by marking the thread SOLVED via the 'Thread Tools' link toward the upper right of the first post. It allows the helpers to concentrate on threads still needing a fix.

Happy Ubuntu-ing !

---

