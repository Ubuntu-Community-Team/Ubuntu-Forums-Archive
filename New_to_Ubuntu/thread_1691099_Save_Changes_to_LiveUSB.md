---
title: "Save Changes to LiveUSB?"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by mdclow on 2011-02-19
I have used Ubuntu 10.10 LiveCD to check out the OS. I know that any changes I make to desktop or configuration are only good for that session of LiveCD.
 
If I run LiveUSB (with flash drive) will changes be saved to the flash drive so they are visable/useable with my next use of LiveUSB?
 
Thanks you.

---

### Post by metalf8801 on 2011-02-19
Did you use the Startup Disk Creator? When using the Startup Disk Creator you should have the option specify the amount of extra space you want to use to save "documents and settings". So if you did that you should be able to save changes.

---

### Post by tea for one on 2011-02-19
> **mdclow said:**
> I have used Ubuntu 10.10 LiveCD to check out the OS. I know that any changes I make to desktop or configuration are only good for that session of LiveCD.
 
If I run LiveUSB (with flash drive) will changes be saved to the flash drive so they are visable/useable with my next use of LiveUSB?
 
Thanks you.

Boot up your Live CD
System > Administration > Startup Disk Creator

Create your USB device with or without persistence.

---

### Post by mdclow on 2011-02-19
What is persistance?

---

### Post by metalf8801 on 2011-02-19
I'm not sure how to explain it (ok I'm not a 100% sure myself) but maybe reading this will help you understand 



"Then choose the desired ubuntu .iso image, the usb device you want to use, erase the disk and set the degree of **persistence** (the slider) you need. Note that the maximum space that can be allocated for persistence is limited to 4GB (maximum file size on a FAT32 filesystem is 4GB). This limit can be overcome and is explained later on. If you do want a larger degree of persistence, set persistence to 128mb for now and continue. Hit Make Startup Disk and wait till it finishes. You are now in possession of a USB drive that can be used to run/install ubuntu on most computers. Persistence gives you the freedom to save changes, in the form of settings or files etc, during the live session and the changes are available the next time you boot via the usb drive.

To make the persistence larger (> 4GB), while still on your normal Ubuntu Installation, mount the pendrive if it is not mounted already. View the files in the FAT32 partition of the pendrive. You will now be able to see a file called casper-rw. It will be the same size as the value set on the slider. Delete this file. Open gparted :"

copied from [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I hope this helps
Dan

---

### Post by I2k4 on 2011-02-19
I've been happily running from a 4GB USB drive for some weeks - the persistence generally works to save settings between boots quite well.  After trying various versions I've found the Desktop 10.10 runs well with most user support and preinstalled software, but Lubuntu 10.10 is slick and fast, even on the slow drive.  The easiest way to install is using the step-by-step here:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

But these instructions do not list the option on the Pendrive interface to install "persistence" during the setup.  I've found it runs best to set 2GB of Persistence leaving 2GB for the OS on the 4GB drive.  Hope this is useful.

---

### Post by mdclow on 2011-02-21
Thanks for the link on persistence.  I have re-done my LiveUSB load on a 4GB flash drive.  I put in 2GB of persistence as was suggested.  The OS boots from the Flash Drive in about 30 secs which seems much faster than my recollection for the LiveCD.  PLUS I can now save any changes to the LiveUSB such as addition of a document, image, WiFi log on, desktop background, etc.
 
When I take a look at the flash drive via Win7 it shows 1GB free of 3.72GB.  I am assuming that I have that 1GB for changes and data/documents? 
 
One last question.  If I use a 8GB flash drive to what level should I set the persistence when creating a second LiveUSB?   With a response to these two questions I think we can consider this issue solved.  I have a few other questions on other related topics but they are probably better served by a new topic.
 
Thank you, very much, for your guidance.  I am enjoying this adventure into Ubuntu and slowly want to get the OS to be able to accomplish more tasks.

---

### Post by I2k4 on 2011-02-21
> **mdclow said:**
> When I take a look at the flash drive via Win7 it shows 1GB free of 3.72GB.  I am assuming that I have that 1GB for changes and data/documents? 
 
One last question.  If I use a 8GB flash drive to what level should I set the persistence when creating a second LiveUSB?

I've been experimenting since late last year, and on the 4GB drive, after trying 1GB OS and 3GB Persistence, I've found the 2 + 2 seems to give the OS a little more breathing room while enough to store the settings in the Persistence "Casper" file.  I actually found the Lubuntu install pretty functional from a 2GB USB, 1 + 1 Persistence for web browsing - but wouldn't put any demanding software like OpenOffice or GIMP on that.

I've never tried a larger (8GB) drive, but would suggest looking at the amount and demands of the software you want to run - these drives are slow for anything that reads/writes a lot.  I am looking into some faster USB drives advertised on Amazon (not USB 3 but apparently better than my cheap ones.)  

Related to performance, the other caution I have is with the lag in accessing the hard drive during the boot process, which can affect services that need the hard drive.  I have installed Dropbox, for example, on the USB, but recognition of the Dropbox folder on the hard drive is too slow for automatic start during boot.  I disabled it and start the Dropbox app manually.  

Have fun with it.

---

### Post by oldfred on 2011-02-21
If you have 8GB or more, you can do a full install. It is still somewhat slower than a hard drive due to flash & USB limits, but still usable.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

