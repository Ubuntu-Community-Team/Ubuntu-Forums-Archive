---
title: "Not sure what to do after a command line install"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by SageInBlack on 2010-05-01
Hi all,

I am currently having problem with my 10.04 x64 installation...

First Try of the new desktop install disk, after selecting install Ubuntu and the loading screen, i kept getting a blank screen (despite all the waiting for half hour and such). I have tried all the different display ports available on my graphics card to no avail.

So I downloaded the alternative install disk and installed a command-line only system. The command-line displays just fine, but now I have no idea now what to do afterwards to get a normal Ubuntu install as the final result.

I think the main bit of problem is the graphics card as I tried the disk on another computer, and it works just fine... The graphics card I have is the ATI Raedon 5770. And I am using a 64 bit processer.

Thanks

---

### Post by wojox on 2010-05-01
Just run:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by Gone fishing on 2010-05-01
what happens if you login at the commandline and run startx? 

Sorry my mistake didn't read properly wojox is right

sudo aptitude install ubuntu-desktop

---

### Post by SageInBlack on 2010-05-01
Well... I have done it.... but it is no good, after it goes through the boot (or is it the splash) screen, it just all of a sudden turns blank on the log on screen (I think, I can't see it).... (and has waited for quite a while)

---

### Post by wojox on 2010-05-01
Try this thread out [http://ubuntuforums.org/showpost.php?p=9195971&postcount=14](http://ubuntuforums.org/showpost.php?p=9195971&postcount=14)

---

### Post by SageInBlack on 2010-05-03
Thanks, it completely worked :)

sageinblack

---

