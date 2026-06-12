---
title: "NTFS File Sharing"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Anthony M on 2008-04-29
When trying to share any of the files on my NTFS data drive I get the error :

```
Could not change the permissions of folder "xxxxx"
```

What I am doing is simply Right Click>Sharing Options....

I have installed Samaba from Add/Remove.

What else do I need to do? I was able to get samba working in Gutsy, but cannot now in Heron

Thanks!

---

### Post by jetsam on 2008-04-29
NTFS drives mount by default with permissions too restrictive for simple Samba sharing.

Have a look at the second post in this thread:
[http://ubuntuforums.org/showthread.p...ght=NTFS+mount]("http://ubuntuforums.org/showthread.php?t=417785&highlight=NTFS+mount")

Hopefully this will fix the problem so you can use the gui to set up a share.  If it still doesn't work, it should be possible to set up your share manually by editing your smb.conf.

---

### Post by Anthony M on 2008-04-29
Ok, i am now able to share the folder but it still does not show up on my XP machine over the network.

What else is needed?

I have also tries following this guide to no avail:

```
http://ubuntuforums.org/showthread.php?t=202605
```

Thanks!

---

### Post by superprash2003 on 2008-04-29
you need to restart samba for that..type
sudo /etc/init.d/samba restart

---

### Post by jetsam on 2008-04-29
If the restart doesn't do it, double check that you've entered the right workgroup name in System-->Administration-->Shared Folders-->General Properties.  

Rebooting the machine and waiting a bit sometimes works.  Netbios browsing is flaky that way.

A firewall on the Windows machine could cause this problem.

It can cause problems if your ubuntu hostname is longer than 15 characters or has weird characters in it. 

If none of that helps, you may have hit a snag.  There are several options open still, but it may get trickier.

---

