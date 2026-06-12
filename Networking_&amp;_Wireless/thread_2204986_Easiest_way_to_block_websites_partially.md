---
title: "Easiest way to block websites partially"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by shultz.andrey on 2014-02-11
I'am a ubuntu noob. I try to block a website partially. It's mean, that I want allow access to google.com, but deny for google.com/imgres (it's just an example). It's not possible via /etc/hosts file, because it supports only domain. Thanx.

---

### Post by Gone fishing on 2014-02-11
This isn't the easiest thing to do but will work well, you could set up a Squid proxy sever and then use Squid guard / dansguardian to block sites. Otherwise Firefox has has extensions you could use, possibly wou can blacklist sites on your router.

---

### Post by shultz.andrey on 2014-02-11
Thanx for answer. I hear about Squid, but I'am not sure, that I can config him with my knowledge level :) My router support limited list of websites + he doesn't support https connections for blacklist.

---

### Post by Gone fishing on 2014-02-12
I would go for one of the extension tools built for Firefox then

---

### Post by Benjamin_E_Nichols on 2014-07-13
Hello, I was just reading this discussion about setting up a  Squid proxy and thought I would take the time to write a short note to  inform you guys and gals that we offer blacklists tailored specifically for  Squid proxy native acl, as well as alternative formats for the most  widely used third party plugins. So we invite you all to check us out.  We take a great deal of pride in the fact that our works offer a higher  degree of quality than the freely available options.

Quality Blacklists Tailored For Squid Proxy -  [http://www.squidblacklist.org](http://www.squidblacklist.org)

---

### Post by jaimerosario on 2014-07-16
I'm working on a script that configures Ubuntu Server with Squid3/Dansguardian/DHCP/BIND9 (forward DNS only) with Webmin and dgwebmin plugin.
It configures Dansguardian for URLbigblacklist and Squid3, both configured with whitelists and some blacklists. If you are interested, send me a message.

---

