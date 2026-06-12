---
title: "Kernel Panic after software update"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by Ebonhawke on 2010-01-31
I ran update manager this morning and had a number of packages that needed to be updated - I ran the update and there was an error with one of the installs (unfortunately I can't remember which package - should've written that down).  I then rebooted the machine, and got the message
 
*"Kernal panic - not syncing: VFS:  Unable to mount root fs on unknown block [0,0]"*
 
when I booted the machine - tried a couple of different reboots and got the same message - it appears when the computer starts to load Ubuntu (Karmic Koala) - so before the logo.
 
I still had the USB stick with the version of Jaunty Jackalope on it that I used to install Linux on the machine.  I plugged that into the USB port on the computer and tried to at least start the machine through the USB stick.  In the Bios, I set the boot order to be USB/USB/USB and disabled the hard drive boot - but still got the same message
 
Any suggestions?

---

### Post by wjoyce on 2010-01-31
Hi,

Assuming you're using wubi, I had this problem and it was solved by replacing the c:\wubildr file as per post 90 here [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104?comments=all](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104?comments=all)

HTH
B.

---

### Post by Ebonhawke on 2010-01-31
Sorry - definitely a Linux n00bie

The computer on which the above problem is occuring is a Linux-only machine - the HDD was first formatted with JJ - so not sure that's a WUBI machine, as my understanding is that WUBI is a windows-based installer for machines that want to run both Windows and Linux (please correct me if I'm wrong!)

---

### Post by wjoyce on 2010-01-31
lol - the blind leading the blind here - I'm a newbie too :)

You are correct.  Wubi is the windows-based installer, and it's that that I'm using.  Sorry, I can't help much beyond the advice offered above.  Hope you find a solution soon..

---

### Post by Ebonhawke on 2010-01-31
OK - so I created a USB boot disk of Karmic Koala 9.10, and was able to boot up from the USB drive (with some odd hiccups - such as not being able to use the keyboard at the boot menu, and forced to wait until the computer automatically booted)

Using an external HDD as back-up, I'm trying to copy photos/files from the HDD on the computer to the external HDD - with the thought of reinstalling Karmic on the original hard drive (of course, this would wipe out everything currently on the HDD

(I'm having a bit of difficulties as some photos I don't have 'permission' to access, while others I do?)

OR - is there an easier way to copy the files from the USB drive to the original harddrive?

---

### Post by Ebonhawke on 2010-02-01
Today's update

- Copied the files from my original HDD to an external HDD as back-up

- Ran FSCK on the original HDD to check for errors - no errors found

- Reinstalled 9.10 from the USB drive.  Selected "Erase entire disk" and "log in automatically".  Reinstall seemed to go OK (no error messages noted)

When I restart (with the USB drive removed), everything seems OK - logo shows up (which wasn't happening when the problem first started.  However, after the logo appears, it then drops me into a shell, asking for a login name and password!?  If I enter the login name and password that were entered as part of the installation process (again noting that I had selected "log in automatically" as the default) I get the *name$name-desktop* prompt but not the GUI.

Help?

---

### Post by Ebonhawke on 2010-02-01
After doing some reading, I tried 

*sudo apt-get install gnome-desktop*

at the prompt and got the following message

*couldn't find package gnome-desktop*

That could be a problem...

---

### Post by Ebonhawke on 2010-02-01
Further update:

- Tried reinstalling Karmic from the USB drive:  Didn't work

- Reinstalled 9.10 Distro using UNetBootin onto the USB drive:  Didn't work (same message)

- Installed 9.04 Distro on the USB drive:  Couldn't boot from the USB drive - ACP failure - then Kernel panic message.


Bueller...Bueller..Bueller....

---

