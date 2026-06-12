---
title: "Getting computers on a network to talk to eachother"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by cbrands on 2007-09-23
hi
I have two feisty fawn systems connected to a router. The router is configured to use dhcp. Both computers can access the internet.  When I connect to the router I can see the hostname of both machines.

However I do not know how to make the machines to see each other.
If I try 
ssh root@hostA
I get
ssh: hostA: name or service not known

I am stuck. :-(

---

### Post by noob12 on 2007-09-23
If you are using Feisty out of the box and have not disabled avahi, you probably can use "hosta.local" and "hostb.local" as names.  Try it.

If you've got a mixed windows and linux net, I'd recommend winbind.

---

### Post by cbrands on 2007-09-23
Thanks for your reply,
unfortunately
ssh [email]root@hostA.loca[/email]l
gives me the same error

---

### Post by cbrands on 2007-09-23
I reinstalled feisty on both machines. Original problem is gone but now I get.
$ [email]ssh@hostA.loca[/email]l
ssh: connect to host hostA.local port 22: connection refused

How do I open port 22?
:confused:

---

### Post by cbrands on 2007-09-25
Problem solved. 
The openssh client is installed by default but the server is not.
apt-get install openssh-server
:p

---

