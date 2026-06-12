---
title: "Dell Mini won't boot from USB"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Eldar11 on 2009-11-29
while trying to install netbook remix, and setting everything up from a Macbook laptop, the netbook won't boot from the USB stick I've but the ISO on. USB is on top on the boot list, I followed the instructions listed here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and still no luck.
When the Dell boots, and the USB is inserted, it comes up with the message, "No Operating System Found."

Help, please? Is there something else I need to do for setup that i'm missing?

---

### Post by blazemore on 2009-11-30
What did you do to make the bootable USB?
I'd recommend a tool called "unetbootin", which has never failed me. It will even download the iso for you if you haven't got it already.
Don't forget you don't just put the .iso file onto the flash drive; there's a particular procedure to make it work.

---

### Post by Eldar11 on 2009-12-01
I followed the directions on the Install by USB page provided by Ubuntu. remember I said I'm using a Mac to set the drive up, because there is no hard drive space on the netbook to even download a USB installer.

I did this: 
# Download the desired file
#

Open a Terminal (in /Applications/Utilities/) and get admin (type login; admin name; password)
#

Run diskutil list to get the current list of devices
# Insert your flash media
#

Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
#

Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
#

Execute sudo dd if=/path/to/downloaded.iso of=/dev/rdiskN bs=1m (replace /path/to/downloaded.iso with the path where the image file is located; for example, ./ubuntu.img, /dev/rdiskN is faster than /dev/diskN). If you see the error dd: Invalid number `1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M. TIP: Use Drag and Drop to put the full path from the downloaded file in finder.app to terminal.app to except typing errors
#

Run diskutil eject /dev/diskN and remove your flash media when the command completes 

and after that i plugged the USB stick into the netbook and booted up, I had no problems switching the USB media to #1 on the boot order. When it tries to boot from the USB it says "No Operating System Present."
and if you press any key it will repeat the statement until you do a hard shutdown.  Is there a better way to do it on the mac? Or does it have to be created on the computer you're going to install it on? thank you for the suggestion of the USB installer, though I can't download it.

---

### Post by blazemore on 2009-12-02
The problem might be on the Dell end. Rather than changing the order in the BIOS, try and get into a temporary boot menu and select the flash drive from there. Also maybe try a different flash drive.

---

