---
title: "Can't Mount samba share in Debian"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by thabeatsociety on 2008-08-25
Using Ubuntu Debian (file name ubuntu-8.04.1-alternate-i386.iso)

I'm actually reading and writing from the linux machine on the external HDD I have connected to my XP machine.  Only thing I need to do now is create a share with samba on the Linux machine that the Windows machine can see.  Right now, the XP machine sees the Linux machine and it even sees Printers under it, but I'm unable to create a share on the linux machine so the xp one can see an actual folder on it.

I logged in as root in terminal (sudo -i), which put me in terminal as root@ubuntujoe: $ and I brought up sudo visudo, but couldn't edit it the way the tutorial told me to. It wouldn't let me change anything.  That tutorial is here:
[https://help.ubuntu.com/community/SettingUpSamba#Allow%20non-root%20users%20to%20mount%20SMB%20shares](https://help.ubuntu.com/community/SettingUpSamba#Allow%20non-root%20users%20to%20mount%20SMB%20shares)

I also found this, but it didn't work:
[http://www.mariospina.com/braindump/archives/2004/03/24/mount_samba_share.php](http://www.mariospina.com/braindump/archives/2004/03/24/mount_samba_share.php)

I tried going System > Adminisration > Users & Groups and adding root and my user (ubuntujoe) to the same group, root and giving them all the privileges listed in the Privileges tab and then going back to, say, Documents, right-clicking, Sharing Properties and making it a share, but I get the following:

error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares Error Permission denied

You do not have permission to create a usershare.  Ask your administrator to grant you permission to create a share.

I can't login as root from the graphical GUI and getting to root@ubuntujoe: $ in terminal didn't seem to help either. Once I get this figured out, I'm in business.

Any ideas?

---

### Post by dmizer on 2008-08-25
If you're willing to do a bit of work in the command line, please take a look at the second link in my sig.

---

