---
title: "How do I clone the Hard Drive on Dell Mini 9"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by DougM1 on 2009-02-20
I am attempting to upgrade my Dell Mini 9 with a 32G Runcore SSD. How do I clone my existing hard drive onto the new drive? The new SSD came with a USB cable and it downloads Acronis True Image software. Unfortunately it is for Windows only. What are my options? The instructions need to be basic as I am a true Absolute Beginner.

---

### Post by LowSky on 2009-02-20
look around the net. One of the best is Norton Ghost, but I assume there are open source verisons availible. Here are 3 PI found in a matter of seconds

[http://selfimage.excelcia.org/](http://selfimage.excelcia.org/)

[http://sourceforge.net/projects/freeghost/](http://sourceforge.net/projects/freeghost/)

[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by DougM1 on 2009-02-20
As I stated previously I am an absolute beginner. What is a PI?

I tried the download of Self Image and the exe file does absolutely nothing, same as the True Image that came on the hard drive. I am running Ubuntu, so I think that is why they don't run.

I hope there is help out there somewhere!

---

### Post by stchman on 2009-02-20
> **DougM1 said:**
> I am attempting to upgrade my Dell Mini 9 with a 32G Runcore SSD. How do I clone my existing hard drive onto the new drive? The new SSD came with a USB cable and it downloads Acronis True Image software. Unfortunately it is for Windows only. What are my options? The instructions need to be basic as I am a true Absolute Beginner.

Use the full blown gparted.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Probably the best free hard drive cloning software out there.

---

### Post by DougM1 on 2009-02-20
I did as you said and installed as per instructions in the documentation provided. Now, how do I get the application to run? There is no icon nor is it found in Applications.

---

### Post by alenis on 2009-02-20
open a terminal, then
```
sudo gparted
```

---

### Post by bear2 on 2009-02-20
I found the tool you get at [www.clonezilla.org](www.clonezilla.org) to work great.
I tested it on an ubuntu 8.04 desktop machine i had built.
The system had two hard drives in it. I set aside a partition on the second drive for doing a "Disk to Imagefile" dump. I made some changes to the system and then did a restore and it came back intact.

---

### Post by bear2 on 2009-02-21
I found some notes i had on how i used the clonezilla (free download) tool:

[Creating an Image Dump of your Linux Machine OS Drive]

It is assumed you have installed a secondary internal hard drive. In our example machine we have an 80Gb OS drive and an 80Gb  secondary drive.
In ubuntu, we can use the GPARTED partition editor to create a 30Gb partition on drive sdb1 and format it with the EXT3 file system.
To get the clonezilla-live download iso file, go to [http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/)
Click on the link for ‘stable branch iso file’; then on whatever the file link happens to be such as: 
This example is about a 92Mb iso file.  Once downloaded, burn image to a cd.
Reboot your linux box using the clonezilla cd.
The sequence of choices made were:
English &#8730;
Don’t touch keymap &#8730;
Start clonezilla &#8730;
Device-image &#8730;
Local device &#8730;
Select the “b” hard drive to use for mounting the “/home/partimage” folder on.  Eg. hdb1 or sdb1.
Savedisk
[*] –c  client waits for confirmation before cloning
-z1   use gzip compression
Go with the default image file name which is based on the current date and time.
Example file name might be: 2008-06-27-16-img
Source disk to save an image of: hda  (the “a” drive).
A confirmation message appears that you are about to begin a clone of :
Hda1 to /home/partimag/ 2008-06-27-16-img
Once you say ‘y’, cloning image dump begins with a %progress counter at bottom of screen.
A message is display once “finished”.
Now hit the option to reboot.
You will be prompted to remove the clonezilla cdrom during the boot.
In the OS you can verify now that there is a new folder present:
Go to Places, Computer, dblclick on the “34 Gb volume:disk” icon; this is the partition on second hd you created at very beginning.
The folder is now visible that is named  “2008-06-27-16-img”.
In it are seven files which would be used to re-image the OS drive in the event you needed it. (works just like the "disk from image" in ghost).

NOTE: This backup/restore tool works MUCH faster than ghost!! And it doesnt cost you

---

### Post by DougM1 on 2009-02-21
I have a Dell Mini 9 - no CD drive. I managed to clone / copy my old SSD to the new SSD. Upon installing it in the machine and attempting to boot it hangs and on the screen it says "GRUB". What do I do now?

---

### Post by mrbobhcrhs on 2009-03-08
> **DougM1 said:**
> I have a Dell Mini 9 - no CD drive. I managed to clone / copy my old SSD to the new SSD. Upon installing it in the machine and attempting to boot it hangs and on the screen it says "GRUB". What do I do now?

If i remember right you can boot in to a live cd d(or usb) mount the drive and do a reinstall of grub.  

As for DougM1 I copied the windows xp install using a bootable usb key with norton ghost on it (all you need is ghost.exe)  now that is a windows based program.  I have done it also before off of a live cd and useing partimage which is like ghost.

---

