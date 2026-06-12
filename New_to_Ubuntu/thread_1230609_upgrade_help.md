---
title: "upgrade help?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by masonkersnick on 2009-08-03
**[SOLVED]** i want to upgrade my version of ubuntu what options do i have to go about doing this??? and what would my best option be??

---

### Post by jacklinux on 2009-08-03
what version are you running?

---

### Post by Technoviking on 2009-08-03
This page should have the info you need, if your are using Ubuntu 8.04 or later.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

T-V

---

### Post by masonkersnick on 2009-08-03
currently i am running fiesty fawn

---

### Post by jacklinux on 2009-08-03
> **masonkersnick said:**
> currently i am running fiesty fawn
Use the link that Tech posted

---

### Post by Technoviking on 2009-08-03
> **masonkersnick said:**
> currently i am running fiesty fawn

You will not be able to upgrade to Ubuntu 9.04 directly. You will have to upgrade to Ubuntu 8.04 first, then upgrade to Ubuntu 9.04.

To be honest, you may want to backup your data to a USB drive and do a fresh install. Probably faster, and less change of hiccups.

T-V

---

### Post by masonkersnick on 2009-08-03
so this link is it telling me that i have no choice but to skip the 7.10 update and go straight to the hardy update?? and if i do how long would it take roughly?

---

### Post by Technoviking on 2009-08-03
> **masonkersnick said:**
> so this link is it telling me that i have no choice but to skip the 7.10 update and go straight to the hardy update?? and if i do how long would it take roughly?

Depends on you network connection and processor speed. Usually a couple of hours. Also, if you have third party software installed, or use helper script (aka Automatix, etc...) if may cause the upgrade to bork.

T-V

---

### Post by Hospadar on 2009-08-03
I usually like to just backup my files (to a usb drive or dvd's perhaps) and install the new with a cd, then restore my files.  It always works, and for me (an experienced user) it's quick and hassle free.  

That said, the online updates typically work just fine for most people, and can be a lot easier if you are unsure what you are doing.  Especially since you are going to be doing multiple updates to get to the latest version, I would definately suggest that you back up any important personal data.

A note on backups:  Your home directory has all the files that handle the settings for your programs, all your personal data (unless you went out of your way to put it elsewhere) and just about anything else you made without the "sudo" command.  If you have enough backup space, you can just plop your entire home directory onto the backup, re-install, and then move your whole home directory back in.

Also, if you're going to be doing some backup anyways, it might be worth it to think about a separate home partition.  This lets you re-install without having to backup and replace your home partition (although you still have to re-installed programs you added after installation).
This is how all of my disks are set up, and if you feel comfortable doing it, I'd highly recommend it.

Here's a couple good guides to get you started if you do choose a separate /home:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
This procedure requires a total re-formatting of the drive, so you'd need to backup all the data you have right now that you want to keep (probably your entire /home).  That said, it is possible with some clever partition re-sizing and folder relocation to keep your current home directory intact, but if you don't know how to do that, I'd not recommend it.

Whatever you decide to do, ask any questions you have about the procedure here before you do it.  And remember, the best way to not loose all your data in an accidental mis-step is to just back it all up.

---

### Post by masonkersnick on 2009-08-03
thank you to everyone for the help i appreciate the friendly and quick nature in which my questions were answered

---

### Post by LewRockwell on 2009-08-03
back-up your valuable stuff, wipe the partition, and do a fresh install

do this AFTER!!!!!

AFTER!!!!

after you have run the 9.04 LiveCD and see that it actually WORKS!!!!

note: I did one or two upgrades in the past and they both failed in some manner

so...I don't do or recommmend "upgrades" anymore

go figure...

.

---

