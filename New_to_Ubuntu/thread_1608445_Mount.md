---
title: "Mount"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by il pepe on 2010-10-29
i like to mount a shared folder of the network.

so i have changed the /etc/fstab file with cifs and etc...

then i do mount -a (with sudo) and then the folder is accesible. The only problem is i can only 'read' the files but i can't do any changes, nor write to the folder...

because the rights are root. 
I tried to change the rights of the linked folder using the chown command, but that doesn't work...

any thoughts?

---

### Post by bioterror on 2010-10-29
> **il pepe said:**
> i like to mount a shared folder of the network.

so i have changed the /etc/fstab file with cifs and etc...

then i do mount -a (with sudo) and then the folder is accesible. The only problem is i can only 'read' the files but i can't do any changes, nor write to the folder...

because the rights are root. 
I tried to change the rights of the linked folder using the chown command, but that doesn't work...

any thoughts?

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

You have followed these instructions?

---

### Post by il pepe on 2010-10-29
i tried it now, and now i'm not able to mount the file

error -1 (Unknown error 4294967295) opening credential file ~/.smbcredentials

Comes up. It guess it is something with the rights of the file .smbcredentials?

---

### Post by bioterror on 2010-10-29
> **il pepe said:**
> i tried it now, and now i'm not able to mount the file

error -1 (Unknown error 4294967295) opening credential file ~/.smbcredentials

Comes up. It guess it is something with the rights of the file .smbcredentials?

You see, you have to use /home/yourusername/.smbcredentials

> Use of tilde in pathnames such as "credentials=~/.smbcredentials"
20 Feb 2008 TW

Curiously, using credentials=~/.smbcredentials in fstab didn't work. I had to use the full path, i.e. /home/username/.smbcredentials

(This is likely because the tilde "~" is only a shell short-hand alias for "$HOME"; it isn't something recognized system-wide by all programs, especially not in a system file table where the concept of "HOME" doesn't really exist. -Ian!)

---

### Post by il pepe on 2010-10-29
the dmask en fmask didn't work.

I could mount the folder without these enabled. but then i still don't have the rights to write in that folder.

With fmask en dmaks enabled i got: 
WARNING: CIFS mount option 'dmask' is                 deprecated. Use 'dir_mode' instead.
WARNING: 'dir_mode' not expressed in octal.
WARNING: CIFS mount option 'fmask' is                 deprecated. Use 'file_mode' instead.
WARNING: 'file_mode' not expressed in octal.
WARNING: CIFS mount option 'dmask' is                 deprecated. Use 'dir_mode' instead.
WARNING: 'dir_mode' not expressed in octal.
WARNING: CIFS mount option 'fmask' is                 deprecated. Use 'file_mode' instead.
WARNING: 'file_mode' not expressed in octal.

---

### Post by bioterror on 2010-10-29
> **il pepe said:**
> the dmask en fmask didn't work.

I could mount the folder without these enabled. but then i still don't have the rights to write in that folder.

With fmask en dmaks enabled i got: 
WARNING: CIFS mount option 'dmask' is                 deprecated. Use 'dir_mode' instead.
WARNING: 'dir_mode' not expressed in octal.
WARNING: CIFS mount option 'fmask' is                 deprecated. Use 'file_mode' instead.
WARNING: 'file_mode' not expressed in octal.
WARNING: CIFS mount option 'dmask' is                 deprecated. Use 'dir_mode' instead.
WARNING: 'dir_mode' not expressed in octal.
WARNING: CIFS mount option 'fmask' is                 deprecated. Use 'file_mode' instead.
WARNING: 'file_mode' not expressed in octal.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently#CIFS%20Options%20Deprecated]("https://wiki.ubuntu.com/MountWindowsSharesPermanently#CIFS%20Options%20Deprecated")

---

### Post by il pepe on 2010-10-29
how stupid of myself... It was all in the documentation...

thanks a lot!!!

---

### Post by bioterror on 2010-10-29
> **il pepe said:**
> how stupid of myself... It was all in the documentation...

thanks a lot!!!

Np, I just needed to show you the documents.
That's one great thing about Ubuntu that, when there's documents about things, they really rule!8-)

---

