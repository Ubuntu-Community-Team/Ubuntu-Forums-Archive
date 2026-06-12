---
title: "Mail Server qustions"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by chazzn@msn.com on 2011-04-11
Want to install a simple mail server that will allow mailids that are not userids on system. Want the option to scan incoming email and forward somewhere else in some cases and simply trash without storing in others.
want to be able to store subject lines by source, keep counts, message sizes,  date, time, etc for statistical analysis, but may not want to do it all the time. Want simple interface to create new mailids and link them to an owning mailid not necessarily on same system, and it would be conveneint if the interface was web based. can anyone point me to tools or examples of accomplishing this goal? PROCMAIL looks like it might fit in somewhere.

---

### Post by HermanAB on 2011-04-11
Howdy,

Install Citadel.  The Easy install script takes about 20 minutes and results in a full featured mail system that 'Just Works'.  It is also in the repos, so you can also install it with the Software Install wizard:
[http://citadel.org](http://citadel.org)

However, before you install a mail server, you must have your DNS under control.  You need a domain name with A, MX and PTR records.

---

### Post by chazzn@msn.com on 2011-04-11
where de i learn more about the DNS needs? 

Wanting to setup mail server for family and few friends. Some othetr features/capabilities I would  like would br "receive only IDs" and "mailboxes that are limited by size or time, and delete oldest to make room for new.
 
can citadel be configured to do these kinds of things?

---

