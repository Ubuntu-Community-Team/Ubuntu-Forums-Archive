---
title: "Can't connect to Windows 10 External Hard Drive via administrative share"
date: 2017-03-16
forum: Networking &amp; Wireless
---

### Post by lobsta2 on 2017-03-16
Hi there, 

Very new to linux here, but I have been googling around for an hour or so and nothing I've tried has helped. 

I have a Windows 10 desktop that is attached to my 1TB WD External HD which hosts mostly my media files. 

I want to be able to connect to it from Ububtu 16.04 LTS which is installed on my MSI GP62 6QF laptop.  

I have enabled administrative shares in windows via the registry, I have added in 'Administrators' under permissions for the eternal drive on the windows machine and I have checked that the external drive is shared exactly the same as C:/ through sharing in Computer Management (default share). 

I can connect to all administrative share drives on the Windows 10 installation on the same laptop fine, including the external drive. 

I can connect to all other administrative shares from the desktop through Files -> connect to server -> smb://[pcname] using my Microsoft account and correct domain (i.e. the domain of the email that the account corresponds to). From there I can view C$, ADMIN$, print$ and Users$ fine and mount each and all of them. But when I go to double click on I$ (the external drive), I get the error: "Unable to access location - Failed to mount Windows share: Invalid argument.". 

I have tried both workarounds mentioned in: [http://askubuntu.com/questions/574393/failed-to-mount-windows-share-invalid-argument](http://askubuntu.com/questions/574393/failed-to-mount-windows-share-invalid-argument)

Option 1 - Trying nautilus manually through the terminal gives this popup error: "Oops! Something went wrong. Unhandled error message: Failed to mount Windows share: Invalid argument" and this returned in the terminal:

```
(nautilus:2862): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:2862): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:2862): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:2862): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:2862): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
```

however I understand that this is normal for running nautilus through the shell as I get the same response when i just enter 'nautilus'.

Option 2 -  (smbclient) returns this in the terminal:

smbclient -L mandm-pc -U mymicrosoftaccount
WARNING: The "syslog" option is deprecated
Enter mymicrosoftaccount's password: 
session setup failed: NT_STATUS_LOGON_FAILURE

I'm out of ideas (read: google responses) here. The fact that it works perfectly in the Win10 installation that I am dual booting with is maddening. My current workaround is to boot to Win10, copy the file(s) that I want from the external drive to a FAT32 partition that I created for sharing files between OSs then reboot to Ubuntu, which is a PITA when Windows works out that it wants to install updates and restarting out of windows takes 10 minutes while it 'Prepares my Computer'. 

Any ideas??

---

### Post by ajgreeny on 2017-03-17
Have you disabled the Win 10 faststart in its settings and what filesystem is on the external disk?
You must disable faststart as otherwise all ntfs disks and partitions will be flagged as still in use and will be unavailable to any Linux OS.
Faststart means that the partitions are marked as in hibernation, and are therefore not accessible until you fully shutdown Windows 10.

---

### Post by lobsta2 on 2017-03-17
On the laptop or the desktop?

Fast boot already disabled on laptop when I installed Ubuntu. Just did it on the desktop too and waiting for PITA windows update to run now to test. Desktop powered on when I tried to connect from the linux laptop.

External hard drive is NTFS.

---

### Post by lobsta2 on 2017-03-23
Made the suggested changes, still get the same error messages as before. 

Anyone got any ideas?

---

