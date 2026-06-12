---
title: "problem after installing KDE in Ubuntu"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-02-01
I installed KDE in Ubuntu 8.04. After restarting my computer, no graphic environment was loaded. Please, help!

---

### Post by ivanvajar on 2009-02-01
Maybe I should mention that Splash Screen was disabled when system is restarted. Everything was normal when I logged out and back in to KDE or Gnome. But, after restarting, system reported that KDE is not default environment. It just leaves my screen blank, as no system is loaded.

---

### Post by seshomaru samma on 2009-02-01
how did you install kde?

---

### Post by ivanvajar on 2009-02-01
I added repo: deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

and then followed some link saying apt://kubuntu-kde4-desktop/

---

### Post by Ymer on 2009-02-01
I guess with blank screen you meant having the terminal login instead of the graphical login, right?

If this is the case, at the terminal login, login with your username and password. Then enter the following command

```
sudo dpkg-reconfigure kdm
```

Answer any questions it asks and it should be fine.

---

### Post by ivanvajar on 2009-02-03
No, monitor was absolutely inactive. I've solved this problem by running repair of X server from boot menu options. So, if you experience something like this, press 'e' in boot menu and then find repair X server option. I can't remember exactly how it goes at this time.

---

### Post by tomtom1982 on 2009-02-03
Well, I had have an analog problem because gnome was using gdm and kde tried to start kdm. But it didn't worked. So I had to remove kdm and had to run kde with gdm, because I want to have gnome AND kde.

---

