---
title: "Setting up a new computer to boot Windows and Ubuntu"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Rhyader on 2009-01-12
I like Ubuntu.
I HATE Grub!

My previous computer died, and I now have a new compaq presario with Windows Vista installed. So far it has been working very well. I have a second hard drive ordered on which I plan to install linux. It will be either Ubuntu 8.10 or Suse 11.1.  My worry is - that horrid boot manager called GRUB. I see forums festooned with posts of dismay and pain from new users who have installed GRUB only to find that they can no longer boot Windows at all. 

My new computer is one of those that has a BIOS option to tell it which hard disk to boot from "first". Notice this is a firmware setting and should be independent of windows, linux, or any operating system. Right?  Oddly, the SATA disk and DVD are in slots 3 and 4 and 1 and 2 are blank. My new hard drive, a SATA 500Gb, will go in slot 1 I assume. I can then NOT change the boot order and let Ubuntu install with the first disk (slot 3) as the "first" boot disk. In which case Ubuntu will want to put GRUB in the MBR of the first drive, I assume. And then if it screws up (-which seems to happen a lot with GRUB-) I may not be able to boot windows. Alternately I could fool Ubuntu by changing the BIOS setting so that the "second" drive (in slot 1) is the "boot first" drive. Then Ubuntu will install GRUB on THAT drive's MBR... Right? And if it screws up, I just enter BIOS, toggle the setting back, and then the computer will ignore the GRUB on the "second" drive and boot windows from the "first" drive. Um... I think... right? 

Should I be afraid? Which method should I try? Will I have to edit a configuration file by hand and guess what numbers (hd0,1 hd0,0 hd1,0 hd1,1 aaaaaggh!) will make GRUB happy?

---

### Post by Noblacktie on 2009-01-12
Don't worry about Grub messing up your MBR, thus preventing you from booting Windows. It's easy to get Windows back.

Rule for for dual-boot. Windows gets first dibs. 

Anyway, this is for when crap happens with Grub and you want at least Windows back.

If XP, boot up with Windows CD. Get to the C:\ prompt. Type "fdisk /mbr" withour quotes.

If Vista, boot up with Windows CD. Get to C:\ prompt. Type "bootrec /fixmbr" without quotes.

Don't panic :)

---

### Post by Noblacktie on 2009-01-12
If you really don't want to have Grub touch your Windows MBR, install it (Grub) on your second hard drive where Linux goes on (the one you ordered, the one without Vista).

When you start your PC, you should see at the BIOS loadout a line that says something like:

"Press DEL for BIOS options. Press F8 for more boot options"

It might not be DEL or F8 for your PC, these are just examples.

So when you start up, press the F8 key to get a list of which drives to boot up from and select which based on which OS you want to fire up.

---

### Post by Rhyader on 2009-01-12
Yes, I'm hoping this second method will work, since the computer didn't come with a Vista disk.  :( 
It seems safer to use hardware control than software control, even if having to load the bios screen to switch OSs is a pain.

---

### Post by nhasian on 2009-01-12
did you know you could use Windows Bootloader (NTloader) to boot linux instead of using grub?

directions can be found here:

[http://www.tprthai.net/bootmgr.htm](http://www.tprthai.net/bootmgr.htm)

---

### Post by Noblacktie on 2009-01-12
Your system should come with a restoration disc. You should bug your vendor for it unless you seriously plan to abandon Windows completely, which you probably aren't judging from your posts.

I'd also recommend downloading [SystemrescueCD]("http://www.sysresccd.org/Systools.en.php") as a back-up plan, if you're going to forge ahead *sans* the Vista install disc. Just in case. It'll let you get Vista back in the event the bootloader gets mucked up.

---

### Post by anewguy on 2009-01-12
I posted a thread, which is now in the how-to's, quite a long time ago on removing Ubuntu and going back to Windows.  While you may not want to go back to just Windows, you can restore the mbr so you just boot Windows by downloading a program (free) called mbrfix.  It works within Windows and will "reset" your mbr.  In this manner, it is similar to the Windows recovery "fixmbr", except you do not need a Windows installation disk to do it.  Quick and easy - download, execute, you're done.

Dave :)

---

### Post by UriahHeap on 2009-01-12
Your Compaq has a "Recovery Partition" in it, should be "D" drive.  You can create recovery media using a wizard in the Start Menu.  I suggest you create the disks before you play with Linux on it.  (Or, you can come up with some story about how you can't create the disks & call HP Tech support for free disks.)

No, the recovery media are not the same as Windopes installation disks but they will get your pc working again (with all personal data lost).

I use the hardware method on my desktop to use both Windopes & Linux.  I find it far easier to install or repair either of the installations by just disconnecting one of the hard drives, do the repair/install & reconnect the hard drive.

To boot into BIOS, tap the "Delete" key when booting.

Yesterday's a memory, tomorrow's a dream. . . LIVE today!

---

### Post by Rhyader on 2009-01-12
**Thanks for all of your ideas and suggestions.**

(Noblacktie)
This System Rescue CD looks very interesting. And very complex. It will take me quite a while just to read about all its features. But if it works as the webpage promises, then it could repair GRUB, save images of partitions, and even install NTFS-3g. Sounds like something we'd definitely want to have.

Not sure how it would fix a windows MBR, but it does say something about containing floppy images that could boot as if it were a floppy disk. I suppose you would do that to get a windows/dos command line and type fdisk /mbr, or fixmbr, or whatever the vista generation command is. 

Windows Bootloader (NTloader) (nhasian)
I also looked at "Booting Linux from Windows' Boot Manager" and found that interesting. Two questions though: first it seems dated to windows 2000. It uses redhat for an example which leads to the main question about Ubuntu... 
Doesn't Ubuntu **always** want to install GRUB? 
Is there a way to install Ubuntu without any boot manager?
(meaning that you would not be able to run the installation until you set up a boot manager independent of Ubuntu and grub)

Yes, (UriahHeap), my computer is one of those compaq machines with the recovery partition (which WinDoze calls "D:") I've never tried using it. I'll find out how to make recovery disks, and find out if I can get the compaq support people to answer some of my questions.

---

### Post by WitchCraft on 2009-01-12
When you install Ubuntu, it will ask you where you want to install grub.

You need to click on the advanced button, or you're screwed!!!
(behind the advanced button, it hides where it installs grub... first drive by default)

if you miss to press this button, you're screwed!

Just tell it to install grub to the appropriate drive

e.g. /dev/hdb1


Then you can use the windows bootloader to load the Grub  bootloader, which then loads Linux.

You first need to install Linux with grub in /dev/hdb1

Then, when installation is finished, you start windows, you won't be able to start linux.

On vista, you install Easy BCD (freeware, search google), and with that software, you can adjust the windows boot manager.

You maybe need to figure out the correct settings, so you might have to restart a few times until it works...


Good luck.
With Linux, installation is the hardest part.
After you got it working, it is VERY STABLE, and you won't come back to windows, except if you need some software that doesn't run on Linux and not under wine neither (not the case for any software, except MS-Office Access 2007, which just doesn't work correct under wine).

BTW: SuSe is a derivate of Novell and Microsuck... Use Ubuntu, it sucks far less !

PS: I would backup my important files on vista (especially emails and address book), just in case you miss the button and don't figure out how to reinstate the windows MBR...

gmail is a good place to put the data, [COLOR="Red"]**if it is not confidential**[/COLOR]

---

### Post by Rhyader on 2009-01-31
> **WitchCraft said:**
> 
PS: I would backup my important files on vista (especially emails and address book), just in case you miss the button and don't figure out how to reinstate the windows MBR...
gmail is a good place to put the data, [COLOR="Red"]**if it is not confidential**[/COLOR]

Right. I'm very suspicious of these "online backup" thingys.
I use an external harddrive that plugs into the USB port. 
Buy, reformat with linux*, and backup all your stuff. 

Also, you can download a windows vista recovery CD image from Microsoft.
You can boot from the CD and get a command line. Then according to what I
read, you can restore the default MBR. 

* how to format external hard drive in linux. (command line)
Assume you already created a linux partition on the external hard drive.
Lets assume the hard drive is /dev/sdc and your linux partition on it is 
/dev/sdc2. If so, then here's how I did it...

1. Log in as root. Run the terminal. Or type su in the terminal and become root.
2. umount /dev/sdc2
3. If you have unlimited time:
     mkfs -V -t ext3 -c -v /dev/sdc2
   Or if you don't have unlimited time:
     mkfs -V -t ext3 /dev/sdc2
4. e2label /dev/sdc {name}
5. fsck -V -t ext3 -C0 /dev/sdc2 -a
6. When it is finally done
     cd /mnt
     mkdir xdrive
     mount -rwv -t ext3 /dev/sdc2 /mnt/xdrive

Backing up stuff from the windows partition to an ext3 partition is a good
idea, because WinBlows doesn't see ext3 partitions, therefore the many
endless windows VIRUSES can't corrupt what's on a partition they can't 
read. At least that's what foolish me thinks.

---

