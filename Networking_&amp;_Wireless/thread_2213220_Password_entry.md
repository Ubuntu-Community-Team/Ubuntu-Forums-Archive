---
title: "Password entry"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by mohanbylapudi on 2014-03-25
Hi I am using ubuntu 10.04. Now the question is: Is it possible to login through the network after i switced on the pc by using etherwake command.

---

### Post by lukeiamyourfather on 2014-03-25
If installed, you can access the machine with the ssh command (ssh user@host). If not already installed you can install it on the server with the command below.

```
sudo apt-get install openssh-server
```

There's a bit more about it on the Ubuntu documentation site.

[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)

---

### Post by mohanbylapudi on 2014-04-03
Hi, i just waked up my system using etherwake command and i am very far away from that then without logging into system how ssh server works.

---

### Post by lukeiamyourfather on 2014-04-04
> **mohanbylapudi said:**
> Hi, i just waked up my system using etherwake command and i am very far away from that then without logging into system how ssh server works.

If the openssh-server package isn't already installed then you won't be able to connect remotely. It must first be installed on the machine.

---

