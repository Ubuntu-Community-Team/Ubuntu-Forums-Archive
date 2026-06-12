---
title: "Directory server"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by alphanaut on 2007-06-03
Hi there :)

Is there an Directory server for 7.04 Server? Like the one Fedora brags about (fedora-directory-server)?

---

### Post by didijeeeke on 2007-06-03
not one made by ubuntu itself.

Openldap is a option
And you could use the fedora directory server if you want

---

### Post by alphanaut on 2007-06-03
how do I use the fedora-directory-server on ubuntu?

---

### Post by pclancy on 2007-06-06
Here is the Fedora howto: [http://directory.fedoraproject.org/wiki/Howto:DebianUbuntu](http://directory.fedoraproject.org/wiki/Howto:DebianUbuntu)
The same howto posted on Ubuntu's wiki with some more information: [https://help.ubuntu.com/community/FedoraDirectoryServer](https://help.ubuntu.com/community/FedoraDirectoryServer)
And here is the client howto: [https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto](https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto)

I tried it last summer and I was able to install it.  I'm currently revisiting that work now, but I have not had the same success.

You'll notice that at some point in the howto it tells you to do a bunch of things with install.inf, which doesn't exist in the newest version of FDS, instead you need to work on setup.inf.

---

