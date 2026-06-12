---
title: "Hard Drive Install Problems - Let me pick the hive-mind"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2009-11-08
Hi all,

Ive just recently convinced the rest of my family to FINALLY switch over from the dark side to Linux. Ive started to wean them onto open source programs, so that the transition wouldnt be so much of a system shock.

This past weekend, I finally had the chance to install Ubuntu on their old desktop. Its a Dell Dimension 2350, with old-school IDE hard drive and CD rom connectors.

The installer runs fine until it checks the hard drive partitions and sets up the partitioner, at which point it freezes up and i have to close the installer program.

After running a few troubleshooting commands and looking up the system info, i discovered that the livecd cannot mount the hard drive.

I understand that there are a few little problems installing Karmic on computers that do not have a properly updated BIOS; I first had this problem when I tried to install on my laptop. Unfortunately, the BIOS version (still the factory original) is the latest and most recent update; meaning- no possible solution there.

Does anyone know any possible way that one could get the hard drive to mount with the live cd? Ive tried manually searching for it, tried manually mounting /sda, etc... all to no avail.

I dont have ready access to this computer until around Thanksgiving, but possible troubleshooting inquiries would be greatly appreciated, as I might be able to clarify things.

---

### Post by LewRockwell on 2009-11-08
we've been having various difficulties with 9.10

you really should get a copy of 9.04 and give that a go

might as well grap a copy of Puppy Linux LiveCD to give it a test run also

.

---

### Post by yanceypd on 2009-11-08
See if loading up without making changes to operating system. Then selecting install from desktop will work.

---

### Post by ajgreeny on 2009-11-08
Must be something more than simply IDE disks.  I have 9.10 running sweetly on a machine with IDE hard disks and CD/DVD drive and my only difficulty is the open source ati graphics driver; certainly no disk problems.

---

### Post by LewRockwell on 2009-11-08
some BIOS have a selection to protect the hard drive's MBR from being overwritten so you should check for that also

.

---

### Post by tom.swartz07 on 2009-11-12
These are all great ideas! I noticed that there were some problems with the 9.10 live version. Ill try using a 9.04 live cd, and then after that, Ill let you folks know.

I know for sure that booting fully to the livecd desktop doesnt make changes. Ive tried both versions of the installer- the livecd and the alternative install. Both fail to recognize the hard drive.


When I installed 9.10 on my system, I too was unable to recognize my hard drive, but I think that it was because I had just purchased and installed a new drive. Updating the BIOS took care of that, but there is no such option here!

Thanks for the tips, if you could think of anything else- let me know!

---

