---
title: "Message icon on top panel missing on 10.04"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by accordingtofoo on 2010-05-12
Im running Ubuntu 10.04 64-bit installed with wubi. booted my laptop up today, and my message icon on the top panel was missing. i had not yet updated the system, so i did so and restarted. still nothing. its not that big a deal, but i would like to get it back. anyone know why it would have disappeared and how i can get it back? Thanks!

---

### Post by adam22 on 2010-05-12
Right click on the panel and click add...select notification area.

---

### Post by nathand28 on 2010-05-12
Have you got indicator-messages installed?

---

### Post by accordingtofoo on 2010-05-12
> **adam22 said:**
> Right click on the panel and click add...select notification area.

my notification area is still there, just the the little envelope icon that has empathy and evolution in it.

> Have you got indicator-messages installed?

how can i tell if its installed?

---

### Post by adam22 on 2010-05-12
```
sudo aptitude install indicator-messages
```

---

### Post by accordingtofoo on 2010-05-12
acemcbadass@ubuntu:~$ sudo aptitude install indicator-messages
[sudo] password for acemcbadass: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ok. now what? and thank you for your help. this is kind of odd for me. im an expert at windows, so its very frustrating being so helpless on linux.

---

### Post by adam22 on 2010-05-12
Do you need to have set up evolution or empathy first? 

Maybe...right click on the notification area where the mail should be (possibly the volume is in the same one) and remove it...then add to panel and select indicator applet.

---

### Post by phaile on 2010-05-12
I've just started getting this problem too. I had gwibber, empathy and evolution set up, all using the mail notification icon fine. Now it just doesn't show.

None of the solutions suggested so far have fixed it.

---

### Post by accordingtofoo on 2010-05-12
well, now that you mention it, i just noticed that my volume and battery are gone as well. lets try adding indicator applet and.... YES! they're all back. not in the right place, but close enough for me. i wonder why it disappeared in the first place... o well. Thank you very much for all your help.

---

### Post by adam22 on 2010-05-12
It's possible to rearrange the stuff up there, but you may have to clear space or delete the panel...at least it's back though!

---

### Post by phaile on 2010-05-12
> **accordingtofoo said:**
> well, now that you mention it, i just noticed that my volume and battery are gone as well. lets try adding indicator applet and.... YES! they're all back. not in the right place, but close enough for me. i wonder why it disappeared in the first place... o well. Thank you very much for all your help.

Right enough, my volume icon's gone too. Adding the indicator applet sorted it. Cheers guys :)

---

### Post by DarkRage4 on 2010-05-30
Glad to hear you got your icon back, and to put it back in the right spot simply right click on it, uncheck lock to panel then right click and click move. Then move it to were you want :)

---

### Post by cptNightrain on 2010-06-26
Had the same problem too and removing the notification area then adding it back to the panel worked for me as well. I'm also on 64 bit lucid.

---

### Post by YaronSh on 2010-08-18
Indicator applet it is! Thanks a lot!

---

### Post by irvingswiftj86 on 2010-09-03
I just had exactly the same problem. I could not see my envelope icon. Its the weirdest bug. I fixed it by moving the whole top bar (dragging the by whilst holding alt) to the bottom of the screen and it reappeared! So I put the bar back to the top and its completely back to normal.

I'm sure this is not an intentional feature of Ubuntu!!!!

---

### Post by irvingswiftj86 on 2011-01-24
It just happened again! Fix: Adding a new indicator applet worked for me. I then removed the old one and put the new one in the same place where the old one was.

---

### Post by [Snc] on 2011-01-24
> **accordingtofoo said:**
> well, now that you mention it, i just noticed that my volume and battery are gone as well. lets try adding indicator applet and.... YES! they're all back. not in the right place, but close enough for me. i wonder why it disappeared in the first place... o well. Thank you very much for all your help.

You can move it, just right click on it and select Move.

---

