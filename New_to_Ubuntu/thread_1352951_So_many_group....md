---
title: "So many group..."
date: 2009-12-12
forum: New to Ubuntu
---

### Post by ludydoo on 2009-12-12
Bonjour!

Is it normal that there is so many user groups on my system now ? I installed Apache2 webserver, eclipse, and lots of modules for apache. Look at all the groups ! And moreover, most of them are empty... Should I delete them or just let them there? Cause it's kind of nasty.

```


root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:ludovic
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:ludovic
fax:x:21:
voice:x:22:
cdrom:x:24:ludovic
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:ludovic
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
fuse:x:103:
lpadmin:x:104:ludovic
ssl-cert:x:105:
messagebus:x:106:
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:
couchdb:x:113:
haldaemon:x:114:
admin:x:115:ludovic
saned:x:116:
pulse:x:117:
pulse-access:x:118:
gdm:x:119:
ludovic:x:1000:ludovic
sambashare:x:120:ludovic
mysql:x:121:
Debian-exim:x:122:



```

---

### Post by 3rdalbum on 2009-12-12
They all look pretty normal to me. It's part of the Linux security system - each of those "groups" is locked down tightly to whatever tasks/files the program needs to use. If they didn't exist, then large tracts of the system would need to run as root, which is a security nightmare.

---

### Post by ludydoo on 2009-12-12
Even if they are empty ?

---

