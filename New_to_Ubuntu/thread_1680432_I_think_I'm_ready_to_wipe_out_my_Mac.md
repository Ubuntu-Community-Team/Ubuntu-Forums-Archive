---
title: "I think I'm ready to wipe out my Mac"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by hillbillyhotrod on 2011-02-02
Hello all, I went and bought a used laptop to try out Ubuntu a few weeks ago and I love it. I have always loved Macs but I think I'm ready to cut the cord. I have a Quicksilver 2002 dual 1 Ghz, 1.12 gb of ram. A 38gb and a 56gb hard drive and want to wipe it out completely.  First hurdle I'm going to have to cross is that it doesn't read dvds don't know why but it doesn't. Also I've read that it is a big pain to put Ubuntu into these, and seeing as how I'm probably going to have to do it via thumb drive I don't even know where to start. Any help would be appreciated.
Sláinte
Russ

---

### Post by Ziplock on 2011-02-02
> Mac

We would encourage Mac users to download Ubuntu Desktop Edition by burning a CD for the time being. But if you would prefer to use a USB, please follow the instructions below.
 
Note: this procedure requires an .img file that you will be required to create from the .iso file you download.
 
TIP: Drag and Drop a file from Finder to Terminal to 'paste' the full path without typing and risking type errors.
 
Download the desired file

Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)

Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)

Note: OS X tends to put the .dmg ending on the output file automatically.

Run diskutil list to get the current list of devices

Insert your flash media

Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)

Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)

Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
Using /dev/rdisk instead of /dev/disk may be faster.
If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.

Run diskutil eject/dev/diskN and remove your flash media when the command completes

Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick

These are the instructions found on the download page for installing Ubuntu via thumb-drive with Mac.

---

### Post by hillbillyhotrod on 2011-02-02
See the problem with that is that right after I start reading it I get confused. My question is more can I do a wipe and install from a USB and how to go about it. I know its not gonna be fun because it's only 1.1 but i really think i want to do it.

---

### Post by Carson5696 on 2011-02-02
What do you mean by 1.1
And yes you can most definitely wipe your Mac when installing, Remember Ubuntu is made for you to start over.

STEP 1: Obtain the installation medium |
You can download a Live CD to see what Ubuntu will be like or an install CD to install it. NOTE: Live CD's are a lot slower since they keep loading things off of the CD.
After you've downloaded it. Burn the image onto a CD using your favorite app. I recommend Disk Utility or Roxio's Toast. 

STEP 2: Installing UBUNTU
After you've burned it, keep the CD it and reboot and hold the C key down to boot from the CD. When it load, keep the defaults and hit enter. Choose your language, hit enter. It'll ask you how you want to partition your hard drive. If you know these settings set them. Otherwise just wipe out the entire hard drive and whatever's left you'll have for free space. The next thing it'll prompt you for a bit is your first user and your password. NOTE: The password does not show up, so don't freak out if you start typing characters and nothing appears. Just type in your password and hit enter, verify it, hit enter. The installation will continue installing stuff and finally reboot. When it reboots it'll setup everything. Don't hold down the C key to boot from the CD, just let the setting up continue.

Your Welcome ;)

---

### Post by hillbillyhotrod on 2011-02-02
Thanks, I'm using Ubuntu to download it for my Mac because I cant get it to read DVD's for some reason so I'm going to try to install it with a USB and I was referring to the old and slow USB when I said 1.1

---

### Post by Carson5696 on 2011-02-02
Oh, Your Welcome always glad to help!:p

---

### Post by rg4w on 2011-02-02
If memory serves, your Mac model uses a PowerPC chip, before Apple switched to Intel.  If that's the case, you'll want to get the PowerPC build of Ubuntu, which can be downloaded here:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by hillbillyhotrod on 2011-02-02
good thing you mentioned that because i totally forgot about the different version

---

### Post by hillbillyhotrod on 2011-02-02
Now the question is going to be getting it from my Compaq nc6400 to a thumb drive to the Mac

---

### Post by hillbillyhotrod on 2011-02-03
Ok, I have the iso file on my desk top and I'm trying to make the start up disk using a thumb drive but it doesn't pull it up

---

