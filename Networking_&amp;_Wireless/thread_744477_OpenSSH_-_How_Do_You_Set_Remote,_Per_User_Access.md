---
title: "OpenSSH - How Do You Set Remote, Per User Access?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by umechanism on 2008-04-03
I use OpenSSH to connect to my Linux machine remotely and wish to allow my father to connect as well under his own username and password.  I have created a username and password for him on my machine (he lives two states away :) ).  I tested the connection from my office computer (remote) by logging in with FileZilla sftp and entering his username and password.  It connected just fine but he has access to every folder on my machine!  I only want him to have access to one particular folder that I have setup for him.  How do I do that?  

Basically, I only want him to see one folder and not be able to browse anywhere else on my computer.  Instructions on how to do this would be greatly appreciated.

Thanks!

---

### Post by warp99 on 2008-04-03
You can use rbash (restricted bash) to keep him to his own home directory:

[http://nthillaiarasu-linux.blogspot.com/2008/01/openssh-deny-or-restrict-access-to.html](http://nthillaiarasu-linux.blogspot.com/2008/01/openssh-deny-or-restrict-access-to.html)

---

### Post by Eiríkr on 2008-04-03
What you want sounds like chrooted ssh access.  Have a look [here]("http://www.howtoforge.com/chrooted_ssh_howto_debian") and [here]("http://www.minstrel.org.uk/papers/sftp/") for ideas on how to set that up.

Cheers,

Eiríkr

---

