---
title: "Linux Fat Clients?"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Phantom784 on 2007-05-07
Is there a way to set up Ubuntu systems (or other Linux systems, for that matter) to be thick clients?  By this, I basically mean being able to have one user name that works throughout a computer lab (or whatever) and lets your home folder follow you, like what many schools do with windows machines.  I'm assuming that this would be done with some sort of central server.

---

### Post by organica on 2007-05-07
> **Phantom784 said:**
> Is there a way to set up Ubuntu systems (or other Linux systems, for that matter) to be thick clients?  By this, I basically mean being able to have one user name that works throughout a computer lab (or whatever) and lets your home folder follow you, like what many schools do with windows machines.  I'm assuming that this would be done with some sort of central server.

Well, i'm no linux sys admin yet, but you could set up your /home folder on a main server.  All the clients would use the /home folder on the server as a network mount at boot.

---

### Post by Phantom784 on 2007-05-07
Yes, but I'm looking at each user having thier *own* home folder that gets mounted from a central location, based on the name they use to log in.  And is there any software/tutorials for/about setting up a network like this?

I've read a lot about linux *thin* clients, but nothing about fat clients, which is why i'm wondering if it's been done, especailly considering pratically every school's windows labs use something like this.

---

### Post by insane_alien on 2007-05-07
why would they need separate home folders? surely having separate user folders within a central /home folder would be more efficient it would do the same thing.

---

### Post by Spartan.II.117 on 2007-05-07
what you're looking for is basicly a roaming user(or a bunch of them) this is wow the computerlabs work, i'll look into how this is done.

---

### Post by Spartan.II.117 on 2007-05-07
aha! i found it!

active directory is how windows gets it's users to comply with the server permissions.

From: [http://ubuntuforums.org/showthread.php?t=351580](http://ubuntuforums.org/showthread.php?t=351580)

> **irongeek said:**
> Well, you can make a Linux box authenticate against Active Directory via kerberos and winbind. It's easier to do in OpenSUSE than in Ubuntu. Heres some info on doing it in Ubuntu:
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by christhemonkey on 2007-05-07
And if you are wanting the server end to run linux as well:
[https://help.ubuntu.com/7.04/server/C/openldap-server.html](https://help.ubuntu.com/7.04/server/C/openldap-server.html) (this link is for feisty specific)
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer) (whereas this seems mildly outdated)

---

### Post by Phantom784 on 2007-05-08
I see what you're saying with just a shared /home folder, for some reason i was only thinking of a /home/whatever that switched on every logon.  I'm assuming that /etc/passwd would also have to be linked to the server.  However, instead of also linking /etc/shadow, is there another way to get user accounts to authenticate with the server?  (linking /etc/shadow doen't quite seam safe)

---

### Post by netztier on 2007-05-08
> **Phantom784 said:**
> Is there a way to set up Ubuntu systems (or other Linux systems, for that matter) to be thick clients?  By this, I basically mean being able to have one user name that works throughout a computer lab (or whatever) and lets your home folder follow you, like what many schools do with windows machines.  I'm assuming that this would be done with some sort of central server.

Whithout knowing exactly how to to this all with Linux/Ubuntu, think along these lines and terms:

You need some central user database that will - in a nutshell - replace each clients local /etc/password, /etc/group  an the other stuff-like-that files. Instead of searching information in these files, the local authentication module queries a server (and maybe then caches the result for some time). **NIS** is one of the "classic" UNIX ways to do this, **LDAP** might be another, more modern way (basically Window's ActiveDirectory is also LDAP-based, if we oversimplify a bit). The key is to have consistent UID/GID numbers for all users across your domain.

Then you need some central repository for your home directories - an **NFS server** might come in handy here. It might be possible to do it with Samba, but NFS is what is "native" to unixoid operating systems. Upon login, each user's home directory gets mounted into the local filesystem at /home/<username>. 

Some shared directories for "team directories" might be a good idea, too. And if your environment is going to be large, don't forget to think of disk quotas. The NFS server can of course be the same machine as the one with the LDAP server on; this of course depends on how large your environment is going to be.

I'm sure that there's tons of other things to consider (like running your own DNS/DHCP server for your local domain, so that forward and reverse lookups are always fast and accurate) and then a truckload or two more - I'm just trying to give a few directions.

best regards

Marc


One possile starting point for a bit of reading: [http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap) and maybe [http://home.subnet.at/~max/ldap/](http://home.subnet.at/~max/ldap/)

---

### Post by Phantom784 on 2007-05-08
Based on some of the protocol names and documents you found, I found the following handbook all about setting up a computer lab in Linux.  Hopefully someone will find it useful :)

[http://www.vanemery.com/DAS/DAS-manual.html](http://www.vanemery.com/DAS/DAS-manual.html)

---

