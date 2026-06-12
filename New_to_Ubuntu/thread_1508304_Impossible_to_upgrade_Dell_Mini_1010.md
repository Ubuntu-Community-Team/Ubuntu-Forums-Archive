---
title: "Impossible to upgrade Dell Mini 1010?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by mnoyes on 2010-06-12
How do you upgrade a Dell mini 1010 8.04.lts lpia system to lucid? 

I can't upgrade using update manager, nor from the command line. I also can't boot from a USB stick (can't change BIOS boot order because the USB stick doesn't show up as an option)...

I'm also willing to just do a clean install of Lucid...

---

### Post by C.S.Cameron on 2010-06-12
Does your USB drive show up as a hard disk?

---

### Post by pizza-is-good on 2010-06-12
Do you have a CD drive?

How did you install it in the first place?

---

### Post by mnoyes on 2010-06-12
I installed startup manager and set it to show boot options.

With a bootable USB stick in the drive, the only options are to boot from the hard drive (the pre-installed kernel 2.6.24-24-lpia), to boot from the hard drive in recovery mode, and System Restore. No other drive shows up.

The Dell Mini 1010 came with Ubuntu 8.04 pre-installed. There is no internal CD drive.

Thanks for your help, by the way.

---

### Post by C.S.Cameron on 2010-06-13
Will bios let you select the USB stick as your first hard drive?

---

### Post by snowpine on 2010-06-14
Press '0' at boot to get the list of devices (including, hopefully, your USB).

---

### Post by sb5551 on 2010-06-14
Hey mnoyes,

Sorry, I didn't see your replay on the other thread. You need to put it onto the usb stick like you said you did. Insert the usb stick. Then restart your computer you need to hit f12 for boot option as soon as the dell screen pops up. It is only there for about half a second. It took me three times to get it when I was looking for it, but it'll say it on the bottom right corner. Then go to removable drives and hit enter. The computer will automatically look for the usb, so it needs to be plugged in. If there is a problem send me a message or I'll keep an eye for this thread.

---

### Post by mnoyes on 2010-06-16
Thanks. I was able to get the boot list, but the USB stick was not on it.

I tried using qgrubeditor -- which seems to allow me to designate which drive to boot from -- but couldn't get it set up right.

In the meantime I needed to use the computer for work, so I just restored backed up files and am using it with the Dell installed 8.0.4.2 lpia.

The Dell version of Ubuntu is also making it hard for me to install software from other repositories, for example files I need to enable a printer I bought.

Has anyone successfully installed Ubuntu 10 on a Dell mini 1010? How?

---

### Post by sb5551 on 2010-06-16
Thats weird. On my 1010, I just hit enter on the option for removable device and it booted from the usb drive. Was there anything else plugged into the computer?
 
When put ubuntu onto the usb stick did you just drag and drop the iso file to the stick or did you use a program like UnetBootin which will make the usb stick bootable?
 
Edit: If you do need to use the program Unetbootin, I think it will format the usb stick so make sure there aren't any important files on it.

---

### Post by mnoyes on 2010-06-17
That's interesting. I couldn't get it to show up at all. I used Unetbootin, too. Which version of Ubuntu 10 did you use? There are a few options: net version, live version...

I was hoping to use the netbook remix.

Also, did you have any concern about losing functionality of the Dell software?

---

### Post by sb5551 on 2010-06-17
I used the netbook remix. I have not had a problem with any hardware or software yet. When I first installed it, the wireless didn't work, but a reinstall fixed that. Just make sure you use an ethernet cable to download all the latest updates and drivers. 

Sorry, I cant help you out its hard to diagnose whats going on over the internet.

---

### Post by Perkins on 2010-06-18
Rather than spend hours trying to figure out what's up with your particular machine for why it won't boot from USB, I will suggest a few things that I did not see mentioned above:

0)  run: sudo update-manager -c
     This forces the update manager to check for a newer version.

1)  Download the alternate install ISO and use gmount-iso to mount it on /cdrom.  You should then be able to open that folder and execute cdromupgrade to upgrade your system.

2) Borrow a USB CD-ROM drive.  Most machines these days will recognise them and boot from them without too much trouble.

3)  If that doesn't work, get one of [these]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&CatId=3770") and just plug your hard drive into a different machine and do whatever you want with its contents, including doing a fresh install of whatever you like.  (Well, it won't work with Windows unless you're prepared to go to all manner of headache.  But anything else you like.)  Personally I recommend disconnecting whatever other drives are in said different machine first, just to be sure there are no accidents.  :)

---

### Post by mnoyes on 2010-06-24
Thanks for the advice. I appreciate it. For the time being, I'm going to stick with the Dell Ubuntu 8.04.2 until I have enough time to really work on it. I'm thinking of getting an external hard drive, installing Ubuntu on that, booting from it, reformatting the mini1010 and installing Ubuntu 10. Any reason that should not work, assuming I can get the mini to boot from the usb drive?

---

### Post by snowpine on 2010-06-24
> **mnoyes said:**
> Thanks for the advice. I appreciate it. For the time being, I'm going to stick with the Dell Ubuntu 8.04.2 until I have enough time to really work on it. I'm thinking of getting an external hard drive, installing Ubuntu on that, booting from it, reformatting the mini1010 and installing Ubuntu 10. Any reason that should not work, assuming I can get the mini to boot from the usb drive?

No rush to upgrade, as 8.04 will be supported through April 2011.

When the time comes to install a new version, I think you will find it easiest to [install from a USB stick]("https://help.ubuntu.com/community/Installation/FromUSBStick") or from an external USB CD-ROM drive.

---

### Post by pjman on 2010-07-30
mnoyes - Before deciding to reinstall to a newer version please read up on the issues with the GMA500 (poulsbo) which is in the Dell Mini 1010.

[http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

