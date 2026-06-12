---
title: "ubuntu samba server &lt;-&gt; Vista problem"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by muzehyun on 2008-09-23
My ubuntu has 2 network interfaces
1. eth0: It is directly connected to vista machine. It is for faster file transfer. No router or anything between this. Each side of interface has it's own static IP address. (ssh is well working using this)
2. wlan0: It is connected to internet (wireless router). Port number 139, 445 is forwarded to ubuntu machine.

From Vista using publicIP(wlan0: through internet)
I can access to ubuntu samba \\publicIP\sharedir. Username/password pair is also working well.

From Vista using privateIP(eth0: direct ethernet cable)
I can see list of samba folders \\privateIP.
But I cannot login to \\privateIP\sharedir
It says
----
\\privateIP\sharedir is not accessible. You might not have permission to use this network resource. ....
----

in smb.conf, I added 'security = user' and other directory specific parameters.

Connection is from same vista machine to different interface in same ubuntu machine. I cannot figure what makes it different.



Thank you

Sean

---

### Post by superprash2003 on 2008-09-23
do you have any firewall installed in the ubuntu machine which may be blocking?? check your smb.conf file (/etc/samba/smb.conf) and ensure that it is NOT set to listen to  only one interface..

---

### Post by muzehyun on 2008-09-23
!!!
It's working now
But I don't know why

What I've done is..
1. turn off 'Network discovery'
2. reboot Vista

Then I can open samba folder with '\\privateIP\sharedir'


Thank you

Sean

---

