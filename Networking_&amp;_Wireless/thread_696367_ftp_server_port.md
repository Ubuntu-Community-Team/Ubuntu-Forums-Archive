---
title: "ftp server port"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by bschleusner on 2008-02-13
Ok, I set up a crappy little FTP server over the weekend for no particular purpose, and it worked fairly good because I am on DSL and have a static IP so I can access it from anywhere, and I had a couple users set up, and everything was going good.... until

I checked the security log and found that within 3 days there were thousand of "oracle' and 'Administrator' login attempts from an IP that was from Guam!!!!!!  :mad:

now, I tried changing the FTP port from using port 21 to 51123 (just a random port), and opened the port on my router, and when I tried logging back in, it refused connection.

What am I doing wrong? How do I get it to change port?


BTW, I am using GPROFTPD to configure all of this.

---

### Post by ghostdog74 on 2008-02-13
how are you connecting to your FTP server? If your FTP server supports using another port
```

# ftp  ftpserver <portnumber>

```
also your router needs to know this port number.
IMO, there's really no need to change the port number. If you are paranoid, use a more secured file transfer mechanism, like SSH.

---

### Post by bschleusner on 2008-02-13
ok, that was my problem. I was just typing it in wrong with the port number. :lolflag:

thanks! I guess I should have read the man pages first....:D

---

### Post by HermanAB on 2008-02-14
BTW, the simplest way to prevent these annoying script kiddie attacks is with a simple rate limit in iptables.  Add the following lines to the bottom of /etc/rc.d/rc.local, to limit new login attempts to once per minute:

iptables -I INPUT -p tcp -m state --syn --state NEW --dport ssh \
-m limit --limit 1/minute --limit-burst 1 -j ACCEPT
iptables -I INPUT -p tcp -m state --syn --state NEW --dport ssh -j DROP

That will defeat even the most patient hacker.

Cheers,

Herman

---

