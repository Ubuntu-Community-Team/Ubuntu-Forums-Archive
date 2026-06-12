---
title: "Virtual Box Fatal Error:"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Kellemora on 2011-06-16
Hi Gang
I have VirtualBox installed on Ubuntu 10.04.1
I have previously installed Windows XP-Pro in VirtualBox, no problems.
Now I'm trying to install Windows XP-Home and keep getting the Fatal: No bootable medium found.
Yes I have the correct CD selected!  Even tried a second CD drive.
AND, when the CD is installed it will open up in Linux lower panel while VirtualBox is running waiting for it.
Then I get the black screen with the Fatal: No bootable medium.
I've ready about 100 complaints about this error and none of them have a resolution....
Most of the responses say the CD is bad or they didn't select the CD player, etc.  Neither of those responses fit my situation.
The CD is fine, it loads in Archive Screen, if I boot into it, I get the Install windows screen.  But in VirtualBox I get No bootable medium, etc.
I've tried Passthrough, 2 different CD players, all the settings options available in Settings, etc.  

Any Ideas?  Remember, I've already installed one Windows OS in VirtualBox without a single snag, worked like a charm.  Same computer, just want to add a second OS in VirtualBox, which I understand you can do.  On-line Video's show Win3.11, Win95, Win98, WinXPHome and WinXPPro all on the same VirtualBox selection window of which one to run.
I've seen other video's with like 7 different Linux Distro's running in VirtualBox.....

I wouldn't be so confused if I had a problem installing the first OS.
I checked and used all the exact same settings as the first as well.
Somethings not Kosher here?

TTUL
Gary

---

### Post by ttoilleb on 2011-06-16
One thing to do would be to bypass the CD completely.

Put the Win/XP install CD in a CD drive, once recognized do the following

dd if=/dev/cdrom of=/tmp/winxp-home-install.iso

Be real careful, this could destroy your harddrive if you reverse if and of, look at the manpage.  Also, your system may have cdrom0 or cdrom1, ...

Actually, put the "of" file into a folder of other iso images.  Mine is under /vbox/iso-images.

Now when you define the guest to VBox, define a CD drive and then attached the above file to the drive.  Start the guest and watch Win/XP install.  I do this all the time with what ever guest I am creating.

Not sure why VBox doesn't recognize the cd as bootable - multiple possibilities.  The above bypasses all of them.

Good luck.

---

### Post by Kellemora on 2011-06-16
Thanks TT

But I'm still lost!  Cannot type into the Terminal Window it's froze.

I've now also tried an external USB CD/DVD drive, same results.

Even if I get VirtualBox up to the window just before I hit Final and install the CD, it appears in the lower panel of Ubuntu, NOT in the VirtualBox....

I've also tried going around the horn and using /media/in Ubuntu as a link.
Still, no go.....

I'm going to try a few things on another computer so I don't mess this one up.  Took me a year to get Ubuntu 10.04.1 to even load on one of my computers.  Whereas 8.04 loaded on every one without a hitch and ran perfectly right out of the box.  I'm still not very happy with 10.04.1, many of the features I loved about 8.04 are not present in 10.04.1

I've spent about a year trying to learn BASH and it's still all Greek to me.  Yet I was a cracker jack BASIC programmer eons ago, hi hi....

Thanks again!

TTUL
Gary

---

### Post by JKyleOKC on 2011-06-16
I've had to use the copy-CD-to-ISO technique several times; it not only works but is much faster than working from the CD directly. There are a few additional points for you to know, though.

After you copy the ISO to your hard disk, you have to add it to VBox's catalog of devices to mount. You do this with Virtual Media Manager, accessed from the File menu in the VBox GUI. The ISO file can be anywhere on your disk but it's easier to keep track of them if you put all of them into the IsoFiles directory of your .VirtualBox folder.

Once you have the file listed in Virtual Media Manager, you can assign it as the virtual CD device in the Settings area for your VM. Set the boot sequence to use the CD first, and all should be as desired when you start the VM.

Hope this helps!

Also, to prevent Linux itself from grabbing a USB device first, add a device-specific filter to the USB settings of the VM, in VBox. The built-in user manual tells how, or if you wish I can give you step by step instructions.

---

### Post by Kellemora on 2011-06-16
Thanks JK

I'll do a web search on how to copy a CD to an ISO file....
I've done it before, but I have a very short memory span, hi hi....

Here is something interesting and not logical either.

In VirtualBox if I RUN the WinXP-Pro program (OS), I can install programs from either of the CD's and from the External, they are all listed in the drop down box.  I can also put in the WinXP-Home disk and it comes right up in the installer for it.

Close that out, deleted all previous .vdi files and cleaned out the Manager of them also.  Both Machine and Virtual Hard Drives.
Create a NEW VM for XP-Home, set all the setting identical to the XP-Pro settings, create the new machine, get to the point of installation of the OS and get the Fatal Error.  So I know it's NOT the CD and NOT the Player.
Something is amiss with VirtualBox!
Unless I missed something somewhere reading their manuals.
I have a 500 gig HD, nothing stored on it other than OS items as I use external file servers for data files.  4 gigs of memory, machine ran fine on only 1 gig, but I upped it to 4 recently.  In fact, all of my 512 meg machines run fine, never run out of memory and the swap file is never used.

Thanks for your help!

TTUL
Gary

---

### Post by Kellemora on 2011-06-16
Did everything you said!
Made an .iso from the CD, saved it in a new folder named ISOfiles within the .virtualbox folder, selected it as the source file in the manager, etc.
Still get the Fatal Error message.....

I used Nautilus to make the ISO it had no option to make it bootable that I could find.  But I'll go look again.....

TTUL
Gary

---

### Post by JKyleOKC on 2011-06-17
I don't think that Nautilus will do what you need, which is to make an exact byte-for-byte copy of the entire CD as the ISO. I suspect that Nautilus only copies the files and not the entire structure of the CD.

Using "dd" from the terminal is not at all risky so long as you are very careful with the "if" and "of" parameters. The input file should be your CD drive, the whole drive rather than any partition so that it includes the partition table, and the output file can be whatever you care to name it. I create a new folder in my IsoFiles sub-directory to use, before I start, and specify the "of" parameter with the full absolute path to that new folder.

It's late here so I won't be back until morning, but this should give you enough to keep busy for a while...

---

### Post by minigames on 2011-06-17
> **Kellemora said:**
> Did everything you said!
Made an .iso from the CD, saved it in a new folder named ISOfiles within the .virtualbox folder, selected it as the source file in the manager, etc.
Still get the Fatal Error message.....

I used Nautilus to make the ISO it had no option to make it bootable that I could find.  But I'll go look again.....

TTUL
Gary
I think it is you just try to see, wish you success.

---

### Post by Kellemora on 2011-06-17
OK - Finally got XP-Home in........  Thanks for all your help!!!!!

Now I'm faced with another problem.....
Installing OS's like Win95 or Win98 that I have the ORIGINAL CD's for.
They use SETUP.EXE

I've downloaded the files necessary to get me to the A: prompt.
However, to do this, you have to set the CD to the ISO file.
Adding a second file to the CD player causes VB to skip over the ISO and you get the Fatal Error.

I wonder if I load XP-Home again, and then run Win95 setup.exe if it will overwrite XP with Win95?

Worth a try, can't hurt anything!

TTUL
Gary

---

### Post by JKyleOKC on 2011-06-17
There's a special how-to on the vbox forums site at [http://forums.virtualbox.org/](http://forums.virtualbox.org/) about installing these older versions of Windows. They need special drivers that are not part of the standard vbox installation, and in any event have no official support. I believe the thread is in the "Windows Guests" area but you can search for "Win98" to locate it.

You can get around the problem of running "setup.exe" by creating a virtual floppy, much like the creation of the virtual CD to install XP, but the driver problem will remain. It's been enough to keep me from attempting to load Win98SE into a VM; instead one of my systems is set up to dual boot it for the few times that I need access to some of its features!

---

### Post by Kellemora on 2011-06-17
Hi JK

READ THAT and decided I'm NOT going to put those older OS's in there!

Seems they don't work very well either since VB wasn't designed to handle them properly.

Over the years I've kept the various exe files, EG: the Original WRITE program, not the newer one under the same filename.
Most of them still run on XP perfectly!

I'm going to mark this solved now!

FWIW:  VB is NOW seeing the XP-Home CD, all the same settings as I've tried for a few days now.  So, I set it up again from the Original CD and removed all traces of the one I installed from the ISO made from the CD.  Although I'm sure they are identical.  Already have it registered with Mickey$oft so it won't cut out on me.

Again, thanks for all of your help!

TTUL
Gary

---

