---
title: "&quot;Check the logs&quot;"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by amiacamal on 2011-07-11
So I know that malware isn't going to be a major concern while im using ubuntu, but on browsing the security forum it seems to me that network intrusions are a much bigger problem. Not that ubuntu is weak to network intrusions, just that they are the more likely cause when people say they have been "hacked".

A common response is to tell people to "check the logs" for "unusual activity", My question is this, Which logs exactly? and how does one interpret "unusual activity"? 

-Amiacamal

---

### Post by frankbooth on 2011-07-11
First of all, to prevent these kind of things you'll want a *strong* password. That will take care of some of your paranoia. ;)

Second, what services are you running? You won't get "hacked" out of nowhere :). Neither are all intrusions a big concern unless they've got user rights. You might also want to read about [iptables]("http://en.wikipedia.org/wiki/Iptables").

Logs should be located at:
```
/var/log/
```

---

### Post by Grenage on 2011-07-11
Normally one would check /*var/log/auth.log* for dubious-looking login attempts.  'Unusual' would generally be a ton of failed logins, or sessions that really wouldn't have been you (or the system).

Network intrusions aren't really a bigger problem, they're just one of the few problems that all computer systems are susceptible to.  A good firewall, password, and disabling unused applications will almost guarantee safety.  Keeping applications up to date will make sure that security patches are applied.

---

### Post by amiacamal on 2011-07-11
10+ char/letter/number pass ought to do for now :) i'm not really paranoid about it, i just mean that its something iv recently become aware of. on windows i hadn't considered it! All i really wanna use the laptop for is gmail, youtube, facebook etc, but im also gonna be using it for my final year project ( not that thats of any interest to hackers). im just thinkin of if sometime in the future, i do notice something strange, whats my first step in seeing what happened, to avoid coming here and making one of those threads that goes:

"i'v been hacked"
-> no you havent.

--upon re-reading i just made no sense....--

---

