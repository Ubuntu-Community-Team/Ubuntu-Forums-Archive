---
title: "[SOLVED] Samba not working before logging on"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by mamlouk on 2007-12-26
I have a shared samba folder on my Gutsy 64-bit edition running a 2.6.23 kernel, and I noticed that I cannot access my folder from the network except after I log on my computer. I do not know if it makes a difference, but my shared folder is on an external USB2.0 drive.

How do I let Samba run even if I'm not logged on?

---

### Post by mightyteegar on 2007-12-27
> I do not know if it makes a difference, but my shared folder is on an external USB2.0 drive.

This may indeed make a difference.  The drive likely isn't mounting at boot time.  

Are you running GNOME?  Under normal circumstances, a USB drive plugged into an Ubuntu machine will not be mounted until you log in because gnome-volume-manager (which handles automounting in Ubuntu) doesn't run until then.  Here are some solutions:

1.  If you don't mind leaving the USB drive on all the time while the computer is on, you can edit /etc/fstab to automatically mount the USB drive on system startup.  Note that if you do this, and you ever power up with the USB drive off, your boot time is going to increase, possibly significantly.  **IMO this is the best way to create a permanent connection suitable for Samba sharing.**

2.  From the login screen, you could drop to a terminal, log in and start gnome-volume-manager in the background.  Kind of cumbersome, but it is an idea.  

3.  Here's what I do: since I run fluxbox, gnome-volume-manager doesn't start at all unless I tell it to.  So I configured .fluxbox/startup to load gnome-volume-manager when I log in.  However, I don't know if g-v-m stays running in the background when I log out or not.

---

### Post by mamlouk on 2008-01-01
Thanks a lot Mighty, this is really informing and right to the point.

Sadly, I tried mounting the USB drive from fstab using ```
UUID=4250EAE650EADFA1 /media/external     ntfs    defaults,umask=007,gid=46,noauto 0       1
```
Noting that the directory /media/external is created, but it did not mount automatically. I tried logging on and doing a ```
sudo mount -t ntfs-3g /dev/sda5 /media/external
``` and it was mounted.

I don't think that adding an entry in fstab would force gnome-volume-manager to work at startup. Seems I have to start it up with a script or something. Will keep you posted, and thanks for the help.

---

### Post by santosh_gr on 2008-01-01
Your original fstab entry was 

UUID=4250EAE650EADFA1 /media/external     ntfs    defaults,umask=007,gid=46,noauto 0       1

Change it to the settings given below

UUID=4250EAE650EADFA1 /media/external     ntfs    defaults,umask=007,gid=46 0       1

Note: I have removed the entry noauto.  If the noauto option is specified the /media/external does not auto mount during reboot.  Auto mount is tasked care with the defaults which you specify.

---

### Post by mamlouk on 2008-01-08
That worked, thanks :)

---

