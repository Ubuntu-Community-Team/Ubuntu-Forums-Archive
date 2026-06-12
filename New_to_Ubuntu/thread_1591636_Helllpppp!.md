---
title: "Helllpppp!"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by abwoitas on 2010-10-09
ok i am a complete beginner on ubuntu i have a dell mini 9 and am running hardy heron.
anyways i downloaded some stuff on accident and deleted some stuff i shouldn't have. to get to the point i want to completely delete everything and start over the way it was. It just came with ubuntu so i cant like switch back to windows. i just want everything deleted and restarted plz help

---

### Post by nothingspecial on 2010-10-09
A few more details might help.

What have you done?

---

### Post by CharlesA on 2010-10-09
Just download that version of Ubuntu and burn it to a cd or throw it on a USB stick.

---

### Post by anewguy on 2010-10-09
Or even check and see if they put a recovery partition on the hard drive for you that you can access during boot.  My Acer netbook came with one (albeit Windows).

Dave

---

### Post by abwoitas on 2010-10-09
well i donwloaded a crap load of applications that dont do much. Which slowed the computer. Then as i was trying to get rid of applications like pidgin and evolution mail, it deleted extra things idk what. Now when i restart my netbook there are no borders on the top or bottom of the screen only icons of web browser and skype. i cant open anything either, like the package manager wont load due to errors, but i cant reach it anyways because the border with file,system, places, etc isnt there.

---

### Post by nothingspecial on 2010-10-09
> **abwoitas said:**
> well i donwloaded a crap load of applications that dont do much. Which slowed the computer. Then as i was trying to get rid of applications like pidgin and evolution mail, it deleted extra things idk what. Now when i restart my netbook there are no borders on the top or bottom of the screen only icons of web browser and skype. i cant open anything either, like the package manager wont load due to errors, but i cant reach it anyways because the border with file,system, places, etc isnt there.

Removing pidgin and evolution can mess things up in 8.04

reboot and select recovery mode

type

```
sudo apt-get install ubuntu-desktop
```

Then ```
exit
```

Then start as normal

---

### Post by Gone fishing on 2010-10-09
I'd download the latest Ubuntu 10.04 or possibly Mint. Burn the live CD, then start up on the Live CD, plug in an external hard drive and backup everything you wish to keep.

Then install and let the new Ubuntu use the whole disk, it would be even better, to in the install create three partitions one for /, one for /home and a small one for swap.

---

### Post by ubudog on 2010-10-09
Yeah, it's pretty stupid that it does that, so, you can reinstall, just put Ubuntu on a USB Disk, or use the CD you installed with.  Or, I made a script for this exact problem which happened to me a while back.  It fixed everything for me, got back all my lost apps, so it may install some stuff that you don't want.  You can just edit that stuff out if you want.  Let me know if you want it.

---

### Post by nothingspecial on 2010-10-09
You will need a wired connection for that to work.

---

### Post by abwoitas on 2010-10-09
0kay but how can i get to terminal without those borders, is there a keyboard combo to open it?

---

### Post by nothingspecial on 2010-10-09
Ctrl Alt F2 

at the same time, you will have to log in, and you will need a wired connection

---

### Post by abwoitas on 2010-10-09
the only way i can connect is my wifi i dont have a wired connection

---

### Post by nothingspecial on 2010-10-09
If you are connected it will still work if you can get to a terminal - Ctrl Alt F2

If not, we can do it manually

---

