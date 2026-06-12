---
title: "mount smbfs name mangling issue"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by trelaf on 2007-08-26
Hi,

I am trying to mount an smb share, nautilus can see and browse the share fine, however when i try to mount it with **sudo mount -t smbfs //computer_name/share_name /mnt/smb/** I get no errors but when I navigate to the mounted directory in nautilus (or shell) the files all mangled and is not browseable at all.

Here is an ls -l

total 5792785544
?--------- ? ?    ?                     ?                ? 
-rwxr-xr-x 1 root root 127489752380000000 1940-10-24 11:56 ???
-rwxr-xr-x 1 root root 127489752380000000 1940-10-24 11:56 B???
-rwxr-xr-x 1 root root 128224105460000000 1940-10-24 11:56 entsm
-rwxr-xr-x 1 root root 127489759980000000 1940-10-24 11:56 n?c???
-rwxr-xr-x 1 root root 128247356280000000 1940-10-24 11:56 p?

Any ideas?

---

### Post by jakev383 on 2007-08-26
> **trelaf said:**
> Hi,

I am trying to mount an smb share, nautilus can see and browse the share fine, however when i try to mount it with **sudo mount -t smbfs //computer_name/share_name /mnt/smb/** I get no errors but when I navigate to the mounted directory in nautilus (or shell) the files all mangled and is not browseable at all.

Here is an ls -l

total 5792785544
?--------- ? ?    ?                     ?                ? 
-rwxr-xr-x 1 root root 127489752380000000 1940-10-24 11:56 ???
-rwxr-xr-x 1 root root 127489752380000000 1940-10-24 11:56 B???
-rwxr-xr-x 1 root root 128224105460000000 1940-10-24 11:56 entsm
-rwxr-xr-x 1 root root 127489759980000000 1940-10-24 11:56 n?c???
-rwxr-xr-x 1 root root 128247356280000000 1940-10-24 11:56 p?

Any ideas?

Try adding iocharset=utf8 to the mount options to see if that clears it up.

---

### Post by trelaf on 2007-08-26
Thanks mate, but unfortunately no change..

---

### Post by jakev383 on 2007-08-28
Got me stumped.  I'd suggest that the remote FS was in a different language, but you said Nautilus showed the filenames fine so that shoots that down.
Is the remote FS a Windows machine?

---

### Post by will71110 on 2007-08-28
Here is what I did

gedit /etc/fstab

added this line at the bottom

//computername/sharename /mnt/somethinghere smbfs uid=linuxusername, gid=linuxgroup, username=drive credintials, password=password, dmask=0777, gmask=0777,defaults

dont forget to install the resiptories for smbfs.(I use search in the synaptic to install the package.)

You will also have to create a folder in the /mnt folder( replace that where I put something here)

Restart the computer and it should map the drive.

EDIT: If it mount but you cant access it or it's empty when you rebooted,
 umount it then
 mount -a
That usually fixes it

---

