---
title: "Need help, login won't process, command prompt works, help me remove 3d driver"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-03-15
ok i can't get my desktop to load. it just stops which tells me that the driver is to blame the live cd works. So i need a way to remove the 3d driver w/o logging into the ubuntu os. is there anywya to do this?

---

### Post by taurus on 2009-03-15
Well, if you would tell us which graphic card do you have, then you can remove the driver (if you even installed it) from a prompt with apt-get/aptitude.

Did you install a driver for your graphic card?

---

### Post by carml on 2009-03-15
Can you explain better your problem? I didn't understand so well:confused:

---

### Post by 133794m3r on 2009-03-15
ok i have the Ati Radeon xpress 200m i believe. i installed the 3d one from the ati on linux guide used that guide. Made an install for some reason wine didn't work for me it'd get a 3d errors. So i reinstalled the driver. Now it won't evne load the desktop i installed the 9.2 catalyst. I need a way to remove this from the shell prompt @.@

---

### Post by taurus on 2009-03-15
What happens when you run these two commands?

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by carml on 2009-03-15
Ok,did you installed it via System->Administation->Hardware Drivers?

---

### Post by 133794m3r on 2009-03-15
> **carml said:**
> Ok,did you installed it via System->Administation->Hardware Drivers?
No i installed it via [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")
> **taurus said:**
> What happens when you run these two commands?

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```
well as i said i can't even get to my desktop it starts to load then does random things and ends up with a blank screen.
So i could start with the shell and go from there but i'm on the livecd right now as that won't work.

---

### Post by taurus on 2009-03-15
At the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Log in with your username and password.  Then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, press <Alt>F7 to get back to the GUI login screen.  Then restart the X server again with <Ctrl><Alt>Backspace (or reboot).  Log back in and see what happens.

---

### Post by 133794m3r on 2009-03-15
well i have autologon started so should i do the recovery kernel then do that? also offtopic but is it possible to update ubuntu 8.1 to xubuntu like how ubuntu can go to kubuntu? b/c apparently xubuntu is for weaker systems and my system's not exactly that great.

Also it says i can do this and keep my install? does this include all of my core files right like home etc. etc.?

---

### Post by carml on 2009-03-15
The transition from Ubuntu to Xubuntu consist in a change of desktop environment,and yes it's possible,but you need to solve your problem before to switch to Xubuntu. :)

---

### Post by 133794m3r on 2009-03-15
ok well here goes teh test @.@ goign to restart w/o live cd and hope to hell this works

---

### Post by 133794m3r on 2009-03-15
just felt like posting here instead of editing so it could be bumped. Didn't work it's still messed up and won't install for some odd reason. :/ apparently no one is able to help me i'll wait another hour if i don't find any help i'll just reinstall the entire os after backing up my important data.

---

### Post by carml on 2009-03-15
Did you tried the recovery option,the one from the boot?

---

### Post by 133794m3r on 2009-03-15
> **carml said:**
> Did you tried the recovery option,the one from the boot?

the recovery kernel? the second one down that says (recovery) i've alreayd tried click clean xorg file. System test and no help  i'll retry the recovery one once more there are 2 i'm going to be using the more recent kernel then the later kernel

---

### Post by carml on 2009-03-15
Yes, I mean the one with the word recovery.

---

### Post by 133794m3r on 2009-03-15
yes i've tried that one, i've also tried the package repair option, and to no avail. Just retried and it'll load the desktop for 8.04 for some reason then jumble it up and freeze.

---

