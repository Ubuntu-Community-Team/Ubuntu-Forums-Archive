---
title: "Remote file access"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by MedellinManDem on 2009-02-20
If I want to access my Ubuntu filesystem (as opposed to access the desktop) from another location, how do I go about doing this?

This includes reading, writing, editing, and downloading. I'm thinking an FTP, but I'm not 100% sure.

Thanks.

---

### Post by ja660k on 2009-02-20
youll need to open port 22 on your firewall/router.
get a dns  hosting service like dyndns
and in ubuntu install openssh

then you can ssh and sftp into your home computer and write/read/remove/upload data...

---

### Post by olangelsa on 2009-02-20
Hello.

I have the same requirement myself and find it to be solved by using openssh. I believe the package is available through Synaptic Package Manager. I think it is called openssh-server, not sure about that though.

I have configured it to use public key authentication. Works very well, and is supposedly quite a bit more secure than regular ftp. It allows for downloading, uploading, and also secure shell access.

Good luck

---

