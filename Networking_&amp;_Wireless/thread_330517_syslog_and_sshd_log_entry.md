---
title: "syslog and sshd log entry"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2007-01-03
I was curious if anyone could tell me what exactly this means.

Jan  1 01:29:50 ubuntu sshd[609]: Connection from 221.10.254.205 port 55175

Does this mean that this ip tried to access my machine? Does this mean that they DID access my machine? How come there is no mention of the username they tried? Is this maybe because I use public/private key authentification? I am thinking yes because when I sometimes connect using putty and don't enter the location of the key putty just shuts down and doesn't continue. Also, I know when I do connect I can see tons of info in the syslog and the auth.log about my connection so I don't think the above log entry is saying that they connected to my machine. At least I hope not!! Any help from someone who actually knows would be appreciated. Thanks. Oh yeah, what does it mean when it says this:
Dec 27 00:00:46 localhost sshd[21581]: Connection from 64.251.27.172 port 54203
Dec 27 00:00:46 localhost sshd[21577]: reverse mapping checking getaddrinfo for 172-27-251-64.serverpronto.com failed - POSSIBLE BREAKIN ATTEMPT!
Dec 27 00:00:47 localhost sshd[21581]: Invalid user sales from 64.251.27.172
Dec 27 00:00:47 localhost sshd[21583]: Connection from 64.251.27.172 port 54280
Dec 27 00:00:47 localhost sshd[21579]: reverse mapping checking getaddrinfo for 172-27-251-64.serverpronto.com failed - POSSIBLE BREAKIN ATTEMPT!

versus just like this:
Dec 26 06:22:20 localhost sshd[19457]: Connection from 217.199.183.150 port 42325
Dec 26 06:22:21 localhost sshd[19457]: Invalid user custftp from 217.199.183.150
Dec 26 06:22:22 localhost sshd[19459]: Connection from 217.199.183.150 port 42479
Dec 26 06:22:23 localhost sshd[19459]: Invalid user bppadmin from 217.199.183.150

and then of course the one I am asking about which is this:
Dec 26 06:24:31 localhost sshd[19675]: Connection from 217.199.183.150 port 55600
Dec 26 06:24:32 localhost sshd[19677]: Connection from 217.199.183.150 port 55719
Dec 26 06:24:33 localhost sshd[19679]: Connection from 217.199.183.150 port 55811
Dec 26 06:24:34 localhost sshd[19681]: Connection from 217.199.183.150 port 55917

These are all in my /var/log/auth.log files

Thanks for any help.

---

### Post by dannyboy79 on 2007-01-16
aren't there any server admins out there that can answer what each of these hits means and what the differences are????? Please........

---

