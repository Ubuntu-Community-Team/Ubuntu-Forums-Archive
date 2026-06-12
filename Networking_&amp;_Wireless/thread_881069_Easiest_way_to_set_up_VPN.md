---
title: "Easiest way to set up VPN?"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2008-08-05
I have an Ubuntu home file server, which has basically become my everything server (smb, http, ftp... all that good stuff). 

Well, a long time ago, before I was witness of the magical glorious radiance that is Ubuntu, it was a Windows file server. VPN was really easy to setup and allowed to me to get to all my crap while on vacation.

Currently, I also have SSH running on the server, which I was using in an experiment in trying to steal my schools bandwidth to download torrents over the weekend - but that didn't work and is besides the fact ;). So anyway, what is the easiest way to setup a PPTP VPN server in Ubuntu? I'm sort of in the transition stage from total noob to educated noob with linux, so I still like GUI setup utilities :p.

On a side note, back to the SSH thing, is it possible to run VPN over SSH where I don't have any ports open except maybe 80 and 21 (i.e. school, work .etc)? I don't really know that much about SSH, so if my idea makes no sense, feel free to tell me :p.

Thanks!

---

### Post by ownaginatious on 2008-08-05
bump...

---

### Post by ownaginatious on 2008-08-06
I'm going to try one more time, and hope that someone answers this time :(.

---

### Post by ownaginatious on 2008-08-09
Someone's gotta know how to do this... :(

---

### Post by Iowan on 2008-08-09
See if [this one]("https://help.ubuntu.com/community/SSH_VPN") helps.  [Here]("https://help.ubuntu.com/community/UserDocumentation?action=fullsearch&context=180&value=vpn&titlesearch=Titles") is a broader search.

---

### Post by webmaster_ph on 2008-08-13
> **ownaginatious said:**
> I have an Ubuntu home file server, which has basically become my everything server (smb, http, ftp... all that good stuff). 

Well, a long time ago, before I was witness of the magical glorious radiance that is Ubuntu, it was a Windows file server. VPN was really easy to setup and allowed to me to get to all my crap while on vacation.

Currently, I also have SSH running on the server, which I was using in an experiment in trying to steal my schools bandwidth to download torrents over the weekend - but that didn't work and is besides the fact ;). So anyway, what is the easiest way to setup a PPTP VPN server in Ubuntu? I'm sort of in the transition stage from total noob to educated noob with linux, so I still like GUI setup utilities :p.

On a side note, back to the SSH thing, is it possible to run VPN over SSH where I don't have any ports open except maybe 80 and 21 (i.e. school, work .etc)? I don't really know that much about SSH, so if my idea makes no sense, feel free to tell me :p.

Thanks!

hi mate,

maybe this would help:

[Step 1]("http://ubuntuforums.org/showthread.php?t=826815&highlight=set+vpn")

[Step 2]("http://ubuntuforums.org/showthread.php?t=854660&highlight=pptp+server+install")

[Step 3]("http://ubuntuforums.org/showthread.php?t=487480&highlight=pptp+server+install")

don't forget to enable port (1723) forwarding on your router and server.

---

