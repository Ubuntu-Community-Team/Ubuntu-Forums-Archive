---
title: "ssh2 via gFTP - 2 networked computers, works from 1 computer, not the other"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by held7over on 2011-03-15
Linksys Router, Ubuntu, Gnome, Firestarter, using gFTP set to SSH2 port 22:

Two Computers on home hardwired network: 192.168.2.10 and 192.168.2.11

I can execute gFTP on 192.168.2.10 and it connects with 192.168.2.11 and works just fine.  :D

However, if I am on 192.168.2.11 and execute gFTP to connect with 192.168.2.10 I get :confused:  :

```
Opening SSH connection to 192.168.2.10 
Running program ssh -e none -l lucky -p 22 192.168.2.10 -s sftp 
3: Protocol Initialization 
Error: Could not read from socket: Connection reset by peer 
Disconnecting from site 192.168.2.10 
Waiting 30 seconds until trying to connect again
---Then it repeats----
```

I have each of the two computer's firewalls configured to allow all connections from the other computer and now in addition to that I also have port 22 specifically allowed for the opposite computer also. That didn't fix the problem.

I then deactivated both firewalls and I still get the above error.

I have also deleted both .gFTP files in their respective home directories at the same time and then tried launching gFTP as a new install in 192.168.2.11 to contact 192.168.2.10 with the same failed result.

Ping:  Both computers ping each other just fine!

What's left???

---

