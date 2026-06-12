---
title: "quick question about puppy linux"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2009-07-10
Is there any way i could boot puppy linux to a floppy drive  im trying to boot it into this old acer computer that was running windows 95 and it wont boot from cd just floppy


or maybe someone has a suggestion on what i could turn it into

---

### Post by jimsheep on 2009-07-10
you could install it on an HDD attached to a different PC, and then move the HDD over to your old WIN95 box.

---

### Post by pyrofreak99 on 2009-07-10
ok but is there anyway to put it on a floppy drive because i dont have a hdd drive

---

### Post by halitech on 2009-07-10
no hard drive in it? really limits what you can do with it...

there are a few floppy based distros that run off ram after booting from a few floppies, check distro watch for more info

[http://distrowatch.com/search.php](http://distrowatch.com/search.php)

---

### Post by mike555 on 2009-07-10
puppy will let you make a floppy that you use to boot from a cd ....... the computer starts from the floppy, the floppy redirects the startup to the cd .....

---

### Post by pyrofreak99 on 2009-07-10
i made a mistake it does have a hardrive   so can u guys post a link to where i could donwload puppy linux to a cd

---

### Post by 0pul3nce on 2009-07-10
> **pyrofreak99 said:**
> i made a mistake it does have a hardrive   so can u guys post a link to where i could donwload puppy linux to a cd
Quick google search game me this

[http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

---

### Post by earthpigg on 2009-07-10
> **pyrofreak99 said:**
> i made a mistake it does have a hardrive   so can u guys post a link to where i could donwload puppy linux to a cd

[http://www.puppylinux.org/](http://www.puppylinux.org/)

also the first result on a google search for 'puppy linux'....

---

### Post by hansdown on 2009-07-10
Here you go pyrofreak99.

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Puppy-Linux-1996.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Puppy-Linux-1996.shtml)

---

### Post by pyrofreak99 on 2009-07-10
Allright i thank u guys for helping me out    one more small question   i was trying to make a folder so i could make my ipod mount but when i try to do it says permisson denied


[COLOR=#33FFFF][B]$sudo mkdir /media/iPod2  this was the file i was trying to make 

but it keeps telling me permisson denied 
[/B][/COLOR]

---

### Post by Ji Ruo on 2009-07-11
Have you checked the BIOS settings to see whether you can change what the PC boots from? If you don't have a CD option there, then you can also try looking for an updated BIOS that might let you do that. Google the name and number of your motherboard (or maybe even just the model of your Acer PC) and check the manufacturer's website.

---

### Post by carml on 2009-07-11
> **pyrofreak99 said:**
> Allright i thank u guys for helping me out    one more small question   i was trying to make a folder so i could make my ipod mount but when i try to do it says permisson denied


[COLOR=#33FFFF][B]$sudo mkdir /media/iPod2  this was the file i was trying to make 

but it keeps telling me permisson denied 
[/B][/COLOR]

I succedeed with ```
cd /media 
```and then the command ```
sudo mkdir A_name_or_your_choice
```.

---

