---
title: "Apache2 with tor hidden service"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by omnicide2 on 2015-07-25
I am fairly new to ubuntu, and trying to setup a hidden tor service. I've read several hundred guides and I cannot for the life of me get this onion site to come up... 

This is the error about the config I get in the terminal when I try to start tor. 
"[warn] permissions on directory /var/www are too permissive"
"[warn] failed to parse/validate config :failed to configure rendezvous options"

When I check my log, this is all I get.
[Sat Jul 25 17:54:50.000962 2015] [:notice] [pid 10123:tid 140054882559872] ModSecurity for Apache/2.7.7 ([http://www.modsecurity.org/](http://www.modsecurity.org/)) configured.
[Sat Jul 25 17:54:50.001120 2015] [:notice] [pid 10123:tid 140054882559872] ModSecurity: APR compiled version="1.5.1-dev"; loaded version="1.5.1-dev"
[Sat Jul 25 17:54:50.001135 2015] [:notice] [pid 10123:tid 140054882559872] ModSecurity: PCRE compiled version="8.31 "; loaded version="8.31 2012-07-06"
[Sat Jul 25 17:54:50.001153 2015] [:notice] [pid 10123:tid 140054882559872] ModSecurity: LUA compiled version="Lua 5.1"
[Sat Jul 25 17:54:50.001163 2015] [:notice] [pid 10123:tid 140054882559872] ModSecurity: LIBXML compiled version="2.9.1"
[Sat Jul 25 17:54:51.001710 2015] [mpm_event:notice] [pid 10124:tid 140054882559872] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Sat Jul 25 17:54:51.001835 2015] [core:notice] [pid 10124:tid 140054882559872] AH00094: Command line: '/usr/sbin/apache2'


I really have no idea what this means. All I can guess is Mod Security isnt configged right and keeping my site from coming up.
Any help would be greatly appreciated.

---

### Post by omnicide2 on 2015-07-26
I've managed to get rid of the errors by doing chmod 700 to the /var/www dir. The onion still won't come up. Please help!

---

