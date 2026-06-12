---
title: "Gen Faulure using beyond trust to join AD Domain"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by marc34 on 2014-09-11
I am attempting to join a Ubuntu 14.4 LTS to an Active Directory Domain. I am ruuning all of my services on windows servers (DHCP,DNS). My Ubuntu server is pullig a static address set on my DHCP client.
I downloaded:
```

sudo -s
wget http://download.beyondtrust.com/PBISO/8.0.0.2016/linux.deb.x64/pbis-open-8.0.0.2016.linux.x86_64.deb.sh

```
When I run the /opt/pbis/bin/domainjoin-cli join *mydomain.local username* I get 

```

root@ubuntu:~# /opt/pbis/bin/domainjoin-cli join *mydomain.local username*
Joining to AD Domain:   *mydomain.local*
With Computer DNS Name: ubuntu.*mydomain*.local

USername@domain password: 

Error: ERROR_GEN_FAILURE [code 0x0000001f]


```

---

### Post by marc34 on 2014-09-11
I now realize that at some point this worked. I am already on the domain lol. Its strange that it never gave me a pass though.

---

### Post by ian88 on 2015-06-03
FOR ANYONE ELSE HAVING THIS PROBLEM REMOVE THIS PACKAGE AND IT'LL FIX THE ERROR - 

> sudo apt-get remove avahi-daemon



Massive thanks to Darren in the comments - [http://www.kiloroot.com/add-ubuntu-14-04-lts-server-to-a-windows-active-directory-domain-fullest-integration/?replytocom=1733#respond](http://www.kiloroot.com/add-ubuntu-14-04-lts-server-to-a-windows-active-directory-domain-fullest-integration/?replytocom=1733#respond)

---

