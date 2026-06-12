---
title: "only root can mount / umount"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by rbprogrammer on 2006-09-04
ok, so this problem is not a big deal, but it's one of those things that i would prefer to have fixed.

i have a network drive at school and i can mount it and unmount it through the (System Settings -> Disk and Filesystems) (kubuntu) perfectly fine. also the read/write permissions works perfectly for the correct users and groups.

the problem is that the samba icon (mounted & unmounted) on the desktop does not work.  i get an error message saying that only the root user can mount / unmount.  this happens when i click on it or if i right click then select mount or unmount.  is there a way to get other users or a group the ability to mount / unmount?

---

### Post by madoka on 2006-09-04
Add the network drive to /etc/fstab.  Then all users should be able to mount / unmount it.

---

### Post by rbprogrammer on 2006-09-04
sorry, i forgot to put this in my post. i already had this in my /etc/fstab

//win.pass.psu.edu/dfs /mnt/PASS smbfs uid=1000,gid=111,noauto,rw,user,credentials=/etc/fstab_smb_credentials_1 0 0

would it be a problem with samba? or is it a mount/umount command error?

---

### Post by joeashcraft on 2008-01-28
Did you ever figure this out?

---

### Post by rbprogrammer on 2008-02-01
> **joeashcraft said:**
> Did you ever figure this out?

in a way i did.... since the creation of the post, i switched from Kubunut to Ubuntu.  now i dont get an icon on the desktop, but i am able to get to the networked university drive.

all i do is connect to the university's network via their vpn client, then open nautilus and just manually type in the url. ie smb://username@university.name.edu/my/folder/path

that probably wont help anyone if they had the same issue, but then again since i created the post there have been updated versions of ubuntu.

---

