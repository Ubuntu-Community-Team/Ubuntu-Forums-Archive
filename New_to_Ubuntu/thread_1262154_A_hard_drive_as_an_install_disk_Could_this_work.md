---
title: "A hard drive as an install disk? Could this work?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by evil_urna on 2009-09-09
I am haveing issues re installing ubuntu on my pc. It keeps locking on install and wont complete. I am wondering if it is possible to turn another hard drive into a install disk. If I could do this it would tell me if my IDE controller has something wrong with it. I cannot use a USB start up device with my motherboard (ASUS A7N8X) for it has no bootable USB support.

Also if I installed ubuntu onto the drive on another PC and then moved it over to my main PC would that be a problem? They have different chipsets, I know with windows this can be an issue?

Any help or pointers would be helpful.

---

### Post by VastOne on 2009-09-09
> **evil_urna said:**
> I am haveing issues re installing ubuntu on my pc. It keeps locking on install and wont complete. I am wondering if it is possible to turn another hard drive into a install disk. If I could do this it would tell me if my IDE controller has something wrong with it. I cannot use a USB start up device with my motherboard (ASUS A7N8X) for it has no bootable USB support.

Also if I installed ubuntu onto the drive on another PC and then moved it over to my main PC would that be a problem? They have different chipsets, I know with windows this can be an issue?

Any help or pointers would be helpful.

I have done this by creating a working version of Ubuntu that I want and when I build a new machine I simply dd the info from my current drive to the new drive and even with different chip sets and different mobo's I have had no issues. 

So you could take the hd from one drive to the other machine and you should get a boot. I have done this many times, but I deal with new equipment only, so you might have an issue with the age of the hardware.

I know it will not blow up or melt if you tried it, so fire away. And if it works, check back here on how to dd a drive to restore or create a new build.

---

### Post by evil_urna on 2009-09-09
I tried it with 9.04 last night and it went nuclear on me. Crashes left and right, it would mess up updates massively. I even caught giving me the finger I think. I am trying it now with 8.10. I hope it works

---

### Post by LewRockwell on 2009-09-09
ASUS A7N8X might be similar to this:
[http://www.driverheaven.net/reviews/asus/index.html](http://www.driverheaven.net/reviews/asus/index.html)


You should check to see that you have the latest BIOS:
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)


In our opinion that motherboard should have board level USB boot BIOS support


Looks like you might need to use the alternate install version of 9.04
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)


.

---

### Post by evil_urna on 2009-09-09
> **LewRockwell said:**
> ASUS A7N8X might be similar to this:
[http://www.driverheaven.net/reviews/asus/index.html](http://www.driverheaven.net/reviews/asus/index.html)


You should check to see that you have the latest BIOS:
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)


In our opinion that motherboard should have board level USB boot BIOS support


Looks like you might need to use the alternate install version of 9.04
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)


.


Ok I am downloading the alt installer and will try that. I just downloaded all the updates for the 8.10 drive I installed and swapped over. And they failed to install. This is the same issue I had with the 9.04 install I did yesterday. I am not sure why this is doing this. If I hammer on it and try to force the updates over and over again like last night I fear I am going to brick the OS again.

I am going to try the alt installer in about a hour when it finishes downloading.

I am also going to attempt to get a copy of what terminal says when it crashes out over here

---

### Post by evil_urna on 2009-09-09
```
Sep  9 15:43:46 scott-desktop -- MARK --
Sep  9 16:00:27 scott-desktop kernel: [ 2260.711522] dpkg[6691]: segfault at 43000014 eip 08052900 esp bff76ac8 error 6
Sep  9 16:23:46 scott-desktop -- MARK --
Sep  9 16:27:05 scott-desktop kernel: [ 3857.550056] eth1: link down.
Sep  9 16:35:33 scott-desktop kernel: [ 4365.593202] dpkg[7614]: segfault at 72737543 eip 08052900 esp bf995398 error 6
Sep  9 16:38:06 scott-desktop kernel: [ 4517.956943] apt-check[10991]: segfault at 00000047 eip b7bfa677 esp bfb36c50 error 4
Sep  9 16:58:20 scott-desktop kernel: [ 5732.194713] usb 3-4: new high speed USB device using ehci_hcd and address 2
Sep  9 16:58:21 scott-desktop kernel: [ 5732.327647] usb 3-4: configuration #1 chosen from 1 choice
Sep  9 16:58:21 scott-desktop kernel: [ 5732.430009] usbcore: registered new interface driver libusual
Sep  9 16:58:21 scott-desktop kernel: [ 5732.476681] Initializing USB Mass Storage driver...
Sep  9 16:58:21 scott-desktop kernel: [ 5732.492696] scsi2 : SCSI emulation for USB Mass Storage devices
Sep  9 16:58:21 scott-desktop kernel: [ 5732.500666] usbcore: registered new interface driver usb-storage
Sep  9 16:58:21 scott-desktop kernel: [ 5732.500678] USB Mass Storage support registered.
Sep  9 16:58:26 scott-desktop kernel: [ 5737.497530] scsi 2:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
Sep  9 16:58:26 scott-desktop kernel: [ 5737.499774] sd 2:0:0:0: [sdb] 15695871 512-byte hardware sectors (8036 MB)
Sep  9 16:58:26 scott-desktop kernel: [ 5737.500778] sd 2:0:0:0: [sdb] Write Protect is off
Sep  9 16:58:26 scott-desktop kernel: [ 5737.503509] sd 2:0:0:0: [sdb] 15695871 512-byte hardware sectors (8036 MB)
Sep  9 16:58:26 scott-desktop kernel: [ 5737.504514] sd 2:0:0:0: [sdb] Write Protect is off
Sep  9 16:58:26 scott-desktop kernel: [ 5737.504533]  sdb: sdb1
Sep  9 16:58:26 scott-desktop kernel: [ 5737.505940] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Sep  9 16:58:26 scott-desktop kernel: [ 5737.506008] sd 2:0:0:0: Attached scsi generic sg1 type 0

```

This is what i get when I try to update. I think. I pulled this from the logs.

---

### Post by halitech on 2009-09-09
are you trying to download updates somewhere else, put them on a thumbdrive and then install them once the hard drive has been installed in the original machine?

those messages are all in regards to a thumbdrive

---

### Post by woedend on 2009-09-09
If you could rip an install disk as an img file, then dd said img file to the hard drive, it should act as a bootable device and think its a live disk(similar to say, a usb thumb drive.  A flash drive is in essence structured much like a hard drive should be.  I've never tried it but i don't see why it wouldn't work.  On another note, you could grab the alternate version which includes all the packages, put them into a folder, and basically use your second hard drive as a repo by doing something similar to dpkg -i *.deb.  You would still need to get a base install on first, though.

---

### Post by evil_urna on 2009-09-09
> **halitech said:**
> are you trying to download updates somewhere else, put them on a thumbdrive and then install them once the hard drive has been installed in the original machine?

those messages are all in regards to a thumbdrive

whoops. No I am trying to use the package updater.

I just tried to run it again and here is what I got

---

### Post by halitech on 2009-09-09
just do your base install in the machine with the working cd drive, then place the drive back in the machine with no cd. Get it connected to the internet and do the updates that way.

---

### Post by evil_urna on 2009-09-09
> **halitech said:**
> just do your base install in the machine with the working cd drive, then place the drive back in the machine with no cd. Get it connected to the internet and do the updates that way.

Thats what I am doing. Where in the log should I look for the info on the Package Upgrade?


Thanks to all of you for the help so far.

---

### Post by halitech on 2009-09-09
did you download the updates to a thumbdrive or just what are you doing? when doing updates from the net, it shouldn't have anything to do with a thumbdrive or pre-downloaded files.

---

### Post by evil_urna on 2009-09-09
> **halitech said:**
> did you download the updates to a thumbdrive or just what are you doing? when doing updates from the net, it shouldn't have anything to do with a thumbdrive or pre-downloaded files.

Ignore that. Thats from when I plugged in my thumb drive to transfer the log file over

I am running the alt installer right now.

---

### Post by evil_urna on 2009-09-09
> **evil_urna said:**
> Ignore that. Thats from when I plugged in my thumb drive to transfer the log file over

I am running the alt installer right now.

SUPRISE!

It locked up at 36%, Where it normally locks up. It was trying to install "libgccl"

I am starting to think my motherboard is borked. I have tried about 5 different drives, so i dont think it is that. I am going to try a controller card now and see if is my onboard IDE controller took a nose dive.

---

### Post by LewRockwell on 2009-09-09
> **evil_urna said:**
> SUPRISE!

It locked up at 36%, Where it normally locks up. It was trying to install "libgccl"

I am starting to think my motherboard is borked. I have tried about 5 different drives, so i dont think it is that. I am going to try a controller card now and see if is my onboard IDE controller took a nose dive.

something is borked...indeed

.

---

### Post by halitech on 2009-09-09
try a different cable as well

---

### Post by theozzlives on 2009-09-09
I know for a fact that you can mount an .iso as a CD drive. It's booting that's tricky. I'm sure it can be done but not without a lot of research and googling.

---

### Post by evil_urna on 2009-09-09
> **LewRockwell said:**
> something is borked...indeed

.

I concur.

I have tried a different cable. On a windows install, sometimes you need to have a driver floppy for the controllers to work properly. Could this be an issue here? Also dumping the CD onto a spare HD gives me a GRUB 22 Error

---

### Post by halitech on 2009-09-09
unless you have a really strange machine that doesn't comply to any standards at all, the kernel should be taking care of things. I'd be suspecting the cable or the controller myself.

---

### Post by theozzlives on 2009-09-09
I wonder if creating a rescue floppy in Startup Manager could allow you to mount an .ISO on a hard drive (sdb) and install on sda?

---

### Post by evil_urna on 2009-09-09
> **theozzlives said:**
> I wonder if creating a rescue floppy in Startup Manager could allow you to mount an .ISO on a hard drive (sdb) and install on sda?

at this point I am willing to try anything

---

### Post by theozzlives on 2009-09-09
I also read in a ubuntu wiki where you could install off an internet connection.

---

### Post by evil_urna on 2009-09-09
here is something that bothers me. It will format and partition the drives no problem. It only freaks out and locks up when it is installing the OS, If it was a faulty controller then would it not be unable to see the drives, and even if it could would it not then fail to access them?

---

### Post by theozzlives on 2009-09-09
Have you ran a mid5sum on the ISO? Tried a new burn? Run CD check from the main menu?

---

### Post by evil_urna on 2009-09-09
> **theozzlives said:**
> Have you ran a mid5sum on the ISO? Tried a new burn? Run CD check from the main menu?

I have tried two different burns of 9.04 and 8.10. and done cd checks. I just ran an md5sum on the ISO of the alternate install disk and it came up good.

---

### Post by theozzlives on 2009-09-09
Unfortunately I run a business and had an emergency come along. Hopefully someone will pick up where I left off. Sorry.

---

### Post by evil_urna on 2009-09-09
I got the alternate install disk to work. I let the installer partition the drive itself instead of doing it manually. The problem is now that when it tried to install software sources it failed. I did have an internet connection and if I skip that part, the install completes, but I do not have a GUI. I get a text terminal and if I use the "sudo /etc/init.d/gdm start, gnome does not start.

Any ideas now?

---

### Post by evil_urna on 2009-09-09
ok I tried a reinstall to see if would find the updates. And no. It came up with a red screen and a grey box that says:

              [!!] Select and Install software
                   Installation step failed
         an installation step failed. You can try to run the       failing item again from the menu, or skip and choose something else. The failing step is: Select and install software

It gives me a menu that lets me restart any part of the install or skip steps. If I retry it asks me to choose no automatic updates install automatically, or manage with Landscape. 

Google tells me landscape is something that is not for me. Last time I chose automatically and it gave me the terminal screen with no option to open gnome. 

any ideas?

---

### Post by evil_urna on 2009-09-10
Well I replaced My Motherboard. that seemed to do the trick

Thanks for everyone's help

---

