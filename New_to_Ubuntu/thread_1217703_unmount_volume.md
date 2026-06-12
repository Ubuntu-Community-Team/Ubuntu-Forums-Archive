---
title: "unmount volume ???"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-19
i was trying to delete something from my #2 desktop and i right clicked it...  the send item to trash was not selectable... i tried to drag and drop it to trash and that was not allowed...  i right clicked it again and clicked unmount volume and its icon then was gone...

does unmount volume remove this unwanted program ???

thanks...

---

### Post by earthpigg on 2009-07-19
> **NOTAGEEK said:**
> 
does unmount volume remove this unwanted program ???

a 'volume' is a partition or thumb drive or cd drive or hard drive (internal or external) or something similar.

unmount just means 'don't look at it right now'.

mount, of course, means 'look at it right now'.

Ubuntu is very good at mounting/unmounting automatically, so usually you do not need to worry about it.

edit: if you want to mount it again, it is probably in places -> computer -> look on the left side.

---

### Post by philcamlin on 2009-07-19
unmount is a removable drive 

its a lazy version of unplugging it :popcorn: basically

---

### Post by NOTAGEEK on 2009-07-19
> **earthpigg said:**
> a 'volume' is a partition or thumb drive or cd drive or hard drive (internal or external).

unmount just means 'don't look at it right now'.

mount, of course, means 'look at it right now'.

Ubuntu is very good at mounting/unmounting automatically, so usually you do not need to worry about it.
  

i restarted and sure enough it is back on the#2 desktop...

this is a stupid windows program that got loaded automatically with my lg optical drive and turns out to be built into the lg's drive... 

there is more about it here [http://ubuntuforums.org/showthread.php?t=1216969](http://ubuntuforums.org/showthread.php?t=1216969) ...

i would hope by having it on my desktop that it is not installed and would like to get rid of it...

thanks...

---

### Post by NOTAGEEK on 2009-07-19
> **philcamlin said:**
> unmount is a removable drive 

its a lazy version of unplugging it :popcorn: basically
i found out how to easily remove it on that other thread but those are for removing it from windows...

thanks...

---

### Post by laffinet on 2009-07-19
What is this icon called ?

Right click on it, select properties, select Permissions. This wil show you the permissions for this file. I bet only root has read an write access. 
In that case you have to be root to delete the file. You can do this via the terminal, or via the file manager.

Assuming you are using Ubuntu, open a terminal (accessories -> terminal) and type

```
gksudo nautilus
```

Now enter your password. This will give you a file manager with root priviliges. Now navigate to your desktop (/home/yourusername/Desktop). Highlight the file you want to delete, hit delete (or right click and select delete/move to trash). This should do the trick.

---

### Post by Bondy on 2009-07-20
It probably got installed by Wine or a similar Emu locate your Wine should be in applications tab and go to unistall wine software

---

### Post by NOTAGEEK on 2009-07-20
> **laffinet said:**
> What is this icon called ?

Right click on it, select properties, select Permissions. This wil show you the permissions for this file. I bet only root has read an write access. 
In that case you have to be root to delete the file. You can do this via the terminal, or via the file manager.

Assuming you are using Ubuntu, open a terminal (accessories -> terminal) and type

```
gksudo nautilus
```Now enter your password. This will give you a file manager with root priviliges. Now navigate to your desktop (/home/yourusername/Desktop). Highlight the file you want to delete, hit delete (or right click and select delete/move to trash). This should do the trick.


checking properties--- basic tab---type-inode directory...  4 items total---608.1kb...

permissions tab---permissions of cdrom0 could not be determined...


> **Bondy said:**
> It probably got installed by Wine or a similar Emu locate your Wine should be in applications tab and go to unistall wine software

it got installed automatically on a brand new computer by installing the 9.04 os from disc...  it has to do with the lg optical drive...

---

### Post by 3rdalbum on 2009-07-20
> **NOTAGEEK said:**
> it got installed automatically on a brand new computer by installing the 9.04 os from disc...  it has to do with the lg optical drive...

I'm familiar with this. Basically, instead of providing a CD with drivers on for a specific device, the device has some flash memory and the ability to emulate a CD drive. The driver/software is in the flash memory, so when you plug in the device for the first time, you get the "drivers CD" appearing. After installing the provided driver, the emulated disc will not appear again.

Of course, this isn't applicable for Linux. However, it's possible to tell the "udev" system to unmount the emulated CD as soon as it appears, so your device can work like normal. Unfortunately I've never done this before; all I know is that it can be done, and I've seen a howto in Linux Format. Maybe 6 months ago?

You might want to use Google to search for a howto, about how to tell udev to remove the emulated CD. Remember, all sorts of devices these days are shipping with this ridiculous* system.

After you find out about it, make sure you submit a bug report to Launchpad. The appearance of the emulated CD is not a bug, but your modifications can be implemented in the next version of Ubuntu so nobody has to hack around with udev to get your drive working properly.

*It's ridiculous to ship a DVD burner with this sort of thing; it's not like a DVD burner actually needs any drivers, and it's not like it's inconvenient to insert a CD to install software as the drive is right there :-)  I bet licensing the technology is more expensive than pressing a CD, and it means Linux users are more wary of buying your device.

And for other sorts of devices that have these emulated CDs, like 3G modems, the better solution is for the manufacturers to get together and create a single, standard driver that will work with any standard device of that class. That way you don't have to license ANY weird technology or press CDs, consumers don't have to install drivers all the time, you don't have to maintain a driver, and your device will always work no matter the operating system.

---

### Post by NOTAGEEK on 2009-07-20
> **3rdalbum said:**
> I'm familiar with this. Basically, instead of providing a CD with drivers on for a specific device, the device has some flash memory and the ability to emulate a CD drive. The driver/software is in the flash memory, so when you plug in the device for the first time, you get the "drivers CD" appearing. After installing the provided driver, the emulated disc will not appear again.

Of course, this isn't applicable for Linux. However, it's possible to tell the "udev" system to unmount the emulated CD as soon as it appears, so your device can work like normal. Unfortunately I've never done this before; all I know is that it can be done, and I've seen a howto in Linux Format. Maybe 6 months ago?

You might want to use Google to search for a howto, about how to tell udev to remove the emulated CD. Remember, all sorts of devices these days are shipping with this ridiculous* system.

After you find out about it, make sure you submit a bug report to Launchpad. The appearance of the emulated CD is not a bug, but your modifications can be implemented in the next version of Ubuntu so nobody has to hack around with udev to get your drive working properly.

*It's ridiculous to ship a DVD burner with this sort of thing; it's not like a DVD burner actually needs any drivers, and it's not like it's inconvenient to insert a CD to install software as the drive is right there :-)  I bet licensing the technology is more expensive than pressing a CD, and it means Linux users are more wary of buying your device.

And for other sorts of devices that have these emulated CDs, like 3G modems, the better solution is for the manufacturers to get together and create a single, standard driver that will work with any standard device of that class. That way you don't have to license ANY weird technology or press CDs, consumers don't have to install drivers all the time, you don't have to maintain a driver, and your device will always work no matter the operating system.


thanks for the lead... ill do some googling and see what i can turn up... i will also pay a visit to lg support but doubt if i get very far there... i also found out that this pertains to only 1 model of lg opti drives and i wonder how come ???

---

### Post by 3rdalbum on 2009-07-20
> **NOTAGEEK said:**
> i also found out that this pertains to only 1 model of lg opti drives and i wonder how come ???

The emulated CD thing is relatively new. Earlier this year I bought an LG DVD burner/Blu-ray combo and its software came on a real CD.

---

### Post by NOTAGEEK on 2009-07-20
> **3rdalbum said:**
> The emulated CD thing is relatively new. Earlier this year I bought an LG DVD burner/Blu-ray combo and its software came on a real CD.


im still having a fit trying to get rid of this stupid bluebirds thing...

---

### Post by p0cky84 on 2009-07-20
<Alt>+F2 >> Run
```
gconf-editor
```
From there:
```
App->nautilus->desktop
```
Uncheck **volumes_visible**.

-p0c

---

### Post by NOTAGEEK on 2009-07-20
> **p0cky84 said:**
> <Alt>+F2 >> Run
```
gconf-editor
```From there:


this takes me to the config editor...


```
App->nautilus->desktop
```Uncheck **volumes_visible**.

-p0c

when i get to config editor i dont know what to do with App->nautilus->desktop...

help...

thanks...

---

### Post by p0cky84 on 2009-07-20
Would you mind posting a screenshot of your gconf-editor window?

---

### Post by Bondy on 2009-07-20
> **NOTAGEEK said:**
> 

it got installed automatically on a brand new computer by installing the 9.04 os from disc...  it has to do with the lg optical drive...

Hmm I think I posted this in the wrong thread lol, It was meant to be a reply to another post

---

### Post by NOTAGEEK on 2009-07-20
> **Bondy said:**
> Hmm I think I posted this in the wrong thread lol, It was meant to be a reply to another post


hmmmm is right... thanks...

---

