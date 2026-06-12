---
title: "external HHD"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by marcellux on 2010-03-31
hello,

I have an external HDD Lacie, it was working fine till now. When I plug it in the usb port I get following message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I know I could fix this by formatting the HDD, but I have data inside of it! 

If I plug it into windows it works just fine.

any idea how could I fix this?

---

### Post by bumanie on 2010-03-31
Do what the message says to do, if you have a windows OS - even a friend's windows computer would do if you don't have windows yourself  - Go to cmd in windows and run chkdsk on the drive > chkdsk <drive letter for lacie> /feg. if lacie is seen as drive f: in my computer chkdsk f: /f 
The message is most likely telling you that the NTFS filesystem on the external hdd is in an inconsistent state and windows/chkdsk is the best tool to use for fixing NTFS filesystem problems.

---

### Post by switch10 on 2010-03-31
make sure in windows you "safely remove device", or whatever that option is.

---

### Post by undecim on 2010-03-31
> **switch10 said:**
> make sure in windows you "safely remove device", or whatever that option is.

+1

NTFS drives are a pain about this.

---

### Post by Calash on 2010-03-31
> **switch10 said:**
> make sure in windows you "safely remove device", or whatever that option is.


I have never had an issue with this.  Personally I just make sure the USB is not active and pull the plug.  Technically the correct way is to shut down the device.

Is it a 1 or 2tb Lacie?  Where I work we have had a few go with bad power supplies, causing all sorts of drive corruption as they spin the drive up and down rapidly.  Easiest way to tell is to hold the power brick to your ear.  If it is making a noise that is not a good sign, even if the drive is working good.

---

### Post by undecim on 2010-03-31
> **Calash said:**
> I have never had an issue with this.  Personally I just make sure the USB is not active and pull the plug.  Technically the correct way is to shut down the device.

You've obviously been used FAT formatted drives then. And even on FAT formatted drives, that can cause problems occasionally. The "Safely remove" operation will power down the device, so that is what you need to do before removing it.

---

### Post by marcellux on 2010-04-05
I did what the message told to do but I did not get any remarkable results. I solved the problem, well I skipped it indeed: went to a windows box, the HDD was working fine in there, but when I tried to copy and paste its content to a new HDD, I got the message the data could not be read... I tried to do the same but only with one folder and it worked out fine, I was doing so until I could isolate the defective file which was causing the problem: it was 3 files only, and they were MP3 files!!!  two of them had question marks (?) and the other ("). I tried to delete them but the access was denied... so I copied all other files and then I formated the drive. Now it works perfectly.
But still I cannot understand what went wrong in there!!

---

