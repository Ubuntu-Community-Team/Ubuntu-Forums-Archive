---
title: "stun install error"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by JacksonL on 2007-02-06
hi. I'm trying to install stun (sudo aptitude/apt-get install stun) and it returns the following error: 

$ sudo apt-get install stun
Reading package lists... Done
Building dependency tree       
Reading state information... Done
stun is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up stun (0.96.dfsg-1) ...
No primary IP given. Exiting.
invoke-rc.d: initscript stun, action "start" failed.
dpkg: error processing stun (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 stun
E: Sub-process /usr/bin/dpkg returned an error code (1)

anyone know how to fix this? I'm trying to use stun for VOIP with ekiga

---

### Post by bmt on 2007-02-07
You shouldn't have to install stun as a separate package in support of Ekiga.  The stun package is for a stun server -- Ekiga has stun *client* capabilities built, which is all that's necessary for it to get out through a firewall (generally).

Are you having problems with Ekiga?

---

### Post by autosaver on 2007-03-24
I solved this by (as root) edit /var/lib/dpkg/info/stun.postinst.
The problem was that the script tried to start stun after the installation, but stun needs to be configured before that can happen, so edit that file and comment out everyfing (from the first if to the last fi).

---

