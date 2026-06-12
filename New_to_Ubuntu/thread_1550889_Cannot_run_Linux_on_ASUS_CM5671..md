---
title: "Cannot run Linux on ASUS CM5671."
date: 2010-08-11
forum: New to Ubuntu
---

### Post by NatalieEGH on 2010-08-11
I bought this computer yesterday and downloaded Ubuntu 10.4 both the 32 and 64 bit versions.  I burned both iso images.  I changed the boot sequence to do the DVD drive first.  I then tried booting off the disks.  They both stop before Ubuntu starts.  I got an old Ubuntu disk and it gets farther.  It will get me to where I can do things like kill and ps and a whole list of commands but it does not boot to where the orange screen appears and you can use the gui.

The computer is an ASUS Essentio Desktop (CM5671).  It has a dual core Intel 64 bit processor (E5500 dual core at 2803MHz).  It has 4GB memory.  It has an Intel® Graphics Media Accelerator X4500 (G45/G43 Express Chipset).  It is one of those everything integrated on the motherboard systems.

Can anyone provide suggestions.  I have a LOT of parts from prior systems including an EGA nVidia GT7800 video card (I know video is sometimes a problem).  


Any help would greatly be welcome as I am signed up for a course in Linux starting Monday.  I was assured by the people at Best Buy that the system ran Linux before I bought it.

My e-mail is [EMAIL="talia_egh@yahoo.com"]talia_egh@yahoo.com[/EMAIL].

---

### Post by lkraemer on 2010-08-11
My first thought would be for you to VERIFY the MD5SUM or SHA256 of each
of the downloaded ISO's.  If these VERIFY Correctly, then I'd suggest
trying to burn another copy on CDRW and burn it at the slowest speed,
and as Disk at Once (DAO).  Then try that CDRW on a couple of computers
to test the LiveCD.  That way you know what it does on several Computers.
Hopefully it will work on your new system.  (I use K3B since it does
the MD5SUM of the the ISO.  Most are now converting to SHA256)

I assume you have Windows XX installed and probably are wanting to make a
Dual Boot system.  If you are going to blow away Windows, and are making a
fresh install, then you may try the Alternate Install CD for Ubuntu.
But it does an INSTALL Versus LiveCD, and uses text mode.

Another option would be to get a New Hard Drive, stick it in another system,
install Ubuntu, and then stick this drive into your new system.
But, that assumes you have that capability.
 
Good Dual Boot Site:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

lk

---

### Post by NatalieEGH on 2010-08-11
The Ubuntu 10.4 disk that I was trying to use on this computer worked on a Dell Optiplex GX270.  I even got onto the internet.  Both systems have Intel chips for the CPU though this one is part of much newer series.  

I tried putting in a video card.  It did not seem to recognize it.  As it kept sending the signal to the integrated video.  The bios had setting for the video under Northbridge.  I tried all 4 settings.  They were like PCI/PEG, PEG/PCI (original) and two others I cannot remember.

The biggest problem with the optiplex is it was given to me after I was burglarized by someone as something they just had laying around and had basically abandoned 2 years ago.  I cannot seem to get it to recognize a hard drive.  I have tried putting in good drives from my Windows 95 (Pentium Pro 1 GB disk) and Windows 3.11 (i486 250MB disk) machine.  It does not see them.

---

### Post by NatalieEGH on 2010-08-11
Oh, actually after verifying it was working good, I was going to install VMWare and basically ignore the base OS except for booting up.  Put something like deep-freeze on it so it could not be trashed and not even bother with applying updates.

---

### Post by waynefoutz on 2010-08-11
the old dell probably has a bad hard drive controller. 

on the Asus, if you are booting into a blank screen, which is a common problem with older video cards on this version of Ubuntu, follow this guide, see if it helps.


[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")


If that doesn't work, try live booting into another distro like PCLinuxOS (I choose that one because it seems to run on everything I try it on,) and see if it's Ubuntu or your hardware.

---

### Post by lkraemer on 2010-08-12
Yes, I forgot about trying the Boot Cheatcodes.  That might get it booting.

Ditto on trying PCLinuxOS........

If the Controller is defective on your older Dell, you could always buy
a PCI Controller Card for the IDE Drive, and turn "OFF" the one in the BIOS.
That should get it booting, assuming the 80 conductor IDE Cable is good, and
the drive is jumpered correctly for Master/Slave or Single Drive (typically no jumper),
and located at the correct plug on the IDE Cable.  If your BIOS
doesn't see the Hard Drive, there is no sense trying to continue.

lk

---

### Post by pingjocky on 2010-08-12
Any luck? Im in the same boat.  I just bought this Asus and 10.10 alpha 2 works but alpha 3 has a issue with the i915 drivers.

---

### Post by NatalieEGH on 2010-09-09
I apologize for taking so long posting this.  I have so many accounts all with different passwords.  Usually it is easy to find how to get it reset and/or sent to you again. 

I could not find anyway to run Linux as the operating system for the computer, but I DID FIND A WAY TO RUN LINUX.

I am using VMWare's VMPlayer.  That is FREE software from VMWare, at least at present a subsidiary of EMC (a fortune 500 company in business for 28 years, and a major player in the mini-computer/mainframe market).

The graphics and sound are not that great, but that is because of the default graphics and sound drivers.  If you can find a graphics or sound driver for your hardware that runs under Linux it will work, I have been told.  Unfortunately neither product built into my motherboard has such.  

Off topic --
I have tried using another video card (it does have a pci-e 16x slot) but I could not seem to get it to work, the video kept going to the integrated video even though I could swear, I disabled that in the bios.) but have had no luck there, I want to warn that it might not use another video card.

---

### Post by procco on 2010-09-09
Not sure if this will solve your problem but I just spent the last 5 hours trying to get Ubuntu 10.04 to run on a Gateway ZX6900 (23" touchscreen, Intel GMA X4500HD integrated graphics). Every time I booted (USB key, CD) I would get a black screen.
Here is how I fixed it:
When you boot you need to add "nomodeset" after "quiet splash" in the boot options (depending on your boot media you can press F6 for boot options or hold shift to see the grub menu, press e to edit and add nomodest as shown below):
```
RecordFail
infmod ext2
set root=[hd0,6]
Linux/boot/vmlinuz-2.6.32-21-generic root=UUID=f1030290-8220-455b-fd4\-6d6b43b6d6c0 ro  quiet splash nomodeset
iniprd /boot/iniprd.img-2.6.32-21-generic
```Hit ctrl-x to boot and you should be okay.
The system booted into low graphics mode and did the following to fix that:
Install the latest Intel drivers and the latest kernel.  Instructions can be found here:
[HTML]http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx[/HTML]After rebooting everything worked - including the touchscreen.

---

### Post by crowderd on 2010-09-15
I have this same computer and can verify that the above post was my solution. When I tried to install I would get the splash screen followed by alot of random text... then froze. I restarted and pressed shift when I saw the splash screen (one with keyboard and human) and pressed F6 for boot options and selected nomodeset. After that it installed perfectly. On every boot it was doing the same so I had to edit the command as explained in above and add nomodeset again. Not having problems with graphics but working great now.  I have tried this with 10.04 (32bit and 64bit) and 10.10 BETA (32bit)

---

