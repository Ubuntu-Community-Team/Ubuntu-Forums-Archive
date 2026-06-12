---
title: "Samba shares keep timing out!"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-05-16
Hi!  I have a server hosting some samba shares.  Sometimes if I am transferring a very large file, it fails because the "connection times out."  Is there some smb.conf or other parameter I can edit that will give me more time before the connection times out?

Thanks in advance!

---

### Post by MegaJim on 2009-05-16
Do you actually get a "Timeout" message?

If not its likely a problem with the network rather than samba config ... I used to get similar problems until I switched my server from wireless to wired.

---

### Post by pi.boy.travis on 2009-05-16
I'm pretty sure the problem is with Samba, because I never get a timeout with sftp or nfs. . .

---

### Post by mprince on 2009-05-16
You could check and see if your smb.conf file has an option for 'deadtime' and adjust that.

--

Also, you might be able to workaround this by entering the IP address and connecting to the share that way: 
[I]
smb://192.168.0.*/sharename[/I]

rather than:

*smb://workgroup*

---

### Post by pi.boy.travis on 2009-05-16
> **mprince said:**
> You could check and see if your smb.conf file has an option for 'deadtime' and adjust that.

--

Also, you might be able to workaround this by entering the IP address and connecting to the share that way: 
[I]
smb://192.168.0.*/sharename[/I]

rather than:

*smb://workgroup*

I didn't see a deadtime parameter in smb.conf or the respective man page.  I'll have to try using the specific IP address.

---

