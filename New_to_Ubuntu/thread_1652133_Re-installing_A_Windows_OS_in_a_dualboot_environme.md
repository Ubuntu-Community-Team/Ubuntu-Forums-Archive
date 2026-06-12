---
title: "Re-installing A Windows OS in a dualboot environment"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by mistypotato on 2010-12-24
I have a Dual Boot machine with Windows Vista on the first partition and Ubuntu 10.04 on the second partition.  This is a very common situation with Ubuntu users so I feel this is very much related to Ubuntu users.

Due to an application that corrupted the Windows registry, and a potential malware app that may have installed itself in the MBR, my Windows Vista install was trashed.

Since I couldn't find any threads specifically about completely  re-installing the Windows OS in what I call a Linux environment, (since Grub is the boot loader and since Linux is the most important OS on the drive), I'm going to figure out how to do it and post a how to here.

The challenge is to re-install Windows Vista OVER the current copy, completely refreshing the install and also the MBR while leaving the Linux partition in-tact.

For my purposes, in the future, I'm not going to create "Dual Boot" disks.  Going forward from now on, I'll always have two hard drives.....one for Linux and one for Windows.  
The selection of boot OS will not be a Grub decision, but rather a BIOS change selecting the desired OS.  That way, future problems with Windows (and inevitably they always come sooner or later), it is MUCH easier to clean up a trashed Windows install that is on it's own hard drive than when it's installed as a second OS on a dual boot hard disk.
Besides, the Linux install is too important to allow it to be put at risk due to Windows vulnerabilities and instability issues.  

Anyway, as I figure out how to do this properly, I'll post it here for others who find themselves in this situation.

---

### Post by Quackers on 2010-12-24
Your problems may arise if you re-install Vista with a recovery dvd or partition. These could insist on using the whole drive.
There would be no such problem if you are using a Vista installation disc.

---

### Post by amjjawad on 2010-12-24
> **mistypotato said:**
> I have a Dual Boot machine with Windows Vista on the first partition and Ubuntu 10.04 on the second partition.  This is a very common situation with Ubuntu users so I feel this is very much related to Ubuntu users.

Due to an application that corrupted the Windows registry, and a potential malware app that may have installed itself in the MBR, my Windows Vista install was trashed.

Since I couldn't find any threads specifically about completely  re-installing the Windows OS in what I call a Linux environment, (since Grub is the boot loader and since Linux is the most important OS on the drive), I'm going to figure out how to do it and post a how to here.

The challenge is to re-install Windows Vista OVER the current copy, completely refreshing the install and also the MBR while leaving the Linux partition in-tact.

For my purposes, in the future, I'm not going to create "Dual Boot" disks.  Going forward from now on, I'll always have two hard drives.....one for Linux and one for Windows.  
The selection of boot OS will not be a Grub decision, but rather a BIOS change selecting the desired OS.  That way, future problems with Windows (and inevitably they always come sooner or later), it is MUCH easier to clean up a trashed Windows install that is on it's own hard drive than when it's installed as a second OS on a dual boot hard disk.
Besides, the Linux install is too important to allow it to be put at risk due to Windows vulnerabilities and instability issues.  

Anyway, as I figure out how to do this properly, I'll post it here for others who find themselves in this situation.

In my signature, there's a guide for Dual-Booting. 3 different scenarios and I'm working on other 2 so total of 5 different scenarios which means 5 guides in 1.

In your case, you want to (say) remove Windows while Ubuntu is installed then re-install a fresh copy for Windows.
Very simple and there are lots of guides about that too.

1) Format Windows Partitions while you're on Ubuntu
2) From Terminal run : 
```
sudo-update grub

```
3) Reboot and start installing Windows
4) Once done, make sure you can login to Windows
5) If yes then insert Ubuntu LiveCD/USB and [re-install GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
6) Done

Yes, I need to add that to my guide but I need some screenshots so that will be soon :)

---

### Post by amjjawad on 2010-12-24
> **Quackers said:**
> Your problems may arise if you re-install Vista with a recovery dvd or partition. These could insist on using the whole drive.
There would be no such problem if you are using a Vista installation disc.

Then guess the better option is to format, right?

---

### Post by Quackers on 2010-12-24
I personally format any partition when I'm installing an OS over the top of another one.

---

### Post by amjjawad on 2010-12-24
> **Quackers said:**
> I personally format any partition when I'm installing an OS over the top of another one.

Same here. Even if I'm installing the same OS.

---

### Post by mistypotato on 2010-12-24
> **amjjawad said:**
> 
In your case, you want to (say) remove Windows while Ubuntu is installed then re-install a fresh copy for Windows.
Very simple and there are lots of guides about that too.

1) Format Windows Partitions while you're on Ubuntu
2) From Terminal run : 
```
sudo-update grub

```
3) Reboot and start installing Windows
4) Once done, make sure you can login to Windows
5) If yes then insert Ubuntu LiveCD/USB and [re-install GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
6) Done

Yes, I need to add that to my guide but I need some screenshots so that will be soon :)

This sounds like the path I would need to take.
My MAIN concern is not destroying my Linux Install.
I also need to make sure this method would remove any potential MBR viruses.
Viruses, Trojans and malware are so clever.  A few times I found that NOTHING short of a total Low Level format of the entire drive could get rid of them.  But I think my current situation is a result of installing Kiwi Syslog software.  The install went bad and immediately my Window Vista install fell apart.

---

### Post by mistypotato on 2010-12-24
Hey,

I suppose that's another very important question I need to answer....

Can a Windows virus embed itself in the MBR of a Linux install.

In other words, assuming I DO have a virus (malware), I want to make sure I eradicate it fully.

---

### Post by wiggy25 on 2010-12-24
These are great for a complete novice to Ubuntu/Linux like me.

Question though, must you have the original Vista install disc to re-install it?
I only ask, as in my case the Vista software is stored on a partition on the hard drive.

Cheers

Ian

---

### Post by Quackers on 2010-12-24
wiggy25, the problem with the recovery partition is that it may insist on using the whole disc to re-install Windows, which would wipe out any other OS on the same drive. An installation disc wouldn't insist on that.
You should also make a set of recovery dvd's on your system. There is likely to be a means of doing that somewhere in your machine. Partitions can become corrupt, but if you've got the discs you're still ok if that happens.

---

### Post by amjjawad on 2010-12-24
> **mistypotato said:**
> Hey,

I suppose that's another very important question I need to answer....

Can a Windows virus embed itself in the MBR of a Linux install.

In other words, assuming I DO have a virus (malware), I want to make sure I eradicate it fully.

[http://en.wikipedia.org/wiki/Computer_virus](http://en.wikipedia.org/wiki/Computer_virus)

Also seach google for more info.

As far as I know, Windows Viruses can't work under Linux.
If I remember correctly, the MBR Virus also attack sector zero and destroy the HDD or that must be another one ... not very sure.

I'm using Linux to stay away from Viruses so my experience with these stuff not much.

---

### Post by amjjawad on 2010-12-24
> **mistypotato said:**
> This sounds like the path I would need to take.
My MAIN concern is not destroying my Linux Install.
I also need to make sure this method would remove any potential MBR viruses.
Viruses, Trojans and malware are so clever.  A few times I found that NOTHING short of a total Low Level format of the entire drive could get rid of them.  But I think my current situation is a result of installing Kiwi Syslog software.  The install went bad and immediately my Window Vista install fell apart.

If you're going to re-write the MBR or anything related to the MBR, you won't be able to boot Ubuntu but that's so easy to fix ... just re-install GRUB2 to the MBR.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

But yes, some viruses are smart enough.


So, have you been attacked by one?

Edit: [http://antivirus.about.com/od/securitytips/a/bootsectorvirus.htm](http://antivirus.about.com/od/securitytips/a/bootsectorvirus.htm)

---

### Post by AZinOH on 2010-12-24
Any chance you could install ClamAV or Avast for Linux into Ubuntu and then use it to scan the Windows partition? Probably wouldn't hurt to try. ClamAV should be in the Ubuntu software Center, Avast can be found:  [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

---

### Post by mistypotato on 2010-12-24
> **AZinOH said:**
> Any chance you could install ClamAV or Avast for Linux into Ubuntu and then use it to scan the Windows partition? Probably wouldn't hurt to try. ClamAV should be in the Ubuntu software Center, Avast can be found:  [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

Yes,
you can do this.

However, in my experience, people place far too much faith in virus scanners.

They are mostly effective against viruses that have been out for at least a month or more
because it takes a while for them to be discovered, examined by anti-virus authorities and then for a bit longer for scanning definitions to be created.  By that time, the person or people who released it in the first place have already released a new variant and the cycle repeats.
The people creating these things are not always kids.  Often now they are some of the most binary aware, computer savvy people alive.
They know every trick and every defense that could be used and how to circumvent it.

Rarely are you fully protected.

In addition, once a virus gets on your computer anti-virus programs are usually modified so that they either do not update even though it appears they do) or they do not actually report malaware (because the code is changed to protect the virus).

It's a vicious cycle.

---

