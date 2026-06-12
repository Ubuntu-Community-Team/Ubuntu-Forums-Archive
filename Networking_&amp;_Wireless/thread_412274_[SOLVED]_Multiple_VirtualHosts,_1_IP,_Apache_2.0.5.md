---
title: "[SOLVED] Multiple VirtualHosts, 1 IP, Apache 2.0.55 (Dapper) - fail with no warning"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-04-17
Good even gentlemen,

I'm having a simple, but odd problem with my Dapper LAMP server at the moment.

I've initiated 2 virtualhosts based off of the original "default" file provided by Apache2. I've disabled "default" and enabled "example1.com" and "example2.com" manually at first, then using 'a2ensite' and 'a2dissite' just to be certain.

You can see the files below. The only change made in the "apache2.conf" file, is where I added:
```
ServerTokens Prod 
NameVirtualHost #.#.#.#
```

*Please note: #.#.#.# is a masked IP address, as well as example1.com and example2.com are masked FQSNs. The file names are the same, without the ".txt" concatenated.*

The error I recieve shortly before it fails is:
```
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

Now that's an obvious error: It simply says I don't have a ServerName for my default site. This shouldn't make Apache [fail] on startup.

Can you point out what is flawed in my three configuration files? No other file (such as "httpd.conf" or "ports.conf") has been modified.


Thank you for your time.


Lastly, I noticed that my 'NameVirtualHost' is below my 'Include' line in "apache2.conf". I've switched it around to begin BEFORE the 'Include' line, and it still fails.

---

### Post by altonbr on 2007-04-19
bump.

---

### Post by altonbr on 2007-04-22
Well, basically all I did was take out the Include call to the "sites-enabled" folder at the bottom of the apache2.conf file, and wrote my own, extremelly basic, VirtualHost dirivatives.

---

