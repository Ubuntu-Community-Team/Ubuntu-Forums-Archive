---
title: "i screwed it up :( - freeze on bootscreen"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-15
I recently changed my settings (getting a new theme, which works fine), login screen (which seems to work) and boot screen to ...infinity (using these instructions. [http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13))

Now when i restarted and booted, it gets stuck on the bootscreen. I select Linux (top one) from GRUB and it just gets stuck on the bootup. Right now i am using low graphics failsafe mode.  Any suggestions? I was going to ask if there was any way to do the equivalent of Window's Restore last working session, but i like the changes i've made (aside from the boot screen).

I'll try changing the bootscreen back, but any suggestions?

Also, while I'm at it, is this normal? In GRUB i have what looks like two linuxes and a windows. i could have sworn i installed lynx fresh. (attached image)

---

### Post by wolfen69 on 2011-04-15
> **RememberWhenItRained said:**
> 
Also, while I'm at it, is this normal? In GRUB i have what looks like two linuxes and a windows. i could have sworn i installed lynx fresh. (attached image)

Yes, that is normal after doing updates. For the heck of it, at the grub prompt, boot to the 3rd line down. (the 2.6.32.28 kernel) and see what happens.

---

### Post by Rubi1200 on 2011-04-15
Did you also run the final command to update initramfs that was given in the instructions?

As wolfen69 suggested, try the older kernel and/or recovery modes.

---

### Post by RememberWhenItRained on 2011-04-15
changed boot screen back to normal and it works.

---

### Post by RememberWhenItRained on 2011-04-15
> **Rubi1200 said:**
> Did you also run the final command to update initramfs that was given in the instructions?

As wolfen69 suggested, try the older kernel and/or recovery modes.
yes, i did do the update.

---

### Post by Rubi1200 on 2011-04-15
If the problem is fixed, please mark this thread Solved using the Thread Tools near the top of the page.

---

