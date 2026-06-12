---
title: "What to do in the command prompt"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by suvid on 2009-11-17
Hi this is the first time ever that I am trying to use any linux system. I had though that I would be able to get to a desktop directly to a desktop like user interface when I installed ubuntu 9.10 using wubi. All I can reach to, is a command prompt, I don't know the appropriate command to get to desktop if any or has my installation process gone all wrong? Help me to run ubuntu for the first time!

---

### Post by BDNiner on 2009-11-17
Your install process has gone wrong. A default install of Ubuntu should bring you to a desktop log in. What are the error messages displayed as ubuntu starts? you can just type the message as displayed.

---

### Post by decoherence on 2009-11-17
> **BDNiner said:**
> Your install process has gone wrong. A default install of Ubuntu should bring you to a desktop log in. What are the error messages displayed as ubuntu starts? you can just type the message as displayed.

Like BDNiner said, you certainly should be getting a desktop rather than a command line.

I would try just re-running the install first. If it still doesn't work... well, I know nothing about Wubi. My suggestion would be to test Ubuntu with you hardware using a LiveCD. This Wubi thing could be a video driver problem, but again I know nothing about Wubi. What kind of grpahics card do you have? ATI, nVidia or Intel? (don't need specific model)

Sorry about the lousy first impression but don't give up!

---

### Post by suvid on 2009-11-17
I have ATI video card installed, when I first ran the install process it showed me a desktop, but later when it rebooted the system after install I selected to load ubuntu and when I did that the screen went to a command prompt which had grub 1.97 beta on top and it showed me a command window which had something like sh:grub> and I was supposed to write commands which I know nothing about. There was no error message, it just went to a command prompt

---

### Post by decoherence on 2009-11-18
> **suvid said:**
> I have ATI video card installed, when I first ran the install process it showed me a desktop, but later when it rebooted the system after install I selected to load ubuntu and when I did that the screen went to a command prompt which had grub 1.97 beta on top and it showed me a command window which had something like sh:grub> and I was supposed to write commands which I know nothing about. There was no error message, it just went to a command prompt

If it's bailing out on GRUB it means it can't even start loading Linux. Did you use any special settings when you installed Wubi? (I haven't done it myself so I don't know what special settings there might be.) If not, just wipe it out (I think you use Add Remove Programs control panel) and try again. Before you do, check the md5 sum on the file you downloaded to make sure it didn't get corrupted during the download... 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

That has the hashes themselves (you want the one for Wubi.exe) and there is a link on that page called HowToMD5SUM that will explain the process of checking them.

Getting shot down so early in the boot process leads me to think something went terribly wrong during the Wubi install. That or it's time for another GRUB2 slapfest...

Good luck, and let us know how it goes.

---

