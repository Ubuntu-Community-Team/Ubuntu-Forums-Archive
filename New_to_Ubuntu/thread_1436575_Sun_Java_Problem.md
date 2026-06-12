---
title: "Sun Java Problem"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by tversteeg on 2010-03-22
HI im new to ubuntu and i keep getting this error message for sun java.
 
Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first. 
please put it simply im new to ubuntu.

---

### Post by mrboojive on 2010-03-22
The problem is that you have multiple installation programs open at once. For example, maybe you have Synaptic open and apt running in a terminal. Just try closing everything except the program you are using to install Java.

---

### Post by tom.swartz07 on 2010-03-22
> **tversteeg said:**
> HI im new to ubuntu and i keep getting this error message for sun java.
 
Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first. 
please put it simply im new to ubuntu.

Follow the link in my signature to get the most up to date version of java. It involves a little bit of copy and paste, but youll be set for good after that.

---

### Post by tom.swartz07 on 2010-03-22
> **tversteeg said:**
> HI im new to ubuntu and i keep getting this error message for sun java.
 
Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first. 
please put it simply im new to ubuntu.
Post above got it right.

Follow the link in my signature to get the most up to date version of java. It involves a little bit of copy and paste, but youll be set for good after that.

---

### Post by mrboojive on 2010-03-22
> **tom.swartz07 said:**
> youll be set for good after that.

For good... or until the next version of Java comes out. ;) It might be better for a newbie to just install from the repos.

---

### Post by tom.swartz07 on 2010-03-23
> **mrboojive said:**
> For good... or until the next version of Java comes out. ;) It might be better for a newbie to just install from the repos.

Nope, my method outline in my sig sets the update alternatives so that Java is automatically updated through the Update manager when a new version is rolled out.


Just make sure that you follow all the way to the bottom of the page, and dont skip anything.

---

### Post by mrboojive on 2010-03-23
Doesn't update-alternatives just tell the system where to find Sun's Java once it's installed? It seems like you would still have to go back to Sun's website and download a new .bin when a new update comes out.

---

### Post by tom.swartz07 on 2010-03-23
> **mrboojive said:**
> Doesn't update-alternatives just tell the system where to find Sun's Java once it's installed? It seems like you would still have to go back to Sun's website and download a new .bin when a new update comes out.

You are correct. If I remember correctly, though, the .bin file adds the PPA automatically when it is unpacking. 

I havent gone through this in a few months, so Im a bit rusty as to the time that it happens, but I do know that it is added to updates. 


Even at that rate, Java isn't updated at that great of a schedule. I think its only been updated 7 times since 2006.

---

