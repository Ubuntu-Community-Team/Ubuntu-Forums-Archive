---
title: "Connecting with SSH when username is email-address"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by erkkir on 2008-01-11
Hi,

Im connecting to my webserver using SSH-connection. Im having some problems because my username is an email-address(contains @-character). When i try following; 

places->connect to server as a username i put [email]myname@myserver.com[/email]

This seems to cause problems. Next window is prompting the password for [email]myname@myserver.com[/email] but it will not accept my login. However if i leave the password field empty in the previous window, ubuntu is asking for both username and password. There if I put the username containing @-character and the correct password it works, but is asking every 2 minutes again the same username and password even if i checked the box 'remember forever'.

I assume the problem is the @-character. I also havent figured out how to make ssh connection using command prompt with such a username. Obviously 'ssh [email]myname@myserver.com@myserver.com[/email]' is not the right syntax. Any ideas how to solve this?

Thank you,

Erkki

---

### Post by reckless2k2 on 2008-01-11
for giggles try:

```
ssh yourip -l user@yourip
```

that's a lowercase L not a number one.

---

### Post by erkkir on 2008-01-15
Good, ssh from command line works fine with -l

Anyway, places->connect to server doesn't seem to understand email-address as a username. Might be a bug? Is there some file that stores the information of the remote locations?

Thank you in advance,

Erkki

---

