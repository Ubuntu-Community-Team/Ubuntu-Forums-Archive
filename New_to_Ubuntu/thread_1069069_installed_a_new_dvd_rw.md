---
title: "installed a new dvd rw"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by DarinB on 2009-02-13
i installed a new dvd rw Samsung sh202n lightscribe dual layer on a friends pc with 8.04.1 new install
the dvd does not show up in places but when i pud it a dvd i can open the dvd but when i go to play it it gives the error with totem could not open you might not have permission to open file.

---

### Post by kestrel1 on 2009-02-13
Try using a different cable to connect the drive to the motherboard & make sure that the plugs are fully inserted in to the sockets (motherboard & Drive)

---

### Post by DarinB on 2009-02-13
yep it does come up as a drive in computer although it does come up with no permissions.

---

### Post by kestrel1 on 2009-02-13
If there is no disk in the drive the permissions should show up as 'couldn't be determined'

---

### Post by DarinB on 2009-02-13
yeah i put in a dvd. which works no problem on my machine running 8.10. And the disk comes up on desktop, when i open it and click open with media player. i get the error. i also added all the dvd codex libdvdcss already. but it seems to be a permission thing.

---

### Post by DarinB on 2009-02-13
i don't know if this helps but it does say permission can't be determined when i click on the device in computer

---

### Post by egalvan on 2009-02-13
Thr CD/DVD burner on my machine shows this in fstab:

**/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0**

check it against your own fstab.

---

### Post by kestrel1 on 2009-02-13
Have you tried more than just the one media player?

---

### Post by egalvan on 2009-02-13
> **DarinB said:**
> i don't know if this helps but it does say permission can't be determined when i click on the device in computer

Under *computer* ALL of my devices show the permissions as un-determined.

And until I insert some media, the optical drive does not show on my desktop or in *Places*.

---

### Post by DarinB on 2009-02-13
it does even with the media in.when i try to play it in movie player... the error comes up permissions not determined.

---

### Post by kestrel1 on 2009-02-13
With DVD's & CD's the permissions cannot be determined, with or without disk's.
This is normal.
I would try a different media player. VLC is very good.

---

### Post by DarinB on 2009-02-13
vlc also says it can't open the dvd in the new dvd rw player how do i check the fstab

---

### Post by DarinB on 2009-02-13
there is no entry for it in /etc/fstab???
i have no idea what to do now?????

---

### Post by DarinB on 2009-02-13
how do i make a new dvd player mount???
Doesn't it need a mount point like the cd player???????

---

### Post by DarinB on 2009-02-17
i apologize for posting this twice, i wasn't getting an answer so i tried to move this to the hardware and laptop forum. and while doing that i figured out how to fix it. I would have preferred to close the thread but i haven't figured out how to do that. So here is how i fixed it in case anyone faces the same problem.

i upgraded the device firmware in windows and now it works fine. teh hardware web site wouldn't let me do it on ubuntu.

---

### Post by kestrel1 on 2009-02-17
Sorry not to have posted back, but I was busy & really couldn't think of many more options.
I am afraid that manufacturers hardly ever allow upgrades to firmware from Linux, mores the pity. That might have been one option  I would have suggested after trying another drive, but with it being a new device it is not always the first thing :(
Still at least you got it going :)
Good job & thanks for posting the result.

---

### Post by itendo on 2009-02-17
do you have the ability to use the optical drive for data and other uses, and the core problem is with playing DVDs? (jw if it is a fault of the media rather than the drive itself)

---

### Post by DarinB on 2009-02-18
it all works fine now. 
It was the firmware that needed updating.

---

