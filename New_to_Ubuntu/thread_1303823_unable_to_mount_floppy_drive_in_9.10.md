---
title: "unable to mount floppy drive in 9.10"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by shadow120 on 2009-10-28
im trying to get my floppy drive to mount it will not mount on its own from under places.  when i try to mount it in the terminal i keep getting an error "Unable to mount location No media in the drive".  also when i look under /media it is not listed.  from what ive googled this seems to be the problem but i havent found how to fix it.  am i on the right track here.  any suggestions would be appreciated thanks

---

### Post by mikilion on 2009-10-30
It is a bug:
[https://bugs.launchpad.net/ubuntu/+bug/272970](https://bugs.launchpad.net/ubuntu/+bug/272970)

---

### Post by LarryMi on 2009-10-31
> **shadow120 said:**
> im trying to get my floppy drive to mount it will not mount on its own from under places.  when i try to mount it in the terminal i keep getting an error "Unable to mount location No media in the drive".  also when i look under /media it is not listed.  from what ive googled this seems to be the problem but i havent found how to fix it.  am i on the right track here.  any suggestions would be appreciated thanks

We have the same problem.  What we are doing is opening the terminal and running the command" mount /dev/fd0  After we do, an icon is displayed on the desktop, then we can use Nautilus as usual.

---

### Post by bwallum on 2009-11-01
This bug is back in Karmic.

How can I get the 'Floppy Drive' (listed in Places) to show me the contents of a floppy disk?

---

### Post by kevinpugh on 2009-11-19
I have the same problem with Karmic. Nautilus will not mount the floppy. Even from command line the mount does not always allow access to the floppy from nautilus.
 
PcLinuxOS, Puppy, DSl and Jaunty all happily work with the same hardware.

---

### Post by LarryMi on 2009-11-22
Just checking to see if the floppy issue was fixed.  Apparently not.

I really needed my drive (in addition to other issues), so I made the switch last week to Mandriva.  Everything works perfectly!

In addition to my floppy, I had problems with my Blu-ray and viewing the properties of some video's.  These have all been reported as bugs and I don't know why they work in Mandriva, but they do.  Skype is exceptional with Mandriva too!

It took a few days gathering experience, but it has worked out for me.  Mandrivia is truly exceptional!

I'd like to thank the [HowtoForge]("http://www.howtoforge.com/the-perfect-desktop-mandriva-one-2010.0-with-gnome") for there wonderful tutorial!

---

### Post by Tonyr63 on 2010-01-28
Hi
 
This is a serious bug that also affects my system.  Has a fix for this been released?
 
In addition my CR ROM reads data disks fine however if you load a music disk it unmounts and dissappears from Places only to immediately reappear when the disk is ejected.
 
How do I resolve these problems with core input devices?

---

### Post by bwallum on 2010-01-28
I agree, this is a serious issue that the devs consistently ignore. There is a workaround while you beat the drum in [Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/441835")

On the very top panel right click then left click to select 'add to panel'.
Select 'Custom Application Launcher', press the Add button

Set the following fields:-
Type: Application in Terminal
Name: Mount floppy drive
Command: sudo mount /dev/fd0/ media/floppy0 -o user
Comment: Use this short cut to mount the floppy drive

Press OK and a new launcher icon should appear in the top panel.

You can repeat the process to set up a launcher to demount the drive. In this case you could use:

Type: Application in Terminal
Name: Unmount floppy drive
Command: sudo umount /dev/fd0
Comment: Use this short cut to unmount the floppy drive

Hope that helps.

EDIT:
You can 'prettify the icons'. Right click on the default 'spring' icon and select properties. The 'Launcher Properties' window will appear. Left click on the icon and a 'Browse icons' window appears. You could try:

/usr/share/icons/gnome/24x24/devices/gtk-floppy.png

to mount and 

/usr/share/icons/oxygen/22x22/devices/media-floppy.png

to unmount.

Plenty to choose from, note the pixel size indicated in the path.

EDIT
You can now find a 'standard' Disk Mounter to put in your top panel. Right click on the top panel (or bottom one if you prefer), left click 'Add to Panel', scroll down to find Disk Mounter, double click it and it will appear on your panel. To get the floppy to show, place a floppy disk into your floppy drive, choose 'Places', left click on Floppy Drive (the drive gets rescanned to detect media) then use your top panel Disk Mounter to mount and open the floppy disk.

To remove any home made mounter in the top panel, right click on the item and choose 'Remove from Panel'

---

### Post by kevinpugh on 2011-02-14
Ubuntu 10.04 also fails to mount the floppy.

What is the work round in words of less than one syllable please ...

KevinPugh

---

