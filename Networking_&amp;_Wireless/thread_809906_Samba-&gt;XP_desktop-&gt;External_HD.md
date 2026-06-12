---
title: "Samba-&gt;XP desktop-&gt;External HD"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Melk79 on 2008-05-27
I'm trying to get to my Western Digital External HD, which is hooked into my WinXP Desktop, to work remotely with my laptop below.  I can access my desktop shares fine (both read and write) and that functionality worked right out of the box.  I've made the External HD shared from the Windows box, but I get prompted for a password to access the drive when navigating with Nautilus from my laptop.  Nothing I enter works, but the default lists my ubuntu username and a domain of WORKGROUP.  On another [post]("http://ubuntuforums.org/showthread.php?t=809560") today, it refers to creating a samba password, but I'm hesitant to do that since I'm working great with the desktop itself right now.  Any thoughts on the next steps?

---

### Post by Melk79 on 2008-05-28
Bump

---

### Post by superprash2003 on 2008-05-28
samba username is required only if you want to share files present in your ubuntu machine which is to be accessed from xp.. but this is just the opposite.. open windows explorer, click on Tools->Folder Option and click on View ( i think) and ensure that "Enable Simple File Sharing" in unchecked, now try sharing files.. and when a username and password is prompted in ubuntu, enter the username to access windows xp..

---

