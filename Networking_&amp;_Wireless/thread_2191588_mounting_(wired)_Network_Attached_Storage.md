---
title: "mounting (wired) Network Attached Storage"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by amerkfan on 2013-12-03
[COLOR=#333333]I have an Ubuntu 12.04 server set up and I want to create a mount point for the Corza NAS in fstab. Being a newbie I am having trouble finding the correct path to the device (on my network at 192.168.0.12). I tried \\192.168.0.12\root also \mnt\md1 and a couple others. I tried creating a credential file and mount-cifs, but still no luck.

[/COLOR][COLOR=#333333]I need to figure out the path to use to mount this NAS. I've tried the two above, including /public at the end, I've tried several variations (changing the ip to the device name, etc.) of 'mount -t ext3 //192.168.0.12:/NAS-2TB/public /mnt/nas2tb -o username=xxxxxx,password:xxxxx' and get the message: mount: special device 192.168.0.12:/NAS-2TB/public does not exist also /home/tom# 'mount -t cifs //192.168.0.12/public /mnt/nas2tb' got prompted for a password and received this: mount error(13): Permission denied. I am using the correct username/password combo, or at least the one I use to access the drive with Windows and to access the admin screens. [/COLOR]

[COLOR=#333333]I am trying to get it to mount before I edit fstab, and I am at a loss. Any help or suggestions are greatly appreciated. I am setting this up as a backup device.[/COLOR]

---

### Post by Kirboosy on 2013-12-03
The basic mount command is *```
mount -t cifs //<server>/<share> <mountpoint>
```*

You should try the following

```

mount -t cifs //192.168.0.12/public /mnt/md1 
```

There might be a bit more too it but the fstab will end up looking something like this
```
//192.168.0.12/public /mnt/md1 cifs  guest,uid=1000,iocharset=utf8  0  0
```

[Mounting Samba Shares from a Unix Client]("https://wiki.samba.org/index.php/Mounting_samba_shares_from_a_unix_client")

Hope that helps!
~Caboose

PS there is also official documentation on the Ubuntu Wiki
[Mount Windows Shares Permanently ]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

---

### Post by amerkfan on 2013-12-03
Excuse my ignorance but I tried both the methods, for the mount command I am prompted for a password which I entered and get an error "mount error(13): Permission denied". I also have another nas on 192.168.0.10 which now mounts correctly using your suggestions, both are set up with the same user/pw combos, so I am perplexed why they both don't work. They are both Patriot Nas, on is a Corza (192.168.0.12), the other a Valkarie (192.168.0.10). One thing, I don't know if it makes a difference, is that the .12 nas has a different user for admin, where as the .10 nas has the user that is the same as the windoze and Linux users. Also, any suggestions on how I can add a credentials file for each? would that help in the permission denied error?

Thanks for your help and patience

** update: using the resource above [Mount Windows Shares Permanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") I came across a solution. For the older nas, I added domain=<mydomain> to the fstab entry and it works. I'd still like to get instruction on how to add a credential file

---

### Post by Kirboosy on 2013-12-03
I would recommend changing the settings from .12 to match .10 since you know that .10 works. 

If you don't want to change it for.12 from the fstab will look something like this

```
//192.168.0.12/public /mnt/md1 smbfs username=**username_of_nas**,password=**password_of_nas**,uid=**your_id**,gid=**your_group_id** 0 0
```

The bold words would obviously need to be substituted for your real credentials. 

~Caboose

---

### Post by amerkfan on 2013-12-04
Thanks for the help, I have it working now

---

### Post by Kirboosy on 2013-12-04
Ok great! I'm not sure how much help I was but I'm glad you got it solved.

~Caboose

---

