---
title: "Will not boot after making directories in /usr"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by kidwai on 2011-07-20
Hello,

I made several folders in /usr for a site I had to upload something for. After that I did ```
sudo chmod 644 /usr
``` because the site couldn't read it. I went away for a few minutes and when I came back, it had locked the screen and the password pop up wouldn't come up, no matter whether I touched the touchpad or pressed keys.

I shut it down (by pressing the power key until it shut down) and rebooted it. After it was reboot, it gave me an error saying that the display, input device and graphics could not be read correctly. I tried to continue with a normal resume but the screen just flickered and the same pop up  came again and again. Even after going into command line, it would not boot and X isn't recognized. I can't go root or delete the files.

Is there anything that I could go to get it working.

It is a LG X200 netbook, 32 Bit Ubuntu 10.04. It worked for a year before it suddenly started doing this. I'm scared that I messed it up :(

Help would really be appreciated

---

### Post by smurphy_it on 2011-07-20
Looks like you removed all of the Execute bits.

my /usr is 0755

---

### Post by kidwai on 2011-07-20
i only did it for the site. but now I can't get it back?

---

### Post by mokrates on 2011-07-20
2 options:

option 1:
since your box doesn't boot, try, in grub, to select the 'single', 'failsafe' or 'recover' option (don't know what it's called, but it's all the same, it boots into single user mode or 'runlevel 1')

you will be asked for your password and then get a text-console. on that you can
```
chmod +x /usr
``` to re-add the executable-flags on /usr which are needed.
then: reboot

option 2:
boot a live-cd, mount the drive with /usr on it, and change the permissions from there.

---

### Post by kidwai on 2011-07-20
AWESOME.

IT WORKS! Though I had to go to root :P

---

### Post by mokrates on 2011-07-20
'course it does ;)

---

