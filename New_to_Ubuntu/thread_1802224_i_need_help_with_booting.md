---
title: "i need help with booting"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by mj360 on 2011-07-11
when i boot into ubuntu it say try (hd0,0) ext2 do anyone know why this happening and how to fix this ?

---

### Post by Drone4four on 2011-07-11
Boot into a Live environment using either a USB key or CD and then follow this guide here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Rubi1200 on 2011-07-11
Please do not attempt to install, reinstall, or otherwise modify GRUB. 

This is a Wubi install and installing/reinstalling GRUB will fail and likely cause Windows to fail with booting too.

The error you are getting is caused by grub4dos (which Wubi uses to boot via the Windows bootloader) hanging on an ext3 or ext4 partition - in your case most likely the /dev/sda1 partition.

To confirm this, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

If you do not have a LiveCD/USB, go to the Ubuntu site and download and burn a copy (there are instructions on the page how to do this):
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

