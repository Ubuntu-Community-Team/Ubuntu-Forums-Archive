---
title: "Formatting Hard drive"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by cdo on 2010-10-30
I have tried numerous fixes to no avail . Is there a way to reformat your entire hard drive from a Linux - Ubuntu Live CD ?  

Note: The Live Cd is the only way i can make anything operational .

---

### Post by Verbeck on 2010-10-30
how about system>administration>disk utility OR gparted?

---

### Post by CharlesA on 2010-10-30
Like delete the partitions?

Use gparted from a Ubuntu livecd:

```
sudo gparted
```

I used sudo since I don't believe the livecd has gksu installed, but I could be wrong.

---

### Post by cdo on 2010-10-30
> **CharlesA said:**
> Like delete the partitions?

Use gparted from a Ubuntu livecd:

```
sudo gparted
```EDIT: Before anyone gets in a tiff about using sudo - I don't believe the livecd has gksu installed, but I could be wrong.

I pulled up gparted but it shows no devices detected ?

---

### Post by CharlesA on 2010-10-30
What does this return?

```
sudo fdisk -l
```

---

### Post by cdo on 2010-10-30
system > adminstration > disk utility just shows the DVD drive as unpartioned .

---

### Post by cdo on 2010-10-30
A bunch of info of which none i understand .   :-)

---

### Post by cdo on 2010-10-30
Guys , i had a hard drive with both Windows and Ububtu on it . Our autistic  son trashed the computer and the only way i can get on line is with the Ubuntu Live CD ( which i think means the boot manager has disappeared ) . Just trying to figure out how to totally re-format the hard drive so i can re-install Linux .

---

### Post by Verbeck on 2010-10-30
> **cdo said:**
> A bunch of info of which none i understand .   :-)
could you post the output here

---

### Post by cdo on 2010-10-30
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

---

### Post by Verbeck on 2010-10-30
its sudo fdisk -l  (ell, not one)

---

### Post by cdo on 2010-10-30
Yeah , i know it's a bitch but i also know Linux group is the best on - line resource . Just have to have someone see the problem that maybe has experiencd the problem .    :-)

PS - Am having a bonfire as soon as i can locate all the Windows CD's in my house .   :-)

---

### Post by cdo on 2010-10-30
ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk-L
sudo: fdisk-L: command not found
ubuntu@ubuntu:~$

---

### Post by CharlesA on 2010-10-30
> **cdo said:**
> ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk-L
sudo: fdisk-L: command not found
ubuntu@ubuntu:~$

There's a space between fdisk and -l

```
sudo fdisk -l
```

But yeah, if disk utility is only showing yer dvd drive, then something is wrong. Have you checked in the BIOS to make sure that the Hard drive is being seen?

---

### Post by Verbeck on 2010-10-30
if it still doesn't work, try copy-pasting the command from the post above

---

### Post by cdo on 2010-10-30
Checked ... no hard drive showing .  Someone suggested that Windows has compressed the hard drive and that's the reason ? All geek to me .   :-)

---

### Post by CharlesA on 2010-10-30
> **cdo said:**
> Checked ... no hard drive showing .  Someone suggested that Windows has compressed the hard drive and that's the reason ? All geek to me .   :-)

That's not possible.

It's more likely that the hard drive cables came loose. You'd have to open the PC up and make sure the cables are connected securely.

---

### Post by cdo on 2010-10-30
The hard drive cable is fine .  It is ( hard drive ) , however two and a half years old so maybe that's an issue . I got a private e-mail telling me that Windows would over ride Grub if you installed Grub first (which I did) . And 2 days ago when i tried to enter Windows it would not boot ... which suggests to me that the boot process has been corrupted and might explain why i can't find a way to re-format the hard drive ? 

One Linux person suggested that i would have to pull the  hard drive and install in a Windows based machine to unblock ? I am a babe in the Linux/Microsoft ocean  so willing to try pretty much anything .   :-)

---

### Post by CharlesA on 2010-10-30
The only thing that installing Windows after Linux would do is screw with the bootloader (NTLDR instead of GRUB).

It wouldn't cause a drive not to be seen in the BIOS.

---

### Post by Bartender on 2010-10-30
When you say your autistic son trashed the PC, what do you mean exactly?  Do we suspect physical damage, as in he knocked it onto the ground?  Or that he somehow blew up the software?

If you suspect blunt force trauma, then we're probably looking at a loose cable or some other physical damage.  Maybe the cables look good, but a pin broke off.  Try a new cable.  

If you suspect a software issue, I'd suggest going to a working PC and downloading gparted.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Download the LiveCD version, burn it to a CD using ImageBurn (free Windows download) or Brasero if you have a Linux PC handy.

Then boot the ailing PC from the gparted LiveCD.  You've indicated that the disk isn't being detected at all, so gparted might be a waste of time.  I'm suggesting it as a way to double-check that software cannot find the drive.

If gparted sees no disk, pull the HDD and slave it to a Windows or Linux PC.  Windows will ignore Linux partitions but should at least detect a device.  

If you can get the danged HDD to spin up and appear on some other PC, even as a slave, then you could reboot that PC with the gparted LiveCD in the tray, then format the HDD from that PC.

If the HDD is undetectable even as a slave, then I'd guess that you're looking at buying a new HDD and starting over.

---

### Post by cdo on 2010-10-30
Ok , maybe i can try that as someone will be over to help me out later .

---

