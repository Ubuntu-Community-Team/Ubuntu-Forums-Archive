---
title: "libc6 error"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by justin23 on 2009-04-08
I'm trying to get a windows driver to work with my dell 1390 wireless card.  I successfully installed ndiswrapper but i get an error message when i try to install the utility.  It says dependency not satisfiable: libc6.  Please Help!!!

---

### Post by Kareeser on 2009-04-08
sudo apt-get install libc6

---

### Post by justin23 on 2009-04-08
i'm not connected to the net.

---

### Post by NESFreak on 2009-04-08
> **justin23 said:**
> I'm trying to get a windows driver to work with my dell 1390 wireless card.  I successfully installed ndiswrapper but i get an error message when i try to install the utility.  It says dependency not satisfiable: libc6.  Please Help!!!

did you try this?

> **fire7882 said:**
> Good How to but I was able to make the wireless work on my dell e1405 with Broadcom 1390 WLAN by following these steps

Installed ubuntu 8.10
Ran update manager   (System/Administration/Update Manager)
Restarted computer
Went to Hardware Drivers  (System/Administration/Hardware Drivers)
Activated Broadcom B43 wireless driver
Restarted computer

Everything works great now.  I'm a first time linux user and loving it so far.

EDIT:  BTW, This method requires you to be plugged into a network cable.  Once everything gets installed, your good to go.

---

### Post by NESFreak on 2009-04-08
> **justin23 said:**
> i'm not connected to the net.

try finding a lan cable. borrow it somewhere, or pull it out of a random computer. I'm guessing you're using a laptop so it shouldn't be to hard to move it. Once it works. You can safely remove the cable again hoping you'll never need it again

---

### Post by justin23 on 2009-04-08
I'll try that.  Thanks!

---

### Post by justin23 on 2009-04-08
connected to the internet and now i'm getting a message telling me that the computer couldn't download all repository indexes.  And i'm still getting the same error message about libc6.  Any suggestions?  Whats a repository?

---

### Post by NESFreak on 2009-04-08
> **justin23 said:**
> connected to the internet and now i'm getting a message telling me that the computer couldn't download all repository indexes.  And i'm still getting the same error message about libc6.  Any suggestions?  Whats a repository?

As for the not downloading all the indexes, try selecting another mirror. Most of it is explained here: [https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html](https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html)

As for your libc6 problem it came to mind that these drivers require the 32bit version of libc6. Are you running the 64bit version of ubuntu?

---

### Post by justin23 on 2009-04-08
i am running 32 bit.  not 64 and the link to the help topic wasn't good.

---

### Post by justin23 on 2009-04-08
i was a little unclear about the help topic.  the link didn't work.

---

### Post by mc4man on 2009-04-08
You should really post the error message about libc6 noting that it's currently installed and pretty central to the operation of your ubuntu install (in other words you don't want to mess around with it.

If it's libc6-dev that the error is about the try going to System -> Administration -> Software sources and under 'ubuntu software' make sure first 4 lines are checked and under 'updates' tab the first 2 lines. Then click 'close' and 'reload'

---

### Post by justin23 on 2009-04-09
Just wanted to let everyone know that the issue has been resolved. I installed ubuntu 8.1 on my system and all is well.  I managed to get everything to work.  Thanks everyone for the support!!

---

