---
title: "Accessing a windows share"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by hise0001 on 2006-12-04
Hi,

I've just performed a fresh install of Edgy and trying to access some shares on my wife's xp box.  My way of getting samba setup was to:

* System->Administrations->Shared Folders
* The system prompted me for installing samba and I stepped through the wizard.
* Using smbpasswd, I added my ubuntu local account as a samba user.  Created a local account for my wife and added her account to smbpasswd.

So, from my wife's XP box I can access my ubuntu samba shares just fine.  However, going from my ubuntu box to my wife's xp shares, I have some problems.  If I:

* Places->Network Servers
* double-click "Windows Network"
* double-click "mshome"

I receive a dialog box stating:

```
The folder content could not be displayed.
Sorr, couldn't display all the contents of
"Windows Network: mshome"
```.

Any feedback would be greatly appreciated.

Thanks,

--Hise

---

### Post by daniminas on 2006-12-04
you can check the 'groups' are the same.. in the samba config and in the Xp..

and try to open the location in nautilus:
smb://xp_pc_name/shared_folder

;)

---

### Post by Iowan on 2006-12-04
You may need to install **smbfs**.
I don't have the full package name at my fingertips.
[http://www.ubuntuforums.org/showthread.php?t=9950]("http://www.ubuntuforums.org/showthread.php?t=9950")
This thread may have some useful information.

Or...
[http://www.ubuntuforums.org/showthread.php?t=312033]("http://www.ubuntuforums.org/showthread.php?t=312033")

---

