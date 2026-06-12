---
title: "How can I Specify Folders for Users in Samba."
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by celliott on 2008-04-10
Hi all,

I currently have samba setup on my server and it works great. However, i want to create different users and i only want them to have access to specific folders. I also dont want them to see the other shared folders at all.

Is this possible?

Thanks
Chris.

---

### Post by Eiríkr on 2008-04-10
It's possible by setting the "valid users" and "browseable" options in the share definitions.  However, note that setting "browseable = no" means that *no one* can browse to that folder -- they'll have to know it's there.  If the users are on Windows, they can map a network drive once, and mark the "Reconnect at logon" box in the dialog, and then that drive (i.e. the share) will mount automagically every time they log on, so they don't have to remember where the share is.  

If you need browseability, you can still use the "valid users" option to restrict who can get in.  For example, with "valid users = mike, joe, fred" and "browseable = yes", while everyone will be able to see the share, only users mike, joe, and fred will be able to open it.  

Cheers,

Eiríkr

PS -- See the man page sections for [valid users]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDUSERS") and [browseable]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BROWSEABLE") for details.

---

### Post by celliott on 2008-04-10
So there is absolutely no way to make the folder hidden to all users except valid once for that share?

Thanks.

---

### Post by Eiríkr on 2008-04-10
Read my post again -- you *can* make a Samba share hidden, and valid for only one user.  The only trouble is that you cannot make a Samba share hidden for only one user -- it's hidden for everyone, or it's visible for everyone.

---

### Post by celliott on 2008-04-10
Sorry, i mistyped i wanted to know if you were absolutely sure that when u hide a folder, ALL users cannot see it. Even the ones that i want to see the folder.

Thanks

---

### Post by Eiríkr on 2008-04-10
So far as I've seen, if you set "browseable = no", then no user can browse to it.  There's apparently no way of specifying which users can see and which can't, so it's kind of an all or nothing deal.  

Although hiding the folder means no one can see a share, you can still access it directly by means of the Samba pathname, like **\\server\sharename**.  So if the [sharename] definition section in your smb.conf file has "browseable = no", anyone looking at **\\server** will *not* see it, but if they type in the full path, they can still get to it (provided that, if you're using "valid users", their username is listed on that line).  

Cheers,

Eiríkr

---

