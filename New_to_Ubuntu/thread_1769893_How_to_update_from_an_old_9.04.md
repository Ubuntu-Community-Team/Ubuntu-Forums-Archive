---
title: "How to update from an old 9.04"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by CmdGabriel on 2011-05-28
Hi All,
after having some trouble with Ubuntu update a longer while ago, I thought: don't change a running system.
So i am still stuck with 9.04.

The current update seems not longer possible to the acual version. What can I do, if I like to update now?

Regards+Thanks
Gabriel

---

### Post by uRock on 2011-05-28
Burn an ubuntu 10.04LTS disk, create backups of data, then do a clean install. After that you need not worry about upgrading until April 2013.

---

### Post by CmdGabriel on 2011-05-28
> **uRock said:**
> Burn an ubuntu 10.04LTS disk, create backups of data, then do a clean install. After that you need not worry about upgrading until April 2013.

Ok, thats a way. I but since I am never sure, if I get all my data... is there another way. 
I just found this thread:
[http://ubuntuforums.org/showthread.php?t=1295340](http://ubuntuforums.org/showthread.php?t=1295340)

it suggests:
sudo reboot
sudo dpkg --configure -a
sudo apt-get dist-upgrade
would this work out?

---

### Post by uRock on 2011-05-28
If you've already started an upgrade and it broke, then I definitely recommend a clean install.

---

### Post by cogier on 2011-05-28
uRock is right. That is the easiest way. You could upgrade your way through all the later versions but that would take forever and a new install is a much better idea.

---

### Post by AlphaLexman on 2011-05-28
I have a computer that started out with ubuntu 7.10 and has been upgraded version by version to 10.04 with **no** problems. Of course each upgrade was six months apart, but if you have a lot of software additions, sometimes the task of re-installing all of your favorite software that doesn't come installed by default can be just as time consuming as going through multiple upgrades.

---

### Post by snowpine on 2011-05-28
see here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

At the end of the day, you may find a fresh reinstall is the quicker and more reliable option.

---

