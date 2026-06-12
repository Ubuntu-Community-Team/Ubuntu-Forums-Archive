---
title: "Virtual Box?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Bunnies on 2010-09-21
I cannot seem to get my VirtualBox working. I keep getting the error displayed below - has anyone else gotten this? If so, what can be done about it?

'FATAL: Could not read from the boot medium! System halted.'

p, li { white-space: pre-wrap; }    General
   Name:
   Win7
   OS Type:
   Windows 7
 p, li { white-space: pre-wrap; }    [IMG]http://ubuntuforums.org/:/machine_16px.png[/IMG]
  General
   Name:
   Win7
   OS Type:
   Windows 7
    
   [IMG]http://ubuntuforums.org/:/chipset_16px.png[/IMG]
  System
   Base Memory:
   512 MB
   Processor(s):
   1
   Boot Order:
   Floppy, CD/DVD-ROM, Hard Disk, Network
   VT-x/AMD-V:
   Enabled
   Nested Paging:
   Enabled
    
   [IMG]http://ubuntuforums.org/:/vrdp_16px.png[/IMG]
  Display
   Video Memory:
   28 MB
   3D Acceleration:
   Enabled
   2D Video Acceleration:
   Enabled
    
   [IMG]http://ubuntuforums.org/:/attachment_16px.png[/IMG]
  Storage
   IDE Controller
       IDE Primary Master:
   Win7.vdi (Normal, 20.00 GB)
     IDE Secondary Master (CD/DVD):
   Adobe Photoshop CS4 Extended.iso (661.83 MB)
     IDE Primary Slave (CD/DVD):
   Host Drive TSSTcorp CDDVDW TS-L633C (sr0)
     IDE Secondary Slave:
   NewHardDisk1.vdi (Normal, 2.00 GB)
   Floppy Controller
       Floppy Device 0:
   Empty
    
   [IMG]http://ubuntuforums.org/:/sound_16px.png[/IMG]
  Audio
   Host Driver:
   PulseAudio
   Controller:
   ICH AC97
    
   [IMG]http://ubuntuforums.org/:/nw_16px.png[/IMG]
  Network
   Adapter 1:
   Intel PRO/1000 MT Desktop (Internal network, 'intnet')
    
   [IMG]http://ubuntuforums.org/:/serial_port_16px.png[/IMG]
  Serial Ports
   Port 1:
   COM1, Disconnected
    
   [IMG]http://ubuntuforums.org/:/shared_folder_16px.png[/IMG]
  Shared Folders

---

### Post by bradleypariah on 2010-09-21
This may not be very helpful, but have you tried to do the installation over again?  It might have just been a bunk install.
Did you try to install a Windows 7 x64 onto an x86 Linux Virtual Machine?

---

### Post by Bunnies on 2010-09-21
Not the 64bit, no. I'll retry installing it and report the results.

---

### Post by Bunnies on 2010-09-21
Same error. :/

---

### Post by bradleypariah on 2010-09-21
That's odd.... how were you able to complete the install in under two minutes?
Something's not working correctly.
Is Windows saying that the installation has completed?
If not, how far does it get?

---

### Post by perspectoff on 2010-09-21
Do you have the Adobe Photoshop .iso set as your virtual CD drive?

It will try to boot from that if you do and give you that error.

Make sure you have the CD drive set to be your actual CD drive, not the .iso.

---

### Post by Bunnies on 2010-09-21
> **perspectoff said:**
> Do you have the Adobe Photoshop .iso set as your virtual CD drive?

It will try to boot from that if you do and give you that error.

Make sure you have the CD drive set to be your actual CD drive, not the .iso.

I am using Ubuntu, atm, and reinstalled the Virtualbox from the Synaptics Package Manager.

I tried to use a disc, but I'm not sure if I should have something already on the disc to run it, or if it should be a blank CD?

---

### Post by waynefoutz on 2010-09-21
try disabling VT-x/AMD-V. That's usually the fix.

---

### Post by Bunnies on 2010-09-21
Same error. Do I need Win7 on a disc to boot from, using this virtual box?

---

### Post by wilee-nilee on 2010-09-21
Exstract to a ISO and use it, and turn up this. 
Display
Video Memory:
28 MB

To 128, it just gives more available it is not all used but it runs much better.

So we are assuming here that when you hit the start and get the error you look in the top panel to make sure the win dvd is checked.

I always use a ISO so I'm not familiar with using a hard copy to load Vbox.

---

### Post by uRock on 2010-09-21
Is your Windows 7 a system restore disk or directly from MS? If it is your machine's restore disk, then it will not work with VBox.

---

