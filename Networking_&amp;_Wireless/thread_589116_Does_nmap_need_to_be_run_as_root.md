---
title: "Does nmap need to be run as root ?"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by munwin on 2007-10-23
I am now using Gutsy, and it appears that I can run nmap as a normal user (ie, not using sudo). I am sure under 7.04 and earlier you HAD to use sudo.

Am I wrong, or has it changed now, so that any user can run nmap ?

Am running the command
nmap -vv ip -p80
where ip is an ipaddress on my network I wish to scan...

---

### Post by anubhavrocks on 2007-10-23
Unprivileged users can execute connect scans.

---

