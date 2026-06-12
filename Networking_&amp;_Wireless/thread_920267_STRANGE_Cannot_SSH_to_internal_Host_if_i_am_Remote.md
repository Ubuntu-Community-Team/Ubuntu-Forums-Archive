---
title: "STRANGE: Cannot SSH to internal Host if i am Remote"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by axel1973 on 2008-09-15
hi anybody

first of all i need to show you the szenario ive got here. this makes things a lot easier.

SZENARIO/Infrastructure
========================

[ME@WORK-WinXP]
|
|
|
((INET CLOUD))
|
|
|
[MYROUTER@HOME(debian etch)]
|
|
|
((LAN Cloud))------[some WinXP Client also on LAN]
|
|
|
[some UBUNTU 8.04.1 AMD64bit DESKTOP Ed. server]   {TARGET}


Problem is:
============

it seems for somehow i cannot ssh my ubuntu server from my router-host (debian) if i am connected to the router from remote (work). 

AT HOME: i can ssh the ubuntu from my winxp client, from my router (debian etch) without problems even vice versa. perfect! (last testet this morning)

AT WORK: i can ssh to my debian router. Now connected to my debian router it seems i cannot ssh to my ubuntu. if im on my debian and do a "ssh ubuntuserver" it hangs for some seconds and then reports a message like this:

"
router:~# ssh ubuntuserver
ssh_exchange_identification: Connection closed by remote host
router:~#
"

so im locked out.

however.. PING to ubuntuserver works, nmap to ubuntuserver works. i can reach webserver, pop3 and even ssh port of the ubuntuserver from my debian router, where i am sitting right now using ssh. 

BUT...no ssh link is been accomplished. and therefor i cannot check logs and stuff on the ubuntu side.

on ROUTER-Side there are NO SSH/SSHD LOGS AT ALL! Nothing about SSH in /var/log/messages , nothing in /var/log/syslog !

so i tried it using VERBOSE mode...

debian:~# ssh -vvv ubuntu
OpenSSH_4.3p2 Debian-9etch2, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ubuntu [192.168.0.7] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug3: Not a RSA1 key file /root/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
debian:~#


whats going on here?!:confused:

regards
Axel

---

### Post by axel1973 on 2008-09-15
PS:

i also tried to "tunnel" my SSH request to ubuntuserver through ssh@debian using putty on my Work-PC (win xp) - no luck! no error message at all, but also no connection :)

---

