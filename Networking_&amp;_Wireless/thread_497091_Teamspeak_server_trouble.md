---
title: "Teamspeak server trouble"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by darmot7 on 2007-07-09
ok, i have ubuntu 7.04 desktop installed
ive followed a how to similar to [http://ubuntuforums.org/showthread.php?t=236834&highlight=teamspeak+server](http://ubuntuforums.org/showthread.php?t=236834&highlight=teamspeak+server)

heres my issue.

i can connect to the teamspeak server by entering a lan IP (i.e. 192.168.*.*) and obviously others cant join that IP. so i try using my routers IP to connect, its sends me back the error 
"no reply from server" "maybe the server is offline" "or maybe teamspeak is not running on it"

i have port forwarding allocated on my d-link router to my static IP, i have no idea what i need to do to allow people to connect to my teamspeak server.

im pretty new to linux, sorry if im non-descriptive

please let me know if i need to give anymore information.

---

### Post by qsheets on 2007-07-14
3 questions...

[LIST=1]
[*]Did you forward the port of that teamspeak (i.e. 8767)?
[*]Is it marked as UDP and not TCP?
[*]Did you also forward ports 51234 and 14534 (both TCP)?
[/LIST]
Answers should all be yes. If not fix those and try again.

---

