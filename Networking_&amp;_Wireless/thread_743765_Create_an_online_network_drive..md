---
title: "Create an online network drive."
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by sswittch on 2008-04-02
Hi,

I am currently running UBUNTU 6.10 i386 and would like to create an online network drive accessible from windows machines with some sort of authentication.  I currently have a working LAMP server utilising php5.  I know this is a linux forum but I would also like to be able to map these drives on a Windows Distrib.

I want to host an accounting file (hence the authentication) that can be opened and modified and resaved to the server.

Kind Regards,

Dave

---

### Post by dmizer on 2008-04-03
not sure exactly what you're wanting to do here, but sharing files on the internet is extremely hazardous.

instead of doing this on a webserver, you may want to consider a vpn server.  that way, people can log into the vpn and join your network just as if they were local.  then they can mount samba shares just as if they were on your lan.

openvpn howto:
[http://ubuntuforums.org/showpost.php?p=1407320&postcount=5](http://ubuntuforums.org/showpost.php?p=1407320&postcount=5)
openvpn sample .conf file:
[http://ubuntuforums.org/showpost.php?p=1407374&postcount=6](http://ubuntuforums.org/showpost.php?p=1407374&postcount=6)
original thread starter:
[http://ubuntuforums.org/showthread.php?t=239219](http://ubuntuforums.org/showthread.php?t=239219)

---

