---
title: "ubuntu update to jaunty- will I keep everything?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by DaybreakBoy on 2009-04-22
I have looked a round a bit, but all my searches bring up problems with update manager "not doing its job".

My question is; when I update, will all my audio and video codecs still be there, and will my sound config (which took me like three weeks to get working) be the same, will evoloution mail still have my calender appointments, and so on. 

TL;DR, is it as time consuming updating from intrepid to jaunty as it is moving from windows to linux?

---

### Post by halitech on 2009-04-22
most people are going to post here when they have issues, very few post to say "Hey, I did the update and things went smoother then fine wine and everything is great" so its hard to say how many times updates go well in ratio to when they go wrong.

In theory, everything *should* go fine but as in any case when you are making major changes to your system, make sure you back up *everything* you don't want to lose in case something does go wrong.

I'm not sure on a time frame but will probably depend on the speed of your internet connection and the speed,memory, hard drive of your computer as to how long it will take.

---

### Post by DaybreakBoy on 2009-04-22
Thank you. 
If I can express myself a little clearer, is going from one release to another like doing an "update" (where it only replaces certain parts), or like doing a "reinstall" (all add-ons are gone, all preferences revert to default)?

---

### Post by halitech on 2009-04-22
it will be an update and programs and preferences will be saved but the version numbers will be changed unless they have dropped a particular app and replaced it with something else.

---

### Post by DaybreakBoy on 2009-04-22
Thanks Halitech.

---

### Post by Shpongle on 2009-04-22
any idea about themes and stuff, are they replaced by the default in jaunty?

---

### Post by nandemonai on 2009-04-22
Themes and the like are by default installed into hidden directories in your /home directory and hence will not be lost on a distribution upgrade.

---

### Post by Shpongle on 2009-04-22
ah ok, thanks for the info :)

---

### Post by bm13084 on 2009-04-22
is it better just to reformat and reinstall? or is this pretty much the same as far as gaining new features?

---

### Post by nandemonai on 2009-04-22
There are two schools of thought on fresh or upgrade.

1. Fresh is cleaner and a fresh slate.

2. Upgrades keep most if not all of your existing settings but can leave residue.

Personally I go fresh and just remount my separate /home partition. 

Though this release I went completely fresh as I had a lot of junk I didn't want anymore in Ibex (KDE, XFCE and the like). I've been testing since early beta.

---

### Post by TrueDego on 2009-04-22
When I upgraded from 8.04 to 8.10, I lost my network settings.  I was using a Broadcom wireless card and it didn't save my NDISWrapper settings but lucky for me I blogged it so it wasnt to hard to get everything back.  Other than that, all of my Ubuntu upgrades have been flawless.  Just save your home folder(s) elsewhere and you should be able to keep everything.  

Side note, I have FF 2 on this computer and if I upgrade to 9.04, will all of my info be sent to FF3 or will FF2 still be my browser?

---

### Post by presence1960 on 2009-04-22
> **nandemonai said:**
> There are two schools of thought on fresh or upgrade.

1. Fresh is cleaner and a fresh slate.

2. Upgrades keep most if not all of your existing settings but can leave residue.

Personally I go fresh and just remount my separate /home partition. 

Though this release I went completely fresh as I had a lot of junk I didn't want anymore in Ibex (KDE, XFCE and the like). I've been testing since early beta.

+1

I always do a clean install. My separate /home partition retains my settings. But that is my personal preference. Either way (clean install or upgrade) will work.

---

### Post by bm13084 on 2009-04-23
yeah, i usually do a clean install each time... but i was wondering because i'm feeling lazy about redownloading ALL of my programs and redoing ndiswrapper etc...

thanks for the info :)

---

### Post by Bios Element on 2009-04-23
> **bm13084 said:**
> yeah, i usually do a clean install each time... but i was wondering because i'm feeling lazy about redownloading ALL of my programs and redoing ndiswrapper etc...

thanks for the info :)

Set a day aside, get a big snack ,something to drink ,a few good movies and just spend a day configuring things. Trust me, you'll thank yourself later.

---

### Post by raymondh on 2009-04-23
> **nandemonai said:**
> There are two schools of thought on fresh or upgrade.

1. Fresh is cleaner and a fresh slate.

2. Upgrades keep most if not all of your existing settings but can leave residue.

Personally I go fresh and just remount my separate /home partition. 

Though this release I went completely fresh as I had a lot of junk I didn't want anymore in Ibex (KDE, XFCE and the like). I've been testing since early beta.

+ me too

Fresh from 8.04 to 8.10 to 9.04 beta and now 9.04 RC.  Waiting a week or so before I do a fresh Final 9.04.  Only once did I try a network upgrade (8.10 to 9.04 beta) and I had to re-do with a fresh install.  Thank you, whoever thought about separating / from /home, /etc, /var. /boot :)

---

