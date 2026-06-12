---
title: "Cannot automount hard drive"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by ono2010 on 2010-02-10
I have tried to solve this problem with all of the forum posts I could find, to no avail.

I have an Asus EEE PC 1000, running Ubuntu 9.10 NBR. I am attempting to set the 32GB SSD to automount on startup.

I reformatted it to ext3 and followed the instructions at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

The drive does not mount at startup, or show in my list of drives. When I mount it through GParted, it still does not show up on my desktop or my list of drives. 

The relevant entry in my /etc/fstab file is this:

/dev/sdb1  /photos   ext3   defaults, umask=000   0  1

Help? Thanks!

---

### Post by Satoru-san on 2010-02-10
does /photos exist?

If not you need to make a directory there, or I couldn't imagine that it would mount.

```
sudo mkdir /photos
```

---

### Post by ono2010 on 2010-02-10
Yes, that directory exists. I double-checked. Thanks though.

---

### Post by Satoru-san on 2010-02-10
Try mounting it manually just to see if its not something else.

```
sudo mount /dev/sdb1 /photos
sudo chown -R <YOUR USERNAME> /photos
nautilus /photos
```

if that doesnt work then we have another problem other than it just not automounting.

---

### Post by ono2010 on 2010-02-10
Saturo-san,

When I follow these commands, it does mount, but it shows the following message in Terminal:

(nautilus:2022): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


Andrew

---

### Post by ono2010 on 2010-02-11
*bump*

---

### Post by mwcrowley on 2010-02-11
Just a suggestion, 
Double check that the drive is /dev/sdb1, I have usb drives that will change drive letters after being remounted.

---

### Post by Morbius1 on 2010-02-11
> The drive does not mount at startup, or show in my list of drives. When I mount it through GParted, it still does not show up on my desktop or my list of drivesYour original fstab entry has an extra space in it and a umask=0000 which is for windows filesystems. You also stated that you want the drive to show up on your desktop. A mount point off "/" won't do that.

What I would do is this:

Open **Terminal**
Type **sudo mkdir /media/Photos**
Type **gksu gedit /etc/fstab**

I would put a "#" in front of the entry you have for sdb1 so that it looks like this:
```
 [COLOR=Blue]#[/COLOR]/dev/sdb1  /photos   ext3   defaults, umask=000   0  1
```Then I would add this one:
```
 /dev/sdb1  /media/Photos   ext3   defaults 0 2 
```Save the file, exit gedit, and back in the Terminal:

Type **sudo umount /photos**
Type **sudo mount -a**

[COLOR=Blue]EDIT: It will mount as owned by root so you'll need to fix that:

[/COLOR]**[COLOR=Blue]sudo chown -R your_user_name /media/Photos[/COLOR]**


 Now see if you can access /media/Photos. If you can't please post the output of the following command so we can make sure we're all looking at the same partition:

**sudo blkid -c /dev/null**

---

### Post by ono2010 on 2010-02-11
It always mounts as /dev/sdb1 - it's an internal SSD.

---

### Post by Morbius1 on 2010-02-11
Please post the output of the following commands please:

Open **Terminal**
Type **cat /etc/fstab**
Type **sudo blkid -c /dev/null**

---

### Post by ono2010 on 2010-02-11
That worked - thank you!!!

---

