---
title: "[SOLVED] Computer is blocked"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by stringkarma on 2008-06-28
I have posted some of this story already but I wanted to repost as the situation now seems to focus a little differently.

The [backstory]("http://ubuntuforums.org/showthread.php?t=839968"):

I have 3 computers. Lets call them home, work and server.

When connecting through ssh I can connect:
- from home to server
- from server to work
- from home to server to work
but when I try to connect from home to work I get:

```
ssh: connect to host ems4.rrc.uic.edu port 22: Connection refused

```

Turns out I cannot connect directly from home to work at all. VNC for example also fails.

So we check the ports.

From home to work I get:

```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-24 21:48 CDT
All 1714 scanned ports on work.workserver.com (***.***.***.***) are closed

Nmap done: 1 IP address (1 host up) scanned in 0.235 seconds
```

though from server (or home to server) to work I get:
```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-24 21:51 CDT
Interesting ports on work.workserver.com (***.***.***.***):
Not shown: 1707 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
113/tcp  open  auth
631/tcp  open  ipp
1234/tcp open  hotline
5900/tcp open  vnc
8000/tcp open  http-alt

Nmap done: 1 IP address (1 host up) scanned in 0.129 seconds
```

As per a suggestion I have made sure that all the netmasks are correct.

Also I have tried using home (a laptop) from another physical location with another ip address. Still nothing.

This leads me to believe that somehow one or the other computer is actively blocking the other.

What configuration files or blacklists can prevent nmap from finding open ports?

Thanks for any help!

---

### Post by stringkarma on 2008-06-30
Anyone, Anyone

---

### Post by lisati on 2008-06-30
Your home machine might be blocked at your work's end. Some IT departments get nervous about who they let in.

---

### Post by stringkarma on 2008-07-02
Well talking to the IT guys did help, but not because they blocked me. One of the guys took a few sessions to look at everything. Somehow the routing tables on home had a route put into place that would only let the connection occur on the work subnet. This is never possible at my house and when I take my computer to my working location I have to disconnect the work computer's ethernet cable to plug in home (a laptop). I could never have connected!
All is solved but I think this may be the strangest thing I have seen since I stared my foray into linux over a year ago.

---

