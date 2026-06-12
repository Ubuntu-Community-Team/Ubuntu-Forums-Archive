---
title: "Cifs share mounts and browses but no access to files"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Mjr_Rip on 2008-06-26
im pretty new to this, but in the final stages of setting up a box to play around on, and learn the way of linux.

The box is running hardy, and is connected to my home network, which contains a Hawking Nas drive. i can mount the drive from the command line using either mount -t cifs   or smbmount  and the drive mounts, and shows up correctly.  The mounted volume is browsable, but upon attempting to open and image file, i just get an access denied error.

so i went through and used chown to change the owner of my mount point to my user, and made sure i had read and write permissions to that folder.  as long as i mount without using sudo the owner of my mount volume stays the same, but apparently i dont have access to any of the files on the volume.

ive also tried to use fstab to mount the drives at bootup, which has the same effect, and mounted drive, but with no access.  With this method i also get errors on shutdown.

interestingly im not able to use  places > connect to server... to connect to my NAS drive, although i can mount it from the command line.

ive spent hours trying to get this thing working, and am rather close to giving up now, so any help would be most appreciated.

Thanks

ps. oh yeah, and ive tried using dir_mode=0777 & file_mode=0777 etc, ive added utf8 as charset, ive tried noperm and nounix as various guides included those options, but all to no avail.

---

### Post by Orion2000za on 2008-06-26
I would say install smb4k - though that is a KDE Ubuntu tool. I struggled like forever with  your problem but smb4k sorted it. Maybe someone can suggest a Gnome alternative?

Sinclair

---

