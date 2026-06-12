---
title: "Can't mount network drive"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by rh995 on 2011-06-27
I've looked all over to try to find out how to mount my external hard drive in ubuntu. It works in windows, and I've tried editing /etc/fstab but nothing works. mount -a just does nothing. Please Help!!!!!

---

### Post by Bradburts on 2011-06-27
Hi,
There's a short tip at:
[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)
and better:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
 
hope that helps.

---

### Post by rh995 on 2011-06-28
Unfortunately, I tried both methods, and neither works. I get an error when I use the nfs method, and samba or cifs times out. I will paste both errors below:
nfs:
"mount: wrong fs type, bad option, bad superblock on HD-CELU2-6C5F:/share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
cifs:
"mount error(110): Connection timed out
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)"

I can't get the eight+end parentheses to stop turning into a smiley face. Sorry.

---

### Post by skippycampbell on 2011-06-28
Is this for a desktop or a server? 
What Ubuntu version are you running? 10.04 ?

_For Graphical interface_:
Click on "System"  then "Administration" then "Disk Utility"
This will at least let you see if the drive is recognized by the system.

_Server or Command line interface_:
sudo fdisk -l

---

### Post by Morbius1 on 2011-06-28
You need to answer one fundamental question - at least for me.

Are you mounting a network drive that happens to be an external usb drive?

Or are you mounting an external usb drive connected to your own machine?

All this cifs stuff is for the network - not going to help you if the drive is attached to your local machine?

---

### Post by mcduck on 2011-06-28
> **Morbius1 said:**
> You need to answer one fundamental question - at least for me.

Are you mounting a network drive that happens to be an external usb drive?

Or are you mounting an external usb drive connected to your own machine?

All this cifs stuff is for the network - not going to help you if the drive is attached to your local machine?

+1 to this.

.. and of course the current contents of the /etc/fstab file would be rather important. It would be much easier to just look at the file to see what's wrong than it is to try to guess what might be wrong there. ;)

---

### Post by rh995 on 2011-06-28
I am running a desktop, version 11.04 Natty

The drive is on my network, not directly connected to my computer via usb.

The contents of /etc/fstab are:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Mount //HD-CELU2-6C5F/share
//HD-CELU2-6C5F/share /media/drive-z smbfs credentials=/home/ray/.smbcredentials,uid=1000 0 0

---

### Post by skippycampbell on 2011-06-28
The USB drive that is attached to the computer is what ? linux? windows?   Does this computer with the drive attached able to see the USB drive?

---

### Post by rh995 on 2011-06-28
It's not a usb drive, it's an external hard drive

---

### Post by mcduck on 2011-06-29
Wait a second, I just realized something

> 
I get an error when I use the nfs method, and samba or cifs times out.

So you've tried three different network share types. Do you actually know what type network drive is using? (the type of the share is not something you can decide at the machine trying to mount the drive).

Well, at least NFS seems quite unlikely since you've accessed the drive from Windows.

Also do you have the smbfs package installed?

---

### Post by Morbius1 on 2011-06-29
There's a real lack of information here for anyone to help you with any kind of clarity.
>          It's not a usb drive, it's an external hard drive     What does that mean? Sata connected?

We still don't know for sure where this external drive is located. Attached to a Windows machine, a Linux machine, router, ...

We also don't know what version of Ubuntu you are using. If you are using an older version of Ubuntu then you need to install the "smbfs" package as mcduck stated earlier. But if you are using the latest Ubuntu then the package is now "cifs-utils".

Either way the fstab line should be modified to replace the smbfs filetype to cifs:

> //HD-CELU2-6C5F/share /media/drive-z [COLOR=Blue]**cifs**[/COLOR] credentials=/home/ray/.smbcredentials,uid=1000 0 0     

---

### Post by Morbius1 on 2011-06-29
Well, I did something out of the box just now. I did a google search on "HD-CELU2-6C5F". It appears that this is a Buffalo device - one of these to be exact[:]("http://www.buffalotech.com/support/warranty/:")
Desktop Hard Drives:
> DriveStation™ Quad USB 3.0, DriveStation™ Duo USB 3.0, DriveStation™ Axis USB 3.0, DriveStation™ USB 3.0, DriveStation™, DriveStation™ Axis LED, DriveStation™ Axis, DriveStation™ TurboUSB, DriveStation™ Combo, DriveStation™ FlexNet, DriveStation™ AV, DriveStation™ DataVault, DriveStation Duo™, DriveStation™ Quad, DriveStation Quattro™ TurboUSB, DriveStation™ Combo 4, DriveStation Quattro™ Rackmount 

 [http://www.buffalotech.com/support/warranty/]("http://www.buffalotech.com/support/warranty/:")

---

### Post by Jacobonbuntu on 2011-06-29
> **rh995 said:**
> I've looked all over to try to find out how to  mount my external hard drive in ubuntu. It works in windows, and I've  tried editing /etc/fstab but nothing works. mount -a just does nothing.  Please Help!!!!!

Hi rh995, assuming it is a smb shared NAS, this is a pretty good howto  that learned me to do the trick. you have to find out the ip adress, but  probably your NAS will be able to show it on the display:

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

hope it works!

---

### Post by Morbius1 on 2011-06-29
Despite what others may say I do try to be accurate in my posts :wink:  but something I wrote although accurate is somewhat misleading:
> If you are using an older version of Ubuntu then you need to install the  "smbfs" package as mcduck stated earlier. But if you are using the  latest Ubuntu then the package is now "cifs-utils".It turns out if you install the "smbfs" package all it does is install "cifs-utils" so either way will work.

My recommendation is to install cifs-utils:
```
sudo apt-get install cifs-utils
```
Redo the fstab line to this:
>  			 				//HD-CELU2-6C5F/share /media/drive-z [COLOR=Blue]**cifs**[/COLOR] credentials=/home/ray/.smbcredentials,uid=1000 0 0 			 		
Then do the following again and see if you connect:
```
sudo mount -a
```

---

### Post by Jacobonbuntu on 2011-06-29
I might have missed something, but shouldn't he first create the /media/drive-z directory to mount the drive in?

also: wouldn't it be saver to store the .credentials-file somewhere else then /home? (did he create that file as well anyway?)
and also: wouldn't the auto -mount option be convenient?

---

### Post by rh995 on 2011-06-29
I do have the smbfs package installed, but I have no Idea what sharing system my external hard drive uses. Any idea how to find out?

---

### Post by rh995 on 2011-06-29
Attached is a screenshot of the properties window when I open it in windows.

---

### Post by rh995 on 2011-06-29
> **Jacobonbuntu said:**
> I might have missed something, but shouldn't he first create the /media/drive-z directory to mount the drive in?

also: wouldn't it be saver to store the .credentials-file somewhere else then /home? (did he create that file as well anyway?)
and also: wouldn't the auto -mount option be convenient?

The mount folder already exists, and I just edited .smbcredentials in nano and saved it to my home folder. I set the permissions to only be root, so It's pretty secure.

---

### Post by rh995 on 2011-06-29
> **Morbius1 said:**
> Despite what others may say I do try to be accurate in my posts :wink:  but something I wrote although accurate is somewhat misleading:
It turns out if you install the "smbfs" package all it does is install "cifs-utils" so either way will work.

My recommendation is to install cifs-utils:
```
sudo apt-get install cifs-utils
```
Redo the fstab line to this:

Then do the following again and see if you connect:
```
sudo mount -a
```

Unfortunately, I tried this, and it still timed out after a while when I tried to mount the dive (sudo mount -a).

---

### Post by rh995 on 2011-06-29
> **Jacobonbuntu said:**
> Hi rh995, assuming it is a smb shared NAS, this is a pretty good howto  that learned me to do the trick. you have to find out the ip adress, but  probably your NAS will be able to show it on the display:

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

hope it works!

How do I find out the ip adress?

---

### Post by Morbius1 on 2011-06-29
** Look at your router's log to see what ip address it assigned.

** You can ping it by name which will tell you what it's ip address is:
```
ping HD-CELU2-6C5F
```** You can install nmap and do a scan:
```
sudo apt-get install nmap
```Then run this:
```
sudo nmap -sP 192.168.0.100/24
```
[COLOR=Blue]*Change 192.168.0.100 to your own ip address on the machine you are posting from.*[/COLOR]

---

### Post by Jacobonbuntu on 2011-06-29
...or install netdiscover:
sudo apt-get install netdiscover

then: sudo netdiscover

(just another programm, I tried both, this is a very easy one, nmap is also good of course :p )

---

### Post by rh995 on 2011-06-29
> **Jacobonbuntu said:**
> Hi rh995, assuming it is a smb shared NAS, this is a pretty good howto  that learned me to do the trick. you have to find out the ip adress, but  probably your NAS will be able to show it on the display:

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

hope it works!

I did your suggestion, pinging HD-CELU2-6C5F from my windows machine to find the ip adress, and it worked! I successfully mounted my network drive. Thank you all for your help.

---

### Post by Jacobonbuntu on 2011-06-30
> **rh995 said:**
> I did your suggestion, pinging HD-CELU2-6C5F from my windows machine to find the ip adress, and it worked! I successfully mounted my network drive. Thank you all for your help.
Ah, great to hear it worked!

have a good time,
Jacob

---

