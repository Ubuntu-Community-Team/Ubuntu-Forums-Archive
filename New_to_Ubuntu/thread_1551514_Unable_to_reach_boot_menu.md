---
title: "Unable to reach boot menu"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by browny254 on 2010-08-12
Hi, I have just set up Kubuntu 10.04 to dual boot with Windows 7, but whenever I reboot nothing is able to boot from the hard drive. I have a Kubuntu 9.10 live cd that I instead boot to, which unlike my 10.04 cd gives a list of options of what to do, one of which is to boot from the first hard drive. Doing this brings up grub and I can boot fine, but how can I get it to display the grub menu automatically?


Also on a completley unrelated matter, I am trying to set up a PPPoE connection in kubuntu using sudo pppoeconf, but it is not finding my wireless connection, even though that is present. Ive never had this problem before as my modem used to authenticate with my old isp automatically, but that doesnt work with my new isp. So i havent really got any experience with this so it could just be something simple i am missing...?

Thanks.

---

### Post by oldfred on 2010-08-12
I would first try reinstalling grub to sda (if that is your drive you boot from). Boot into your install.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

You can reinstall from a liveCD also 
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

