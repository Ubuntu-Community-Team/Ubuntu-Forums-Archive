---
title: "hostnames dont work?, only IP`s??"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by kgls13349 on 2007-11-09
Hi,
i have recently setup virtual hosts on my ubuntu 6.06 server, running apache2
ive managed to get apache restarting fine, but i am unable to get anything up when typing names in my browser, i type in the name of my virtual hosts and all i get is an internet search page,
however i dont think this is anything to do with my virtual host setup, for some strange reason i cannont get my servers default page up by tying in its host name either, yet its IP address works perfect :confused:

im kinda confused as to why but i always have had a problems with hostnames on my networks, my two windows machines cannot see eachother properly either despite all being setup identically, and all machines can asses my server as it acts as a fileserver :confused:

i dunno, strange problem that i dont know the reason for :(

---

### Post by Peter09 on 2007-11-10
Not sure that this is connected, but there is a problem with DHCP in Gutsy. Can you connect to other machines on your network by host name (assuming that you do not use the /etc/hosts file for name resolution)

---

### Post by kevdog on 2007-11-10
Sounds like you dont have a proper dns server when making your internet connection to do name resolution.  Its an alternative, however you could set up ubuntu to use opendns for your dns servers if you wanted to (there are some minor annonyances but it does work).  Here are some instructions if you are interested:

[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

