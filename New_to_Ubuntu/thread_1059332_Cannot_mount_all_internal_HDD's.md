---
title: "Cannot mount all internal HDD's"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by jbehl on 2009-02-03
Hi there, I looked in the forums and found a few problems like what I'm having, but none exactly the same. Being a complete newb to Ubuntu, I need some help. 

I installed Ubuntu 8.10 on a machine with two HDD's. One is a 36.7GB Raptor SATA and the other is a internal 160GB SATA. The 160GB has always been my storage for pictures, music, and downloads. 

It still has all of those files on it from when it was on my XP machine. Now that XP is gone, I would like to be able to have access to that drive in Ubuntu. I did a complete new install from CD last night, could see the drive when going through the install process, but once everything was loaded, I could see the drive in places>"computer", but could not open it as it would not mount. My USB drives mount fine, but nothing on the 160GB SATA drive.

One thing I can think of I might have done wrong was to choose the guided partition option during the install. The 160GB drive was an option, but I didn't want it wiped clean so I opt'ed for the Raptor drive for the Ubuntu install. Would the other option, the automatic option allow for the OS to mount the drive?

Thanks for the help.

Regards-

JBehl

---

### Post by wolfen69 on 2009-02-03
> **jbehl said:**
> I could see the drive in places>"computer", but could not open it as it would not mount.

what does it say when you click on the drive?

---

### Post by newbee70 on 2009-02-03
> **jbehl said:**
> Hi there, I looked in the forums and found a few problems like what I'm having, but none exactly the same. Being a complete newb to Ubuntu, I need some help. 

I installed Ubuntu 8.10 on a machine with two HDD's. One is a 36.7GB Raptor SATA and the other is a internal 160GB SATA. The 160GB has always been my storage for pictures, music, and downloads. 

It still has all of those files on it from when it was on my XP machine. Now that XP is gone, I would like to be able to have access to that drive in Ubuntu. I did a complete new install from CD last night, could see the drive when going through the install process, but once everything was loaded, I could see the drive in places>"computer", but could not open it as it would not mount. My USB drives mount fine, but nothing on the 160GB SATA drive.

One thing I can think of I might have done wrong was to choose the guided partition option during the install. The 160GB drive was an option, but I didn't want it wiped clean so I opt'ed for the Raptor drive for the Ubuntu install. Would the other option, the automatic option allow for the OS to mount the drive?

Thanks for the help.

Regards-

JBehl

click on places "top left of screen" click on the drive you see there.

---

### Post by Logan 1229 on 2009-02-03
Try going thru { places --> (name of your 160GB harddrive) }
  This may ask for your authorization. Enter it if so & it should mount.

  If going thru places->my computer-> 160GB, the drive needs to be mounted first.

  In case you require it: To setup mounting so you don't have to enter a password everytime you mount:
  ->System->Administration->Authorizations
  Now locate folder "storage" then select/highlight "Mount file systems from internal drives". Click on "Grant", then under (popup) "Benificiary", select user(s) & "constraints" (if choose to-I didn't), click "Grant", enter authorization password, enter, and voila!

Hope this helps!

---

### Post by jbehl on 2009-02-03
> **wolfen69 said:**
> what does it say when you click on the drive?

It telling me it's unable to mount location.

It's not listed in the places drop down menu but a SCSI drive icon is on the Computer - File Browser Screen.

---

### Post by Andy06 on 2009-02-04
Despite 8.10 having out of box support for NTFS, actually mounting and using them is a bit of a pain which gets worse when you try and "manage" them with a program. I have had the same issues as you on multiple computers.

What you need to do is goto System>Administration>Users and Groups, then click on your user name and select unlock, enter your password and select account privileges in the new thing that comes up, here make sure to select "access external storage" and "mount user space filesystems FUSE". While you're at it, tick other stuff that you might need.

Try now, you should be able to mount. If not, install Disk Manager from add/remove or synaptic package manager, its like NTFS config, but I think its way better and definitely has more features. The GUI is pretty simple and self explanatory.

Disk manager will appear in System>Administration>Disk manager.

In 1st tab (General), select detect devices on start up and enable write support, then configure you devices. There is an auto configure option too.

---

### Post by Andy06 on 2009-02-04
Hey wait, don't you have another thread like this too?:D

I was thinking, wow two guys with the same problem, same day, similar names

---

