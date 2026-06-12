---
title: "Hard drives spin down?"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by Zenze on 2010-06-28
I have a basic smb/nfs file server running 10.04 on my home network. Everything is working out great but I have one concern...

Does Ubuntu stop spinning/turn off the hard drives after a certain period of inactivity? I am concerned about preserving the life of the drives.

Thanks in advance.

---

### Post by crackpotfox on 2010-06-28
well, i'm a bit new to ubuntu but i'm on a laptop and in power settings, i can tell it to spin down when possible

---

### Post by mikewhatever on 2010-06-28
Does Ubuntu stop or start spinning down the drives? Spinning down the drivers when inactive will both prolong their life time and preserve power. On the other hand, excessive spinning down may shorten the drive's life time.
Just check yours and tell us what's the deal. ;)

---

### Post by crackpotfox on 2010-06-28
i'm not sure, i found it in power management when  was trying the live cd

---

### Post by mikewhatever on 2010-06-28
crackpotfox, the OP runs a server, which means there is likely no GUI (Graphical User Interface) of any kind.

---

### Post by Zenze on 2010-06-28
Yes I am using the server edition with no gui. However, I can install the gui if that is the simplest way set a time for the drives to spin down.

---

### Post by warfacegod on 2010-06-28
I *believe* the one you want is power-management-preferences-settings. See what that gets you in CLI.

---

### Post by mikewhatever on 2010-06-28
Zenze, instead of worrying about the unknown, check how many times the drives are spun down, say, in 24 hours and post the results.
You can do it with **smartmontools**.
```
sudo apt-get install --no-install-recommends smartmontools

```
When done, run the check on, say, /dev/sda
```
sudo smartctl -a /dev/sda
```

---

### Post by crackpotfox on 2010-06-28
oh well, i guess that i should have just let someone with more experience tell him ;)

---

