---
title: "Accidently deleted smb.conf + How do i set up the following sharing"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2008-06-29
Hey everyone

I deleted smb.conf, I tried reinstalling the samba packages but nothing is happening, smb.conf just stays empty, anyone have any ideas on how to fix it?

When I do get everything working does anyone know or have any guide to set up the following kind of thing on my computer

I want a videos file that I can access and change and another user account that can access but not change, a file that I can access and change and another user account can access and change and some folders only I can access and change.

Im sorry if thats not very clear, Im not v. good at explaining myself. Any help would be great

Cheers
Gaunt

---

### Post by Wobblybob on 2008-06-29
in a [Terminal] type or copy and paste sudo touch /etc/samba/smb.conf this will give you a blank samba conf file then you may want to check out this thread [http://ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing]("http://ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing") which explains how to set-up a samba share and conf file.

---

### Post by Iowan on 2008-06-29
Here's a copy of the original.

---

### Post by mattgaunt on 2008-06-30
Cheers guys got it up and running :-)

Gaunt

---

