---
title: "SSH Remote Login Help"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Sepherra on 2009-05-18
I am reading on terminal emulators and the term variable and am very confused. How exactly do I use ssh say from another computer to log into my ubuntu installation remotely with commands?

---

### Post by gtr32 on 2009-05-18
In short, if you have both client and server with ssh installed and configured:

ssh [email]user@server.mydomain.org[/email]

More info:

[http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

From windows, use putty:
[http://www.cse.unsw.edu.au/~helpdesk/documentation/Putty.html](http://www.cse.unsw.edu.au/~helpdesk/documentation/Putty.html)

---

### Post by XCan on 2009-05-19
Putty is available in the packate manager in Ubuntu as well. It can be quite handy if one uses a lot of bookmarks etc. You can also forward X using ssh, meaning that you can run graphical applications on the remote machine on a local machine. For graphical intense applications, make sure you use the compression flag (-C) for this though.

---

### Post by MrWES on 2009-05-19
> **XCan said:**
> Putty is available in the packate manager in Ubuntu as well. It can be quite handy if one uses a lot of bookmarks etc. You can also forward X using ssh, meaning that you can run graphical applications on the remote machine on a local machine. For graphical intense applications, make sure you use the compression flag (-C) for this though.
 

You can also use WinSCP (secure copy), if you just want to copy files to and from a Windows machine and Ubuntu.

[http://winscp.net/eng/download.php]("http://winscp.net/eng/download.php")

I would look into logging in via ssh keys versus the traditional login:password.
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")
[http://ubuntuforums.org/showthread.php?t=84399]("http://ubuntuforums.org/showthread.php?t=84399")
And I would also disable 'root' logins via
```
/etc/ssh/sshd_config
```
```
PermitRootLogin no

```

~Bill

---

### Post by gtr32 on 2009-05-19
> **MrWES said:**
> 
And I would also disable 'root' logins via


Ubuntu has them disabled by default starting from 8.04 (I think, I was able to do that in earlier versions). I don't think it is even possible to enable it anymore.

For X you need to enable XForwarding on the server side, which I don't think is enabled by default.

---

### Post by nandemonai on 2009-05-19
Remember that, if you're sitting behind a NAT connection you'll need to forward a port to your local machine (22 by default). Also if you're running a firewall you'll have to allow this port.

---

