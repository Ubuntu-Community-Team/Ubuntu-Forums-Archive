---
title: "ftp"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by rayban2 on 2015-02-09
Hi,
I'm a beginner with Ubuntu and I have some problems and issues. 
I'm thinking to install a ftp on Ubuntu
I have a doubt about this.
Must I create all the users on the system ?
For example, if my ftp has 30 users, must I create 30 users on the Ubuntu ? or is there other possibility ?


Thanks 

*[SIZE=1](I'm new in Ubuntu and learning English, Sorry for my mistakes)[/SIZE]*

---

### Post by TheFu on 2015-02-09
a) FTP is non-secure and really shouldn't be used anymore (or in the last 15 yrs).
b) sftp which is part of the openssh-server is a secure replacement.
c) You can use different authentication methods for different services. This is controlled through PAM.
[http://askubuntu.com/questions/262425/how-to-configure-pam-d-files-for-ldap-over-ssh-on-12-04](http://askubuntu.com/questions/262425/how-to-configure-pam-d-files-for-ldap-over-ssh-on-12-04) is one way.
LDAP tends to be the desired method these days.  Some ISPs use DBs to hold user login info.

---

