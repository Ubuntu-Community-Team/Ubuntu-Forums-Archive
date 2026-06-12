---
title: "Stupid CIFS/SMB Questions"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by taddy_porter on 2009-08-27
I'm trying to modify my /etc/fstab to automount a NAS drive. I connect via samba at smb://media/share. When I set mout to //media/share it can't connect. I can get an ip address to work, but my internal IP address can change. Is there a way to get the lan name to work?

---

### Post by nandemonai on 2009-08-27
The NAS should be setup with a static IP, if not I'd suggest doing so else it'll be painful to deal with.

Then just use that IP in your /etc/fstab line for mounting the NAS.

---

