---
title: "Raid 1 on Gigabyte Motherboard"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by bnhrobotics on 2009-10-19
I am looking to create a RAID 1 mirror of two data disks. I have Ubuntu 9.04 and Win7 on my main HD and then I have two 'extra' drives I want to use simple for the RAID 1 data mirror. My motherboard (Gigabyte GA-MA790X-UD4P) has two forms of RAID. The user manual mentions "AMD SB750 SATA controllers" and "GIGABYTE SATA2 SATA controllers". Currently, my RAID disks are set up with the Gigabyte controller. The drives are also unformatted.

I am not entirely sure what is possible, so let me list what I hope to accomplish, so maybe I can narrow down my choices.

1) If possible I would like to access the RAID from both Linux and Windows. 
2) I would like to be able to access the RAID from the network.

-If the RAID is installed in windows, can ubuntu be set up to access it?
-If installed in Ubuntu, could windows access it?
-Which OS would be better to install the RAID in?
-will my other windows/ubuntu computers on the network be able to access the raid?

I understand that there are software raids and fake raids. I don't know if either of my raid systems are dedicated hardware or not. I know that the first is on the southbridge and the second is on a Gigabyte chip.

For reference: [http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ProductID=3031](http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ProductID=3031)


So what options do I have? Once I know that, I'll work from there. Thanks

---

### Post by superdav42 on 2009-10-19
In order to use your RAID in Linux and windows linux must have the drivers for it. To see if your raid controller is properly recognized you can look at the output of ```
dmesg
``` It will probably say something about raid or the sata controller in there. The true test will be to see if Linux see one device or two seperate devices. Just run ```
ls /dev/sd*
``` to see a list of all the drives detected on your system. sda will probably be the main one you are booting from and then hopefully there is a sdb which is your raid drive. You can use ```
sudo cfdisk /dev/sdx
``` to see what is in the drive and how big it is, just do not delete anything.

---

### Post by bnhrobotics on 2009-10-19
Thanks. Looks like I will have to go the software RAID route, judging by what I have found. Is there any way to add the software raid without doing a complete reinstall of Ubuntu? And is the only way to do it with the alternate installation disk?

---

