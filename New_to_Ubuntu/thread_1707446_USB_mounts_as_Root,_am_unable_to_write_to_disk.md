---
title: "USB mounts as Root, am unable to write to disk"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by marty331 on 2011-03-15
I'm very reluctant to post and beg for help.  I truly feel that I've searched the forums and have not come up with a solution that works so here I am hoping that someone out there can help.

I have a problem that when I plug in a USB drive it mounts as Root and I do not have permission to write to the disk.  In the properties tab it shows the owner as root and the group as root.   I see the message at the bottom that says "You are not the owner, so you cannot change these permissions."

Can someone help me out?  Thanks in advance.

---

### Post by fabricator4 on 2011-03-15
> **marty331 said:**
> I have a problem that when I plug in a USB drive it mounts as Root and I do not have permission to write to the disk.  In the properties tab it shows the owner as root and the group as root.   I see the message at the bottom that says "You are not the owner, so you cannot change these permissions."


What file system is the USB drive formatted in?  Is this a "pen drive" or is it an external hard drive?

Chris

---

### Post by marty331 on 2011-03-15
The filesystem is HPFS/NTFS and it is an external hard drive.  However, I have this same problem with any thumb drive that I plug in as well and most of those are FAT32.

---

### Post by fabricator4 on 2011-03-15
> **marty331 said:**
> The filesystem is HPFS/NTFS and it is an external hard drive.  However, I have this same problem with any thumb drive that I plug in as well and most of those are FAT32.

Is this while you are logged in as the original administrator user you made when you set Ubuntu up, or have you made a limited desktop user?

Chris

---

### Post by marty331 on 2011-03-15
I am logged in as the original administrator.  What else can I tell you to help figure out the issue?

---

### Post by fabricator4 on 2011-03-15
> **marty331 said:**
> I am logged in as the original administrator.  What else can I tell you to help figure out the issue?

Don't worry, we're getting closer.  :-)

Using Disk Utility and without removing the USB drive, unmount the USB drive, then mount it again.

Can you access it properly now?  It should show your username as being the owner.

Chris

---

### Post by marty331 on 2011-03-15
Genius!  The did it!  Thank you very much for your help!

So why do I have to do that now?  When I first install Ubuntu I could just plug them in and now something has changed.  Any ideas?

---

### Post by fabricator4 on 2011-03-15
> **marty331 said:**
> Genius!  The did it!  Thank you very much for your help!

So why do I have to do that now?  When I first install Ubuntu I could just plug them in and now something has changed.  Any ideas?

Something has been installed or altered that has changed how the devices are being mounted.

Check in synaptic package manager that a program called usbmount has not been installed.  There was a problem at one point where this was coming installed in a distro (10.04?) and it was causing a problem where USB devices were being mounted with root as the owner.  I seem to recall this was a topic in a bug report on launchpad.

Chris.

---

### Post by rem18 on 2011-03-18
Hi I have a similar problem
I can no longer write to me usb pendrive
I took a look at the previous advise however everytime I acess files on the drive I get a message saying document in use unknown user etc.
On other occasions I have have had a message saying that I do not have rights to write to the file.
I can open a copy if I want and save that new as written but I cannot write to the original file.
I have been over and over the the permissions but it wont let me make changes to file access when I apply the changes it just puts the setting back to "---" or tells me I am not the user.
Any ideas please
Thanks

---

### Post by weezyrider on 2011-03-18
I had this with both a USB stick and an SD card. The SD card was only used in a camera, but somehow both the external devices had INF files on them. The USB stick I know where the file came from, but on the SD card no clue.  Neither device would let me write or format. Didn't have "permission"  I ran both through the XP laptop with all protection, and let NOD32 delete what it called "trojans." I could then reformat and write to the cards in Ubuntu with no problem. 

The SD card caused a bit of trouble on the XP drive. I got the error "no disk in drive" because of that inf file. (I was transferring something from one computer to another and that file was part of the transfer) The XP drive on the desktop does not have an internet connection, so it has no security. I've always scanned everything through the other drive, which was 2K before Ubuntu. And since the card had never been anywhere but in a camera, I never scanned it. 

This is why I wanted an AV on Ubuntu. Eset just came out with a Linux version. I installed it, grabbed some operation type files from another offline XP computer, stuck the USB stick in Ubuntu and NOD32 promptly picked up those files as malicious. It also deleted them, at my request so I could now write to the USB stick and format it. So maybe Ubuntu doesn't need an AV, the other files I download sure do!   If you have other computers running other OS, and tend to use the same USB stick, you need to check what's on it. Ubuntu won't run it, but it also won't tell you why.  W

---

### Post by rem18 on 2011-03-18
It only happened a few days ago
I suspect that an update installed something.
Anyway now I can only open a ne copy of the doc and modify and save somewhere else
Its very annoying.
Any help about how to get my rights back much appreciated.
If not I will have to format the pendrive and hope that works
thanks

---

### Post by Cfossy2 on 2013-03-21
After following the advice regarding usbmount, and removing this program, I am now able to access all files and write to the disk as well.:P

---

### Post by coffeecat on 2013-03-21
Back to sleep, old thread.

---

