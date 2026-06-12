---
title: "Ubuntu on Arm devices eg palm tx"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Giantyak on 2011-04-16
Hi everyone,

I have a palm tx (arm based device with tft-touch screen and 802.11b wireless and bluetooth 1.1) and i want to put ubuntu on it (remove the palm os completely). 

I'm thinking a Ubuntu Unity type of distribution would be good. Also ubuntu light would be interesting. (not really interested in most of the stuff in the "dock" i don't use IM or skype etc etc)

I'm looking at this project/experiment as i want a pda/tablet device to wander around with. I've considered the ipad and also some eee pc t101mt. Obviously the later two devices are more powerful, but they are bigger and i want to see how ubuntu can work with a touchscreen device.

In the end i'd like to run my palm tx and another device with ubuntu as the 1-2month standby time on the palm tx is epic and i have a solar charger for it....very handy.

I've seen that linux was first put on palm tx back in 2008? but there was some problem with wireless support. A solution was found, but who ever found it pretty much kept it to themselves.

***How do i install ubuntu on my palm tx?***

Cheers,

Yak

---

### Post by MasterProg on 2011-04-16
As far as I know, you can't install Ubuntu on a Palm TX.

---

### Post by Legeril on 2011-04-16
Ubuntu does not support touch screen as far as I know, so even if you could install it it would render the device useless (or at least that function of it, I have no knowledge of the device in question)

---

### Post by 3rdalbum on 2011-04-16
Ubuntu supports touch screens in general.

Your Palm TX has either 128mb of RAM, or 128mb of storage space (not entirely sure which). If it's RAM, then you MIGHT POSSIBLY be able to get an LXDE desktop to run, but certainly not Unity. If it's storage space, then no chance. Also, you'd have to check with the hacking community, not this one.

---

### Post by Giantyak on 2011-04-16
Bare in mind i'm a monkey when it comes to linux, i really have no idea and a very small understanding of how it works and no understanding of the commands etc.

I kept researching for a while after my post, and turned up some stuff.

has a interesting vid but explains nothing about the form of linux used, but does show that the linux ware had touchscreen support.
[http://palmaddict.typepad.com/palmaddicts/2008/12/palm-hacking-ma.html](http://palmaddict.typepad.com/palmaddicts/2008/12/palm-hacking-ma.html)

found this which has the all important premade palm tx kernal, which i presume contains drivers that i need, and a rootfs which i also presume contains the settings i need to make the os run "calibrated" to the device i'm using?
[http://atrey.karlin.mff.cuni.cz/~miska/]("http://atrey.karlin.mff.cuni.cz/%7Emiska/")
which is from:
[http://l4p.hackndev.org/trac/wiki/Bootpacks](http://l4p.hackndev.org/trac/wiki/Bootpacks)
Its for Angstrom opie i don't know what that is.

I'm willing to try the 2nd option i found. The problem is that all these alternative OS's seem to run from the 1gb sd card, which is fine, but theres some complication where the device jams on restart or "shutdown" of the device...and you have to short circuit the battery or cut it out and re-solder it in...or wait a few weeks for the battery to go flat...

From what i understand this complication comes from not being able to write into the palm tx's internal memory...I dont understand why i couldnt "flash" in some other os over the top of the palm os ware?

My 1 + 1 = linux?

palm tx kernal + palm tx rootfs = the means to have linux os on palm tx? correct?

if this is true then the drivers and rootfs stuff can be used with a different kernal to be able to use a distribution of ubuntu? (provided the afore mentioned resources are available)

Here we see my limited understanding of linux. I don't know if im getting confused with the terminology of where the "Drivers" are kept...eg repositary vs kernal.... im learning?

Oh and it looks like there is definitely some wireless support for linux palm tx now. I wonder if somehow linux also can support the IR and bluetooth....Edit: There is info on how to make bluetooth work....

edit again:
Here is some instruction on how to extract the wireless stuff from the palm tx using coco? which was the method for making wireless work in linux?
[http://l4p.hackndev.org/node/276](http://l4p.hackndev.org/node/276)

---

### Post by Giantyak on 2011-04-16
> **3rdalbum said:**
> Ubuntu supports touch screens in general.

Your Palm TX has either 128mb of RAM, or 128mb of storage space (not entirely sure which). If it's RAM, then you MIGHT POSSIBLY be able to get an LXDE desktop to run, but certainly not Unity. If it's storage space, then no chance. Also, you'd have to check with the hacking community, not this one.

I don't know what lxde is, but i googled it and it looks pretty. If i knew how to add all the pieces of the puzzle i could try it...it seems especially worth it now that the wirless and bluetooth can be made to work.

I have some friends that have passed the right of passage of compiling their own kernal ages ago, but share nothing with me, though one always helps me when i get stuck trying various distibutions on my desktops and netbook.

---

### Post by richaoj on 2011-04-16
I have a palm tx that I messed around with for a while.  I think the projects involved are all almost dead.  

You can't install linux, but what you can do is load up a distro (there are various ones designed for the device, like angstrom and angstrom opie) onto a SD card, and use a special application to boot to the sd card.  I got it working, but generally found it to be not really worth it.

---

### Post by Giantyak on 2011-04-16
> **richaoj said:**
> I have a palm tx that I messed around with for a while.  I think the projects involved are all almost dead.  

You can't install linux, but what you can do is load up a distro (there are various ones designed for the device, like angstrom and angstrom opie) onto a SD card, and use a special application to boot to the sd card.  I got it working, but generally found it to be not really worth it.

Why wasn't it really worth it?

---

### Post by scott-ian on 2011-04-16
It wouldn't have much functionality, but I would do it for the sake of doing so.

---

### Post by Giantyak on 2011-04-17
I've come to the conclusion thats its only really a viable option if you can physically remove the mask rom chip with the palm OS and then reinsert another chip which is RAM. Then you could run linux off an SD and not have the problems associated with the mask rom chip...

Essentially the palm tx's great potential is forever limited to its current state :(

Still i have two of them so ill try Angstrom opie anyway. I might learn something.

---

### Post by 3177 on 2011-04-17
i dont remember exactly what palm my father had(it had a III in it.) But he was able to replace windows mobile with xubuntu 9.04, so I don't think you will have a problem. Id recommend installing 10.04 and compiz(for touch screen stuff, ex resize shortcut etc.)

---

### Post by richaoj on 2011-04-17
> **Giantyak said:**
> Why wasn't it really worth it?
Functionality was severely limited.  Getting wireless to work was a serious pain in the ***.  I don't remember the exact procedure, but I remember it was painfully difficult.  And then I got it working and was like meh.  I checked again and the most recent packages are from 2008, so not much has changed since i tried.

---

