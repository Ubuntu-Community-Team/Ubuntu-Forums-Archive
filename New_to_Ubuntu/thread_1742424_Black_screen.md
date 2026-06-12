---
title: "Black screen?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by kostageas on 2011-04-28
This deals with 11.04 ONLY.

I run the live USB, and get to the main install page and click try ubuntu.  I get a totally black screen with a mouse.  I can move the mouse around, but that's it.

---

### Post by K_45 on 2011-04-28
What are your specs? Laptop? PC?

---

### Post by kostageas on 2011-04-28
Laptop.  3GB DDR3, 2.8ghz AMD 64-bit CPU, ATI graphics, 320GB 5,400 rpm HDD.

It's a Dell Inspiron.

---

### Post by K_45 on 2011-04-29
Boot up the live CD, then press F4 at the menu screen, select safe graphics mode, then try loading it up.

---

### Post by kostageas on 2011-04-29
Okay, here's what I did.  I clicked f4 like you said, but it didn't give me that option.  So I clicked f6 which gave me a new menu.  The first option on the new menu was expert mode.  I did not select this.  I selected the first two options after that one.  I was able to boot fine.  Graphics worked, wireless worked, my touchpad worked (yay!!) so I installed.  Now when I boot up without the live USB, I log into my account and it takes me to a purple background (the regular background) and shows me a moveable mouse.  That is all that ever comes up.  Is it possible to set those first two things I set for the live USB to my hard drive?  Any help appreciated.  (I'm posting via live USB)

---

### Post by kostageas on 2011-04-29
Bump.

---

### Post by kostageas on 2011-04-29
The options I selected were 'acpi=off' and 'noapic'

Hope this helps?

---

### Post by K_45 on 2011-04-29
If acpi is disabled you'll lose all power management, but to set it permanently, look here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

towards the bottom.

---

