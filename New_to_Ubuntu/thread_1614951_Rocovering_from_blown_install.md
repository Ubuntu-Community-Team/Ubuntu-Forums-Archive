---
title: "Rocovering from blown install"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Pbethe on 2010-11-06
I made an abortive attempt to install Xubuntu last year.  I killed off two CD drives in that attempt.  Anyone who wants to read the whole sad story can see it here:
[http://ubuntuforums.org/showthread.php?t=1180017&page=1]()
On that computer I need to boot from a diskette to get into linux, not the best, but it has been useful.  I have satisfied myself that the partitioning went OK.  Now, I find, Supergrubdisk2 is available for download.  It has a great feature; it allows you to boot from an Ubuntu .iso image stored on your hard drive.  I plan to put off buying a new CD drive and install Lubuntu without burning a CD.

I hope someone can give me some advice on how to go about this.  Should I do a clean install into that ext3 partition and then install grub?  Maybe I should delete the ext3 and use the free space to create an ext4 partition.  Also, I could pretend like I am beginning from scratch and tell it that I want to do a dual boot install.  What do you think?

---

### Post by sikander3786 on 2010-11-06
Which version of Lubuntu are you going to install now? 10.04 or 10.10?

What do you plan to do? Clean install or dual boot? You need to be specific on that.

What is the current partition setup?

Were you able to boot the Lubuntu/Ubuntu .iso by using Super Grub or you need help on that?

---

### Post by CharlesA on 2010-11-06
The ubuntu installer should install grub automatically.

What are you trying to accomplish?

---

### Post by X-Tarzan on 2010-11-06
i boot most .iso OS from virtualbox , you should try it

---

### Post by Pbethe on 2010-11-06
> **sikander3786 said:**
> Which version of Lubuntu are you going to install now? 10.04 or 10.10?

What do you plan to do? Clean install or dual boot? You need to be specific on that.

What is the current partition setup?

Were you able to boot the Lubuntu/Ubuntu .iso by using Super Grub or you need help on that?

Four views and three replies already, I hit the jackpot, thanks.
Using Windows 98:( I have downloaded Lubuntu Maverick to c:\iso-boot\.  Booting from Supergrub2 I have booted this iso.  It acts as if I had a Lubuntu Maverick boot CD in a working CD drive.  Cool stuff, huh?  I want to set up a dual boot, Windows 98 and Lubuntu.

So, running in live CD mode, I get a desktop with an install Lubuntu Maverick icon.  Things seem to work.  I can run a terminal and do this:
sudo blkid
/dev/loop0: TYPE="iso9660" 
/dev/loop1: TYPE="squashfs" 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="120_GB" UUID="2D10-09F6" TYPE="vfat" 
/dev/sda5: UUID="f5fea9fc-fb3d-4505-972e-24d18738dd11" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="96c101c8-5f22-48c4-85b2-afae1ee3a6a9" TYPE="swap" 
The one primary partition on the hard drive is sda1; sda5 and sda6 are logical partitions.
I have plenty of space; sda1 is my Windows partition:

df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    189572    179240     10332  95% /
none                    181396       180    181216   1% /dev
/dev/sda1             41967520  16087008  25880512  39% /isodevice

There is 1 Gbyte of swap.

I have nothing worth saving in sda5; it is too old, and I can't boot it, anyway.

---

### Post by CharlesA on 2010-11-06
Why do you not want to burn the ISO to a cd and boot off of it?

---

### Post by sikander3786 on 2010-11-06
You can simply format sda5 to ext3/ext4 whatever you prefer (ext4 is default FS for Ubuntu), leave sda6 as it is a swap partition.

Choose manual partitioning from Ubuntu installer and choose sda5's mount point as '/' and let Grub install to the default location. Everything should be fine then.

I don't know how Grub2 will act with Windows 98, will it pick it up or not as I have never done that before (win98 is pretty old now).

Hope for the best.

---

### Post by Pbethe on 2010-11-06
> **CharlesA said:**
> Why do you not want to burn the ISO to a cd and boot off of it?

The first CD drive that died was old, but the second was a nine year old new-in-the box drive.  It had been sitting on a friend's shelf for nine years, then he gave it to me.  Half of me wonders if there is some weird kind of hardware incompatibility, but the other half remembers the saying, "you get what you pay for."  This way, I can get on with the install without having to buy and install a new drive.  Again, if you want to see the whole story, follow the link in my original post.  I was ready to tear my hair out, and I don't have hair to spare.

---

### Post by CharlesA on 2010-11-06
> **Pbethe said:**
> The first CD drive that died was old, but the second was a nine year old new-in-the box drive.  It had been sitting on a friend's shelf for nine years, then he gave it to me.  Half of me wonders if there is some weird kind of hardware incompatibility, but the other half remembers the saying, "you get what you pay for."  This way, I can get on with the install without having to buy and install a new drive.  Again, if you want to see the whole story, follow the link in my original post.  I was ready to tear my hair out, and I don't have hair to spare.
Read it already. I haven't had any problems with using different CD rom drives, but then again - I think the oldest PATA drive I've got is a regular burner, which isn't really that old.

You are really making more work for yourself by trying to fuss with using supergrub to boot an ISO off a hard drive and install from that iso.

As long as you verify the MD5SUM and burn at 4x speed, you should get a good burn. Of course, I've never used Win98 to burn cds at all, so maybe that's what's hanging you up. I don't know of any recent software that'll run on a Win98 box.

EDIT: Also, if/when you get around to booting off a cd, you can "check the disc for defects" to see if it's a good burn.

---

### Post by Pbethe on 2010-11-12
> **CharlesA said:**
> Read it already. I haven't had any problems with using different CD rom drives, but then again - I think the oldest PATA drive I've got is a regular burner, which isn't really that old.

You are really making more work for yourself by trying to fuss with using supergrub to boot an ISO off a hard drive and install from that iso.


That may be so, but I have already put in a whole lot of work into trying to boot and install from a CD.  Looking back at old log files that I managed to save, I see stuff like this:
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
Nov 14 21:30:15 ubuntu kernel:  hdd: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Nov 14 21:30:15 ubuntu kernel:  ide: failed opcode was: unknown
Nov 14 21:30:15 ubuntu kernel:  end_request: I/O error, dev hdd, sector 1280664
Nov 14 21:31:15 ubuntu kernel: ide-cd: cmd 0x3 timed out

For years now, I was having problems with booting from CD, and no one from these forums was able to explain what the problem was.

Yesterday, I managed to install without running out and buying a CD drive.  The problem is that I can't log on. :confused:
I must have fat-fingered the password the same way, twice.  That is the sort thing that can happen regardless of the installation media.  Any ideas on what I should do now?

---

### Post by DM was on fire! on 2010-11-12
Download USB-Universal-Installer and your .iso. Then open up the installer and click "select other .iso," then navigate to it and check your USB drive. I can't remember, but I' m pretty sure USB 2.0 was out for 98.

---

### Post by CharlesA on 2010-11-12
That error points to a problem with the hard drive, not CD drive.

What does it do when you try to login?

Try hitting Ctrl + Alt + F1 and trying to login to that and see what it says as well.

> **DM was on fire! said:**
> Download USB-Universal-Installer and your .iso. Then open up the installer and click "select other .iso," then navigate to it and check your USB drive. I can't remember, but I' m pretty sure USB 2.0 was out for 98.

The USB 2.0 specs were released in 2000 and I think they finally got it to transfer at those speeds in XP. USB support in Win98 is iffy at best.

---

### Post by Pbethe on 2010-11-13
I am in luck; two replies and a solution to the thread "Forgotten Password", all within minutes of my posting.  Here is a great article:  [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)
It tells how to log on with root privileges, find the account names and reset a password.  I have succeeded in logging in.  So far, so good.  Thanks for all the help, this may motivate me to spend the money to buy a CD/DVD drive.

---

### Post by Pbethe on 2011-02-13
OK, I can mark this one as solved.  I can boot into Lubuntu and Windows, although I need to use a Super Grub diskette to get into windows.  

Mine is a real special case, what with CD drives dying at an alarming rate in this computer.  If some one is in a similar situation, I can provide details on how I did it.:KS

---

