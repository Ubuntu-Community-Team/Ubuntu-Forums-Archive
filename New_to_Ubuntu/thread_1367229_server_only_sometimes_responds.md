---
title: "server only sometimes responds"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Pevichaey5 on 2009-12-29
hey
my ubuntu server only responds like 50% of the time

i know my ssh is fine, i've tested it loads, its my primary way to manage my server and my web is fine and my dynamic dns is updated

but if i try to connect to it via my domain name, [http://thexero.ath.cx](http://thexero.ath.cx) it only works sometimes, else the connection times out, this applies to apache as well as ssh, main problem here though while i'm trying to get the mail up and running, it does this and i cannot work like this

any suggestions from people?

---

### Post by CharlesA on 2009-12-29
I can connect to the webserver fine (get the default apache page).

Are you running on a non-standard port for any services?

---

### Post by Pevichaey5 on 2009-12-29
all default ports
22 ssh
25 smtp
80 web
110 pop3

i didn't have this problem when i was running windows server so i know its not my network

---

### Post by CharlesA on 2009-12-29
Could it be that yer ISP is blocking some of those ports during peak hours or something?

I really don't know, since you said it worked with Windows Server. *shrugs*

Could the machine have been compromised?

---

### Post by Pevichaey5 on 2009-12-29
it seems like to go to sleep or something after a few hours

for instance

if nothing connects to it for like 4 hours, i have to use the manual internal ip, then the domain name works

not sure if there is something doing that or not but i dunno

---

### Post by sandyd on 2009-12-29
what are you using to update the ip address.

ddclient?

if you are, you must realize that ddclient "sleeps"

see below (look at the part with a teal background)

---

### Post by Pevichaey5 on 2009-12-29
i am

but i haven't had to update my machine in days, i think my ip changes every 14 days

everytime i run the ddclient, it says no update is nessceary

when i woke up, the domain didn't work, and the connection timed out

when i ran the ddclient, it said no update nessecary, then the domain worked

but it happens several times a day

---

