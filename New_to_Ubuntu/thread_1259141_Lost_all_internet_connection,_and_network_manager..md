---
title: "Lost all internet connection, and network manager."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by kronos262 on 2009-09-06
I lost all connection in Xubuntu.

I came home, and went on, and I kept getting failed connection.

Then I noticed at the top I lost where it showed I was connected to the internet.

I go to network and notice network manager was gone.

So I did sudo su apt-get install network-manager net-tools and it says it fails to install. 

Any help on this one?

---

### Post by coldReactive on 2009-09-06
What's the output of terminal when you run network-manager in it?

---

### Post by kronos262 on 2009-09-06
you mean after the apt-get install

unable to fetch some archives.

---

### Post by coldReactive on 2009-09-06
> **kronos262 said:**
> you mean after the apt-get install

unable to fetch some archives.

That's because you're not connected to the Internet.

I meant what happens when you run network-manager ITSELF in Xubuntu's terminal.

---

### Post by kronos262 on 2009-09-06
it tells me to install it.

---

### Post by izziere on 2009-09-06
Is it just wireless that is failing?  Do you still have a wired connection?

Post the output of /etc/network/interfaces and ifconfig here.

---

