---
title: "Auto mounting drives at login."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by WastePotato on 2009-01-18
Hi. 

How can set Ubuntu to auto mount my Vista partiton (NTFS) at login/boot?

Secondly, how can I prevent mounted drives appearing on my desktop?
It's annoying as hell. :(

Any help would be appreciated. Thanks. :)

---

### Post by WastePotato on 2009-01-18
:(

---

### Post by sully101 on 2009-01-19
You could install autofs and have it mounted when you access it or you need to edit your /etc/fstab.

type ```
man fstab
``` in a terminal to read the manual or do some googling to find a how to

---

### Post by cjv8888 on 2009-01-19
Have a look at this How To for Automounting any drive at boot.

[HTML]http://ubuntuforums.org/showthread.php?t=802699&highlight=automount+boot[/HTML]

---

### Post by Messyhair42 on 2009-01-19
post output of these commands in a terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

i used the ntfs configuration tool

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

it can set a mount point for ntfs drives. unmount the ntfs before doing this though

---

### Post by vanadium on 2009-01-19
A remark: bumping a thread after 30 minutes is considered rude. It is fine to bunp a thread after 24 hours, though.

For the "icons", there are some options

1) You can disable the display of drive icons on the desktop all together. Drawback is that also icons for USB sticks or removable hard drives will be gone, which might not be what you want.

2) If you only want to get rid of icons of permanently mounted drives, then mount the drives under /mnt instead of /media. Only drives mounted under /media do show on the desktop. With this approach, USB drives will still acquire an icon on the desktop.

---

### Post by WastePotato on 2009-01-20
> **vanadium said:**
> A remark: bumping a thread after 30 minutes is considered rude. It is fine to bunp a thread after 24 hours, though.

For the "icons", there are some options

1) You can disable the display of drive icons on the desktop all together. Drawback is that also icons for USB sticks or removable hard drives will be gone, which might not be what you want.

2) If you only want to get rid of icons of permanently mounted drives, then mount the drives under /mnt instead of /media. Only drives mounted under /media do show on the desktop. With this approach, USB drives will still acquire an icon on the desktop.


I was told by staff that it's rude to bump a thread if it hasn't even fallen off of the page yet. They said that if it's off the page, it's ok. :oops: 

1) Yes, I'd rather have that option. I don't like any icons on my desktop. How do I do that? :(

Thanks.

---

### Post by Joeb454 on 2009-01-20
I use the guide in my sig to Automount my Vista partition (and yes, I did write the guide :p). It works fine, and I think it's a nice easy way to do.

To hide the drives from your desktop, open up gconf-editor (either from a terminal or Alt+F2), and I believe it's under

Apps > Nautilus

You need to find "Show volumes on Desktop" and uncheck it. I can't remember if that's exactly where it is in gconf, because I'm not on ubuntu right now :(

---

### Post by drs305 on 2009-01-20
> **Joeb454 said:**
> To hide the drives from your desktop, open up gconf-editor (either from a terminal or Alt+F2), and I believe it's under

Apps > Nautilus

You need to find "Show volumes on Desktop" and uncheck it. I can't remember if that's exactly where it is in gconf, because I'm not on ubuntu right now :(

```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

Change the value to 'true' to display them again.

---

### Post by WastePotato on 2009-01-20
!!!!

Thanks! \o/

---

### Post by Joeb454 on 2009-01-20
> **drs305 said:**
> ```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

Change the value to 'true' to display them again.

Well that certainly makes things easier ;)

Thanks drs305 :)

---

