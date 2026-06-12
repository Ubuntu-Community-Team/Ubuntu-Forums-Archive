---
title: "updating my BIOS?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by I am &gt;= Wes on 2009-01-03
I recently built a computer with one of my friends, it was quite the experience for both of us.  I have everything working, I'm currently running 64 bit Vista, and I'm happy enough, but it's not Linux.  My friend claims that in order to run the iso to install Ubuntu I need to update the BIOS on my motherboard.  I have an ASUS brand Intel P43 express chipset (P5QL-E) and I am having one hell of a time trying to update the BIOS to do this.  I'm trying to get 64 bit Ubuntu, and I can't even get close. I've tried going to the Intel website and updating the BIOS with the updating program they have, I don't know what else to do.  Any help is greatly appreciated.

--Wes

---

### Post by HotShotDJ on 2009-01-03
> **I am >= Wes said:**
> My friend claims that in order to run the iso to install Ubuntu I need to update the BIOS on my motherboard.Have you tried ignoring your friend's questionable advice and running the 64 bit Ubuntu installer?  Create the CD in Vista and then boot from it.  See what happens.  I doubt that you need to flash the BIOS.  What makes your friend believe that you do?

---

### Post by I am &gt;= Wes on 2009-01-03
My friend claims that he's had to do it before.  I've tried it without and Vista won't recognize the iso, let alone run it.

---

### Post by HotShotDJ on 2009-01-03
> **I am >= Wes said:**
> My friend claims that he's had to do it before.  I've tried it without and Vista won't recognize the iso, let alone run it.You don't "run" an ISO.  It is a disk image.  You burn it to a CD using CD burning software. Stand by... I'll fire up my vista VM and see if I can give you more details.

---

### Post by I am &gt;= Wes on 2009-01-03
On my old computer with XP I could just double click the iso and it would give me the option of either installing or running ubuntu. Vista says it can't recognize it.

---

### Post by EnGorDiaz on 2009-01-03
> **I am >= Wes said:**
> I recently built a computer with one of my friends, it was quite the experience for both of us.  I have everything working, I'm currently running 64 bit Vista, and I'm happy enough, but it's not Linux.  My friend claims that in order to run the iso to install Ubuntu I need to update the BIOS on my motherboard.  I have an ASUS brand Intel P43 express chipset (P5QL-E) and I am having one hell of a time trying to update the BIOS to do this.  I'm trying to get 64 bit Ubuntu, and I can't even get close. I've tried going to the Intel website and updating the BIOS with the updating program they have, I don't know what else to do.  Any help is greatly appreciated.

--Wes

ur friends a dumb *** i have 2 computers with the exact same motherboard the only thing i could think when using the livecd is you have to change the boot device order in the bios

---

### Post by Ruyuk on 2009-01-03
Freak man, I heard if you mess up your BIOS then your screwed.

---

### Post by EnGorDiaz on 2009-01-03
> **I am >= Wes said:**
> On my old computer with XP I could just double click the iso and it would give me the option of either installing or running ubuntu. Vista says it can't recognize it.

that would be wubi

---

### Post by EnGorDiaz on 2009-01-03
> **Ruyuk said:**
> Freak man, I heard if you mess up your BIOS then your screwed.

he doesnt need to "update" his bios he needs to update the boot device order in the bios


dvd
floppy
harddrive

---

### Post by HotShotDJ on 2009-01-03
> **I am >= Wes said:**
>  Vista says it can't recognize it.Yes, Vista sucks.  Get [ISO Recorder v3]("http://isorecorder.alexfeinman.com/Vista.htm"), burn the ISO to a CD, and boot up from it.

---

### Post by I am &gt;= Wes on 2009-01-03
> **EnGorDiaz said:**
> that would be wubi

It wasn't Wubi, I have no idea how it worked, but I know it wasn't Wubi.

---

### Post by mbzn on 2009-01-03
Reading an iso image in windoze require an virtual cd rom. This will be added with either, 
Virtual cd
Alcohol120%
Nero image drive,
Deamon tools.
There might be more. I'm not sure witch of these are available for vista. Alchol should be easyest as it can burn the iso directly.
On most other progams you'll have to mount the iso to the virtual drive and then do and do a disk copy in nero

Hope this helps

---

### Post by EnGorDiaz on 2009-01-03
> **I am >= Wes said:**
> It wasn't Wubi, I have no idea how it worked, but I know it wasn't Wubi.

inside the iso there is wubi.exe thats it

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by abn91c on 2009-01-03
> **I am >= Wes said:**
> My friend claims that he's had to do it before.  I've tried it without and Vista won't recognize the iso, let alone run it.

if you flash the BIOS the wrong way your computer will turn into a 30 pound paperweight. BIOS flashing is not needed to install ubuntu.
Just make sure you burn the image as an ISO use this program, its a free no limits ISO burner and it takes just two clicks to make a live cd: [http://www.download.com/Active-ISO-B...dlPid=10792184](http://www.download.com/Active-ISO-B...dlPid=10792184)
 when installation starts select"guided use entire disk" option if you are getting rid of windows.

---

### Post by EnGorDiaz on 2009-01-03
> **abn91c said:**
> if you flash the BIOS the wrong way your computer will turn into a 30 pound paperweight. BIOS flashing is not needed to install ubuntu.

or any other operating system

---

### Post by baracuda68 on 2009-01-03
If it is a BIOS issue, goto

[http://support.asus.com/](http://support.asus.com/)

 and search for P5QL-E

and select Linux as the OS.


Hope this helps.

---

### Post by jerome1232 on 2009-01-04
> **abn91c said:**
> if you flash the BIOS the wrong way your computer will turn into a 30 pound paperweight. BIOS flashing is not needed to install ubuntu.
Just make sure you burn the image as an ISO use this program, its a free no limits ISO burner and it takes just two clicks to make a live cd: [http://www.download.com/Active-ISO-B...dlPid=10792184](http://www.download.com/Active-ISO-B...dlPid=10792184)
 when installation starts select"guided use entire disk" option if you are getting rid of windows.

+1, Vista just doen't have any software that knows what an iso is, you just need to burn the image to disc.

Here is another how to on doing that.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)


I think your old xp box just had a program that automatically mounted the iso into a virtual drive. So when you double clicked the iso it was mounted as a cd and then the wubi autorun prompt came up.

---

