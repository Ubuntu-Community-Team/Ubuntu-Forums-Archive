---
title: "How to reinstall grub with new settings?"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by jinba.ittai on 2011-01-23
I had 2 ubuntus installed on 1 hdd by accident and just deleted the extra install of it. Im afraid grub was located on that one though since it was teh last one installed.

How do i reinstall grub? Or is there anyway to make it boot straight into ubuntu without the need of grub?

---

### Post by Rubi1200 on 2011-01-23
Reinstall GRUB from the LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by CharlesA on 2011-01-23
Have you run this:

```
sudo update-grub
```

The Rubi1200 posted will probably get the job done.

---

### Post by leclerc65 on 2011-01-23
Program Grub Customizer helps me a lot.

I am starting to to have a feel with Grub in 8.04 then Grub2 makes me lost completely.

---

### Post by CharlesA on 2011-01-23
Generally the stuff that worked for Grub1.5 doesn't work with Grub2. Check out the wiki page on Grub2.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by jinba.ittai on 2011-01-25
Is there any way i can install grub via usb? I turned off my pc that night and forgot about what i had done hence the super late reply. 

I do have another pc on windows xp (moms haha ill convert her soon!) but im not to sure how to install grub to my flash to make it bootable.

---

### Post by CharlesA on 2011-01-28
I think you can, should be able to just install it the same way as you do for a normal hdd.

---

