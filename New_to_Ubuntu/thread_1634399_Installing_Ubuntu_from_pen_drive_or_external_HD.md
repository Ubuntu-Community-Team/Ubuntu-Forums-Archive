---
title: "Installing Ubuntu from pen drive or external HD"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by Katana24 on 2010-11-30
Hi - i want to install the latest version of Ubuntu onto my desktop PC. I have downloaded the ubuntu ISO from the site and saved it to a pen drive and external HD. How would I go about installing it from the storage devices? The desktop doesn't have internet access so this is my only option :P

---

### Post by thatguruguy on 2010-11-30
I always use a USB stick for installing.  Reboot your computer with the stick in the USB slot.  Hit "F12" (or whatever the appropriate key for your computer is) while the computer is starting up to go to a boot menu, and boot from the USB stick.

---

### Post by pricetech on 2010-11-30
You don't need Internet access to install.  Just burn the ISO to disk and go for it.  Use the slowest speed when you burn as a precaution.

---

### Post by andymorton on 2010-11-30
> **Katana24 said:**
> Hi - i want to install the latest version of Ubuntu onto my desktop PC. I have downloaded the ubuntu ISO from the site and saved it to a pen drive and external HD. How would I go about installing it from the storage devices? The desktop doesn't have internet access so this is my only option :P

When you say you've saved it to the pen drive, do you mean you have 'burnt' it? It's not enough to copy files over. Sorry if I've got this wrong. If you haven't burnt the disc image then download Unetbootin and use that.

After you've put the pen drive into the computer you need to enter the menu to boot from it. It's usually F9 or F12 that you need to press when you start the computer up. When the menu has loaded choose the pen drive from it by pressing enter and follow the instructions in the installer. 

andy :)

---

### Post by Katana24 on 2010-11-30
I know you don't need internet access - I was just pointing out that the net isn't available should i need to use it for whatever reason. 
And to andy - I just copied the files over - I didn't burn them. I have a Mac and Im trying to figure out how to "burn" it which is proving difficult

---

### Post by celsdogg on 2010-11-30
Hi,

there are instructions for a few platforms on [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

here are the ones for mac:

We would encourage Mac users to download Ubuntu Desktop Edition by burning a CD for the time being. But if you would prefer to use a USB, please follow the instructions below.

 

Note: this procedure requires an .img file that you will be required to create from the .iso file you download.

 

TIP: Drag and Drop a file from Finder to Terminal to 'paste' the full path without typing and risking type errors.

 

   1. Download the desired file
   2. Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
   3. Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
   4. Note: OS X tends to put the .dmg ending on the output file automatically.
   5. Run diskutil list to get the current list of devices
   6. Insert your flash media
   7. Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
   8. Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
   9. Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
  10.
          * Using /dev/rdisk instead of /dev/disk may be faster.
          * If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
          * If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
  11. Run diskutil eject/dev/diskN and remove your flash media when the command completes
  12. Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick

Regards

---

### Post by Katana24 on 2010-11-30
celsdogg - i tried that but keep getting an error - hdiutil: convert failed - No such file or directory, I put in the absolute path of the .iso file which is stored on my desktop:

hdiutil convert -format UDRW -o ~/Users/myname/Desktop/ubuntu.img ~/Users/myname/Desktop/ubuntu.iso

Any suggestions or would this be something for another forum site?

---

### Post by celsdogg on 2010-11-30
katana24: I will try this on my mac when I get home, and let you know what i find.

---

### Post by Katana24 on 2010-12-01
Hello - quick update here - I decided to go with my families computer which has the Windows OS installed on it. I used the UNet program and, cutting a look story short, have started to create a boot-able USB stick with the latest Ubuntu OS on it. 

As its a boot-able USB stick I know that I can use it to run Ubuntu directly from it - but can i install the OS on the pen drive onto my target desktop computer and if so - how?

---

