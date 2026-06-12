---
title: "Another iPhone question..."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by gregtheCdn on 2011-06-07
Hi everyone...I post this thread out of pure desperation! I have been searching forums for weeks and even asked my Linux-guru buddy to help but to no avail! Please forgive this thread if it is a repost, but as I have tried several other threads, I suspect my problem is unique.

The problem:

As recently as 3 months ago, I was able to connect my iPhone to my laptop and add/remove music perfectly using rythmbox. This has all changed now. I cannot transfer a single track without error messages and many times I get error messages when connecting my iphone to the laptop.

What I am using:

1) Dell XPS M1330 Laptop
2) iPhone 3GS running ios 4.3.1
3) Standard iphone cable (have tried several different cables)

What error messages am I getting:

1) "Error transferring track - Unhandled Apple File Control error (2)" (I get this in Rythmbox when I attempt to transfer tracks)

2) "Unable to mount Greg&#8217;s iPhone - Unhandled Lockdown error (-5)" (I get this sometimes when I plug the iphone in the laptop)

3) I also used to get a "dbus error when pluggin it in, but this seems to have disappeared) 

4) "Error Transferring Track - Error while getting peer-to-peer dbus connection: The name :1.215 was not provided by any .service files" (I get this sometimes when trying to transfer tracks in rythmbox)

This is my lsusb output:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 013: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 012: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 011: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 010: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 05ac:1294 Apple, Inc. iPhone 3GS
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Please please please help me...Let me know what other info you need and I'll do my best to answer. I am a newb at this, so I'm hoping some of you linux-geniuses can help me :-)

Thanks,

Greg

---

### Post by wolfen69 on 2011-06-07
Have you tried using gtkpod for tranferring stuff? Also, make sure you have ifuse installed.

---

### Post by gregtheCdn on 2011-06-07
> **wolfen69 said:**
> Have you tried using gtkpod for tranferring stuff? Also, make sure you have ifuse installed.

I have tried gtkpod and have ifuse installed with the most recent update. I also tried running Vbox with winXP and itunes, but once again, the iPhone is not recognized. This is what is making me think it is a usb mounting issue, I just don't know what specifically.

If any of you awesome peeps can tell me the magic spell to type into Terminal to find the problem, that would be much appreciated.

TIA

G

---

### Post by jeff.biggeek02 on 2011-11-13
I had a very similar error, and this fixed my problem.

[http://fuelledbykrawu.wordpress.com/2011/10/29/how-to-fix-unhandled-error-lockdown-in-ubuntu-while-attempting-to-mount-an-ios5-device/](http://fuelledbykrawu.wordpress.com/2011/10/29/how-to-fix-unhandled-error-lockdown-in-ubuntu-while-attempting-to-mount-an-ios5-device/)

The magic appears to be in a utility called idevicepair, which is part of libmobiledevice-utils.  Unpairing and pairing the iphone caused nautilus to decide it wanted to mount my iPhone 3GS with IOS 5.0.1.

---

### Post by lolpenguin on 2011-11-14
You can run some versions of iTunes in Wine. For a list of the versions that work, [http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=62&sAction=view&sTitle=View+Developer]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=62&sAction=view&sTitle=View+Developer")

---

