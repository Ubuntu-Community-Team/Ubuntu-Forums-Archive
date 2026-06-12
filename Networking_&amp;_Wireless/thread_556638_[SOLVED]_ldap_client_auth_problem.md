---
title: "[SOLVED] ldap client auth problem"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by brenth on 2007-09-21
Hey all, I have followed [this]("https://help.ubuntu.com/community/LDAPClientAuthentication"), and when I run "id user" or "getent passwd", everything works perfect. But, When I try to log in as a ldap user, I get nowhere. When I try to su, I get "su: Authentication failure" and in auth.log I get

Sep 20 12:56:30 ws-047 su[8401]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Sep 20 12:56:30 ws-047 su[8401]: (pam_unix) authentication failure; logname= uid=1000 euid=0 tty=pts/2 ruser=administrator rhost= user=brent
Sep 20 12:56:32 ws-047 su[8401]: pam_authenticate: Authentication failure
Sep 20 12:56:32 ws-047 su[8401]: FAILED su for brent by administrator
Sep 20 12:56:32 ws-047 su[8401]: - pts/2 administrator:brent

I also am having an issue where administrator will not sudo anymore, when I sudo command, I type in the passwd and it just returns to the shell.

sorry for the xpost to the Serve&Security forum, though this might get an answer here also.

Any ideas?
thanks,
Brent

---

### Post by gpredrag on 2007-09-21
HOWTO you mentioned in not universal,may not work in your situation. you should check couple of things:

Does your client realy tries to contact right LDAP server (try running wireshark in Gnome while while login as user in console)?

Does your LDAP realy allows nonauthenticated bind (I am not sure that is Ubuntu/Debian default)?. If it doesn't, you should put binddn and bindpw in libnss-ldap.conf and pam-ldap.conf for some unprivileged proxy user.

libnss-ldap.secret is place for LDAP admin password, and coresponding root_binddn should be put in files mentioned above. 

Also, contrary to many HOWTOs I have read, I couldn't make it work unless libnss-ldap.conf is word readable, even if I run nscd.

---

### Post by brenth on 2007-09-21
Thanks for the reply gpredrag, I am sure that the machine is accessing the ldap server without issue, since I can see info from the server such as "getent passwd". I also just discovered that as administrator, is I type " su brent" and enter the correct passwd, i get "su: Authentication failure". But if I log in via root and su brent, doesn't ask for my pass, and becomes brent. If I create a file in my shared home dir ( or anywhere else) It knows that I am the owner. So, maybe there is something with the passwd part of the auth that is casueing the problem?

---

### Post by gpredrag on 2007-09-22
I can't point you to exact doc that explains it, but from my experience, ldap libraries (at least in debian and ubuntu) always use rootbindn and rootpw (as set in pam_ldap.conf and in libnssldap.con) when effective user id  of the caller is 0 (root).
 su is setuid root command, during pam authentication setuid 0 comes in to effect.
I can't tell if it's your problem, but you can get similar symptoms by setting binddn and bindpw the right way, while at the same time not setting rootbindn and rootpw in ldap.secret.
that way if some user uses: id someotheruser everything works, but someotheruser cant login.
root can  allways use su someone, that's not indicative.

Also contrary to simple explanation during dpkg-reconfigure, rootbinddn doesn't have to be real LDAP database admin. If it is not you wouldn't be able to change password for other users as local root. More precise explanation would be that roodbindn is bind dn used when effective uid is 0 (that is what is said in conf files anyway).

Again try sniffing authentication traffic with wireshark, may be helpfull

---

### Post by brenth on 2007-10-02
So I was able to get ldap users logged in, but I am running into another issue. now, when I su to root, it is trying to log in via a root user in the ldap

administrator@ws-047:~$ su
Password: 
You are required to change your LDAP password immediately.
Enter login(LDAP) password: 

nsswitch.conf 

```

passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

common-account
```
account sufficient     pam_ldap.so 
account required        pam_unix.so use_first_pass
```

common-auth```

auth    sufficient      pam_ldap.so 
auth    required        pam_unix.so use_first_pass
```

common-passwd
```
password        sufficient      pam_ldap.so 
password        required        pam_unix.so 
```
common-session
```
session required        pam_unix.so use_first_pass
session optional        pam_ldap.so
```

what am I doing wrong?

---

### Post by brenth on 2007-10-03
anyone have any ideas?

---

### Post by brenth on 2007-10-04
solved. used these settings [http://ubuntuforums.org/showthread.php?t=195908](http://ubuntuforums.org/showthread.php?t=195908)

---

