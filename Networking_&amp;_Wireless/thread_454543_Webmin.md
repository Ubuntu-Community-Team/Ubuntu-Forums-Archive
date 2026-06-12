---
title: "Webmin"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by kxz9 on 2007-05-25
Hi every body.
first i want to say thank you to all for this Forum.

(My first language is Spanish, so i will to try to express my self the best that i can :p )

well, this is my first time running Squid all was ok until i tried to set Webmin.

( Ubuntu breezy 5 server,  Squid 2 )

the proxy is working but when i try to see the graphical configuration by a browser , i can't see anything.

i don't know maybe i lost some step.  

i' have already installed samba, swat, Webmin, and all the file that i need. I'm asking this because i was look very much before to come to ask for help here :)


This is the configuration of Webmin on my server.

root=/usr/share/webmin
mimetypes=/etc/mime.types
port=10000
host=ATLAS
addtype_cgi=internal/cgi
realm=Webmin Server
logfile=/var/log/webmin/miniserv.log
pidfile=/var/run/webmin.pid
logtime=168
ssl=1
env_WEBMIN_CONFIG=/etc/webmin
env_WEBMIN_VAR=/var/log/webmin
logout=/etc/webmin/logout-flag
listen=10000
userfile=/etc/webmin/miniserv.users
keyfile=/etc/webmin/miniserv.pem
libwrap=1
alwaysresolve=1
allow=all
blockhost_time=300
no_pam=0
logouttime=5
passdelay=1
session=1
blockhost_failures=3
syslog=1
log=1
logclear=
loghost=1
preroot=debiantheme
ppath=
atboot=1
denyfile=\.pl$
extraroot_0=/usr/local/share/webmin



there is not a personal setting so i don't know please, i will thnak all the help. any. If you need more details please letme know.


Thank you

---

