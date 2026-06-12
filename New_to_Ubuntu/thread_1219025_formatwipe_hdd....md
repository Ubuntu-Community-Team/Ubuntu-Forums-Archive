---
title: "format/wipe hdd..."
date: 2009-07-21
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-21
what is the safest most effective way to wipe or format my hdd to as clean and factory fresh as possible ???

thanks...

---

### Post by LowSky on 2009-07-21
use a Ubuntu LiveCD, on it is a programs called Gparted, under System> Admin> partition editor

---

### Post by NOTAGEEK on 2009-07-21
> **LowSky said:**
> use a Ubuntu LiveCD, on it is a programs called Gparted, under System> Admin> partition editor

will this do a better job than  [www.killdisk.com]("http://www.killdisk.com/") ???

my objective is to install a 2nd hdd,,, 1 for ubuntu and 1 for win 7 when available...

thanks...

---

### Post by bacil on 2009-07-21
do 

```

dd if=/dev/null of=/dev/hda

```

of is obiviously your master partition this will for one wipe out whole table and render disk clean becuse you overwriting it with 0 

(command needs to be run from livecd) since it will destroy whole disk

---

### Post by hibliss on 2009-07-21
What is your goal here? Are you trying to make the information on the drive non recoverable?

---

### Post by HermanAB on 2009-07-21
Howdy,

The only way to get it factory fresh is to use the erase functions built into the drive controller (all disk drives have it!).  Only the drive controller can erase the whole platter including bad sectors and the space between tracks - since it *is* the drive controller.

You can activate the erase function with 'hdparm'.  It is a two step process:

```
sudo hdparm --security-set-pass PWD /dev/sdX
sudo hdparm --security-erase PWD /dev/sdX
```

See this: [http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

---

### Post by NOTAGEEK on 2009-07-21
> **hibliss said:**
> What is your goal here? Are you trying to make the information on the drive non recoverable?

i would like to start over with as clean a drive as possible---guess im just wanting it that way...

i have installed 9.04 twice so far (32 bit) and want to do a fresh install of 9.04 (64 bit) on as clean a drive as possible !!!

i paid for a quad core and think i should be using it... i am very new to computing and to 9.04 with much to learn and lots (and lots) of mistakes yet ahead of me... but heck---you only get 1 shot at this planet right ???

then i am undecided as to install the win 7 rc on the 2nd hdd or just wait till the retail version is released to install at that time...

at this point i am leaning to using [www.killdisk.com]("http://www.killdisk.com/") ...

thanks...

---

### Post by Paddy Landau on 2009-07-21
> **NOTAGEEK said:**
> i would like to start over with as clean a drive as possible---guess im just wanting it that way...
All you need do is install. It will repartition and format the drive as necessary. That will "clean" the disk sufficiently to prevent old stuff interfering with the installation.

---

### Post by hibliss on 2009-07-21
Agreed. No need for NSA tools to wipe the drive unless you are concerned about valuable information previously stored on it.

A fresh install from a formatted drive will perform just as well as what you are suggesting.

---

### Post by NOTAGEEK on 2009-07-21
> **Paddy Landau said:**
> All you need do is install. It will repartition and format the drive as necessary. That will "clean" the disk sufficiently to prevent old stuff interfering with the installation.

> **hibliss said:**
> Agreed. No need for NSA tools to wipe the drive unless you are concerned about valuable information previously stored on it.

A fresh install from a formatted drive will perform just as well as what you are suggesting.


OK im convinced---i dont need cia stuff here... just want a clean drive...

thanks...  thread closed...

---

