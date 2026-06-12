---
title: "Windows XP machine asking for username and password of ubuntu machine"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by angus_young on 2007-09-14
Sorry if this has been asked before, but

I have a XP machine which is networked with another XP machine and my beloved Ubuntu machine.

I can happily view both XP machine files on the Ubuntu machine, but when i access the ubuntu machine on either XP machine i get asked for a username and passord first, then i can access the Ubuntu machine no problems.

When i access the ubuntu machine in either XP machine i type in the username and password but there is no way to save this, so its automatic everytime an XP machine swithes on i use my Ubuntu machine as a media server.

Is it possible to either save the username or password on the XP machines or is it possible to switch off the username and password on the ubuntu machine so XP doesnt ask for the password and username.

Cheers for any help

---

### Post by Zorael on 2007-09-14
It is such by default, but there are two things you can do.

The first way, which I don't know exactly *how* to do, is to define which "samba users" are allowed to access your shares. These users need not (?) correspond to actual users you can log onto your Ubuntu system with, but rather some meta-users created through smbpasswd, or some other similar command. There's likely a howto someplace.

The second and much easier way is to allow guests to your shares. This would allow any and all users to access them, so it's a security vulnerability, especially if you're running a wireless network. You have to edit /etc/samba/smb.conf and add "guest ok = true" to each share, which are usually defined at the bottom of the file.

---

### Post by ralvynl on 2007-09-14
@Poster,

Please post a guide, I have being trying tu access my Ubuntu shares from Windows XP but no progress, but I can access Windows Shares from Ubuntu . . Please help

---

