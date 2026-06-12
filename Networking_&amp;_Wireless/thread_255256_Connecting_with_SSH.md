---
title: "Connecting with SSH"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by JPMaximilian on 2006-09-11
How do I use ssh?  I know the ips of the two systems on my network, both runn dapper.  I type ssh *login*@*ipaddress* with the appropriate ips and logins.  Do I need to enable ssh on the systems or something?  Thanks.

---

### Post by DarthMandeep on 2006-09-11
You need to have a SSH server installed and running on the computer you are trying to log into. You also need an account on that computer. If you are using software firewalls, you'll need to open port 22 on the server.

---

### Post by JPMaximilian on 2006-09-11
I install openssh-server with synaptic, how do I go about running it and opening port 22?  Thanks.

---

### Post by Slychilde on 2006-09-11
It should start up automatically, the commnd to start it if SSH isn't running is

```
sudo /etc/init.d/ssh start
```

Yeah, the default port is 22, so it will automatically listen on that port.  If you want to change it edit /etc/ssh/sshd_config.  If you are asking how to set up firewall access, well it depends on what you're running.  If you want to expose it to the internet, you'll  have to open that port on your router and aim it at the openSSH box, etc.  I don't recommend you do this withough making pub/private auth keys, because you will get script kiddies trying dictionary logins.

Cheers, I hope that helps.

---

