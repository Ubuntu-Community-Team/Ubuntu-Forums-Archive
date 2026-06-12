---
title: "Bind9 not resolving."
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by itzpapalotl on 2007-12-18
Well.
I don't even know how to phrase this question.
Bind9 is working just fine, but it won't resolve anything. Won't forward, won't resolve local stuff, nothing. 

It's installed ala "The perfect Server" and living in it's chroot jail. The basic configuration files all check out named.conf,  named.conf.options, /etc/resolv.conf 

Bind9 starts up okay, syslog shows no errors. bit it just plain won't do it's job.

I moved the machine from a testing IP address where it was working, to a permanent IP address, and now it just doesn't work.

Any guesses?

****

Follow up question. What is an rndc.key file and could this thing be the cause of all this?

---

### Post by HermanAB on 2007-12-19
1. Is named running at all?
# ps -e | grep named

2. Does it resolve something forwards?
# dig @localhost [www.yourdomain.com](www.yourdomain.com)

3. Does it resolve something backwards?
# dig @ localhost w.x.y.z

4. What does the log file say?
# tail -f /var/log/messages

5. What happens when you run it in the foreground?
# killall named
# named -f -d 10

Cheers,

Herman

---

### Post by itzpapalotl on 2007-12-19
ps -e | grep named  returns result: 
10400 ?        00:00:00 named

I don't like that ?

dig @localhost [www.mydomain.net](www.mydomain.net)

root@spbb-2:/etc/bind# dig @localhost [www.speedpal.net](www.speedpal.net)

; <<>> DiG 9.4.1-P1 <<>> @localhost [www.speedpal.net](www.speedpal.net)
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 55333
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.speedpal.net](www.speedpal.net).              IN      A

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Dec 18 22:17:24 2007
;; MSG SIZE  rcvd: 34

root@spbb-2:/etc/bind#

dig @localhost [www.ubuntuforums.org](www.ubuntuforums.org)

; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5562
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 13

;; QUESTION SECTION:
;[www.ubuntuforums.org](www.ubuntuforums.org).          IN      A

;; ANSWER SECTION:
[www.ubuntuforums.org](www.ubuntuforums.org).   600     IN      A       91.189.94.186

;; AUTHORITY SECTION:
.                       44197   IN      NS      h.root-servers.net.
.                       44197   IN      NS      b.root-servers.net.
.                       44197   IN      NS      e.root-servers.net.
.                       44197   IN      NS      k.root-servers.net.
.                       44197   IN      NS      g.root-servers.net.
.                       44197   IN      NS      l.root-servers.net.
.                       44197   IN      NS      m.root-servers.net.
.                       44197   IN      NS      j.root-servers.net.
.                       44197   IN      NS      d.root-servers.net.
.                       44197   IN      NS      i.root-servers.net.
.                       44197   IN      NS      c.root-servers.net.
.                       44197   IN      NS      f.root-servers.net.
.                       44197   IN      NS      a.root-servers.net.

;; ADDITIONAL SECTION:
g.root-servers.net.     44197   IN      A       192.112.36.4
h.root-servers.net.     44197   IN      A       128.63.2.53
i.root-servers.net.     44197   IN      A       192.36.148.17
j.root-servers.net.     44197   IN      A       192.58.128.30
k.root-servers.net.     44197   IN      A       193.0.14.129
l.root-servers.net.     44197   IN      A       199.7.83.42
m.root-servers.net.     44197   IN      A       202.12.27.33
a.root-servers.net.     44197   IN      A       198.41.0.4
b.root-servers.net.     44197   IN      A       192.228.79.201
c.root-servers.net.     44197   IN      A       192.33.4.12
d.root-servers.net.     44197   IN      A       128.8.10.90
e.root-servers.net.     44197   IN      A       192.203.230.10
f.root-servers.net.     44197   IN      A       192.5.5.241

;; Query time: 71 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Dec 18 22:19:51 2007
;; MSG SIZE  rcvd: 473

Log files show the following, but I'm not sure what it means.


Dec 18 21:14:07 spbb-2 kernel: [  697.861971] Failure registering capabilities with primary security module.
Dec 18 21:43:07 spbb-2 -- MARK --
Dec 18 21:44:32 spbb-2 kernel: [ 2522.284658] Failure registering capabilities with primary security module.
Dec 18 21:47:31 spbb-2 kernel: [ 2701.718454] Failure registering capabilities with primary security module.
Dec 18 22:03:07 spbb-2 -- MARK --
Dec 18 22:07:43 spbb-2 kernel: [ 3913.002569] Failure registering capabilities with primary security module.

---

### Post by PowerBoardCable on 2007-12-19
Hi,
sounds like my problem. Dig results are the same, ps shows same info and the log file also produces the kernel error that itzpapalotl describes.

> 5. What happens when you run it in the foreground?
# killall named
# named -f -d 10
it seems to run - at least it shows no error, but after a few seconds it disapears from ps -a   | grep named

I have posted my conf files in another thread that I accidentally started:
[http://ubuntuforums.org/showthread.php?p=3978225#post3978225](http://ubuntuforums.org/showthread.php?p=3978225#post3978225)
itzpapalotl, we could compare?

Cheers,

Mike

---

### Post by PowerBoardCable on 2007-12-19
Hi,
if it helps, my thread has been resolved:
[http://ubuntuforums.org/showthread.php?p=3978744#post3978744](http://ubuntuforums.org/showthread.php?p=3978744#post3978744)

Mike

---

### Post by itzpapalotl on 2007-12-20
Happy to compare notes, but let me check your resolved thread, see if I can make it go. If I can, I'll post my roadmap here....

---

