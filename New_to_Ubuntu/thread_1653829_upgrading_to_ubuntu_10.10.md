---
title: "upgrading to ubuntu 10.10"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by anigodin on 2010-12-27
Hi,

I'm currently working with ubuntu 10.04.
in the last few days the update manager is 'nagging' me to upgrade to version 10.10.
The problem is I have an Nvidia video card. it was painful enough to make it work on this version (10.04) and I know there is (or at least was) a problem with the Nvidia driver and version 10.10.

Does anyone knows if the problem was solved and it is safe to upgrade without a problem? or if the problem does not occur when upgrading?


Many thanks.

---

### Post by davidmohammed on 2010-12-27
I dont know what the issue you are referring to - but why dont you backup using clonezilla before doing an upgrade?  If it fails you can then easily revert.

---

### Post by seawolf167 on 2010-12-27
> **davidmohammed said:**
> I dont know what the issue you are referring to - but why dont you backup using clonezilla before doing an upgrade?  If it fails you can then easily revert.

This is probably what I'd do. Image the drive with Clonezilla to an external hard drive, then 

(Mod Note: Deleted unsupported update method. Read [Maverick Upgrades]("https://help.ubuntu.com/community/MaverickUpgrades") for the proper way to upgrade. Mod Note End)

EDIT: If it seems to not work after the upgrade, before you revert back to your old version, see if there is a newer graphics software suite available from Nvidia

---

### Post by Sef on 2010-12-27
> I dont know what the issue you are referring to - but why dont you backup using clonezilla before doing an upgrade? If it fails you can then easily revert.

Much easier is to run the Live CD and see what happens. If the problem exists with the Live CD, then it will almost certainly exist upon installation.

---

### Post by davidmohammed on 2010-12-27
good suggestion - however, the liveCD wont help with installing the proprietary nvidia graphics driver that the OP mentioned...

---

### Post by CharlesA on 2010-12-27
> **davidmohammed said:**
> good suggestion - however, the liveCD wont help with installing the proprietary nvidia graphics driver that the OP mentioned...
True, but it'll let to know if it'll actually run it the standard driver. They can always install the proprietary version and see if it works or not.

In any case backup before upgrading.

---

### Post by anigodin on 2010-12-28
> **Sef said:**
> Much easier is to run the Live CD and see what happens. If the problem exists with the Live CD, then it will almost certainly exist upon installation.


Thank you.
I didnt think about the live CD option. I have another computer, much older one which serve as my media center. it also had an Nvidia card, a much older one (7 years old). I installed 10.10 on it and it worked with the defualt driver but the resulotion was horrible and when I tried to install the Nvidia driver the screen went dark and I could not reverse, so eventually I installed 10.04 with the defualt driver and managed somehow to improve the resulotion.

This computer, the one I use as my main, had a much better Nvidia card and when I instlled 10.04 it took me couple of day of tinkering before I found the right driver (version 173). the real question here (and I'm sorry if I repeat myself) is - will the defualt driver be enough? will it give me full resulotion?

(My Nvidia card is Quadro FX 4400)

---

### Post by davidmohammed on 2010-12-28
The only real way to find out is to try - if you dont want to mess up your current install, either use another Hard-drive, or you can [install]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar") ubuntu to a usb stick and run from there - n.b. you need to have a bios that is capable of booting from  a usb stick.

---

### Post by muteXe on 2010-12-28
Do you truly have a reason to upgrade?
I wouldn't bother if you are completely happy with your current setup.

---

### Post by sparker1 on 2010-12-29
Anigodin, was the problem that you could not get to the logon screen after installation? I just did a clean install on a laptop with nvidia graphics. I had to set "nomodeset" as an option on install and then permanently make the change to grub.cfg when I finally got into the OS. I also had the problem with my PC but all subsequent upgrades went well. I think an upgrade would be OK but a clean install might cause you to go through the "nomodeset"drama.......don't hold me to it though.

---

### Post by anigodin on 2010-12-29
> **sparker1 said:**
> Anigodin, was the problem that you could not get to the logon screen after installation? I just did a clean install on a laptop with nvidia graphics. I had to set "nomodeset" as an option on install and then permanently make the change to grub.cfg when I finally got into the OS. I also had the problem with my PC but all subsequent upgrades went well. I think an upgrade would be OK but a clean install might cause you to go through the "nomodeset"drama.......don't hold me to it though.

Well, I had the problem when I made a clean install. I never tried upgrading. I read somewhere that when upgrading to 10.04 from 9.10 everything will be ok. I wonder if it's the same when upgrading from 10.04 to 10.10

---

