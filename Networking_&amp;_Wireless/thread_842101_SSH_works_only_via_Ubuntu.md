---
title: "SSH works only via Ubuntu"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by Tetsujin-28 on 2008-06-27
The SSH server on my Ubuntu desktop machine has stopped working via remote connections from the Internet or my LAN, even though it still works when connecting directly from the localhost.

From a shell on the desktop, 

ssh username@localhost

  and

ssh username@127.0.0.1

both succeed in giving me an SSH connection to the server on the localhost. However, when I try

ssh username@192.168.1.100

(192.168.1.100 is the server's IP address on the LAN) I eventually get:

ssh: connect to host 192.168.1.100 port 22: Connection timed out

I get timed out regardless of whether I try the connection from the server itself, another machine on the same LAN, or a machine out on the Internet (substituting my outside IP address for the internal address given above). 

I've confirmed that my router is set to forward Port 22 to the desktop machine that's running sshd. I've also confirmed that sshd is listening to port 22 on address 0.0.0.0

Anything I might be missing that could interfere with these connections, even though sshd seems to be working?

Thanks  -T.

---

### Post by perfecttao on 2008-06-27
Can you do an IPtables -L 

It looks like it's a local firewall issue.....

---

### Post by Archmage on 2008-06-27
> **Tetsujin-28 said:**
> I've confirmed that my router is set to forward Port 22 to the desktop machine that's running sshd. I've also confirmed that sshd is listening to port 22 on address 0.0.0.0

Maybe I'm mistaken aber shouldn't this listen to 127.0.0.1 and 192.168.1.100?

---

### Post by superprash2003 on 2008-06-27
yea.. it should listen to 192.168.1.100

---

### Post by Tetsujin-28 on 2008-06-27
iptables -L shows:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   


I understood from other posts on these boards that setting the listening address to 0.0.0.0 (which was the default, and seemed to work for me before) made the machine listen on the designated port for all addresses. Is this not right? I'll try setting the listening address to 192.168.1.100 and see what happens.

---

### Post by Tetsujin-28 on 2008-06-28
>headsmack<

Looks like a recent power problem messed up my router. Not a problem with OpenSSH after all.  Thanks all.

---

