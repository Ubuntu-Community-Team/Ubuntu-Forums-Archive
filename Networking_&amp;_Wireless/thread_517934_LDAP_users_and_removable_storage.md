---
title: "LDAP users and removable storage"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by kesomir on 2007-08-05
I'm now implementing the complete migration to ubuntu hosts (feisty server + ~50 feisty clients) on the primary school network I administer. I currently have a successfully working (but as yet unsecured) LDAP server using GOsa for admin, and nfs shares with working central login to replace the server 2003 box I bravely wiped. 

How-to guide on it's way from me since NONE I found on the net actually work.

Here's my problem:

LDAP users cannot use removable storage (such as USB sticks). 

I have used the pam_group module to "on the fly" add ldap users into the audio, video, floppy, cdrom groups etc, but with removable storage I've hit a wall.

I've added plugdev to the list of groups in pam_group, but this still doesn't work. The usb stick is accessed but no mount is given. I've had messages such as "HAL isn't running" when opening system->preferences->removable devices and media and "you do not have permission to mount this device" when I've switched from a local account (which can access USB) to the ldap user and been able to see the device under "computer:///" but not mounted / on the desktop.

Any ideas? What else does removable storage depend on other than the plugdev user group?

Many thanks in advance.

\\:D/

---

### Post by caspcasp on 2007-08-06
> **kesomir said:**
> I'm now implementing the complete migration to ubuntu hosts (feisty server + ~50 feisty clients) on the primary school network I administer. I currently have a successfully working (but as yet unsecured) LDAP server using GOsa for admin, and nfs shares with working central login to replace the server 2003 box I bravely wiped. 

How-to guide on it's way from me since NONE I found on the net actually work.

Here's my problem:

LDAP users cannot use removable storage (such as USB sticks). 

I have used the pam_group module to "on the fly" add ldap users into the audio, video, floppy, cdrom groups etc, but with removable storage I've hit a wall.

I've added plugdev to the list of groups in pam_group, but this still doesn't work. The usb stick is accessed but no mount is given. I've had messages such as "HAL isn't running" when opening system->preferences->removable devices and media and "you do not have permission to mount this device" when I've switched from a local account (which can access USB) to the ldap user and been able to see the device under "computer:///" but not mounted / on the desktop.

Any ideas? What else does removable storage depend on other than the plugdev user group?

Many thanks in advance.

\\:D/


Hi all

I have configured ldap client on Ubuntu 7.04 using [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) doc except  Caching Name Service directories (optional).

Now getenv passwd works without problem but LDAP's users cannot login on local machine using 'ssh' and 'su - user' shows:
su: Authentication service cannot retrieve authentication info.
Sorry.

What i need to configure in order to users can login on machine?

Thanks.

---

### Post by Tobbera on 2007-09-11
Please see [http://ubuntuforums.org/showthread.php?p=3347625&posted=1#post3347625]("http://ubuntuforums.org/showthread.php?p=3347625&posted=1#post3347625")

---

### Post by Krusty Ruffle on 2007-09-13
I believe you need group plugdev to get the removable media/automounting stuff to work....

---

