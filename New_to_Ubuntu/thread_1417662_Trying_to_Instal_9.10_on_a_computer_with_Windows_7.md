---
title: "Trying to Instal 9.10 on a computer with Windows 7 Beta"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by jmgodish123 on 2010-02-27
This is not going very well.
Either it's been on the main screen where I select "Install Ubuntu" for two and a half hours and done nothing, or it has frozen. Earlier I tried it and just took the disc out and went back to windows, as it's never got to the install screen, only to the part where it is, according to 
[http://www.pcpro.co.uk/forum/viewtopic.php?t=339055&sid=6ab262b519362002b149634377c2ffe7](http://www.pcpro.co.uk/forum/viewtopic.php?t=339055&sid=6ab262b519362002b149634377c2ffe7)
loading into RAM. I can't get it to work properly- I tried to install wubi and partition my harddrive but I can't figure that one out, I'm not confident enough to try it, I think I'll destroy my laptop.

At some point in installation, when I push a key, it started making a noise, almost like a static. when a key is pressed. 

I am installing it on a Compaq Presario C700, it's HDD is 120 GB and it's RAM is just 1GB. Would that make this instal go very slow, or is it possibly something else I should be doing? 
I have been following the step by step I linked above exactly, but as I'm only on step 2, that really doesn't mean too much.

---

### Post by yeats on 2010-02-27
Could be a bad CD burn...  Do you have an alternative medium to install on?  Maybe a Live USB would be better.

---

### Post by jmgodish123 on 2010-02-27
The only medium I have are discs. I could DL another one and write it to another disc and try it, which I think I will, and give that a shot.

---

### Post by 2hot6ft2 on 2010-02-27
The link you gave is a forum talking about compiz.

1) Did you download ubuntu from here?
[http://www.ubuntu.com/](http://www.ubuntu.com/)

2) Did you check the md5sum of the iso as per the instructions here?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
section 5 covers checking it in windows

3) Did you check the md5sum against the md5 hashes here?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

4) Did you follow the burning how to here?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

5) Did you leave the livecd in the computer and reboot to the livecd?

6) Or did you put the livecd in while running windows?

---

### Post by 2hot6ft2 on 2010-02-27
> **jmgodish123 said:**
> I tried to install wubi and partition my harddrive but I can't figure that one out, I'm not confident enough to try it, I think I'll destroy my laptop.
Many of us including myself dual or triple boot and I for one will always do real hard drive installs where each operating system is on ots own partition and/or drive. WUBI is ok for trying it out i suppose but then that can be done with the livecd.
> **jmgodish123 said:**
> At some point in installation, when I push a key, it started making a noise, almost like a static. when a key is pressed.
Look at the indicator for the CAPS Lock. If it's flashing then it's most likely a bad burn or cd.
> **jmgodish123 said:**
> I am installing it on a Compaq Presario C700, it's HDD is 120 GB and it's RAM is just 1GB. Would that make this instal go very slow, or is it possibly something else I should be doing?
It's not going to be super fast with the livecd anyway and if you're doing it while running windows it will be considerably slower but 1GB of RAM will be plenty.

Main thing is making sure the livecd is burned from a good iso, burned slow as possible, and is good so when you install there are no errors.

---

### Post by Mark Phelps on 2010-02-28
Unless you're highly experienced at Linux installs, you should never just try to force an install on an untried machine.  The primary value of using a LiveCD is to test the Linux distro on a box to see how well it works and how well it detects the hardware and installs the right drivers.  This isn't MS Windows where you stick in a driver CD, launch it, and you're done. Linux drivers are detected and installed automatically, so any problems you encounter in LiveCD mode are going to be trivial to impossible to fix later.

Also, your title says Windows 7 Beta -- so does this mean that the hard drive is already fully utilized by Win7?  

To find out, boot into the LiveCD, run the Partition Editor, and look at the layout of your drive.  If it's full, you can still use the full disk mode in Ubuntu to do an install -- but that will erase the existing partition(s) and install its own.

Wubi won't "destroy your laptop", but last time I checked, the Win7 beta period had expired, and given that you need a working MS Windows system to use Wubi, that wouldn't be a good choice.

---

### Post by oldfred on 2010-02-28
Some more sites with graphical dual boot installs. If you decide to not use wubi you should shrink win7 using the wiDual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)
n7 tools and make sure it boots.

---

### Post by -kg- on 2010-02-28
> Also, your title says Windows 7 Beta -- so does this mean that the hard drive is already fully utilized by Win7?

To find out, boot into the LiveCD, run the Partition Editor, and look at the layout of your drive. If it's full, you can still use the full disk mode in Ubuntu to do an install -- but that will erase the existing partition(s) and install its own.

Uh, that shouldn't be the *only* choice, unless Windows 7 has changed something that I'm not aware of.

Assuming that Windows 7 still has "Disk Management" and defragmenter, one should be able to defrag and shrink the Windows partition sufficiently to be able to install Ubuntu in a dual boot configuration.  If the original installation disk is available, you can also save all important data externally, delete the partition, create one that is small enough to leave sufficient room for an Ubuntu installation, and reinstall Win 7 Beta to that smaller partition.

Like I said, unless something has changed that I'm not aware of, it should be possible to shrink the Windows partition sufficiently to install Ubuntu in a side-by-side configuration.  That should be an option presented in the installer partitioner, or you can choose manual partitioning.

Another option would be to obtain and install another hard drive and install to it.  GRUB will replace the Windows installer or you can install GRUB to the MBR of the other hard drive and switch the boot drive in BIOS or physically.

But even in the single physical disk configuration it should be possible to shrink the partition on a 120 GB hard drive and create the requisite partitions in which to install Ubuntu, unless the partition is chock full of files.  If it is, then either remove some of them or move them elsewhere.

---

### Post by Mark Phelps on 2010-03-01
> **-kg- said:**
> Uh, that shouldn't be the *only* choice, unless Windows 7 has changed something that I'm not aware of.

I merely pointed out that the Beta test period for Win7 has expired. So, using Wubi to install inside Win7 would not be a good choice as that version of the OS could become deactivated and nonfunctional at any time.

Of course, there are other options -- and since I'm personally NOT a fan of Wubi, those are the ones I would prefer.

---

