---
title: "absolutely frustrated with install!"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by bakechef on 2010-10-31
Hello all!

I am fairly new to Ubuntu and am quite a novice when it comes to the inner workings of an OS.

I have successfully installed Ubuntu 10.10 on an older laptop, and installed a dual boot with the help of WUBI on another windows machine.  After trying it out for a while I knew that it would serve my purpose well for a new media center pc.

Well I built a computer (first time ever) and that all went really smooth, until I tried to install Ubuntu.

At first I couldn't even get the drive (dvd burner) to read the disks properly, then I hooked up an older drive and bingo, the live CD worked.  The problem came when trying to install on the hard drive.  I would get all the way to the last step, step 7 and the installation would crash giving me the "sorry the ubiquity closed unexpectedly" and "install.py closed unexpectedly" 

Try as I may, I cannot get past this.  I have tried reformatting the drive, making countless new disks from different downloads, both 10.04 and 10.10, both on CD-R and Dvd+R using infra recorder on 2 different burners.

This really has me stumped, I don't know what to do!

This is the machine that I am trying to install on.

I am trying to install 32bit 

AMD Athlon II 3.1 (regor)
2 gig DDR3 ram
500 gig HD (seagate)
BIOSTAR A880G+ AM3 AMD 880G HDMI Micro ATX AMD Motherboard

I don't seem to have the ability to boot from a USB flash drive, weird because an older Dell allowed me to do this.

---

### Post by jroa on 2010-10-31
I know this will sound stupid, but did you try to burn a new CD?  I have had problems like that in the past and I just burned a new CD at the _lowest_ burn speed and it worked like a charm.

---

### Post by bakechef on 2010-10-31
> **jroa said:**
> I know this will sound stupid, but did you try to burn a new CD?  I have had problems like that in the past and I just burned a new CD at the _lowest_ burn speed and it worked like a charm.
Yeah, I tried multiple cds and dvds.  I even tried two different burners.  I always set to burn at the lowest speed.

I thought that would be the issue at first because you just don't always know the integrity of a burn.:)

---

### Post by jroa on 2010-10-31
Did you check the compatibility of your hardware?  You said that your first hard drive did not work, which is a bios driver problem.  Maybe you have some other compatibility issues.  Just a guess, though.

---

### Post by bakechef on 2010-10-31
> **jroa said:**
> Did you check the compatibility of your hardware?  You said that your first hard drive did not work, which is a bios driver problem.  Maybe you have some other compatibility issues.  Just a guess, though. 

sorry if I wasn't clear, it was the first DVD burner drive that didn't work. I tried 2 others that would actually read the disks and get me into the live and into the setup, but the setup wouldn't finish.

---

### Post by uRock on 2010-10-31
Is this the mobo you have? [http://www.biostar.com.tw/app/en/mb/content.php?S_ID=492](http://www.biostar.com.tw/app/en/mb/content.php?S_ID=492)

---

### Post by lkraemer on 2010-10-31
bakechef,
Your ISO file you downloaded has a MD5SUM or SHA256 Verification Hash
code associated.  You should be able to load the ISO in K3B and then
Double Check that the MD5SUM matches with what it is supposed to be
for the ISO.

Also you should burn as DAO (Disk at Once) and at the slowest speed possible.

You should be able to run Ubuntu from the LiveCD (ISO) to test it out.
If it all works correctly, then install it.  If the install fails you 
can try the Alternate CD (ISO) which should overcome any problems getting
the ISO to install.

Once it is installed, Connect Via Ethernet, then UPGRADE the install to the latest updates.

lk

---

### Post by bakechef on 2010-10-31
> **uRock said:**
> Is this the mobo you have? [http://www.biostar.com.tw/app/en/mb/content.php?S_ID=492](http://www.biostar.com.tw/app/en/mb/content.php?S_ID=492)

Yes it is.

---

### Post by bakechef on 2010-10-31
> **lkraemer said:**
> bakechef,
Your ISO file you downloaded has a MD5SUM or SHA256 Verification Hash
code associated.  You should be able to load the ISO in K3B and then
Double Check that the MD5SUM matches with what it is supposed to be
for the ISO.

Also you should burn as DAO (Disk at Once) and at the slowest speed possible.

You should be able to run Ubuntu from the LiveCD (ISO) to test it out.
If it all works correctly, then install it.  If the install fails you 
can try the Alternate CD (ISO) which should overcome any problems getting
the ISO to install.

Once it is installed, Connect Via Ethernet, then UPGRADE the install to the latest updates.

lk

I am not sure what that first paragraph means:confused:

I am able to run the live cd.  I do write disk at once on the slowest speed with infra recorder.

Thanks for your help. Where would I find the alternate iso cd download?

---

### Post by uRock on 2010-10-31
It appears they only have the image available for torrenting. Here is the link [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by waynefoutz on 2010-10-31
I prefer to use unetbootin [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") and have it install it on a usb key. Unetbootin will download the iso, and install it on the thumb drive. Then boot off it, and install. Much faster, more reliable.

---

### Post by bakechef on 2010-10-31
Well I downloaded the alternate cd iso and now the screen is stuck at "partitions formatting" UGH!!!!!!!!!

The disk tested fine and the Hard drive tests healthy!

---

### Post by uRock on 2010-10-31
This may sound odd, but has the disk ever been partitioned or is it brand new?

If it is brand new, then partitioning it with the Gparted LiveCD or Norton Partition Magic to EXT or NTFS, it doesn't matter which, then boot the ubuntu cd and try to install it.

---

### Post by bakechef on 2010-10-31
> **waynefoutz said:**
> I prefer to use unetbootin [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") and have it install it on a usb key. Unetbootin will download the iso, and install it on the thumb drive. Then boot off it, and install. Much faster, more reliable.

Can't seem to find a way to boot from a usb flash drive.  My old dell could do it by resetting the boot order in the bios, but this new board doesn't seem to have that option.

Weird thing is, when I tried to boot from USB on the laptop it failed over and over, when I burned a disk it worked just fine.  Now that disk and all others that I have used, fail in this new machine.

---

### Post by bakechef on 2010-10-31
> **uRock said:**
> This may sound odd, but has the disk ever been partitioned or is it brand new?

If it is brand new, then partitioning it with the Gparted LiveCD or Norton Partition Magic to EXT or NTFS, it doesn't matter which, then boot the ubuntu cd and try to install it.

It was a new OEM bare drive.  I tried Gparted live cd, but I am not sure if I did everything correctly, I may have to go back and revisit that.

It now seems to have partitions from all these attempts to install Ubuntu.

---

### Post by Sef on 2010-10-31
From the Live CD:

Applications > Accessories > Terminal

then copy and paste in this code:

```
sudo fdisk -l
```

Then copy and paste the results here.  

The code will show what partitions you have.

---

### Post by bakechef on 2010-11-01
I feel so completely defeated.

I have wiped out all of the partitions, burned multiple disks on multiple burners (slowest speed), tried both 10.10 and 10.04, and nothing has worked. I have even used 3 different cd/dvd drives.

I have had limited success getting the live version to work correctly.

I don't know what to do other than go out and buy Windows 7.  

I was able to get this working flawlessly on two other computers, everything installed with the CD on the first try. 

UGH!!!!!!!!!

---

