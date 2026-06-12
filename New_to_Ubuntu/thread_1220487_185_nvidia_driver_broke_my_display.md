---
title: "185 nvidia driver broke my display"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-07-22
my update manager came on yesterday and said nvidia driver 185 is ready.  so i didn't think much of it and installed.  well now i can't get my gui back at all.  i think the driver came from the xbmc repo?  

i had to reinstall my xserver.org but still can't get my gui back.

any steps i can try to get back to default so i can enable the driver again?

---

### Post by ~sHyLoCk~ on 2009-07-22
> **northwestuntu said:**
> my update manager came on yesterday and said nvidia driver 185 is ready.  so i didn't think much of it and installed.  well now i can't get my gui back at all.  i think the driver came from the xbmc repo?  

i had to reinstall my xserver.org but still can't get my gui back.

any steps i can try to get back to default so i can enable the driver again?

Maybe try ```
sudo depmod -a
```

---

### Post by fooman on 2009-07-22
try rebooting and at the grub screen,  choose recovery mode.  when it gets to the menu,  choose the "x fix" option.

then continue with normal boot and see if you get back to the desktop.

---

### Post by northwestuntu on 2009-07-22
i'll go give them a shot.

thanks

---

### Post by northwestuntu on 2009-07-23
> **fooman said:**
> try rebooting and at the grub screen,  choose recovery mode.  when it gets to the menu,  choose the "x fix" option.

then continue with normal boot and see if you get back to the desktop.

tried xfix and after it's done and i reboot just hangs at battery check.  ive never had a problem like this before.  use to just do the reconfigure xserver and it would fix it no problem.

---

### Post by flyingsliverfin on 2009-07-23
i had a similar problem once and i ended up just bootng into recovery, then cping the needed files onto my external hdd and reinstalled
sorry, thats just what it might come to

---

### Post by northwestuntu on 2009-07-23
> **flyingsliverfin said:**
> i had a similar problem once and i ended up just bootng into recovery, then cping the needed files onto my external hdd and reinstalled
sorry, thats just what it might come to


i would hate to do that.  anything else i can try 1st?

---

### Post by XCan on 2009-07-23
Can't you trash your xorg.conf so that Ubuntu uses whatever default driver it comes with, and then install your previous driver?

Come to think of it, is 185 really from Canonical's team? Sounds like you got it from a third party repository.

---

### Post by northwestuntu on 2009-07-23
> **XCan said:**
> Can't you trash your xorg.conf so that Ubuntu uses whatever default driver it comes with, and then install your previous driver?

Come to think of it, is 185 really from Canonical's team? Sounds like you got it from a third party repository.

im not sure if you can get rid of xorg? yes the driver came from xbmc repo. 

i wish i never installed it :(

---

### Post by tad1073 on 2009-07-23
give this a go. 
boot into recovery mode and follow those instructions.
[http://ubuntuforums.org/showpost.php?p=7603796&postcount=8](http://ubuntuforums.org/showpost.php?p=7603796&postcount=8)

once you have edited the line, ctrl+x to save, y to accept and hit enter to exit nano

---

### Post by wojox on 2009-07-23
What happens when you go to System > Administration > Hardware Drivers?
Can you turn the old driver back on?

---

### Post by tad1073 on 2009-07-23
he has no display, no gui, so, your suggestion isn't feasible.

---

### Post by gradinaruvasile on 2009-07-23
Did u try the root command line option from the recovery menu?
If u can get to that, u can reconfigure X, or just delete xorg.conf. Best would be uninstalling the nvidia packages with apt-get too.

---

### Post by northwestuntu on 2009-07-23
> **tad1073 said:**
> give this a go. 
boot into recovery mode and follow those instructions.
[http://ubuntuforums.org/showpost.php?p=7603796&postcount=8](http://ubuntuforums.org/showpost.php?p=7603796&postcount=8)

once you have edited the line, ctrl+x to save, y to accept and hit enter to exit nano

all the info was generic. no mention of nvidia or my tv display.  it was pretty much blank?

---

### Post by northwestuntu on 2009-07-23
> **gradinaruvasile said:**
> Did u try the root command line option from the recovery menu?
If u can get to that, u can reconfigure X, or just delete xorg.conf. Best would be uninstalling the nvidia packages with apt-get too.

i tried xfix.  you can delete xorg?

---

### Post by gradinaruvasile on 2009-07-23
If u mean xorg.conf, yes u can. But that way u will have the opensource driver working. U should create a new, default xorg.conf with 

```
dpkg-reconfigure -phigh xserver-xorg
```

if u plan on installing the restricted driver.

---

### Post by northwestuntu on 2009-07-23
> **gradinaruvasile said:**
> If u mean xorg.conf, yes u can. But that way u will have the opensource driver working. U should create a new, default xorg.conf with 

```
dpkg-reconfigure -phigh xserver-xorg
```

if u plan on installing the restricted driver.

did that and still nothing.  it stops at "checking battery state" every time.  i have never had this sort of problem with the video before.  i was always able to bring the gui back up.  this doesn't make any sense at all?

---

### Post by Dougie187 on 2009-07-23
why don't you just try removing the package?

---

### Post by northwestuntu on 2009-07-23
fixed!!! :)

i ended up installing envyng from the console.  had it install the nvidia driver and did a restart and my gui is back.  

thanks everyone for the ideas.

---

### Post by wojox on 2009-07-23
Ok drop into the shell

cd /etc/X11

ls

sudo

cp xorg.conf.failsafe xorg.conf

---

### Post by wojox on 2009-07-23
Good Deal

---

