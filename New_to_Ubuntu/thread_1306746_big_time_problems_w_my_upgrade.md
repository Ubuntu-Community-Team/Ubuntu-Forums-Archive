---
title: "big time problems w/ my upgrade"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by gwilkins82 on 2009-10-30
ok...no idea what is going on.  upgraded this morning, and it had some errors (i didnt pay too much attention to them {i know, i know}) and it seemed to only to a partial upgrade.  the computer didnt even restart once finished.  i initally wasnt too concerned, things seemed to be working.  then i realized there was no sound.  now it appears that the cd drive is not being read.  at this point, i have even tried using my 9.04 live cd (i cannot make a new 9.10 one since it wont read the drive) and just start over (all my files are backed up on an exteral) but the drive does not get read, and it just boots into my quasi-9.10...help!  any idea?  much obliged.  i also tried to make a 9.10 usb start up, but that got bypassed as well...

i know there are several upgrade threads, but didnt see anything that related directly, so started a new one

---

### Post by akelsall on 2009-10-30
Have you thought about just going through the entire upgrade process again, since it sounds like it never fully installed the upgrade? That might be a good starting point.

Andy

---

### Post by kansasnoob on 2009-10-30
> **gwilkins82 said:**
> ok...no idea what is going on.  upgraded this morning, and it had some errors (i didnt pay too much attention to them {i know, i know}) and it seemed to only to a partial upgrade.  the computer didnt even restart once finished.  i initally wasnt too concerned, things seemed to be working.  then i realized there was no sound.  now it appears that the cd drive is not being read.  at this point, i have even tried using my 9.04 live cd (i cannot make a new 9.10 one since it wont read the drive) and just start over (all my files are backed up on an exteral) but the drive does not get read, and it just boots into my quasi-9.10...help!  any idea?  much obliged.  i also tried to make a 9.10 usb start up, but that got bypassed as well...

i know there are several upgrade threads, but didnt see anything that related directly, so started a new one

If your system fails to boot the live CD on reboot that sounds like a BIOS thing. BIOS must try to boot the cd drive before booting the hard drive.

---

### Post by kansasnoob on 2009-10-30
Have you tried in terminal:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

To see what might need to be installed. Maybe even try:

```
sudo apt-get -f install
```

If you get to a point where it won't boot but you can get the Live CD to boot I wrote briefly here how to mount and chroot from the Live CD:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Of course caution must be used!

I'll be out for a bit, back in about an hour.

---

### Post by gwilkins82 on 2009-10-30
> **akelsall said:**
> Have you thought about just going through the entire upgrade process again, since it sounds like it never fully installed the upgrade? That might be a good starting point.

Andy


well, it seems to be running an incomplete version of 9.10, so i cannot upgrade.

---

### Post by gwilkins82 on 2009-10-30
> **kansasnoob said:**
> If your system fails to boot the live CD on reboot that sounds like a BIOS thing. BIOS must try to boot the cd drive before booting the hard drive.

if it is a BIOS thing, what do i do?

---

### Post by kansasnoob on 2009-10-30
> **gwilkins82 said:**
> if it is a BIOS thing, what do i do?

Well, you can look here:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

But first, is Ubuntu still running at all?

If so did you try those two commands?

If so what did it say?

Just FYI the Ubuntu servers must be just getting hammered. I was doing some testing last night and had to install the repo version of Seamonkey in a Hardy live session and it took 15 minutes!

If you need more detailed help with BIOS please tell us what you know about your machine, particularly the motherboard, or if it's an OEM mobo the actual make and model of the puter and we'll try to help.

---

### Post by gwilkins82 on 2009-10-30
> **kansasnoob said:**
> Well, you can look here:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

But first, is Ubuntu still running at all?

If so did you try those two commands?

If so what did it say?

Just FYI the Ubuntu servers must be just getting hammered. I was doing some testing last night and had to install the repo version of Seamonkey in a Hardy live session and it took 15 minutes!

If you need more detailed help with BIOS please tell us what you know about your machine, particularly the motherboard, or if it's an OEM mobo the actual make and model of the puter and we'll try to help.

ok, somethings have now changed, but i dont know what exactly.  i altered the bios settings so that the usb flashdrive would get accessed (it has the 9.10 iso on it) first.  the computer upon starting up sits at the load screen for a long time - it just says gateway/intel on it, with the option to go into the bios settings or setup.  

after a while, it beeps and gives me an ERROR 0200: Failed Fixed Disc and I can hit F1 to continue and F2 to setup.  This will then read the usb flash and load 9.10.  I ran an install from there, and it said that it went fine and the computer needed to restart to finalize.  

with a restart, nothing changes, and if the usb is not in place, nothing will load.  hitting F1 will simply bring a blank screen w/ a blinking cursor (no prompt).  i have gone through the install process twice now.  the second time, it recognized that ubuntu was installed and i had the option to install over it or along side it.  i chose over, but with the same results.

in a tight spot here.  no idea what i have done.  if anyone can help, many thanks.

---

### Post by gwilkins82 on 2009-10-30
ok, not sure how i did it, but another usb reinstall of 9.10 finally got the job done.  whew.  stressful afternoon on the computer.  thanks for all the suggestions!

---

### Post by kansasnoob on 2009-10-30
Awesome! Success is success.

Have a happy buntu experience:D

---

