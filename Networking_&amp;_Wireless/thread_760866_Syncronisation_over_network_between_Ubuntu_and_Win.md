---
title: "Syncronisation over network between Ubuntu and WinXP"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by tendrousbeastie on 2008-04-20
Hi all,

I've recently installed Ubuntu 7.10 on a laptop of mine, and I now need to find a way to syncronise various folders on the laptop and on my desktop (running WinXP SP2) so they keep up to date with each other's date.

The copy of Ubuntu on the laptop is essentially a default install straight from the disc. I've done almost nothing to modify it from defaults.

The WinXP install is also pretty default. It is running on a workgroup setup, on a standard IP4 DHCP setup. All the network shares are password protected (i.e. guest access is disabled for them all).

So, I guess I'd need a sync tool that can access Windows shares. Does anyone have any recommendations? 

I'm quite confortable setting up Samba or other such software on the laptop is necessary, but if any software is required that I haven't heard of I will probably need some help with it.


Ta for any help.

---

### Post by gerbman on 2008-04-21
You might try mapping the Windows share in Ubuntu and using rsync to keep the folders in sync.

---

### Post by tendrousbeastie on 2008-04-21
Thanks for the suggestion. I don't suppose you could give me a hint as to how I'd put together a 'mount' command to map a windows share? 

I can probably figure our rsync myself, but I get very confused with the addressing schemes in Linux compared to Windows - in Windows you can pretty much just address a network share using the format //hostname/share_name/folder/. I understand that linux can operate using something like smb://hostname/share_name but it seem to me lke a lot of software can't use the smb protocol inherently. 

Is this a fair understanding or have I got something wrong?

---

### Post by gerbman on 2008-04-21
> **tendrousbeastie said:**
> Thanks for the suggestion. I don't suppose you could give me a hint as to how I'd put together a 'mount' command to map a windows share?

I think you can use the GNOME GUI to map shares:  Places -> Connect to Server 

> I can probably figure our rsync myself, but I get very confused with the addressing schemes in Linux compared to Windows - in Windows you can pretty much just address a network share using the format //hostname/share_name/folder/. I understand that linux can operate using something like smb://hostname/share_name but it seem to me lke a lot of software can't use the smb protocol inherently. 

Is this a fair understanding or have I got something wrong?

Once you have the share mapped, you can treat the mapped folder like any other folder on your local machine. Suppose your mapped folder is at /mnt/windows_share, running```
rsync /home/ubuntu_share /mnt/windows_share
```should keep the folders in sync. rsync has lots of options to give you the synchronization behavior you want (check out the man page).

---

### Post by tendrousbeastie on 2008-04-21
Thanks for your help with this. Sounds simply enough.

So, a default rsync like you describe will just bring each folder up to the same level. I guess there are more options for conflict resolution and the like that I'll need to investigate.

Do you know if the Gnome GUI adds the mounted network drive to my fstab file, or it the behind the scenes stuff in a different config file?

---

### Post by gerbman on 2008-04-21
> **tendrousbeastie said:**
> So, a default rsync like you describe will just bring each folder up to the same level. I guess there are more options for conflict resolution and the like that I'll need to investigate.I think you'll need to run two rsync commands, one to send files from the Ubuntu share to the Windows share, and one to bring files from the Windows share to the Ubuntu share. Have a look at the --archive and --update options, which should be what you want.

> Do you know if the Gnome GUI adds the mounted network drive to my fstab file, or it the behind the scenes stuff in a different config file?I don't think the GUI adds it to fstab, but read [this]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html") on how to do so.

---

