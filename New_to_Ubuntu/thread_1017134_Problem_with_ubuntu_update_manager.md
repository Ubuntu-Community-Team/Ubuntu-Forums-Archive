---
title: "Problem with ubuntu update manager"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by itsvan on 2008-12-20
Hello everyone,,here is my problem,,,i was doing a normal update to ubuntu through the update manager,,the internet cutoff as it was updating and it froze,it created some error,,now my Mozilla and my pidgin do not respond when i want to open them,,nothing comes up,,that's what ive noticed that doesn't work,,i remember some of the files that was updating was indeed Mozilla,,so maybe it messed up some files?? now when i try to update it this message comes up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
E: _cache->open() failed, please report. 
 


Please help thank you for your time!!!!!!:confused:

---

### Post by adobrakic on 2008-12-20
Have you tried doing what it says?

---

### Post by StevenHarper on 2008-12-20
Hmmm now let me answer that more helpfully:

Open a terminal

Click on the Ubuntu menu 

Choose Accessories

Choose Terminal

Now in that new black window enter

```
sudo dpkg --configure -a
```

this will prompt you for your password (as your running dpkg as a super user)

It will fix the problem

Steve

---

### Post by itsvan on 2008-12-21
HI there,,it worked fine,,but now apparently something with my video card has been restarted and i cant seem to fix it,,the resolution has gone way down,,and the special effects dont work anymore...this happend when i restarted the computer,,then a screen said it coudnt detect my graphics card or soemthing,,and it gave options,,so i choose the best one and it semi did something,,but its not how it used to be ,,what can i do???

---

