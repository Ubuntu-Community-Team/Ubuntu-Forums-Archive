---
title: "Second hard drive not available on network"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by MacDuff on 2007-07-15
I have a second hard drive on my Ubuntu Feisty box.  It is formatted NTFS and is visible and readable from ubuntu but it is not visible from other computers on my LAN, both of which are Windows XP machines.

How can I share the second hard drive over the LAN?

---

### Post by t4thfavor on 2007-07-15
Using a samba share. You will not be able to write to it unless you install ntfs-3g.

In short you can right click on the folder and say share, then the os will install samba for you to configure.

Configure it and set up a samba password. and you will then be able to browse it with windows/linux boxes all day long.

---

### Post by MacDuff on 2007-07-15
I am sooo stupid, (he says smacking himself upside the head).  I have read two books and I am still just as dumb as when I started.  OF COURSE, Linux does not deal with DRIVES, it only deals with FILES.  I did read that somewhere but it did not sink in.  I am so used to being able to share a drive, I did not think to try to share a directory within a drive.  It works perfectly and makes good sense when you think about it.

We "windoz"  have a bit more trouble learning to use Linux because we have to unlearn some of what took us a lot of years to learn about the MS products.

Thank you for you prompt assistance

---

