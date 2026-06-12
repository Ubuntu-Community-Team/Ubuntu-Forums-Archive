---
title: "Partly?- connected to internet ?"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by rfflower on 2008-05-12
I'm a newbie, with Gutsy Gibbon preinstalled on a new Dell laptop.
My wireless card works fine, and after a lot of fiddling I got Firefox to talk to the internet (changed the IPv6 setting '/etc/modprobe.d/aliases - alias net-pf to off). 
I can access other computers on my local network, move files from them to my laptop. 
I can connect to my ftp site through the file browser.
What I can't seem to do is access to the internet with package manager or bittorrent or email or pidgin. 
If I follow the link through Firefox, to a failed package file (error message from package manager) then the file IS there to be downloaded.
I haven't a clue what's happening here. Is there some other configuration setting which "enables" internet access differently to Firefox.
I hope all that makes sense
Richard

---

### Post by dmizer on 2008-05-12
the alias method of disabling ipv6 is extremely dated ([breezy badger i think](https://wiki.ubuntu.com/Releases)).  you should use this howto: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

that should fix things for you.

---

### Post by rfflower on 2008-05-27
Thanks, Things seem to be working fine now.

---

