---
title: "DVD Ripping/Backup"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Law506 on 2009-04-29
Been sitting here for awhile trying to get one of my dvd's backed up to my hard drive and have no success.  Been reading around and tried numerous programs and have had the most success with k9copy, but when I go to actually convert the DVD it never progresses.  Saw a few posts about not having the right codecs and I believe I have gotten all but libdvdcss2 which I can't seem to install correctly.

Any suggestions on a program?  I am sure this DVD is encrypted and this is why I am having issues.

Thanks. :)

---

### Post by alphacrucis2 on 2009-04-29
> **Law506 said:**
> Been sitting here for awhile trying to get one of my dvd's backed up to my hard drive and have no success.  Been reading around and tried numerous programs and have had the most success with k9copy, but when I go to actually convert the DVD it never progresses.  Saw a few posts about not having the right codecs and I believe I have gotten all but libdvdcss2 which I can't seem to install correctly.

Any suggestions on a program?  I am sure this DVD is encrypted and this is why I am having issues.

Thanks. :)

Have you set up the medibuntu repositories:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Law506 on 2009-04-29
Been trying to but keep getting errors with each attempt.  I will check out your link.  Thanks.


Found another page and followed it, checked out the one you provided in the previous post already, one of the first.  It is installed now.. going to test.

and it didn't work..

---

### Post by Law506 on 2009-04-30
Alright, restarted the system for safe measure and it appears to be working.  Turns out the now there is a problem converting the sound to mp3, anyone know that codec? k9copy didn't give me the required codec needed.  Thanks for the help.

---

### Post by anjilslaire on 2009-04-30
```

sudo apt-get install lame

```

Should give you mp3 playback functionality, which might be the cause if you don't have it already, which seems to be the case.

---

### Post by logos34 on 2009-04-30
make sure you also have the codecs metapackage:

> sudo apt-get install ubuntu-restricted-extras

---

### Post by Law506 on 2009-04-30
I had the restricted drivers installed as well.  Loooked around the list of codecs on k9copy and found mp3 (lame) as an option vice mp3 and this worked.  I am able to rip now!  

Thanks for the help :guitar:

---

