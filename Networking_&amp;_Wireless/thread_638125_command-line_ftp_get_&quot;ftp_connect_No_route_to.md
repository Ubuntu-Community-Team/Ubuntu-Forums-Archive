---
title: "command-line ftp get &quot;ftp: connect: No route to host&quot;"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by downslj on 2007-12-11
command-line ftp returns "ftp: connect: No route to host" when trying to connect to an external IP address.

Firefox works fine.

sudo apt-get works fine too.

Here is what I've tried:

sudo gedit /etc/bash.bash.rc 
    added these 3 lines using my specific information:
   export http_proxy="http://domain/user:password@ipaddress:port/
   export ftp_proxy="http://domain/user:password@ipaddress:port/
   export use_proxy=on

Is there another setting that command-line ftp requires to force it to use a proxy?

---

