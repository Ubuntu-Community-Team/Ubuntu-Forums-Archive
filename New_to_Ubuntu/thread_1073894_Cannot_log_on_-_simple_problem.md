---
title: "Cannot log on - simple problem?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by KosmicheCam on 2009-02-18
Hello. I am running Intrepid 8.10 but at the moment cannot get passed the logon screen. The logon screen appears as usual, and I enter the username and password. A black terminal screen appears briefly (too brief to be read fully) before we return to the logon screen. It just does the same thing over and over.

The terminal text does not seem to be listing errors at all. It talks about starting up the display settings. Anyway, I can't think of anything I changed during my last session that could have caused this. If there is a test I can run to help diagnose the problem, I'd be happy to do it.

Thanks everybody.

---

### Post by rickycodie on 2009-02-18
just a guess, cause there really is not alot to go off of, but try this

in the failsafe terminal(if you can get there) enter

sudo dpkg-reconfigure xserver-xorg

it might help and it might not.

---

### Post by taurus on 2009-02-18
So the system just "dumps" you back to GUI login screen after you have entered your username and password?  One thing to check is your disk space to make sure you haven't maxed out the root filesystem--/.

```
df -h
```

---

### Post by listerdl on 2009-02-18
This is really crap advice compared to the above, but have you tried to re-install?

---

### Post by KosmicheCam on 2009-02-18
> **taurus said:**
> So the system just "dumps" you back to GUI login screen after you have entered your username and password?  One thing to check is your disk space to make sure you haven't maxed out the root filesystem--/.

```
df -h
```

Thank you for the helpful advice so far. Unfortunately, I'm not able to enter even the failsafe terminal. Yes, I am just 'dumped' back at GUI login screen!

I haven't tried reinstalling, and of course I'd rather not if I can avoid it...

Any other ideas?

---

### Post by taurus on 2009-02-18
> **KosmicheCam said:**
> Thank you for the helpful advice so far. Unfortunately, I'm not able to enter even the failsafe terminal. Yes, I am just 'dumped' back at GUI login screen!

I haven't tried reinstalling, and of course I'd rather not if I can avoid it...

Any other ideas?

At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then check your disk usage.

```
df -h
```

---

### Post by DarthOpto on 2009-02-18
During boot up hit ESC when you get the options to come up choose one of the recovery options. This will bring up an area where you can try fixing X. 
Also in that window you can go to the console and get the memory information. I had this happen to me once and the problem was that I had too much hard drive dedicated to the swap partition or something like that. It has been awhile. But at least in the recovery mode you can get the information that the others have been asking for.

---

### Post by KosmicheCam on 2009-02-19
> **taurus said:**
> At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then check your disk usage.

```
df -h
```

Thanks taurus. When I tried this I came to a CUI login screen. I tried the username and password, only to get the following ('Hernando' is the name of the computer):

```
Ubuntu 8.10 Hernando tty2
```

After this it asks me to login again, and it keeps repeating... I _was_ able to check the memory usage though (read below).

> **DarthOpto said:**
> During boot up hit ESC when you get the options to come up choose one of the recovery options. This will bring up an area where you can try fixing X. 
Also in that window you can go to the console and get the memory information. I had this happen to me once and the problem was that I had too much hard drive dedicated to the swap partition or something like that. It has been awhile. But at least in the recovery mode you can get the information that the others have been asking for.

DarthOpto. The recovery mode looked hopeful. It allowed me to check the memory usage. There was 3.7GB remaining on the smaller partition, which I think might be root. The larger 160GB partition was only half full as well (I think must have been 'home').

I also tried fixing X, but it didn't allow me to proceed very far with that. It flashes a warning, something about overwriting a possibly customised file backed up in a particular location. Then it brings me back to the recovery menu.

Thanks again for the help both of you! I hope this gives you some clues.

---

### Post by KosmicheCam on 2009-02-21
Has anybody else got an opinion on my problem? If I can't get on, I may need to consider re-installing Ubuntu. In that case I wonder whether applications will remain on my home partition with settings intact? Whatever suggestions you can offer, I'd appreciate it...

---

