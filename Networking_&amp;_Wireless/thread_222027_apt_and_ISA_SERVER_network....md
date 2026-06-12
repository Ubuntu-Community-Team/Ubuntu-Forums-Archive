---
title: "apt and ISA SERVER network..."
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by giohappy on 2006-07-24
I'm a newbie user. I need to work with Linux software for research but I'm not a sytemist... It's not a good start!Il This is my problem: make apt work under a Microsoft ISA SERVER network. 
I set: [http://DOMAIN\USERNAME:PW@IP_PROXY:DOOR](http://DOMAIN\USERNAME:PW@IP_PROXY:DOOR) as environmental variable and in apt.conf. I tried to change slashes to bkslashes and viceversa... Nothing to do, always the same 407 ISA Authentication error.
Other notes: Firefox doesn't download plugins, doesn't open Gmail, works bad with sme other sites... Is it due to the authentication process?
HELP!!!
Important: My network and domain administrator don't want to make variations to the server => I've got to solve the problem by myself (maybe with winbind and samba?).

Giovanni (Italy)

---

### Post by Thund3rstruck on 2006-07-24
To set the proxy for all applications (I believe) there is an applet in System Prefences > Network proxy and I believe there is an env variable called http_proxy. 

As for firefox, it will never download plug-ins correctly (in my experience). You must install them as regular packages (ex: $sudo aptitude install totem-gstreamer-firefox-plugin)

---

