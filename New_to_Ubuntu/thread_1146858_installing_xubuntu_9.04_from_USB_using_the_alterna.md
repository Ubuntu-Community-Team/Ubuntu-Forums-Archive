---
title: "installing xubuntu 9.04 from USB using the alternate install cd"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by aimpau on 2009-05-03
I've been scouring the internet looking for answers about this including the one found in the UbuntuTutorials.

I've been trying to install xubuntu 9.04 from USB using the alternate install ISO.

whenever I try the steps stated in 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

the step where I supposedly type

mount -t vfat /dev/cdroms/cdrom0 /cdrom

I get an error saying that it is an invalid argument.

Is there anyone here who can help me install from USB using alternate-cd install?

Or is another method better? Is it possible to install from my XP partition using Wubi to another HD?

I actually burned the alternate to a CD but NERO had an error which I don't understand, so that "burning to a CD" strategy, I have to hold off that for now.

---

### Post by zvacet on 2009-05-03
You can try [installing from Windows]("https://help.ubuntu.com/community/Installation/FromWindows") or burn with Infra Recorder as is described [here.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by dmeehl on 2009-05-28
aimpau, It means that the device you linked to when you did the 'ln' command was the wrong device. I ran into this problem for a while and was able to get past it by using sdb1 instead of sda1. You may have to play with it until you get the correct device that contains the cd image.

That being said, I still do not have a successful install. After I get past that point and go back to the installer, the installer still tells me that it can not copy the files from the cdrom. I've checked the mount and all seems well. But, it seems that some of the files it is looking for are actually not present. Why would the installer be looking for them?

One more thing, you can use Alt+f4 to check the output from the commands that the installer is running. Using this method, i found out (at least for 8.04.2) that the installer is trying to mount /dev/scd0 and not /dev/cdroms/cdrom0. In onther words, you may have to run the following commands instead of the one ln command you're running:
rm /dev/scd0
ln /dev/sdb1 /dev/scd0

Let me know how far you get, because I'm still stuck at this point.

---

