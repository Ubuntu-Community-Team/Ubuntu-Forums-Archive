---
title: "2 Servers, one authentication server"
date: 2016-09-22
forum: Networking &amp; Wireless
---

### Post by m-knichel on 2016-09-22
I have a classroom with  2 servers.  One is internal running LTSP and file storage.  This is where the user accounts for login are stored.  I have a second server that acts as my gateway and web server.  I currently have the user accounts recreated on this second server and their home directories mounted via nfs from the LTSP server.

I would like to not have to create the user accounts 2 times.  I would also like to be able to point to a single authentication server for accounts I use on the web server.  As I have been reading it seems like LDAP is the way to go for this.

1)  Do I create the users on both servers but only check password on the LDAP server?  If not, then how does my gateway point to a home directory for a given user?
2)  If I use LDAP to authenticate my websiite accounts, then will any user on the server have a website account? or do I create the users on the website and authenticate via LDAP?

I apologize for my lack of understanding of how LDAP works.  Can someone point me to a good tutorial on getting LDAP set up and working?

--
M

---

### Post by SeijiSensei on 2016-09-22
Before you go down the LDAP route, you might considered using the hoary [NIS method]("http://www.linux-nis.org/nis-howto/HOWTO/") instead.  With only a few machines it's a lot easier to set up and maintain than LDAP.

---

### Post by m-knichel on 2016-09-23
Thanks for the tip.  I used NIS years ago but started having issues (cannot recall what though).  Only for single server and client logins.

---

