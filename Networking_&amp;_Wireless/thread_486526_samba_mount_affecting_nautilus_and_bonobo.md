---
title: "samba mount affecting nautilus and bonobo"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2007-06-28
Hi

I added the lines

```
//10.0.0.12/SERVER /mnt/website smbfs dmask=777,username=	0	0
//10.0.0.4/User_folders /mnt/file_server smbfs username=,password= 0 0
```

to my fstab, and with mount -a the mounts work flawless.

However, when I reboot the next morning (now), the desktop doesn't start, the pictogrammes aren't being displayed (see attach), and i cant open file browsers. 
When I rebooted the second time, it displayed error: *Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.Killing bonobo-activation-server and restarting Nautilus may help fix the problem.*

I know that if i remove the smbfs lines, it will work again, but i really like my samba shares to mount....

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=36682&stc=1&d=1183017545[/IMG]

its feisty fawn on a HP dx2200.

---

### Post by Mujaheiden on 2007-07-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/nautilus/+bug/44874/comments/4](https://bugs.launchpad.net/nautilus/+bug/44874/comments/4) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

To once again answer my own post:

> [...] When I changed the auto mount back to noauto and rebooted, the system came right up and the desktop came right up. When I then mounted the smbfs mount manually, there was no delay and Nautilus had no trouble with it. [...] I'm trying CIFS now.

---

### Post by SonicSteve on 2007-07-06
are you having any trouble with unmounting USB drives? i.e. thumb drives, external usb hard drives, etc?
I'm investigating this because I have had this same strange Bonobo message, I have smb mounts although I've been using CIFS mount options not smbfs in my fstab.

---

### Post by Mujaheiden on 2007-07-08
not that im aware of.

---

### Post by Mujaheiden on 2007-07-13
Changed in fstab from

```
//SERVER/User_folders	/mnt/file_server	smbfs	auto	0	0
```

into

```
//SERVER/User_folders	/mnt/file_server	smbfs	noauto	0	0
```

and then stated the crontab editor

```
sudo crontab -e
```

and then  added the line

```
@reboot mount /mnt/file_server
```

Next morning (reboot) it worked.

---

