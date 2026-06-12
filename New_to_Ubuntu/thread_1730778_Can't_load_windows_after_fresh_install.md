---
title: "Can't load windows after fresh install"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by jackjoneslab on 2011-04-16
Using Ubuntu 10.10 and I kinda screwed some things up. Decided to try ubuntu and instead of installing with windows I reformatted the whole drive and lost windows. I install ubuntu off a usb drive. I then recovered with my Windows Vista recovery CD and installed windows, reformatting again. Windows would not load, gave me a black screen saying file not found..something about grub. Then I installed ubuntu again only "with other os". Now I can use ubuntu fine, but when I try to load windows even in safe mode it gets to where it would normally show the desktop and then restarts my computer.

I tend to just try things that seem like the right thing to do and often make things worse so I decided to come here for advice. Did a search for "can't load windows" and none of the situations seemed to fit mine.

---

### Post by drs305 on 2011-04-16
The best option would be to get Windows working again, and then reinstall Grub2 (which is pretty simple).

Use the Windows repair disk/installation disk to fix the MBR and make sure Windows is working. You may be able to accomplish the same thing from the Ubuntu LiveCD.

Assuming Windows is on your sda drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Don't run any other commands to further install lilo.

Try rebooting and see if Windows now boots. If it does, reboot the LiveCD. I'll assume Ubuntu is on sda5. If it's on a different partition, change the first command to the proper partition. Do NOT use a partition number in the second command:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and notice if Windows is in the Grub2 menu on boot. If not, run:
```
sudo udpate-grub
```
after booting into your normal Ubuntu OS.

If you have problems, from the LiveCD go to the following site and download/run the boot info script. Post the contents of the RESULTS.txt file the script produces.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Here are some Windows repair links from forum member *oldfred* if lilo didn't fix Windows:
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

---

### Post by jackjoneslab on 2011-04-16
"Use the Windows repair disk/installation disk to fix the MBR and make  sure Windows is working."

Not sure how to do that. When I boot from the windows CD the only option I get is to restore to factory default. That reformats the entire hard drive right?

---

### Post by drs305 on 2011-04-16
> **jackjoneslab said:**
> "Use the Windows repair disk/installation disk to fix the MBR and make  sure Windows is working."

Not sure how to do that. When I boot from the windows CD the only option I get is to restore to factory default. That reformats the entire hard drive right?

Yes, I think it would, but I'm not a Windows guy. Take a look at the bottom of my last post for *oldfred's* links on how to repair Windows. There should be a way to access a command prompt and run something like "bootrec.exe /fixmbr" (but don't quote or use that without verification from somewhere else).

---

### Post by jackjoneslab on 2011-04-16
I tried putting 
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
in the Terminal. It seemed to install lilo, but wanted me to do something with the config that I could not figure out.

Also I checked my DiskUtility and it looks like windows is on dev/sbd1.. which I guess is a partition?

Sorry I am having such a hard time with your instructions

---

### Post by jackjoneslab on 2011-04-16
checking the oldfred link now, thanks

---

### Post by drs305 on 2011-04-16
> **jackjoneslab said:**
> I tried putting 
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
in the Terminal. It seemed to install lilo, but wanted me to do something with the config that I could not figure out.
Hence the advice to only run the two commands. You don't really want to fully configure lilo. The messages want you to configure lilo but that isn't necessary or desired. In your case, since you say Windows is on sdb, you would use "sdb" in the command.

> 
Also I checked my DiskUtility and it looks like windows is on dev/sbd1.. which I guess is a partition?

Sorry I am having such a hard time with your instructions
No problem. We deal with these kinds of problems a lot so it's easy to forget this stuff is pretty foreign to most users. Don't hesitate to ask questions on these forums.

Yes, sdb1 is the first partition on your second drive (as seen by BIOS). But again, in the lilo command do not use the partition number. Also, you want to set up your BIOS so it boots the Windows partition first, at least for now to get Windows working.

---

### Post by jackjoneslab on 2011-04-16
Back to square one. I have ubuntu10.10 installed and the whole drive is partitioned to it. Windows is not installed at all. I know if I install windows right now from the CD it will not work. What I don't understand is why. I think it might be something to do with the drive being formatted for linux. Is there a way I can reformat my drive for windows before I try booting from the windowscd and installing?

---

### Post by jackjoneslab on 2011-04-16
Is there a way to do a remote desktop with me or is that a lan only thing.

---

### Post by vivek.pandey on 2011-04-16
> **jackjoneslab said:**
> Back to square one. I have ubuntu10.10 installed and the whole drive is partitioned to it. Windows is not installed at all. I know if I install windows right now from the CD it will not work. What I don't understand is why. I think it might be something to do with the drive being formatted for linux. Is there a way I can reformat my drive for windows before I try booting from the windowscd and installing?

i think you should go through this link
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by vivek.pandey on 2011-04-16
> **jackjoneslab said:**
> Is there a way to do a remote desktop with me or is that a lan only thing.

this is quite ambiguous... can you please be a bit clear ...?

---

### Post by K_45 on 2011-04-16
Look here to dual-boot, post if you don't understand any of the instructions:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by jackjoneslab on 2011-04-17
> **vivek.pandey said:**
> this is quite ambiguous... can you please be a bit clear ...?

I was asking if ubuntu had a feature where a remote user could control my computer to see what was going on.

---

### Post by jackjoneslab on 2011-04-17
> **vivek.pandey said:**
> i think you should go through this link
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Thanks I will check that out. I don't have windows 7 though, I have my recovery cd that has vista on it. Not sure if that makes a difference.

I am not sure if ubuntu is for me. How can I just go back to windows? The recovery CD alone does not work so I  guess I messed something up. 

I will try those steps today.

---

### Post by ububeginner on 2011-04-17
> **jackjoneslab said:**
> "Use the Windows repair disk/installation disk to fix the MBR and make  sure Windows is working."

Not sure how to do that. When I boot from the windows CD the only option I get is to restore to factory default. That reformats the entire hard drive right?

Did your CD come bundled with a fully installed system?
Those CDs are ususally not fresh Windows CDs, They come with the manufacturers drivers and run semi unattended installations of windows, giving the user little or no control over the partitioning of the drive, and will quite possibly have the repair option removed. You can download the vista recovery CD [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), 
This is not the installation CD, just the repair part of it.

---

### Post by jackjoneslab on 2011-04-18
> **ububeginner said:**
> Did your CD come bundled with a fully installed system?
Those CDs are ususally not fresh Windows CDs, They come with the manufacturers drivers and run semi unattended installations of windows, giving the user little or no control over the partitioning of the drive, and will quite possibly have the repair option removed. You can download the vista recovery CD [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), 
This is not the installation CD, just the repair part of it.

It did not come with any CD at all, I had to make the recovery CD. Thanks a bunch! That might solve all my problems. Fingers crossed

---

