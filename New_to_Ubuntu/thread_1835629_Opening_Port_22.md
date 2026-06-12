---
title: "Opening Port 22"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by Tinker Tantrum on 2011-08-29
When I type in this command:
```

ssh localhost

```
I get this output:
```

ssh: connect to host localhost port 22: Connection refused

```
My question is: How do I disable the firewall for Port 22.

FYI: I am following the examples in a .pdf book called "The Linux Command Line by William E. Shotts,Jr.".

---

### Post by BitJunkie on 2011-08-29
Is the ssh server (sshd I think) running on your local system? It sounds like there is nothing listening for incoming ssh connections.

---

### Post by bodhi.zazen on 2011-08-29
You have to install and start openssh-server

---

### Post by whitethorn on 2011-08-29
Have you installed the SSH server and started it? 

[https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html)

Have a read here, it'll help you get ssh up and running. Once it's running you can then connect to localhost.

---

### Post by Tinker Tantrum on 2011-08-29
AH HA! That was it. Thanks everyone.

---

### Post by lkraemer on 2011-08-30
You need to be very careful if you are forwarding Port 22 on your Router.

That PDF Document states "if the system is either running or is behind a
firewall it must allow incoming network connections on TCP port 22."

But, if you are on your LAN (Local Area Network) and not connecting via the
WAN (Wide Area Network), then you **DO NOT need to Forward Port 22** on your
Router.  By forwarding your Router's Port you will be continuously attacked
by others in foreign countries, etc.  You can verify this in your logs.

Try playing on your LAN with the Port not Forwarded, or Forward a Higher
Numbered port (50000) to your Routers Port 22 for SSH, and use KEYS, not Passwords.
That will prevent access attempts.

Don't be fooled into thinking your system is SAFE & SECURE, with your Routers Port 22
forwarded.

 
REF:
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11500](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11500)

LK

---

