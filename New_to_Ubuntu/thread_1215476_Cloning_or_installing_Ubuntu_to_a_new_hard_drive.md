---
title: "Cloning or installing Ubuntu to a new hard drive"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Peterfc on 2009-07-17
Hi All

I have been using Ubuntu now unaided by windows my machine is gates free. My son uses my machine a lot and is happy with it but he has constant problems on his windows machine. It took a bit of tweaking to get my machine running for me the way i want. I want to give him a machine running fine like mine. I was looking at.

1/ Clone my hard drive onto a new hard drive and then put a the hard drive in his case. 

2/ Fit a new hard drive to my machine and install and copy the contents/ setting from my machine to the new drive.

What would be the easy way to do this. 

Thanks for reading this thread

---

### Post by scrooge_74 on 2009-07-17
Are both machines exactly the same hardware? 

My advice get him in front of the PC and make him install it (if he is old enough) that way he learns, plus if you install it with him besides the father/son experience you get to practice doing an install and config again

Edit:I just notice that youuse 9.04 if for example the other PC has an ATI card you are in for some work (and may have to use 8.04)

---

### Post by kpkeerthi on 2009-07-17
Both the approaches might cause some trouble if your son's hardware is different from yours. 
I would go for a clean install and [reinstall the preferred packages]("http://ubuntuforums.org/showthread.php?t=1057608").

---

### Post by louieb on 2009-07-17
Might have problems with video and sound but might not.

Anyway cloning one drive to another can be done with  a [GParted-Clonezilla -- LiveCD.  ]("http://gpartedclonz.tuxfamily.org/index.php")Clonezilla has the advantage that it will clone the MBR too. Gparted has the advantage that you can resize partitions as you copy them over. Just have to fix the MBR when your through. [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 

Lately I've cloned a couple of drives using Gparted. Not hard. If it works great. If not you can always do a fresh install.

---

### Post by stwschool on 2009-07-17
Another option (possibly easier) is to do this..

1. Get a list of apps installed (System -> Admin -> Synaptic -> File -> Save Markings As -> Tick "Save full state"). Save this onto a flash drive or something.
2. Zip up your home directory and copy that accross too.
COMPUTER 2
3. Clean install Ubuntu, that'll give you a clean base with working hardware.
4. Get any hardware issues that might crop up dealt with (ie install proprietary drivers etc)
5. System -> Admin -> Synaptic -> Read Markings and install
6. Clean your pr0n off the home directory
7. Sorted.

---

### Post by Peterfc on 2009-07-17
Hi Guys

Sadly my son is not one to solve problems unlike me. Unlike me 

Both machine are almost identical Dell Dimensions 2400 series. If their is a slight difference would this be a problem? as they are almost a year difference in age.

Thanks

---

### Post by CatKiller on 2009-07-17
> **Peterfc said:**
> If their is a slight difference would this be a problem?

It depends on quite how much tweaking you've done :) The base install is pretty portable.

If one machine is using Ati drivers and the other's using NVidia and you've got the proprietary driver installed then you're going to have to re-configure your graphics. If they're both Ati or both NVidia and both cards are supported by the respective drivers then you'll be fine. If you're using open source drivers then you'll be fine. Similarly for proprietary wireless.

EDIT: My 73-year-old technophobe mother managed to install Xubuntu herself. It's not hard. Just be on hand for moral support and I'm sure your son will manage just as well.

---

### Post by philinux on 2009-07-17
> **Peterfc said:**
> Hi Guys

Sadly my son is not one to solve problems unlike me. Unlike me 

Both machine are almost identical Dell Dimensions 2400 series. If their is a slight difference would this be a problem? as they are almost a year difference in age.

Thanks

You could try this approach.
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by Ji Ruo on 2009-07-18
A partial solution is using AptonCD, which would make an .iso file of all the packages you have on your computer including any updates since the version you're using was released. Then you can put the iso on a usb key, or burn it to cd, and move it over to a fresh installation on the other computer. This will give you identical programs on both computers quickly and easily. Unfortunately it's not going to migrate any settings you've put on your computer, but it may still appeal to you. The other advantage is if you have any proprietary drivers which won't work on the new pc, you just need to find them on the list that's created and uncheck them either on the pack or unpack of the iso. Simple!

If you want to try it out -```
sudo apt-get install aptoncd
```Then install it again on the other computer (before updating, as you will have all the packages on your iso).

The only issue I've had with it so far is the program freezing during the packing process on low memory computers (<512MB).

EDIT - Oops, I forgot another major disadvantage of this method. You'll have all the packages on the new computer but you'll have to install them again.

---

### Post by CatKiller on 2009-07-18
> **Ji Ruo said:**
>  EDIT - Oops, I forgot another major disadvantage of this method. You'll have all the packages on the new computer but you'll have to install them again.

It's not too difficult to generate a list of all the installed packages on a machine for automating the install process.

---

