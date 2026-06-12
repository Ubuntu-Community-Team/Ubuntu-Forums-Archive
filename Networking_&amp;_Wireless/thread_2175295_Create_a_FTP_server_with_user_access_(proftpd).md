---
title: "Create a FTP server with user access (proftpd)"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by toni-appelqvist on 2013-09-18
[INDENT] 					I have ptoblem.
When restart ftp:
Stopping ftp server proftpd****************************************** [ OK ] 
** Starting ftp server  proftpd*******************************************  ****** Master  proftpd[29709]: Fatal: UserAlias: missing arguments on line 6 of  '/etc/proftpd/proftpd.conf'


Conffile
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on


# Choose here the user alias you want !!!!
UserAlias userftp

ServerName*** *** *** "ChezFrodon"
ServerType *** *** *** standalone
DeferWelcome*** *** *** on 				[/INDENT] 			
  			   		
What to do?
Thanks

---

