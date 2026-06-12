---
title: "named[862]: resolver priming query complete: every 20 seconds"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by holiday on 2018-06-20
BIND 9.11.3 Ubuntu 18.04 kernel 4.15.0-23

I am running bind9 as my LAN DNS and it is working for all hosts and forwarding to internet through the google DNS IPs

Why does my log have many instances of this message. 3-4 entries per minute :

      
     named[862]: resolver priming query complete

---

### Post by jsloveiv on 2018-08-19
I've got the same situation.  I upgraded 16.04 to 18.04 and now I'm getting this message every 10-20 seconds.  I haven't changed my DNS config much in 10 years, its authoritative for my home domain and forwards to google for the rest.

Google isn't helping on this one.  Any ideas?

---

### Post by dawdler2 on 2018-09-17
I also had a big fight with this, flooding my logs.

Finally it looks like bind needs the additional configuration option "allow-query-cache" set.

My access control list name is: goodclients

I added the line: allow-query-cache { goodclients; }; 
to my /etc/bind/named.conf.options.

I also had to set:
        dnssec-enable yes;
        dnssec-validation yes;
cause of using google-forwarders.

After reboot: again resolver priming messages ..
I then found out, that this resolver priming immediately stops after calling command dig including the +trace option.
The solution for me now is, that I added a ExecStartPost line in the bind9 service definition.
ExecStartPost=/usr/bin/dig [www.oneinternetsite.com]("http://www.oneinternetsite.com") +trace
Pls. use an existing site here ..
The output of the command then is in journal ...

After checking it reoccurs after 17 hours again.
Created a halfdaily cron job for dig with trace.

---

### Post by k6rfm on 2019-01-23
(withdrawn; suggested solution did't actually fix the problem in the long run.)

---

### Post by dima-zhemkov on 2019-02-18
If you use bind9 as caching DNS server without any custom zones, you should add the line forward only;
to your /etc/bind/named.conf.options.

---

### Post by derobert on 2019-12-05
Sorry for posting on an old thread, but since this shows up high in Google results, it's a known (and fixed) bind9 bug: [https://gitlab.isc.org/isc-projects/bind9/issues/752](https://gitlab.isc.org/isc-projects/bind9/issues/752)

BIND9 maintains a long-term support branch, which doesn't have the fix (it's only on the short-term support and development branches currently). Ubuntu uses the long-term support branch (9.11).

---

### Post by atralb on 2020-06-24
Thanks for the info @derobert. So what can be done then ? The "+trace fix" didn't change anything for me. (I can't update to 20.04)

---

### Post by coffeecat on 2020-06-24
Ancient thread closed.

@atralb, please start your own thread if you need help. The chances of getting help on old abandoned necromanced threads are minimal. Link back to this if it has useful information. The forum member you are addressing has not logged in since posting over 6 months ago.

---

