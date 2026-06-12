---
title: "Ubuntu won't stop booting."
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Hormagaunt on 2010-02-14
My system has several hard drives.  The important ones are these:

Sata 1 - Fedora 12
Sata 3 - Windows 7
Slave 1 - Storage

I downloaded an ISO of Ubuntu 9.10 (64 bit) and burned the DVD of it.  I backed up Slave 1 and then booted off the Ubuntu DVD.  I clicked on "Install Ubuntu", selected Slave 1, and installed onto it.

Subsequently I rebooted the machine, going into the BIOS to boot off Sata 1, so I could get my Firefox settings to replicate them under Ubuntu.

Instead of Fedora 12 booting, Grub 1.97 came up.  It had 5 choices, Ubuntu, Ubuntu Repair, Memtest, some other Memtest, and Windows 7.

Where's my Fedora 12?

(I'm typing this via Win 7.  When I switched to Sata 3, Win 7 came up with no problem.)

I really, really, REALLY need that Fedora 12 back.  My work is on it.

So far, Ubuntu makes me very unhappy.

---

### Post by j.bell730 on 2010-02-14
I assume you didn't update GRUB after you installed Ubuntu.
[http://grub.enbug.org/update-grub]("http://grub.enbug.org/update-grub")
In Ubuntu, go to a terminal and type:
```
sudo update-grub
```
Hope that helps.

---

### Post by Hormagaunt on 2010-02-14
[SIZE=2]Took a bit of work, but I got my network access back.

Did the sudo update-grub.

Didn't do any good.

Absent getting grub working, is there any way I can remove it?  Apparently it's installed itself on Sata 1, the Fedora drive.  How do I get rid of it, so the Fedora drive will come up?  I tried disconnecting the Ubuntu drive, but grub still came up, which indicates that it infected Sata 1.[/SIZE]

---

### Post by Hormagaunt on 2010-02-14
I really need help with this.  It's obviously corrupted my main drive, I've no access to it at all.  Effectively, it's destroyed my system.  If I remove the Ubuntu boot drive, I can't boot anything.

---

### Post by mathfreak123 on 2010-02-14
I don't very much about GRUB2, but I was playing around a bit with it earlier. Have you looked around in /etc/grub.d? There's a file called 30_os-prober, so by the description of the name, it might have something to do with your other OS not showing up.

---

### Post by Hormagaunt on 2010-02-15
(This post was originally made on the Fedora forum, so it references people there who provided information.)


Solved it.

Bob's second suggestion was close to what worked.  Booting off the DVD, I didn't get a command line.  Instead it came up with a menu of choices.  I chose rescue.  That then went through a few steps (language and such) that looked like it's reinstalling, but it then headed off and offered to start up a command line, which I did.

Typing his last command in there didn't work, but the command-line access did show me the contents of the hard drive, so I knew it wasn't totally destroyed.  I then fiddled with some of the things it was saying, I went off and did a bit of reading, and then I tried some of the options for grub-install.  One option was --recheck, which apparently forces it to do a detailed sweep.  It came back with a different device list, and I was subsequently able to reboot to Fedora 12.

My steps for solution:

1) Powered down the machine and disconnected Slave 1, the Ubuntu drive.  (I didn't disconnect the Win 7 drive as Fedora 12 didn't have a problem with it previously).

2) Reconfigured to boot from the Fedora DVD, then brought it up in rescue mode.  Answered questions as necessary and then got the command line.

3) Typed in Bob's "chroot /mnt/sysimage".

4) Typed in "grub-install --recheck /dev/sda"

5) Exited my way out and rebooted.  Fedora 12 came up in due course.  It took a bit longer, but that seems to have been a one-time thing.

6) Rebooted and switched to Win 7.  No problems.

7) Powered down, connected the Ubuntu drive (Slave 1), disconnected both of the others, and rebooted.  Miserable failure.  It reported that there wasn't a bootable OS on the drive.

8) Reinstalled Ubuntu 9.10 from the DVD.  It asks for the following items:
    A) Language
    B) Time Zone
    C) Keyboard
    D) Should it unmount active partitions? (Like the USB drive I forgot and left in.)
    E) Select drive (200 GB or USB thumbdrive)
    F) Who am I to be (name, password)
After answering the above, it installed.

You will note that at no time does it ask anything about grub or anything else, such as optional packages as Fedora 12 asked.  Most especially it didn't ask "do you want grub installed on some other drive?".

9) Powered down, removed the USB drive, then rebooted.  It came up successfully, thereby demonstrating that it didn't try putting grub on the USB.

10) Got network access set up.  (Network access on my system isn't standard.  It goes through a router, but it doesn't go through the usual addresses.  I haven't had a newly-installed OS get it right yet. which is exactly the way I want it.)

11) Spent some time rebooting, switching from drive to drive.  Success across the board.

I've now got the system where I wanted it, 3 independent hard drives, each with it's own bootable OS.  I may, some time in the future, fiddle with grub so that it pops up and gives me options, but at the moment, no.


Learned something along the way, namely that grub apparently always gets installed.  I hadn't realized that that also happens with Fedora 12, and that it invisibly installs to do the booting, unlike Windows, where the bootloader is part of the OS.



Stoat, I'll go looking for that Super Grub Disk and I'll install it on a USB.  I've currently got 5 bootable USB systems, it's a good way to set them up.

Rockdoctor, your file's contents originally came from ubuntuforums.org, a thread dated 2005/04/05, started by vnbuddy2002 and named "HOWTO: Restore GRUB (if your MBR is messed up)".  Part 1 of your file was posted by remmelt, part 2 by wernst.



An important failure happened with this install.  I was using the Ubuntu 9.10 that I downloaded (via torrent) from the Ubuntu website.  During installation, it was told to install to Slave 1.  It was not told to write anything to Sata 1.  Why did it?  And worse, why did it set up the ability to boot to Sata 3 (the Win 7 drive) but NOT to Sata 1, the Fedora 12 drive, even though it was writing *to* Sata 1 at that time?

---

### Post by qyot27 on 2010-02-15
I believe it is indeed possible to not install grub during the rest of the Ubuntu install process.  IIRC, the relevant part is on the very last page of the setup wizard, when you click Advanced.

Also, if what I found on Google was correct, there's also a disparity between grub versions.  Fedora still uses grub legacy, Ubuntu has moved onto grub2.  I doubt it would really matter in the long run, but there is a note that grub2 with Fedora is still in the experimental/testing stage.

---

