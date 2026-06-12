---
title: "System down -- Desktop won't load"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Baasha on 2009-07-17
Running Ubuntu Hardy Heron

Symptoms:  When booting into Ubuntu  it loads the login screen, I can sign in and then the desktop only partially loads.  I get the desktop wallpaper, but no panels and no icons.  Right-clicking on the desktop has no effect.

What I have tried:
1. Boot into recovery mode and select fix x; no change.
2. Go to terminal via recovery mode and run sudo apt-get install ubuntu-desktop; it tells me I already have the latest.
3. dpkg-reconfigure x-server-xorg ; and then startx; no change.
4. run gnome-panel; it tells me it can not open display.
5. run gconf-editor; it tells me it can not open display.
6. run cd ~ && rm -r .gconf/ .gconfd/ .gnome2/  and then reboot.

None of these things has worked.  I am stuck.  I need to access my files.  I am being forced under duress to use a windows system to post here.  That is truly an unpleasant experience.  Can anyone give me a clue as to what I can do to solve this problem?  Thanks.

---

### Post by LowSky on 2009-07-17
sudo apt-get reinstall ubuntu-desktop

---

### Post by Baasha on 2009-07-17
reinstall comes back as an invalid command on my system.  Any other ideas?

---

### Post by Superkoop on 2009-07-17
Apt-get doesn't do reinstall, you have to use Aptitude.

So...```
sudo aptitude reinstall ubuntu-desktop 
```

---

### Post by Baasha on 2009-07-17
Thanks Superkoop.  sudo aptitude worked but I still have the same symptoms:  desktop wallpaper but no panels or icons.

---

### Post by SirBismuth on 2009-07-18
This is weird, I had the same systems when I booted up my system today.  This was after adding the X Org PPAs (not the bleeding edge ones), but I just restarted X, then all was well.  

Will see what happens when I restart after a soft boot or shutdown again, will be annoying IF it keeps happening.

Will also make a note of the option to reinstall the desktop, if it does reoccur.

B

---

