---
title: "Networking OS X and Xubuntu"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by maikunari on 2007-02-11
Hi All,
I'm trying to share files both ways between my ibook and my laptop running xubuntu dapper and I'm having a few problems.

When I try to log into the shared home folder on the xubuntu box from os x using the finder, i type in  smb://192.168.1.4  and it comes up with a dialogue box showing the correct server name, work group name and username.  When i type in the password for that user account though it says the password is wrong, but I don't remember setting any other password.  

Also, I don't know how to log into the ibook from the xubuntu box, what program should I use for this?

Any advice would be greatly appreciated.

Thanks,
maikunari

---

### Post by floof on 2007-02-11
> **maikunari said:**
> 
When I try to log into the shared home folder on the xubuntu box from os x using the finder, i type in  smb://192.168.1.4  and it comes up with a dialogue box showing the correct server name, work group name and username.  When i type in the password for that user account though it says the password is wrong, but I don't remember setting any other password.  


hello,

Probably, you didn't set a SAMBA password for the user on the xubuntu box. try the following command on xubuntu :

```

user@host> sudo smbpasswd -a user

```

where you replace user with the effective username that tries to connect.

Hope this helps.

As for connecting from the linux box to the OS X, I'm not sure, but it should be possible to run a smb server (if not already running) on it.

---

### Post by maikunari on 2007-02-11
Thanks floof,  now I can mount my xubuntu box on my os x box!! Great!!
Now to get it working the other way:)

Cheers,
maikunari

---

