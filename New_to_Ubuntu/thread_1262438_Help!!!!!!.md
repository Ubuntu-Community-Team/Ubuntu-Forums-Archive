---
title: "Help!!!!!!"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by timinator94 on 2009-09-09
I DOWNLOADED ubuntu on my windows machine, burned the iso and tried to boot from it but it says DISK ERROR Please help because i want to try ubuntu badly

---

### Post by earthpigg on 2009-09-09
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

that should get you pointed in the correct direction.

emphasis:
use a CD-R, and not a dvd-r or cd-rw or *anything else*.
burn at the *slowest speed possible*.

---

### Post by drs305 on 2009-09-09
Welcome to Ubuntu timinator94. 

Are you able to even get to the menu? If so, there is a disk check option.

If it doesn't work at all, you might try reburning it a slow speed. Here is the Ubuntu Wiki on burning ISOs:
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by earthpigg on 2009-09-09
edit: was a double post, ignore please.

---

### Post by sandyd on 2009-09-09
more people might help.... if you post a more descriptive thread title.

Have you tried choosing the "check disk for errors" option?
or does the error appear before that.
If the disk has errors, burn the cd slooooowwwwllyyyy. and compare the md5 checksums of the ISO and the MD5 checksum thats provided on the ubuntu site.

edit: they beat me.

---

### Post by timinator94 on 2009-09-09
now i fixed that prob but now when i click install it shows bars across my screen that flash and it appears to freeze up

---

### Post by earthpigg on 2009-09-09
> **timinator94 said:**
> now i fixed that prob but now when i click install it shows bars across my screen that flash and it appears to freeze up

you fixed that problem by burning a new cd properly, or by randomly pointing and clicking around on the probably faulty cd and getting it to go one step farther before presenting another problem?

the more specific you are, the better we can help you.

---

### Post by papuccino1 on 2009-09-09
Here's what you do.

Use a CD-R or a DVD (I used a DVD today so I know for a fact it works) and burn the ISO at 8x speed.

When prompted use the alternate installation so you dont go into live session, it's faster this way.

---

### Post by BobJam on 2009-09-10
> **carlee said:**
> if you post a more descriptive thread title.Another reason to do that is searches.  If people are searching for a solution on, say "iso" issues, then if your post was titled something like "Disk Error on downloading and burning ISO", then it would show up in a Title search.  Not too many people are going to do a Title search on just plain "Help".

Don't mean to be abrasive here, but carlee is right for several reasons.

Just a friendly tip.

---

### Post by QIII on 2009-09-10
> **timinator94 said:**
> now i fixed that prob but now when i click install it shows bars across my screen that flash and it appears to freeze up

Do you have an Intel graphics chipset?

---

### Post by timinator94 on 2009-09-10
> **QIII said:**
> Do you have an Intel graphics chipset?

no i have a msi chipset with an amd athlon x64 3500 with an nvidia geforce 6800

---

### Post by timinator94 on 2009-09-10
Ok i will be more specific with what ive been doing to ubuntu

Ive heard many good things about ubuntu and am looking for a way to ditch windows. I downloaded ubuntu 9.04 of ubuntu.com and used DVD ISO Burner to burn it to a cdr. When i booted from the disk and clicked Install Ubuntu an error popped up and said ''Disk Error"
so mi burned another iso using a different program and in windows it poped up that i could install without booting. So i did that and my comp rebooted and another partition showed up saying ubuntu. I selected it and a load bar poped up after the bar was done vertical lines poped up and danced on my screen. I waited an hour and it was still there so i unpluged it and booted back into windows. Please help

---

### Post by nothingspecial on 2009-09-10
Try booting from the new cd.

---

### Post by presence1960 on 2009-09-10
> **timinator94 said:**
> Ok i will be more specific with what ive been doing to ubuntu

Ive heard many good things about ubuntu and am looking for a way to ditch windows. I downloaded ubuntu 9.04 of ubuntu.com and used DVD ISO Burner to burn it to a cdr. When i booted from the disk and clicked Install Ubuntu an error popped up and said ''Disk Error"
so mi burned another iso using a different program and in windows it poped up that i could install without booting. So i did that and my comp rebooted and another partition showed up saying ubuntu. I selected it and a load bar poped up after the bar was done vertical lines poped up and danced on my screen. I waited an hour and it was still there so i unpluged it and booted back into windows. Please help

You installed via wubi. Boot into windows and go to Control Panel. Uninstall Ubuntu as you would any other program. Then boot the Live CD and hit F4 and choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions").

if that does not work you may want to try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by timinator94 on 2009-09-10
Thanks that worked im online on ubuntu now Thanks again

---

### Post by presence1960 on 2009-09-10
Glad you got it working! Enjoy Ubuntu.

---

