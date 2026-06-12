---
title: "Avahi not working for remote hosts"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by mvsjes2 on 2008-11-22
I have avahi installed in my home network. I like to use it so I can refer to my hosts as 'hostname.local' without any further config. I've had this working on several releases previous to hardy, but since hardy it no longer works.

If I'm on my host 'front1', I can ping 'front1.local' successfully, but I can't ping 'master.local'. If I'm on host 'master', I can ping 'master.local', but can't ping 'front1.local'. In other words, I can only access the local host, not a remote one.

I've searched all over and all I can find is that you merely have to have avahi-daemon running and it all should work.

Any ideas?

---

### Post by Iowan on 2008-11-24
On my Gutsy machine, there is a /etc/avahi/hosts file.  I suppose it could be edited, but I suspect it should happen automatically.  There is also a /etc/avahi/avahi-autoipd.action file that could be investigated.

---

