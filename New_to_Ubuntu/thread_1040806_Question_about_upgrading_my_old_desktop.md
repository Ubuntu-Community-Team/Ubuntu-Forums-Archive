---
title: "Question about upgrading my old desktop"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by oneupmshrm on 2009-01-15
Hi all. As of 2 days ago I am a new Ubuntu user via Wubi.I am running it on my new laptop and love it. I have an older desktop sitting around collecting dust, and was wondering if I took all the files I wanted to keep out and just nuked the hard drive and did a clean Ubuntu install would I be able to breathe some new life into it?

Here are some specs on the desktop:
Dell Dimension 4600
Pentium 4 2.40GHz
512MB Ram
NVIDIA GeForce4 MX 440 with AGP8X

If more info is needed let me know

Thanx:P

---

### Post by logos34 on 2009-01-15
> **oneupmshrm said:**
> would I be able to breathe some new life into it?

Here are some specs on the desktop:
Dell Dimension 4600
Pentium 4 2.40GHz
512MB Ram
NVIDIA GeForce4 MX 440 with AGP8X

are you kidding? Ubuntu can run great on those specs and ram.

---

### Post by jimrz on 2009-01-15
> **oneupmshrm said:**
> Hi all. As of 2 days ago I am a new Ubuntu user via Wubi.I am running it on my new laptop and love it. I have an older desktop sitting around collecting dust, and was wondering if I took all the files I wanted to keep out and just nuked the hard drive and did a clean Ubuntu install would I be able to breathe some new life into it?

Here are some specs on the desktop:
Dell Dimension 4600
Pentium 4 2.40GHz
512MB Ram
NVIDIA GeForce4 MX 440 with AGP8X

If more info is needed let me know

Thanx:P

Should run pretty nicely. If it were me and I had a little money available to put into it, I would add another 512Mb of ram. Also, since vid cards older than the GeForce 6xxx series are no longer supported by the new nvidia drivers (I replaced the mx440 in my old desktop not too long ago for that reason), after the ram you might want to upgrade the vid card (you can find GeForce 6 or 7xxx series at places like newegg at very reasonable prices anymore). Do those 2 things and I think you'll be surprised and really like what that old girl can do.

---

### Post by oneupmshrm on 2009-01-15
Sweet Thanx. I was just wondering because it is really Sloooow :P
I guess my other question would be after I pull the files e.g. Photos,Music, and Video can I import those back into Ubuntu?

I was thinking that this would be great because my children are getting old enough to use a computer for (learning) games and such.They are 4 and 6 so no hardcore gaming lol (thats my job):P

---

### Post by bodhi.zazen on 2009-01-15
Ubuntu will run on that box just fine.

You *might* want a lighter weight OS such as Wolvix, Puppy, DSL, Zenwalk

Other options listed here :

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by handydan918 on 2009-01-15
> **bodhi.zazen said:**
> Ubuntu will run on that box just fine.

You *might* want a lighter weight OS such as Wolvix, Puppy, DSL, Zenwalk

I can't imagine why. That hardware is twice what I run on some of my boxen...
The nvidia card is still supported by the nvidia legacy driver. You can download it from the nvidia site. It's a great exercise in working in a "pure" console environment....

---

### Post by jimrz on 2009-01-15
> **oneupmshrm said:**
> Sweet Thanx. I was just wondering because it is really Sloooow :P
I guess my other question would be after I pull the files e.g. Photos,Music, and Video can I import those back into Ubuntu?

I was thinking that this would be great because my children are getting old enough to use a computer for (learning) games and such.They are 4 and 6 so no hardcore gaming lol (thats my job):P

Sure, just copy them to an external drive/thumbdrive or burn to cd/dvd and copy back over to your ubuntu install. Better yet, just copy them over to your laptop and then move them over to the new install later when you have the desktop up and running.

---

### Post by oneupmshrm on 2009-01-15
> **jimrz said:**
>  Better yet, just copy them over to your laptop and then move them over to the new install later when you have the desktop up and running.

That is a mighty fine idea:) Thanx

---

### Post by jimrz on 2009-01-15
:)

---

### Post by baruch60610 on 2009-01-15
I've got an ancient laptop with only 256 Meg, on which I put Xubuntu.  It works well, though somewhat sluggishly.  but that's because I have a whole GUI-based distro on it.

I have an old tower with only 256 Meg of memory that I use only as a server (no graphical interface, just command line).  It runs quite well, very responsive.

I think that for your needs, a 512 Meg computer should be able to handle a full GUI (graphical user interface) installation such as Intrepid or Hardy.  And you really have little to use, if the thing is just sitting around gathering dust.  Might as well get another few years out of it...

---

### Post by logos34 on 2009-01-15
> **jimrz said:**
> I would add another 512Mb of ram. Also, since vid cards older than the GeForce 6xxx series are no longer supported by the new nvidia drivers (I replaced the mx440 in my old desktop not too long ago for that reason)


> **handydan918 said:**
> That hardware is twice what I run on some of my boxen...
The nvidia card is still supported by the nvidia legacy driver. You can download it from the nvidia site.

I was thinking you could use the 'legacy' driver pkg **nvidia-glx-71**.  Says it's supported:

> Package: nvidia-glx-71 (71.86.04-0ubuntu10) [restricted]

These binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and flat panel displays are also supported.

Please see the nvidia-71-kernel-source package for building the kernel module required by this package. This will provide nvidia-kernel-<version>

The following GPUs are supported: RIVA TNT, RIVA TNT2/TNT2 Pro, RIVA TNT2 Ultra, Vanta/Vanta LT, RIVA TNT2 Model 64/Model 64 Pro, GeForce 6800 Ultra, GeF orce 6800, GeForce 6800 GT, Quadro FX 4000, Aladdin TNT2, Ge Force 6800, GeForce 6800 LE, GeForce Go 6800, GeForce Go 680 0 Ultra, Quadro FX Go1400, Quadro FX Go1400, Quadro FX 3450/ 4000 SDI, Quadro FX 1400, GeForce 6800/GeForce 6800 Ultra, G eForce 6600/GeForce 6600 GT, GeForce 6600, GeForce 6200, GeF orce 6200, Quadro FX 3400, GeForce 6800 Ultra, GeForce PCX 5 750, GeForce PCX 5900, Quadro FX 330/GeForce PCX 5300, Quadr o NVS 280 PCI-E/Quadro FX 330, Quadro FX 1300, GeForce PCX 4 300, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400, G eForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go, GeForce 6600 GT, GeForce 6600, GeForce Go 6600, GeForce 6610 XL, GeF orce Go 6600 TE/6200 TE, GeForce Go 6600, Quadro FX 540, GeF orce 6200, GeForce2 GTS/GeForce2 Pro, GeForce2 Ti, GeForce2 Ultra, Quadro2 Pro, GeForce 6200 TurboCache(TM), GeForce 620 0SE TurboCache(TM), GeForce Go 6200, GeForce Go 6250, GeForc e Go 6200, GeForce Go 6250, GeForce4 MX 460, GeForce4 MX 440 , GeForce4 MX 420, GeForce4 MX 440-SE, GeForce4 440 Go, GeFo rce4 420 Go, GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 5 50 XGL, GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL, G eForce4 410 Go 16M, [COLOR="Red"]**GeForce4 MX 440 with AGP8X**[/COLOR]...


---

### Post by ciborium on 2009-01-16
Just keep the Compiz effects to a minimum and you should be fine.  I ran Hardy on a similarly spec'd IBM up 'till a couple of months ago.

---

