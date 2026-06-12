---
title: "Android Tablet???"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Feyerbrand on 2011-02-01
**FURTHER UPDATED INFO** 

10/25/2011

I am Researching Ubuntu and other Linux Distros.  I dislike the android OS on the tablet that I have.  It lacks support for full apps that I want.  So I have the specs posted below.  I have been searching the web about Embedded Linux and was wondering if there was a way to embed Linux onto this device and run Native Ubuntu (Or another similar distro to Ubuntu IE Lubuntu, Xubuntu, ETC.)

If anyone has a link, or a website hint on how to embed an OS onto a tablet that would be much appreciated.  This tablet sadly doesn't have Host USB or Bluetooth...  So it needs to either flash the OS like a Rom through the ADB interface, or it needs a native touch screen OS installed.  I know Ubuntu has touchscreen support and was hoping that I could use and Operating system I am familiar with.


**Velocity Micro Cruz T103**

```

&#8226; Full color TFT display
&#8226; 7&#8221; diagonal 16:9 800x480 screen
&#8226; Capacitive touch screen
&#8226; Android 2.2
&#8226; 512MB RAM
&#8226; 4GB AND 8GB bundled SD cards
&#8226; Supports PDF, TXT, HTML reader files
&#8226; MP3, WMA, AAC, WAV audio support
&#8226; MPEG-4, H.264, H.263, MOV, AVI video support
&#8226; JPEG, GIF, PNG, BMP image support
&#8226; 802.11n wifi
&#8226; Built in speakers
&#8226; Microphone
&#8226; Headphone jack
&#8226; Mini USB
&#8226; Li-Ion battery - up to 10+ hours of life, 24+ standby
&#8226; Dimensions: 7.5"x 4.75"x .6"
&#8226; Mips Process 800 MHZ
&#8226; 1 GB internal storage

```

Further Info from the system tab

Model Number
PT701

Firmware Version
2.2

Kernel Version
2.6.29-ga4c9897-git
root@cmserver #8

Build Number
Froyo 2.2-r1.1-a4c9897 20101202.144326

Device ID
GS10482000251DT8

---

### Post by slooksterpsv on 2011-02-01
You would need to see if someone has been able to modify the firmware to be able to install Ubuntu on it. Technically Android is Linux, it uses a modified Linux kernel. My 2.2 device uses Kernel 2.6.32 - so technically android is Linux, but it's own "distrobution" in a sense.

What kind of tablet is it?

---

### Post by Feyerbrand on 2011-02-01
well yea I know that android is a different edition of Linux, but its very limited in comparison.  I want to run apps and games that aren't limited to the android os.  

Its a 7 Velocity Micro Cruz t103.  Its nothing special but it does have some healthy specs.

---

### Post by Lucradia on 2011-02-01
> **Feyerbrand said:**
> well yea I know that android is a different edition of Linux, but its very limited in comparison.  I want to run apps and games that aren't limited to the android os.  

Its a 7 Velocity Micro Cruz t103.  Its nothing special but it does have some healthy specs.

You need to add a ppa / source by enabling the other sources option, and listing a source. Google is your friend.

---

### Post by Feyerbrand on 2011-02-01
> **Lucradia said:**
> You need to add a ppa / source by enabling the other sources option, and listing a source. Google is your friend.Is there a method to add PPA/Source Repositories on an android is it it via an emulator?

---

### Post by treesurf on 2011-02-01
You will find more information on what can and cannot be done with that tablet at the xda-developers forum, and possibly other forums.  Here is the subforum dedicated to that device:

[http://forum.xda-developers.com/forumdisplay.php?f=914](http://forum.xda-developers.com/forumdisplay.php?f=914)

---

### Post by Lucradia on 2011-02-02
> **Feyerbrand said:**
> Is there a method to add PPA/Source Repositories on an android is it it via an emulator?

If there is no other sources option, then you can't add third-party sources to your android-OS. Technically, it's a feature Google made, so it's up to the tablet makers / carriers to keep it. There is no emulator to implement it, it has to be there,.

---

### Post by Feyerbrand on 2011-06-02
I also want to know if there is an embedded OS that we can flash onto the device.  It is a MIPS processor so its making it even harder to find any Android OS mods, I just want the full capability of Linux on this tablet.

---

### Post by Feyerbrand on 2011-06-28
doing further research online I have discovered that the jz4760 MIPS processor that the tablet comes with has some support for windows XP through embedded os's.  Now I don't have a clue how to do any kind of flashing the rom onto the device since I lack the keyboard and mouse functionality with a touch screen tablet without regular USB ports... so I am stuck to the genius people out here in the Ubuntu Forums

---

### Post by Lucradia on 2011-06-28
> **Feyerbrand said:**
> doing further research online I have discovered that the jz4760 MIPS processor that the tablet comes with has some support for windows XP through embedded os's.  Now I don't have a clue how to do any kind of flashing the rom onto the device since I lack the keyboard and mouse functionality with a touch screen tablet without regular USB ports... so I am stuck to the genius people out here in the Ubuntu Forums

Well if the hardware can pair to a bluetooth device without forgetting it when installing Windows...

Get a bluetooth keyboard / mouse.

---

### Post by Feyerbrand on 2011-10-25
I updated the First post, if anyone is willing to assist me in getting Ubuntu Embedded I would be forever in your debt!

---

