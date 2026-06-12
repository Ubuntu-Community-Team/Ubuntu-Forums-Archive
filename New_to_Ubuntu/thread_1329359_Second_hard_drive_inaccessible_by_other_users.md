---
title: "Second hard drive inaccessible by other users"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Tejus on 2009-11-17
I recently shifted to ubuntu from windows. I have one physical hard drive where ubunutu is installed, and another where all my data is stored. I can access that second data drive from my user, which was the user created during the installation of ubuntu.

I made another user for my dad, but realized he cannot access the data drive from his user. How do i fix this? I fooled around in "User Privileges" in "User Settings", but nothing worked! The second drive's partitions are just not displayed under "Places" in his user.

And in my user, I cannot access the second drive without entering my password again. Is there a way to automatically mount the second drive on startup without requiring the password again?

---

### Post by undecim on 2009-11-17
To make a drive mount on boot, you will need to add a line to /etc/fstab

For example, if I want /dev/sdb1 (the first partition of the second drive connected to the computer) to always mount to /media/sdb1, then I would first create a directory /media/sdb1, and then add this line to /etc/fstab```
/dev/sdb1 /media/sdb1 auto noatime,nodiratime 0 0
```To make sure that you are using the correct drive, mount the drive like you normally do, then run this command in a terminal: ```
mount | grep media
```And look for your drive. You should get a result similar to ```
/dev/sdb1 on /media/disk type ext4 (rw)
``` That first part (/dev/sdb1 in this example) is your drive device, so you should make sure that matches the first part of what you are putting in fstab.

You may also consider moving you /home/ directory to that second drive. That way, anything you put on your desktop, documents, etc. is all stored on the second drive.

---

### Post by Tejus on 2009-11-17
All right...so "/dev/sdb1" represents my second hard drive's first partition, "sdb2" the second partition and so on?

And can I create a directory in "/media" named "Documents" instead of "sdb2" to mount "/dev/sdb2", or should the names match?

Also, i'm guessing I need to do all this by logging into the "root" user, because the file fstab is read only in my account. How do I log into root?

---

### Post by Paqman on 2009-11-17
> **Tejus said:**
> All right...so "/dev/sdb1" represents my second hard drive's first partition, "sdb2" the second partition and so on?


Yep :)

> And can I create a directory in "/media" named "Documents" instead of "sdb2" to mount "/dev/sdb2", or should the names match?

You can call it anything you like.

> 
Also, i'm guessing I need to do all this by logging into the "root" user, because the file fstab is read only in my account. How do I log into root?

On Ubuntu you don't log in as root, you just preface your command with sudo to temporarily become root.

You might also want to check out the Storage Device Manager (package name pysdm), it's a neat GUI tool for setting up drives that saves mucking about with /etc/fstab.

---

### Post by Tejus on 2009-11-18
:-s Okay...not sure i got you.

If i want to edit fstab and save the changes, where do i type "sudo", in the file "fstab"? Or if you mean i have to edit the file "fstab" using terminal, i have no idea how to :neutral:

---

### Post by screaminfakah on 2009-11-18
Open a terminal and type

```
sudo gedit /etc/fstab
```

Or you can do what Paqman suggested go to Synaptic and search pysdm , install the manager, and use it to setup mounting on boot.

---

### Post by Daughain on 2009-11-18
Tejus, is your dad using a windows machine? In setting up my current LAN I discovered that windows firewalls ( native and third-party) need to be checked to make sure that access to a remote system is allowed. I had to manually add the IP for my linux box to the firewall on one windows box, as well as manually set permissions. In my instance, it was an XP machine with Outpost 2009 firewall installed. I could access the drive from the linux box, but the XP box couldn't access the linux box. I spent a few weeks on this in linux trying to find what settings I had wrong before the windows firewall came to mind, ten min later, LAN was running fine. Hope this helps.

---

### Post by Tejus on 2009-11-18
um...nope, my dad isn't using windows, he is using the same installation of ubuntu as me. Only, my account was the first one created when I installed ubuntu and his account I created later from "Users and Groups".

---

### Post by BDNiner on 2009-11-18
There is a group that allows users to mount external devices like USB drives called plugdev. You should make sure that you dad is a member of this group. Specific instructions can be found on:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by Paqman on 2009-11-18
> **screaminfakah said:**
> Open a terminal and type

```
sudo gedit /etc/fstab
```


That should be:
```
gksu gedit /etc/fstab
```

Since Gedit is a graphical app, you should use gksu instead of sudo. Sudo is only for terminal apps. You could edit fstab within the terminal by using a CLI text editor like Nano:
```
sudo nano /etc/fstab
```
(In fact for fstab it is preferred to do it this way)

---

### Post by Tejus on 2009-11-19
Okay...it worked! Thanks everyone!

I did what undecim said, to add a line to /etc/fstab. That made the drive accessible from startup without a password in both my dad's and my accounts:D

And I realized I need to know more about this teminal thing...this thread helped:
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by Tejus on 2009-11-19
Okay...one last problem it seems:

I wanted to mount a partition initially called "sdb3" or "Games" (which was what it was called when I had WinXP) at bootup but calling it "Other Stuff" instead of the original name . 
I successfully created a folder in /media using:

```
sudo mkdir /media/Other\ Stuff
```Then I typed this into /etc/fstab:

```
/dev/sdb3 /media/Other\ Stuff auto noatime,nodiratime 0 0
```But it didn't work.

The error I get if I try to go to Places and click on "Games" is:

**Unable to mount Games**

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 16 in /etc/fstab is bad
mount: can't find /dev/sdb3 in /etc/fstab or /etc/mtab

Any idea what might be going wrong?

---

