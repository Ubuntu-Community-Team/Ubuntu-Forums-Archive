---
title: "Fiesty + Samba, no love?"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by theredcross on 2007-04-27
Clean install up to fiesty, and now when i try to share folders with samba anyone (including myself) that tries to browse to the folder on the network is met with the error message
```
The file or folder smb://mahdi-desktop/MAHDI does not exist.
```
I've tried editing the smb.conf as accorded to in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_home_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_home_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29)
but no luck.
```
[MAHDI]
        path = /home/mahdi/
        valid users = krootox
        force user = nogroup
        create mask = 0700
        directory mask = 0700
        guest ok = Yes
        case sensitive = No
        strict locking = No
        msdfs proxy = no

```
can't figure this out!

---

### Post by theredcross on 2007-04-29
tried any number of different configurations, and discovered that I am perfectly capable of sharing folders OTHER than my home folder, which gives the same error no matter what happens.

---

### Post by malefisocu on 2007-06-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				According to other posts, you should be able to fix it commenting the line msdfs proxy = no and restarting the samba server
sudo /etc/init.d/samba restart

In my case, I have not this line in my smb.conf but I also cannot see any shares after upgrading  to feisty.

I think I will have to downgrade all the samba package.

This is related to a major bug in feisty.

---

