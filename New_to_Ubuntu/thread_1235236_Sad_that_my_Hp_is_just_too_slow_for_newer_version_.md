---
title: "Sad that my Hp is just too slow for newer version of Ubuntu"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by FrancesL on 2009-08-08
Sadly, I will need to look for another Linux OS to use on my Hp pavilion desktop. 7.10(?) think it was that version,  Ubuntu worked fine but with the progression of updates, even with taking it back from Jaunty to Hardy, it is still so slow. Has anyone got any suggestions for a less demanding Linux that would work with older machine? specs are in signature. Thanks:(

---

### Post by Temposs on 2009-08-08
Have you tried Xubuntu? It's supposed to be lighter weight, but it's still an official Ubuntu.

[http://www.xubuntu.com/](http://www.xubuntu.com/)

---

### Post by FrancesL on 2009-08-08
will have a look thanks!

---

### Post by Durden on 2009-08-08
Xubuntu or Debian with the window manager of your choice.

I haven't noticed a speed difference over the last few versions personally. Maybe you should try turning off desktop effects, or perhaps invest in a new video card? 

It's nice that Linux runs on older hardware but it can't run perfectly on the same hardware forever. Eventually you need to update things on the hardware end to keep up.

---

### Post by Vakman on 2009-08-08
Those specs should run it nicely, have you tried simply doing a fresh install over updates? Either way Xubuntu is a nice choice. Xfce desktop environment is what it uses. You could try CrunchBang Linux but that is for way older machines than yours really. Unless you really like OpenBox I suppose. You could try Linux Mint, I find it somehow faster overall. Not quite sure why but might be worth a try. Both CrunchBang and Linux Mint are based on Ubuntu. Xubuntu is like someone said earlier though, from the same people, official. Good luck in your choice.

---

### Post by lkraemer on 2009-08-08
Give CrunchBang 9.04 a try.

lkraemer

---

### Post by presence1960 on 2009-08-08
your specs should run 9.04 just fine. I just installed 9.04 to an HP a710n with  1 GB RAM and a 40 GB hard disk and 2.4 GHz Athlon 64 CPU with 128 MB integrated graphics and it runs 64 Bit 9.04 very nicely. is very snappy compared to the XP that is dual booting with it. My client is very happy with Ubuntu.

---

### Post by SunnyRabbiera on 2009-08-08
It might be your video card, do you have a intel graphics card?

---

### Post by utnubuuser on 2009-08-08
With those specs Ubuntu Hardy should run reasonably quickly.  You sure this isn't a video configuration/driver issue? I've Installed Ubuntu Hardy on my thinkpad with an ATI card, and without a couple minor adjustments to the xorg.conf file it seems to run very sluggishly, but as soon as I get the right settings for the video card it's ok.

4ogig hdd, 1gig ram, 1.7mhz processor

PS. Something called CrunchBang Linux is a really lightweight Ubuntu derivative that I've installed on an old P3 HP 1ghz processor and had it running as speedily as my 1.7ghz P4 thinkpad

---

### Post by Ji Ruo on 2009-08-08
Jaunty is actually supposed to be faster than Hardy.

I've personally found that Xubuntu doesn't make much of a performance improvement, although it does have more lightweight applications by default. Another desktop that you can try that is even lighter is LXDE. My laptop is a lot worse off than yours - its an 800Mhz Celeron with only 256MB of SDR RAM - but with the LXDE desktop I can get a reasonable performance out of it. If you want to try it```
sudo apt-get install lxde
```Then you can logout and choose the LXDE desktop by clicking 'options'.

Another thing you can do to improve performance somewhat is to use the ext4 filesystem which is a new filesystem available in 9.04 (it is eventually supposed to replace ext3). If you're planning to reinstall 9.04, choose to manually edit the partitions. Then all you have to do is edit your main partition, choose 'ext4' and tick the format option, and choose '/'. You should already have a swap partition on there so that's all you need to do.

Probably the biggest delays your computer is experiencing is from the software you are using. The biggest culprits would be Open Office and Firefox. If they are running too slow for you, then consider lightweight alternatives such as Abiword for your word processor and a different browser (I've heard epiphany is very lightweight).

HTH

---

### Post by 67GTA on 2009-08-08
You might want to check out WattOS. It is based on Ubuntu and uses LXDE for the desktop environment. It is lighter than XFCE, and still has most of the creature comforts of Gnome.

[http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by FrancesL on 2009-08-08
*[or perhaps invest in a new video card?* 
Intel Graphics card may well be the problem but the slow down is quite marked
I have no effects on at all. 
but thanks for input..as a pensioner with very limited budget to spare at this time I cant afford new card..but will look to see about saving for one..

---

### Post by FrancesL on 2009-08-08
> **presence1960 said:**
> your specs should run 9.04 just fine. I just installed 9.04 to an HP a710n with  1 GB RAM and a 40 GB hard disk and 2.4 GHz Athlon 64 CPU with 128 MB integrated graphics and it runs 64 Bit 9.04 very nicely. is very snappy compared to the XP that is dual booting with it. My client is very happy with Ubuntu.

As you say, I would have expected it to run fine ..from reading all the forums and seeing the specs on machines that have no issues...got me beat to be truthful. 
the graphics card is what I keep finding mentioned in forums..particularly Intel cards..and I have Intel 8284 5g/GL [Brooldale-G] so at a loss..thanks for input
Not running nor do I need or expect to Compix..:confused:

---

### Post by FrancesL on 2009-08-08
> **SunnyRabbiera said:**
> It might be your video card, do you have a intel graphics card?

Yep..got it in one!

---

### Post by FrancesL on 2009-08-08
> **Ji Ruo said:**
> Jaunty is actually supposed to be faster than Hardy.


Probably the biggest delays your computer is experiencing is from the software you are using. The biggest culprits would be Open Office and Firefox. If they are running too slow for you, then consider lightweight alternatives such as Abiword for your word processor and a different browser (I've heard epiphany is very lightweight).

HTH
 Ok all your suggestions are noted & certainly happy to give the alternative software a go. thanks

---

### Post by lswb on 2009-08-08
I have no problems with speed of operation with a pentium M laptop 1.4Ghz 1GB memory intel graphics, using either 8.04 or 9.04. I did however need to use info from
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
to get decent video performance with 9.04.

For that matter, my older laptop with a Pentium 3, 650Mhz, 512MB memory also runs 8.04 fine with special effects disabled.

---

### Post by sandyd on 2009-08-08
an ancient Dell Latitude CSx (reallly ancient) 500mhz w/ 300mb ram. (with 8 mb video card which is actually crap compared to the new intel cards) can run ubuntu 9.04 out of the box. your machine is waaayyy better than that laptop ( i just dug it out of my closet to try it) and should be able to run ubuntu 9.04

---

### Post by Ji Ruo on 2009-08-08
> **FrancesL said:**
> Ok all your suggestions are noted & certainly happy to give the alternative software a go. thanks

Actually, looking at the specs again - your computer should be able to run the default applications and desktop with no problems. I would consider the other advice given about trying a fresh install or to improve the performance of the Intel graphics.

A few short questions that might help - When did you start noticing the problem and how big was the difference? Was it after an upgrade to a newer version or something else you can point to? Is it slower for some applications than others or is it just slow for everything?

---

### Post by tgalati4 on 2009-08-08
Get a new hard disk, that will speed things up.  

Try slitaz, your machine won't get much faster than that distro.

Look at your RAM, are they matched? (1.5 GB unlikely).  Try 2 GB of matched DDR2 553 RAM, you will get a speed-up if the RAM chips are matched and the highest rated speed that your machine can handle.  You can also overclock your memory timing (say from 5-5-5-5-14 to 4-4-4-4-12 for instance).

You might be able to overclock your processor as well.

---

### Post by jimn1547 on 2009-08-09
Ubuntu is Ram sensitive-I lowered my ram and speeded up 9.04    :)     cpu  load  if you watch will drop.

---

### Post by Durden on 2009-08-09
> **jimn1547 said:**
> Ubuntu is Ram sensitive-I lowered my ram and speeded up 9.04    :)     cpu  load  if you watch will drop.

How does "lowering" your ram help? If you want more speed you get more ram. You aren't making any sense here.

As to the Intel graphics, Ubuntu 9.10 will work better with them. They rewrote the intel graphics drivers and I am seeing twice the performance I got in 9.04 on my laptop.

---

