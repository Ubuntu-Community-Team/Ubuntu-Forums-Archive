---
title: "Playing CD's"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Jasieu on 2009-09-22
Absolute Newby when it comes to Linux of any flavor.  Couple of questions.  Just installed 9.04 on an old Dell Pentium 4.  When I play a CD the disc seems to be working but nothing shows up on the screen to play it.  When I go to the required application it doesn't show the CD that I have inserted.  Another question why can't I turn on visual effects?  Does it need a special video card?  Thanks

Jasiu

---

### Post by wpshooter on 2009-09-22
What "application" are you opening ?

---

### Post by Jasieu on 2009-09-22
Whatever the standard issue is, "Rhythmnbox"?

---

### Post by ghostborg on 2009-09-22
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Go to Mediabuntu to make sure all the necessary codecs are installed.
If you don't see your cd then its not being mounted properly.
Click on Places and it should show up as Audio CD also on your Desktop
unless you turned that off.

As for your video card click on System, Administration, Hardware Drivers.
Check to see if a video driver is available. This should enable the Compiz desktop. Then install the Compiz Setting Manager to tweak effects.

Good Luck.

---

### Post by Flimm on 2009-09-22
I'd recommend you stick with the standard packages in the Ubuntu repositories (rather than medibuntu) and install "Ubuntu restricted extras". Click Applications, Add/Remove, and search for "ubuntu restricted extras". Tick it and click apply changes.
A quicker way of doing the same thing is to type this in a terminal:```
sudo apt-get install ubuntu-restricted-extras
```

---

