---
title: "Question about file sharing."
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Exxi1e on 2009-10-31
Hello,

I am very new to the Linux scene and i had some questions about setting up Samba.

I currently am running Ubuntu 9.04 as a file server.  I am able to setup shares and connect them to a windows xp and windows 7 machine successfully.  The only way i can do that is to allow everyone full control to the share.

I was wondering how i would setup a share on Ubuntu using Samba so that only the administrator (myself) can have full access to the share and everyone else have read only.

I had done some research on configuring Samba but could not get the answer i was looking for.  If someone could assist me with this setup, or point me in the right direction i would appreciate it.

Thanks!

---

### Post by Oropher8598 on 2009-10-31
Short answer: this goes in your smb.conf file.
```

[exampleshare]
		path = /home/username/example
		comment = Example Samba share
		read only = yes
		write list = tom dick
		guest ok = yes

```
For more detail, see [http://oreilly.com/catalog/samba/chapter/book/ch06_02.html](http://oreilly.com/catalog/samba/chapter/book/ch06_02.html).

The rest of that book is worth reading too... :)

**Edit:** I found [this](http://codeidol.com/other/samba/) a helpful guide too, esp. the troubleshooting section ;)

---

### Post by Exxi1e on 2009-10-31
Thanks for the response. 

Ok i set it up like this, but it prompts me to enter a user name and password.

I enter the ubuntu credentials and it will not except them.  I enter them on the windows machine in the format of UBUNTUNAME\username then password.

---

### Post by Oropher8598 on 2009-11-01
If a share is set to accept guests, it shouldn't be prompting for a username/password for read access. If you've set it *not* to accept guests, you'll need to set a 'valid users' option. Then make sure you're using a username/password combination that's set to valid for the share you're trying to connect to.

Also, I'd try connecting *from the machine hosting the share*, as a start for troubleshooting auth/login problems. Eg if you run 'smbclient //127.0.0.1/sharename -U username' in the terminal you should get:
```
**$ smbclient //127.0.0.1/sharename -U username**
Password: <enter password>
Domain=[EXAMPLE] OS=[Unix] Server=[Samba x.x.xx]
smb: \> quit
```What response does it give you?

---

