---
title: "Unity, nVidia...not workin!"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by mang0 on 2011-05-08
[SIZE=3]Hey guys, I'm very new to Ubuntu (installed 4 days ago, had been on 10.10 LiveCD a couple of times before).  Before I go any further, my specs:

AMD Athlon 1.46 Ghz processor [/SIZE][SIZE=3]
RAM: 1.5 GB
OS: Dual booting Ubuntu 11.04 and Windows XP
if you want to know anything else, just let me know! :)
So...I had a few problems to begin with, but most of them are fixed now. I've just got a couple more:

1). Okay, I know this has been posted before, but I haven't found anything to fix it yet. I have a nVidia Geforce FX 5200 graphics card, and when I installed Ubuntu, the 'Additional Drivers' thing popped up, telling me I needed to install an nVidia driver if I wanted to use the Unity interface (I do). I clicked install, and It installed fine, and asked me to restart. I did so, but it still wasn't the Unity GUI. I opened the 'Additional Drivers' and found this: [/SIZE][SIZE=3]
[IMG]http://www.truploader.com/uploads/5_8_2011/321986Screenshot-AdditionalDrivers.png[/IMG]


which showed that I had installed the driver, but it wasn't in use. I need to make this in use so I can use the Unity GUI. any help greatly appreciated! [/SIZE][SIZE=3]
mang0.[/SIZE]

---

### Post by Ragnew on 2011-05-08
I believe there are many major problems with unity (Especially regarding to nvidia) and overall i have found 11.4 to be very unstable. I am also experiencing similar problems and have not been able to find a solution (Mine even crashes while installing nvidia drivers) so at the moment i have reverted back to 10.10 until such time as they get around to fixing it.

---

### Post by mang0 on 2011-05-08
Aw, that's annoying....like I said, I have more then one problem, the other one I've got is Ubuntu crashing. Every so often it just freezes and I have to force shutdown with the power button...Thanks for the quick reply!

---

### Post by Sidewinder1 on 2011-05-08
Mang0
First *WELCOME TO UBUNTU AND UBUNTUFORUMS!*  =D>
I wish I could help more but I run LTS versions of ubuntu; currently 10.04, Lucid Lynx.
So I am not terribly familiar with the current problems with 11.04. 
That's kinda' the point.
Remeber that the search bar above is invaluable when trying to solve problems.\
Best of luck!

Side

---

### Post by Sidewinder1 on 2011-05-08
> **mang0 said:**
> Aw, that's annoying....like I said, I have more then one problem, the other one I've got is Ubuntu crashing. Every so often it just freezes and I have to force shutdown with the power button...Thanks for the quick reply!

Forcing shut-down with the power button is the absolute last resort; it may cause further problems.
The preferred method is: While holding down Alt and print-screen/sysrq and shift (for upper case) type REISUB (which is busier spelled backwards) pausing about two seconds between each letter.
This method should maintain your machine state and prevent data/configuration loss.
HTH, Side

---

### Post by ffeingol on 2011-05-08
Hello,

I downloaded and installed the latest driver from the Nvidia site and it's working well with my card.  It wont' show in the additional drivers, but it is working.

---

### Post by mang0 on 2011-05-08
> **Sidewinder1 said:**
> Forcing shut-down with the power button is the absolute last resort; it may cause further problems.
The preferred method is: While holding down Alt and print-screen/sysrq and shift (for upper case) type REISUB (which is busier spelled backwards) pausing about two seconds between each letter.
This method should maintain your machine state and prevent data/configuration loss.
HTH, Side

Ah, thanks, for welcoming me to the forums, and also for you reply :D I thought there would be some key command, but obv ctrl+alt+del doesn't work.....thanks for that :)

---

### Post by Sidewinder1 on 2011-05-08
My pleasure!
This is how I learned from 2007 to present, on these forums. I only discovered the
#ubuntu channel within the last 9 months or so; wish I would've found it sooner.

Side

---

### Post by spikoley on 2011-05-08
It looks like you have this [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Make sure you update the bug, it will let them know it is widespread and needs to be fixed.

---

### Post by mang0 on 2011-05-08
great thanks!

---

