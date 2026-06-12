---
title: "Samba Help (sharing help)"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by eighto2 on 2007-01-06
So I'm able to share via samba, my roomate has his own login/pswd and can access my shares... great, but what i was wondering is there anyway to allow a user to access 1 folder, but not access another, would that have to be added somewhere in the samba.conf or  is there an advanced samba tool out there?

---

### Post by kidders on 2007-01-06
Hi there,

You mean you'd like to be able to give someone access to your server, but lock them out of certain shares? One way of doing this is to use the "valid users" directive for a given share. For instance, you could try something like "valid users = root,@video" to lock out anyone that wouldn't be able to start an X session locally.

I'm sure there are many pretty graphical tools that can do this sort of thing for you, but I always find it more convenient to tinker with smb.conf directly. :-)

---

### Post by eighto2 on 2007-01-06
But i dont want to lock him out of starting an xsession, and i dont mind if its a non gui way to do this,,.

---

### Post by kidders on 2007-01-07
> **eighto2 said:**
> But i dont want to lock him out of starting an xsession.

Then don't. Samba has no control over that anyway. :-)

---

