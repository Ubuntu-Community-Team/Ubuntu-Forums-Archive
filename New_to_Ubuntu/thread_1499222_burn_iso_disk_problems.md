---
title: "burn iso disk problems"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by davellew69 on 2010-06-01
Hi , any ideas to my dilema, I seem to be having problems burning 10.04 onto a disk, I have used various disk burning software , inc1 infa recorder, but each time I end up with WUBI instaler? when i load the disk into the laptop and run to install, I get nothing, I have even lsft the machine  for over an hour ?

Any ideas what is wrong

---

### Post by spiky001 on 2010-06-01
I take it you dont want to install under wubi? if not have yo set the bios to boot from cd then booted of cd?

---

### Post by XubuRoxMySox on 2010-06-01
When you download the Ubuntu .iso file, save it on your hard drive. Then open your CD-burning application and burn the file **as an [COLOR="Red"]image[/COLOR]**, *not* as a data file.

Now when you're ready to install Ubuntu, put in the CD you just burned and reboot your computer. On most computers, during boot-up, and usually right after the manufacturer's logo is displayed, there's a short little display that offers something like "Press F12 for Boot Options" (your computer's message may be different - watch for it and quickly press whatever key it says for Boot Options or Boot Order. Most people say to press it repeatedly a few times.

That should take you to a little screen where you can select "first boot device." This is where you tell your computer to **boot from the CD-ROM** instead of the Hard Drive. Do that, hit Enter, and watch the magic happen from there!

Just be aware that Ubuntu runs a little slower from the LiveCD than it does when it's actually installed on your machine. Take it for a test drive! Kick the tires, play, have fun! You're using Ubuntu Linux without any changes to your computer at all.

Now if you decide you want to install Ubuntu, there's an icon for that. Just click on it, answer a few questions (your location, name, choose a password, etc) and you're on your way.

Enjoy,
Robin

---

### Post by davellew69 on 2010-06-05
Gone through the whole thing agin, burnt a image disk, but still got the same problem

---

### Post by davellew69 on 2010-06-05
LOl sorry I think i`m in luck , watch this space !!!

---

### Post by Mark Phelps on 2010-06-05
You sure you're booting directly from the CD?  Asking because when you boot into an OS and insert an Ubuntu disk -- it PRESUMES you want to do a Wubi install and offers that by default.  When you boot directly from the CD, it assumes you want to install to its own partition, not a Wubi install.  Sounds like you're really booting from the hard drive, not from the CD.

---

