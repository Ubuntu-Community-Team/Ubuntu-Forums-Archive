---
title: "ssh"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by packetsmacker on 2008-12-19
I am trying to ssh into Ubuntu server 8 form my Mac running OS 10.4 I get this error

Please contact your system administrator.
Add correct host key in /Users/username/.ssh/known_hosts to get rid of this message.
Offending key in /Users/username/.ssh/known_hosts:3
RSA host key for 192.168.100.103 has changed and you have requested strict checking.
Host key verification failed.


It works fine using Putty on my Windows box.

---

### Post by jerome1232 on 2008-12-19
I think deleting this file "/Users/username/.ssh/known_hosts" ought to get you working.

I don't know if you edited that though, is username really your username? lol.

---

### Post by __Frank__ on 2008-12-20
Although deleting the file will work, you can just open it with an editor and remove the offending entry.

---

### Post by packetsmacker on 2008-12-21
thanks frank. removing that entry with the ip 192.168.100.103 worked.

---

### Post by bodhi.zazen on 2008-12-21
Yes you can remove the keys, but you should be asking yourself why the key changed ???

See : [http://www.securityfocus.com/infocus/1806](http://www.securityfocus.com/infocus/1806)

Now if you changed the key on the server, update the client. If you are not sure, consider checking with your (server) sys admin.

---

