---
title: "EEEBuntu Update Help"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by essartee4 on 2010-09-06
So im brand new too Ubuntu and completely lost however messing around is quite fun.

Im used to mac and windows but anyway

I picked up a Asus Eee PC netbook for cheap so i decided to load EEEbuntu Standard on it through the usb drive and its working great "actually posting from the netbook now"

Heres my problemo,  when i go to update to 9.04 i get an error message saying...
"This script detected the following installed services which must be stopped before the upgrade: gdm"

Im lost on what this means?

---

### Post by Insomnia64 on 2010-09-06
gdm is the Gnome Display Manager. I had to do this recently for a nvidia driver install on debian. So there may be better ways to do this that other users will provide but this is what i did.

First drop to a terminal with Ctrl+Alt+F1 and log in

then do:
```
sudo /etc/init.d/gdm stop
```

you can then do:
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
to update your system

Then restart gdm with:
```
sudo /etc/init.d/gdm start
```

Finally Ctrl+Alt+F7 will bring your graphical interface back

---

### Post by essartee4 on 2010-09-06
when i do the command 'sudo apt-get update' i get an error...

"E: dpkg was interrupted, you must manually run "dpkg -- configure -a to correct the problem.

---

### Post by Insomnia64 on 2010-09-06
Have you tried running ```
sudo dpkg --configure -a
```?

If that fails try ```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by ajgreeny on 2010-09-06
So now in the command line run ```
sudo dpkg --configure -a
```then try the update again.

I am not sure quite how well an update will go, however, as the new version of eeebuntu is now called Aurora and is based on debian, not ubuntu.

It may be simpler, and better, to download a new iso and re-install clean with the new version, or perhaps even try ubuntu UNE if you really want a *buntu version.  The 10.04 UNE is absolutely terrific!

---

### Post by essartee4 on 2010-09-06
Im up for a fresh install, whats the best OS to run on my eee netbook?

Link for download?

---

### Post by Sonybuntu on 2010-09-06
> **essartee4 said:**
> Im up for a fresh install, whats the best OS to run on my eee netbook?

Link for download?

Don't have an EEE but try Jolicloud. It has excellent netbook support.

---

### Post by essartee4 on 2010-09-06
I just like the EEEbuntu because all my drivers still work with me having to do nothing. Humm

---

### Post by TCHebb on 2010-09-07
I have an EEE 1005PE, and IIRC, UNE 10.04 worked almost perfectly. I only remember a small backlight glitch which I fixed with instructions from [this]("https://help.ubuntu.com/community/EeePC/Fixes") page, which also has lots of useful info for all EEE models.

---

