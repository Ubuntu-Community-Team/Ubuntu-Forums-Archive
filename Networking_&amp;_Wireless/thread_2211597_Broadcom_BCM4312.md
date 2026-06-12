---
title: "Broadcom BCM4312"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by henrik4 on 2014-03-16
As my first question, and as a totally new user of Lubuntu, I really need to know how to install the wifi driver on my **emachines em250 netbook**. I installed Lubuntu on it, and everything works fine except the wifi which doesn't seem to exist. 


[LIST]
[*]**After running some commands, I got this info about my system: **

  01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY

  [14e4:4315] (rev 01) 
[/LIST]
  and

  
[LIST]
[*]Lo no wireless extensions.
  eth0 no wireless extensions. 
[/LIST]


  So after many, many hours of searching and reading, I came upon these instructions at this link:[INDENT]   [http://ubuntuforums.org/showthread.php?t=1421768](http://ubuntuforums.org/showthread.php?t=1421768)


 [/INDENT]
-------------------------------------------------------
> 
1. Download Broadcom 802.11 Linux STA driver from the following web page:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

2. Extract and build the driver. Below is a description of this step from README.txt:

                                                                              Originally Posted by **README.txt**                                      


                 BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:

For 32 bit:     hybrid-portsrc.tar.gz
For 64 bit:     hybrid-portsrc-x86_64.tar.gz

# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make

When the build completes, it will produce a wl.ko file in the top level
directory.

If your driver does not build, check to make sure you have installed the
kernel package described in the requirements above.
                      
     
 
Got from here: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

3.  Now you need to run 'sudo make install' from the same floder where you ran 'make'.
The driver wl.ko will be installed into the following folder:
/lib/modules/<kernel-version>/kernel/net/wireless

4. Now you need to load this driver into the system.
You can do this by performing the following commands:
# cd /lib/modules/<kernel-version>/kernel/net/wireless
# sudo depmod
# sudo modprobe wl
Please note that <kernel-version> is a string with YOUR linux kernel version,
so you need to adjust the first command.  

[HR][/HR]  


Now the thing is, almost all of that description is greek to me. It  assumes that you know a bunch of stuff about Lubuntu already. Is there  anyone out there kind enough to interpret these descriptions for me,  step by step, so that I can try to install the driver. After all, what  is a netbook without wifi.

---

### Post by westie457 on 2014-03-16
Hi
 If you have already installed the Broadcom STA driver it will not work with your wireless chip. 

Assuming you have a working cable connection, open a terminal ```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rfv wl
```
If you have not managed to install the Broadcom driver you can ignore the above command.

Instead run these ```
sudo apt-get install linux-firmware-nonfree
sudo modprobe wl
sudo modprobe ssb
sudo modprobe b43
```

Edit extra: If the 'wl modprobe' returns no output run 'sudo modprobe -rfv wl' again and ignore the command to load the 'wl' element of the driver.

Ignore any error about 'module not found'. Stop at the one that returns to a blank line and unplug the cable. You should now have a working wireless connection Click on the Network Manager icon (looks a bit like a fan) pick you wireless connection, input the necessary password. Job done.

Post back here if successful so this can be marked 'SOLVED'
Any problems post back here with the error messages. We will then go for the full diagnosis.

---

### Post by henrik4 on 2014-03-17
Nothing noticable changed. While something seemed to be installed when running the "sudo apt-get install linux-firmware-nonfree", I got these messages after typing in the "sudo modprobe wl":

> 
james@james-eM250:~$ sudo modprobe wl
FATAL: Module wl not found.
james@james-eM250:~$ sudo modprobe -rfv wl
FATAL: Module wl not found.
james@james-eM250:~$ sudo modprobe ssb
james@james-eM250:~$ 


Sudo modprobe ssb doesn't seem to do anything..

---

### Post by henrik4 on 2014-03-20
Alright! I just noticed it seemed to have worked after all!.

Thanks!

---

### Post by susan3 on 2014-03-23
Hi!  I also have the Broadcom BCM4312 card, but in my Lenovo Ideapad S10-2.  Yesterday I downloaded Lubuntu 13.10 onto a bootable flash drive per the procedure at [http://www.pendrivelinux.com/put-lubuntu-on-a-flash-drive-using-windows/](http://www.pendrivelinux.com/put-lubuntu-on-a-flash-drive-using-windows/).  It works fine, in that I can boot from the USB drive and start up Linux.  But I can't get the wireless working.  I found this thread, and tried to follow the procedure in the 2nd block of code in post #2.  The first step seemed to work, in that it downloaded and unpacked something, but with the second step I get a message "FATAL:  Module wl not found."  I would appreciate any suggestions to help this Linux newbie past this error.  Thanks.

---

### Post by chili555 on 2014-03-23
> **susan3 said:**
> Hi!  I also have the Broadcom BCM4312 card, but in my Lenovo Ideapad S10-2.  Yesterday I downloaded Lubuntu 13.10 onto a bootable flash drive per the procedure at [http://www.pendrivelinux.com/put-lubuntu-on-a-flash-drive-using-windows/](http://www.pendrivelinux.com/put-lubuntu-on-a-flash-drive-using-windows/).  It works fine, in that I can boot from the USB drive and start up Linux.  But I can't get the wireless working.  I found this thread, and tried to follow the procedure in the 2nd block of code in post #2.  The first step seemed to work, in that it downloaded and unpacked something, but with the second step I get a message "FATAL:  Module wl not found."  I would appreciate any suggestions to help this Linux newbie past this error.  Thanks.Perfect! What we want to see is that *wl* is gone forever, since it is wrong for your device. If you have installed the firmware, I suggest you reboot and give us a report!

---

