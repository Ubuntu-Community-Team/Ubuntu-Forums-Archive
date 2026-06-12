---
title: "HDD clicking after update"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by junior09 on 2011-02-14
Hello All I ran an update last night restarted my computer now it hangs at the startup splash and my hdd is clicking. My hdd led stays on everything was running great prior to the update. I need any help I could get this is a major problem please help my last resort is opening the hdd and trying to fix the problem from there

---

### Post by NightwishFan on 2011-02-14
Hold shift while booting so that the grub boot loader menu shows up. There should be multiple entries for ubuntu. Try booting to an older kernel. (one of the lower entries). If that does not work, boot into "recovery mode" at this same menu and choose "net root" option, then run this command:
```
apt-get -f install
```

Then press ctrl+alt+del to reboot when the command is finished working.

---

### Post by junior09 on 2011-02-14
I have tried going to a lower kernel and running the script nothing it keeps taking me back to the dos like screen and its still clicking when is booting up

---

### Post by matt_symes on 2011-02-14
Hi

Check the hard discs SMART status from the disc utility application. Yo0u can do this from a LiveCD.

Kind regards

---

### Post by junior09 on 2011-02-14
I loaded the live cd and it does not see the drive

---

### Post by matt_symes on 2011-02-14
Hi

From the liveCD open a terminal and type

```
sudo fdisk -l
```

That is a small L above. Post the results back.

Kind regards

---

### Post by gradinaruvasile on 2011-02-14
Then most likely the drive is dead.

---

### Post by Oathanvil on 2011-02-14
[FONT=Verdana]HDD drives only start to make audible clicking noises just before they fail.[/FONT]
 
[FONT=Verdana]27 years working with Hard drives started out with 5 1/4 floppy drives then half height double density drives off ribbon cables all externals up to the present date and time.[/FONT]
 
[FONT=Verdana]I worked rebuilding robotics as one of my technologists positions.[/FONT]
 
[FONT=Verdana]Drives that click and you can hear them is generally not a good sign if you can back data up at all if you need to do so.[/FONT]

[FONT=Verdana]The clicking is some times an issue where the drive read head has gone past is software limit and is hitting the hardware stops internal inside the drive. Some applications can force a drive past the software limits and physically damage them.[/FONT]

[FONT=Verdana]I once witnessed an MPA80 go past a software limit and throw a 200 pound drive head through the plexiglass shield around the automated robot and it land on a million dollar reflow oven 25 feet away.[/FONT]

[FONT=Verdana]I know extreme right but size is irrelevant when it comes to software driven hardware.[/FONT]

---

### Post by junior09 on 2011-02-14
I have tried to run it nothing

---

### Post by scouser27 on 2011-02-14
I came across this topic a few months back. 

Have a look here
[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking#Possible_solutions_.28Linux.29](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking#Possible_solutions_.28Linux.29)

Might help

Also this
[http://www.linuxquestions.org/questions/ubuntu-63/hdparm-apm-hard-drive-clicking-sound-588770/](http://www.linuxquestions.org/questions/ubuntu-63/hdparm-apm-hard-drive-clicking-sound-588770/)

---

### Post by matt_symes on 2011-02-14
Hi

Other things to try. Check there are no loose cables in the PC. Try a different cable. Move the disc into another computer. Can it be seen there ?

It's not looking good though. A clicking hard drive is a bad sign. Your best bet is to see if you can read it some way and, if you can, backup your data. 

Kind regards

---

### Post by junior09 on 2011-02-14
I have put the drive in my sata external case and plugged it into my laptop running mandriva It sees the drive no problem when I try to access it the drive starts clicking

---

### Post by matt_symes on 2011-02-14
Hi

Backup your data right away. You can run other tests on the drive after that.

Kind regards

---

### Post by gradinaruvasile on 2011-02-14
I have seen drives fail under Windows and Linux and they go the same way sometimes without any prior indication. The "Disk Utility" however shows bad sectors (from SMART) quite early, but it does not warn about it if there are few. I had 1 bad sector on a drive and that was enough to lock my system from time to time.

Most likely:
1. There is no direct connection to Ubuntu, Linux or whatever, it just failed. I have seen 1-2 years old drives fail even they were used very little (under Windows and Linux).

2. If it is clicking and is not seen by the OS+BIOS, it is really dead. Check the dmesg output when it starts clicking (using it as external/secondary drive).

---

### Post by scouser27 on 2011-02-14
Can you read the drive from another distribution or did it ever work without the clicking?

---

### Post by junior09 on 2011-02-14
its not reading Im going to open it I think i have another motor somewhere thank you for all the help

---

### Post by gradinaruvasile on 2011-02-15
If it is clicking it may not be the motor.

---

### Post by Paqman on 2011-02-15
> **junior09 said:**
> its not reading Im going to open it I think i have another motor somewhere thank you for all the help

If it's still under warranty, don't open it, just get it replaced.

---

