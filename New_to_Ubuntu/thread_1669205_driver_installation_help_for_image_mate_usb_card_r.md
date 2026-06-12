---
title: "driver installation help for image mate usb card reader"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by mikeprosceo on 2011-01-17
I have been trying to load the driver for an image mate usb card reader.  I've tried following the instructions below but have had no luck, I guess because I don't really know what I am doing.  I see the device listed by going to Places and then selecting computer but that is as far as I can get.  Can anyone help or explain these installation directions?  I loaded Root onto my computer which I am assuming I needed to do but now I am lost.  - Mike


STEP 1 - Plug the USB device into the PC. 

NOTE:**Verify the device is detected by going into System Tools > Hardware Browser and enter root password.**This will display your hardware information.**Go to Hard Drives and it should be listed under /dev/sda. 

STEP 2 – Mount the device 
1.*Open terminal window 
2.*Go to the mnt directory 

[imdeemvp@localhost imdeemvp]$ cd /mnt/ 

3.*login as a root 

[imdeemvp@localhost mnt]$ su 
Password:****** 

4.*create a directory on where to mount the flash drive 

[root@localhost mnt]# mkdir usbflash 

5.*Mount the flash drive using the mount command. 

[root@localhost mnt]# mount /dev/sda1 /mnt/usbflash 

6.*To check the files in the USB device the ls command. 

[root@localhost mnt]# ls usbflash

---

