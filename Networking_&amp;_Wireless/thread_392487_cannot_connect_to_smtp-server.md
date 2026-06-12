---
title: "cannot connect to smtp-server"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by groova on 2007-03-24
Hi there,

I have a problem connecting to my smtp servers: Namely, I am unable to do so.

I am using Thunderbird as my e-mail client of choice and can recieve e-mails just fine. But when trying to connect to the two different smtp-servers that I can use (and have from windooze xp before makeing the step to Ubuntu) it times out and gives the error-message:

[COLOR="DarkRed"]Sending of message failed.
The message could not be sent because the connection to teh SMTP-server smtp.web.de failed. ...[/COLOR]

I have also tried to use

> telnet smtp.web.de 25

from a terminal, but that also just blinks after translating it to the ip-address.

I am not aware that I have a firewall running. Is there a default firewall installed with Ubuntu 6.10 that I don't know about? 

Any other thoughts?

---

### Post by Floppyjoe on 2007-03-24
Are you using the right ports and are you sure you typed your passwords and usernames correctly?

---

### Post by groova on 2007-03-25
Yes, I am certain that port 25 is supposed to be used. (I've also tried port 578 after reading the forums, but alas, no joy either).

I would love to get as fas as username/password authentication... :(

---

### Post by groova on 2007-03-25
Never mind. My ISP has a new rule that you have to use their SMTP-server...

DUH! :roll:

---

