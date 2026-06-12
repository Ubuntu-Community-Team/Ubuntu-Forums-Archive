---
title: "Install XP Over Ubuntu With USB With Broken Keyboard"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by demonboy on 2011-04-01
I have an annoying problem. I need to send my computer in to a repair shop due to a number of hardware issues. Currently I have Ubuntu installed but I live in India and so to make life easier, and to delete all personal data from the hard drive, I want to reformat the hard drive and install XP before handing it over.

The problem is that there is an issue with the keyboard. The 'e' key is permanently stuck and I have to press random keys to stop it. It is impossible to pause at the grub screen.

What I need to do is boot up from USB with the XP iso on it. However because Ubuntu is currently installed do I need to reformat the USB stick to something other than FAT? I mounted the XP iso using UNetbootin but at boot-up it did not recognise the XP OS. I formatted the USB stick with both FAT32 and ext2.

Your confused...

---

### Post by arochester on 2011-04-01
You have no need to go to Grub. You need to change the Boot order, so the computer will boot from USB before the Hard Drive. 

How you do this will depend on the Make and Model of your Computer (I assume that it is a laptop because otherwise you would just swap to a new keyboard.)

I have two Dells. I can either go to BIOS by pressing F2 at startup, and permanently change startup order, or press F12 and temporarily change startup order

---

### Post by Zintha on 2011-04-01
> **arochester said:**
> You have no need to go to Grub. You need to change the Boot order, so the computer will boot from USB before the Hard Drive. 

How you do this will depend on the Make and Model of your Computer (I assume that it is a laptop because otherwise you would just swap to a new keyboard.)

I have two Dells. I can either go to BIOS by pressing F2 at startup, and permanently change startup order, or press F12 and temporarily change startup order

+1

Also, if you can't find BIOS Boot order, go into the BIOS Setup, usually its in there too.

But it depends on your mobo.

---

### Post by demonboy on 2011-04-01
Sorry guys, I should have explained that I did this. When I boot from USB first it just says 'Operating system not found' or words to that effect. Despite mounting XP on the USB and changing boot order to USB first it ignores the stick.

What is the correct procedure for mounting XP on USB to run on an Ubuntu-formatted hard drive?

---

### Post by Zintha on 2011-04-01
Usually its the other way around...

Thats a weird one, wasn't sure if you could boot windows from a USB to begin with.

---

### Post by demonboy on 2011-04-01
You can because I've done it before, but I've never reformatted an Ubuntu-only hard drive back to XP.

---

### Post by demonboy on 2011-04-01
Can anyone else help? Any pointers?

---

