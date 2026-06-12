---
title: "How do I set up an SSH server and forward X?"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by IAmAnarch on 2010-06-07
I would like to set up an SSH server and forward X over it. How?

---

### Post by nhasian on 2010-06-07
on the server simply install openssh-server

```
sudo apt-get install openssh-server
```

then on the client use the terminal to log into the server with the -X switch to enable X11 forwarding.

for example:

```
ssh -x username@ipaddress
```

---

### Post by Joeb454 on 2010-06-07
> **nhasian said:**
> on the server simply install openssh-server

```
sudo apt-get install openssh-server
```

then on the client use the terminal to log into the server with the -X switch to enable X11 forwarding.

for example:

```
ssh -x username@ipaddress
```

Note that if it's on a remote server - that server will also need X11 installed, else nothing can be forwarded ;) I know it sounds simple, but it's a common trap to fall into

---

### Post by IAmAnarch on 2010-06-07
> **nhasian said:**
> on the server simply install openssh-server

```
sudo apt-get install openssh-server
```

then on the client use the terminal to log into the server with the -X switch to enable X11 forwarding.

for example:

```
ssh -x username@ipaddress
```
And which port would I need to have forwarded by the network administrator to make it accessible over the Internet?

---

### Post by Sandertje on 2010-06-07
Port 80 is the common internet port over which http requests are done. You could also use port 443 if you want it secure (https).

EDIT: it all comes down what you want to do with it. A couple of friends of mine use ssh through port 80 so they can use IRC at their university (which block any other port than 80 or 443), for instance. In theory, you could use a lot of ports, depending on what you want to do with it.

---

### Post by bodhi.zazen on 2010-06-07
> **IAmAnarch said:**
> And which port would I need to have forwarded by the network administrator to make it accessible over the Internet?

By default ssh uses port 22.

Just make sure you understand how to secure the server -

use ssh keys, disable passwords, and use iptables or denyhosts or fail2ban to block brute force attempts.

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by IAmAnarch on 2010-06-07
> **Sandertje said:**
> Port 80 is the common internet port over which http requests are done. You could also use port 443 if you want it secure (https).
I think that that one is blocked for incoming connections too. Cox doesn't like web servers unless you have a special plan that allows it. I did some research a while back for another project to see if there was an unassigned port and found 2400. IDK if it's still unassigned.

**EDIT:** wrong topic

---

### Post by alphacrucis2 on 2010-06-07
> **IAmAnarch said:**
> And which port would I need to have forwarded by the network administrator to make it accessible over the Internet?

The default port for ssh is tcp 22.

---

### Post by IAmAnarch on 2010-06-08
> **alphacrucis2 said:**
> The default port for ssh is tcp 22.
Whoops, wrong topic!

---

