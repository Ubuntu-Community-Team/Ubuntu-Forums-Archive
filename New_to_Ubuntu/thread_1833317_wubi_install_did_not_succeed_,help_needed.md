---
title: "wubi install did not succeed ,help needed"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by sed_y on 2011-08-25
Hi,
My laptop has 64 bit windows vista.
I want to install Ubuntu on my laptop. I have 2 problems
1) I cannot boot linux from Cd-ROM. my CD-ROM does not work.
2) I don't want to disturb whatever is already loaded into my windows. 

so, I installed Ubuntu through **wubi** . It installed all right and then system rebooted.
however, after reboot, I am getting message
> [1) ubi-partman failed with exit code 10 
2) the username you entered is invalid

any idea why is this happening.

what should i do so that it boots properly? I did not make 
new partition before installing. Is it required? 

thanks
sedy

---

### Post by bcbc on 2011-08-25
Did you use any special characters in your username?

---

### Post by sed_y on 2011-08-25
hi,
yes , i used underscore.
anyways, i guess i can take care of the username issue,
but what about the other error?

sedy

---

### Post by bcbc on 2011-08-25
_ should be okay unless it's the first character. Can you confirm if it is, as it should be a bug if wubi allows this and then ubiquity fails it.

If this is not the cause of the other problem...

when you get the error, can you drop to a terminal Ctrl+Alt+F2 and run:
```
sudo parted -l
sudo fdisk -l
```
If the first command fails it might indicate some partition corruption, in which case the second command might indicate the problem. Otherwise, just write down the response. (Those are lower case -L's)

Also, do you have a raid/fakeraid setup?

---

### Post by sed_y on 2011-08-26
hi,
1) yes, i used underscore not as the first character
This time, i get two messages at the start
> 
1)the selected partition (partition 1 of /var/lib/partman/devices/=dev=sda) already contains the following file system images
/ubuntu/disks/root.disk
please uninstall these before trying again

2)no root file system is defined
please correct this from the partitioning menu.

2)I ran the two commands and results seem ok.
i have indicated these below
```

sudo parted -l

```
> 
MODEL :ATA TOSHIBA MK255GS(scsi)
Disk /dev/sda :250 GB
Sector size (logical/physical): 512B/512B
Partition Table : msdos
Number start     end   size type   file system flags
1      32.3kb  236GB  236GB primary ntfs       boot
2      236GB  250GB  13.8GB primary ntfs       

```

sudo fdisk -l

```
> 
Disk /dev/sda :250.1 GB, 250059350016bytes
255 heads,63 sectors/track, 30401 cylinders
units = cylinders of 16065 *512 = 8225280 bytes
Sector size (logical/physical): 512B/512B
I/O size (minimum/optimal): 512B/512B
Disk identifier : 0x6b26cb2

device   Boot  start   end   blocks    id   system
/dev/sda1 *    1       28721 230701401 7 hpfs/ntfs       

/dev/sda2     28722    30401 13494600  7 hpfs/ntfs       


3) i ran the md5 checksum program on the ISO image.i saved the checksum, and then reverified it . it did not cause any problem. if this is the way it should be, then, I have verified the ISO image.

4)How do i check whether I have Raid/faakeraid.
i guess I should not have a RAid.

sedy

---

### Post by bcbc on 2011-08-26
The partition table looks good. 

Running ```
sudo blkid
``` might show if ubuntu is interpreting fakeraid metadata. Or trying the 'nodmraid' boot option might work. Maybe you should just zip up the logs and attach them here:
Ctrl+Alt+F2,
```
sudo sh /host/ubuntu/install/custom-installation/hooks/failure-command.sh
```
(This zips up all the logs to \ubuntu\installation-logs.zip )

This doesn't make much sense to me:
> 1)the selected partition (partition 1 of /var/lib/partman/devices/=dev=sda) already contains the following file system images
/ubuntu/disks/root.disk
please uninstall these before trying again

What release are you installing?

---

### Post by sed_y on 2011-08-26
hi,
> sudo blkid 
did not show fakeraid.

I just copied the contents of the failure-command.sh below

> 
#!/bin/sh
set -x

if [ -e /host/ubuntu ]; then
    zip -r /host/ubuntu/installation-logs.zip /var/log
fi
if [ -e /isodevice/ubuntu ]; then
    zip -r /isodevice/ubuntu/installation-logs.zip /var/log
fi

msg="The installation failed. Logs have been saved in: C:\ubuntu\install\installation-logs.zip.

Note that in verbose mode, the logs may include the password.

The system will now reboot."
if [ -x /usr/bin/zenity ]; then
    zenity --error --text "$msg"
elif [ -x /usr/bin/kdialog ]; then
    kdialog --msgbox "$msg"
elif [ -x /usr/bin/Xdialog ]; then
    Xdialog --msgbox "$msg"
fi

reboot

I am not able to run the command 
> sudo sh /host/ubuntu/install/custom-installation/hooks/failure-command.sh
because as soon as I type half of the command, some data
starts appearing about system etc.

should i uninstall and install again?

sedy

---

### Post by bcbc on 2011-08-26
Try:
```
sudo zip -r /host/ubuntu/installation-logs.zip /var/log
```

Can you boot from a USB key? It might be worthwhile [creating a bootable Ubuntu USB]("http://www.ubuntu.com/download/ubuntu/download") and then booting in live mode - select "Try it" (without installing) and then running the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

What release are you installing?

---

### Post by sed_y on 2011-08-26
hi,

```
sudo zip -r /host/ubuntu/installation-logs.zip /var/log
```
gives error
```
illegal -
```
then, lot of stuff starts appearing beginning with microcode error...

the version is 11.04 .
i thin, i will uninstall first, re install, and if  still does not work,will do the USB way.

sedy

---

### Post by lordjj on 2011-08-26
Hi sed_y,
If your CD-ROM doesn't work, I would suggest you use a USB Flash Drive.
So if you want a full (non-Wubi) install you can just uninstall Wubi and use a program like LinuxLive Usb Creator (Download [here]("http://www.linuxliveusb.com/")) that you can install on Windows, give it an Ubuntu ISO image that you can download off of the [Ubuntu Website]("http://www.ubuntu.com/download/ubuntu/download"), and plug in a flash drive. Then boot your pc from the flash drive (you might wanna check your BIOS settings to enable Booting from USB).

Edit: Oh I didn't notice bcbc had already pointed that out :P -bcbc had helped me out in a thread before :P, Hi there!

---

### Post by sed_y on 2011-08-27
hi ,
i uninstalled and reinstalled ubunu 11.04 using wubi. it works fine now.
however, I have few clarifications
1)after installation, when full GUI came up , the sytem shutdown 
without any dialog box asking to do so. was this normal?
2) within home dir, some directories like root are not accessible from within GUI. is this normal? so, do i need to use chmod 
to change their access level from the terminal?
3) the login prompt dialog shows the username that i used 
while installing the first time( which had failed ) while the name
on the extreme right corner (left of shutdown symbol )on desktop 
shows my username which i used for the second time installation.
Why is this so?

thanks
sedy

---

### Post by bcbc on 2011-08-27
1. wubi uses an unattended installation that includes a reboot at the end, so it's normal
2. You don't have access to /root without elevating your privileges. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
3. Wubi sets up your select user account using the userid you entered, but uses your Windows userID as the Description. With the GUI login the Description is presented, but on other login prompts and the desktop indicators, your userid is shown. To change, hit the windows start key, enter "user" and pick User account management - then you can change it.

---

### Post by sed_y on 2011-08-27
thanks bcbc

> Wubi sets up your select user account using the userid you entered, but uses your Windows userID as the Description. With the GUI login the Description is presented, but on other login prompts and the desktop indicators, your userid is shown. To change, hit the windows start key, enter "user" and pick User account management - then you can change it.

I guess you are referring to windows start? i did that and changed 
the pC login id to whatever ubuntu shows for login prompts.
but, after logging into ubuntu, it still shows me 2 id's. is there 
a way to do it from within ubuntu?

sedy

---

