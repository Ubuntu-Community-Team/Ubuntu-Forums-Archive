---
title: "Blank screen"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by savafan on 2010-02-27
I finally got Ubuntu 9.10 working on this new 64bit system but I had a few bugs to work out with the video card. For some reason my videos had a blueish tint to them. I tried the VLC player & had the same effect. I looked at re-installing the drivers for my nvidia card & upon restart, I have a blank screen. I know that the system is there, I just cannot see it.

Last time this happened there was something not set correctly in my Bios menu, but I have no idea what that was. I had someone else fix that for me. Not sure if it is the same problem this time.

Any advice before I have to call in the techs again?

---

### Post by MooPi on 2010-02-27
Is the tint only the video window or the entire screen ?

---

### Post by savafan on 2010-02-27
Videos only. Everything else seemed fine at the time

---

### Post by joshd2189 on 2010-02-28
restart into recovery mode and then run this command:
```
sudo dpkg-reconfigure xorg.conf
```

that should get your graphics back.

for your blue people problem (what you don't like avatar?)- ive had it before and i remember it was just changing a setting in the movie player.  Edit->Preferences->Display or something

look here though [https://answers.launchpad.net/ubuntu/+source/totem/+question/7373]("https://answers.launchpad.net/ubuntu/+source/totem/+question/7373")

---

### Post by savafan on 2010-02-28
Thank you for the help. Unfortunately, I ran that code & the message I received was "xorg.conf is not installed"

I have Ubuntu loaded on my old system is 32bit format. When I got my new 64bit system, things did not go as smoothly as it did on the old system. I did receive a few errors along the way. All seemed ok for the first day with the exception of Flash issues & getting my two screens to work properly.

Would it be advisable to try to reload the disc & start over? Also, should I consider loading the 32bit version on this new computer. I have both discs but would very much like to see the 64bit performance & do not know if the 32 would run properly either.

---

