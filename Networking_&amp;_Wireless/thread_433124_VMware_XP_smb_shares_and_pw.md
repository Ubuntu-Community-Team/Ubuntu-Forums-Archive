---
title: "VMware XP smb shares and pw"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by SteinbergerNate on 2007-05-04
Hello,
I've been using XP on a vmware machine for a while now and using an SMB share to transfer data back and forth between the host and client os. It's working great except even though I checked the box to reconnect at startup, it still doesn't reconnect at startup and it asks me for a password when I go to connect to the share (I have the share mapped to a drive letter) 

It works, but I've finally gotten annoyed enough with it to try to get it to work the way I want it to work. Does anyone know what the problem could be?

---

### Post by ola on 2007-05-04
Hi!

I'm not really sure about this but I had some similar issues that were solved by changing my login name in Windows to be the same as my login name (and samba name). It might be worth a try!

If that doesn't work you could try to change security to share instead of user in Samba. This means that you can access your shared folders based on the Linux permissions instead of using a user name to login to samba. If you go this route you probably will want to change the interfaces and bind interfaces to limit Samba to only allow your VMWare image to have access.

---

### Post by SteinbergerNate on 2007-05-10
Ah ha! Thank you! I had my username on XP the same as linux but I had no password associated with that username. I assigned a password that was the same as linux and voila! It worked like a charm!

---

