---
title: "apt-get internet access"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by derek71 on 2010-06-19
I have installed Ubuntu 10.04 server and I am configuring Shorewall 4.4 as the firewall.

I would like to restrict access between the machine and the rest of the world via explicitly allowing connections to the sites needed for time sync, software updates and such.

My question is what sites/ports are required to access the apt-get repositories?  What other sites are required by the OS?

---

### Post by 3rdalbum on 2010-06-19
> **derek71 said:**
> I have installed Ubuntu 10.04 server and I am configuring Shorewall 4.4 as the firewall.

I would like to restrict access between the machine and the rest of the world via explicitly allowing connections to the sites needed for time sync, software updates and such.

My question is what sites/ports are required to access the apt-get repositories?  What other sites are required by the OS?

You want to restrict outgoing connections? To what purpose, exactly? Normally with firewalls you just restrict incoming connections, and leave outgoing connections uninterrupted.

Apt-get works on HTTP (port 80 TCP outbound) as far as I know, but it does depend on what mirror you are using as some mirrors run on FTP (port 21 TCP outbound).

As you've posted in Absolute Beginner Talk I'm assuming that you are getting mixed up between incoming and outgoing connections; in order to use Apt-Get or check your e-mail etc you only use an outgoing connection, which is safe. You don't use any incoming connections to do these things.

---

