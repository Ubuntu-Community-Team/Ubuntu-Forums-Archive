---
title: "ddclient cannot determine IP address"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by Johnny K on 2007-12-08
For some reason, whenever I run **sudo ddclient**, I get the following error message:
```
WARNING:  unable to determine IP address
```
What could be causing this? I need to find an answer because I use ddclient as part of a "Lojack" system (see: [http://www.arsgeek.com/?p=1612](http://www.arsgeek.com/?p=1612)). The "Lojack" system is dependent on ddclient, so if it isn't working I have no Lojack :(

Thanks in advance :)

---

### Post by Johnny K on 2008-01-24
Unfortunately, I am still suffering this problem. I hate to bump, but it this very important and I want to make sure I can find my laptop if it ever gets stolen :)

Is anyone else experiencing this problem, or does anyone have any ideas why this is happening?

Thanks alot

---

### Post by thantos on 2008-01-25
What dynamic DNS service are you signed up with?  
What does your /etc/ddclient/ddclient.conf look like?
What have you tried/searched on the forums to fix this?

---

### Post by Johnny K on 2008-01-25
I just did a search and and was able to find a post on another forum that I didn't find a few weeks ago. It turns out that chaning the ddclient.conf line
```
use=if, if=web
```
to
```
use=web
```

fixes the problem. Weird, but whatever. Thanks alot!

---

