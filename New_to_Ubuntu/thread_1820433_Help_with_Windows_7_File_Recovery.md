---
title: "Help with Windows 7 File Recovery"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by squirrelpirate on 2011-08-07
Hello,

Last night I experienced some problems with my laptop. I run Windows 7, and I think I picked up a virus or malware somehow. There was a fake Windows box that popped up and started messing up my desktop. As I was trying to get my anti-virus software in order, my shortcuts started to disappear off of my desktop. I tried to shut down the computer as quickly as possible to stop whatever was happening. I restarted and my program shortcuts came back, but I cannot see any documents or pictures in My Documents, etc.

I've heard and read some things about Ubuntu, so I downloaded it today (v 11.04). I burned the CD and tried to run the CD, but I received an error message. I installed Ubuntu parallel to Windows 7 (which, from some of the posts I've read on here, may not have been the best idea). I'm completely new to Ubuntu/Linux and am trying to read as much as I can to familiarize myself.

I have looked at the two howtogeek.com articles referenced here. I could not launch the Live CD, so I could not follow the first article (on backing up files from a dead computer). I tried following the "Recover Data Like a Forensics Expert" article, but got an error while trying to reload the Package Manager. The error said that I could not download all repository indexes, that it failed to fetch them from my CD-rom, and to use apt-cdrom for something I don't understand.

When I've run my computer in Windows 7, I've had difficulty with Java/Flash, etc. I think there's something that's missing that's causing these problems. I don't want to be the new guy who asks for help in a panic, but I'm just not able to follow the most common solutions. Any help would be greatly appreciated. Let me know if you need any more information.

Thank you!!

---

### Post by nns2006 on 2011-08-08
> **squirrelpirate said:**
> Hello,

Last night I experienced some problems with my laptop. I run Windows 7, and I think I picked up a virus or malware somehow. There was a fake Windows box that popped up and started messing up my desktop. As I was trying to get my anti-virus software in order, my shortcuts started to disappear off of my desktop. I tried to shut down the computer as quickly as possible to stop whatever was happening. I restarted and my program shortcuts came back, but I cannot see any documents or pictures in My Documents, etc.

I've heard and read some things about Ubuntu, so I downloaded it today (v 11.04). I burned the CD and tried to run the CD, but I received an error message. I installed Ubuntu parallel to Windows 7 (which, from some of the posts I've read on here, may not have been the best idea). I'm completely new to Ubuntu/Linux and am trying to read as much as I can to familiarize myself.

I have looked at the two howtogeek.com articles referenced here. I could not launch the Live CD, so I could not follow the first article (on backing up files from a dead computer). I tried following the "Recover Data Like a Forensics Expert" article, but got an error while trying to reload the Package Manager. The error said that I could not download all repository indexes, that it failed to fetch them from my CD-rom, and to use apt-cdrom for something I don't understand.

When I've run my computer in Windows 7, I've had difficulty with Java/Flash, etc. I think there's something that's missing that's causing these problems. I don't want to be the new guy who asks for help in a panic, but I'm just not able to follow the most common solutions. Any help would be greatly appreciated. Let me know if you need any more information.

Thank you!!
I am not expert,but as a general advice I suggest this. 

First advice: Back up your data before messing up with your computer :p .Now coming to your problem
1. In windows there is an option for restoring. Do it for a previous day and back up all data first. 
2. you are not able to boot from Live CD - why is that? You should be. Can you check this in Other machine?

---

### Post by carverj on 2011-08-08
> I've heard and read some things about Ubuntu, so I downloaded it today (v 11.04). I burned the CD and tried to run the CD, but I received an error message. 

Do you remember the error message? When you pop in the CD, if your BIOS has been setup to boot from CD first in the order, the operating system should load from disk. Assuming you have downloaded and run the appropriate version of Ubuntu for your system.

---

### Post by sikander3786 on 2011-08-08
Yeah, first of all download Ubuntu i386, 32-bit (as it runs fine on 64-bit too) via Torrent preferably:

[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

Burn it to disk at the lowest possible speeds or a USB:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

Set your Bios to boot from CD-ROM or USB whichever applicable and boot it. You can try recovering your files from the Live environment without even installing Ubuntu. You can try photorec:

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by Mark Phelps on 2011-08-08
Just to clear up what is obviously a COMMON misconception -- MS Windows does NOT have an option for resetting the PC back to a previous date.  What it does have is an option for overwriting current versions of system files and the Registry with older versions.  THAT is what System Restore does.

Unfortunately, that does not restore older versions of data files.

If shadow copy is turned on, you may be able to restore older versions that way -- but you have to do it manually for each and every file.

---

