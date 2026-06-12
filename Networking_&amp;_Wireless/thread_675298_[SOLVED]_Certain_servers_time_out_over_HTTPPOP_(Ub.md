---
title: "[SOLVED] Certain servers time out over HTTP/POP (Ubuntu, iBurst, DNS and XP and ICS)"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by miserabledutchman on 2008-01-22
This is a Gutsy installation that gets its internet from an XP SP1 machine, static ip's as per the usual 192.168 etc setup.  

The windows machine (which is gateway 192.168.0.1) can get into webmail server (webmail.jetweb.co.za)  just fine -

the same request times out from this machine, which can connect fine to this forum, and any other site i've tried.  Tracert to these servers hops around and eventually hit a dead end.  Ping works but probably irrelevant (yes/no?)  since there are redirects to get past.  

The same server  (mail.jetweb.co.za) also times out from Evolution.  Thunderbird too.

This setup worked 100% 2 days ago before I fuddled around with pppoeconf to try to get an ethernet-linked iburst modem to work from ubuntu with no success.  this modified my dsl-provider file, and my resolve.conf is also not original.  

i've got the iburst device back on the windows box, a blank dsl=provider file, and a resolv.conf file that reads:
[FONT="Courier New"][COLOR="DarkGreen"]nameserver 196.30.31.193
nameserver 192.168.0.1
domain mshome
nameserver 196.46.70.1
search mshome.net
nameserver 208.67.222.222
nameserver 208.67.220.220[/COLOR][/FONT]

changing mtu hasn't worked.
adding dns servers hasn't worked.
:confused:

EDIT: The problem was the machine used as a gateway - it was Windows XP Pro Service Pack 1.  Installed SP2 and problem was solved.  If any one can shed any light on what the detail is behind this...

---

