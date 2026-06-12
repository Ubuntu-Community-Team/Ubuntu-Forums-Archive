---
title: "scp as root with rsa key"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by peterroots on 2008-11-19
Hi I have created a problem for myself!!
I have a network that I have set myself up to access several machines by ssh using rsa key pairs and stopped password logins.
works fine
the problem is if I now want to copy a file to a root owned area on another computer I can't do it with scp as only I have access to the computer by ssh with my key.
Normally I would work on the other computers, having logged in as myself, with sudo to get root access.
Obviously I could copy the file to my home folder using scp then login with ssh and sudo cp the file to where I want it but I have a file (sources.list) I want to copy to several computers to get them all using my apt-cacher server for updates.  Seems a bit of a fiddle whereas with a straight scp to the target I just need to keep editing the ip address to repeat the process.
any ideas?

---

### Post by DonnieP on 2009-01-03
Did you ever get an answer to this?  I have the same question.

---

### Post by peterroots on 2009-01-15
no afraid I did not

---

