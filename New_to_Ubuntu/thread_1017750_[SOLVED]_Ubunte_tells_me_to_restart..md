---
title: "[SOLVED] Ubunte tells me to restart."
date: 2008-12-21
forum: New to Ubuntu
---

### Post by jorge ortega on 2008-12-21
After having had a very messy day with Ubuntu 8.4 the computer is telling me all the time to restart the system for the new updates to take place or something like that; I've restarted it many times and keeps happening.
I can't even think what to try. Help please

---

### Post by anjilslaire on 2008-12-21
To make sure everything is updated correctly, open a terminal and do 
```

sudo apt-get update
sudo apt get upgrade

```

And reboot one more time.

---

### Post by jorge ortega on 2008-12-21
If I did that...am I not upgrading to Intrepid?

---

### Post by zvacet on 2008-12-21
No,you will not.For upgrade to next release you need to run 

```
sudo apt-get dist-upgrade
```

**sudo apt-get update** sync your source list with repositories.
```
sudo apt-get upgrade
``` upgrade packages in your existing release

---

### Post by shredder12 on 2008-12-21
well if you want to upgrade to intrepid you can refer the following article..
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by jorge ortega on 2008-12-21
I've just done as recommended with no result? What else could I try?

---

### Post by handydan918 on 2008-12-21
Try booting using the second entry on your grub boot menu. This should be the previous kernel, and may allow you to boot if the newest kernel is fubar.

---

### Post by anjilslaire on 2008-12-21
> **jorge ortega said:**
> I've just done as recommended with no result? What else could I try?

Please clarify "No result"
WHat is th status of th system? Is it still prompting you to reboot? If Yes, does it give any indication as to why it wants to reboot? Wat does the reboot prompt say, exactly?

---

### Post by jorge ortega on 2008-12-21
After several kernel updates I've got 3. As recomende (I think) I chose to boot with the oldest and seemed to work. Then I rebooted again normaly and -cross fingers- it is fine

Thanks so much to everyone

---

