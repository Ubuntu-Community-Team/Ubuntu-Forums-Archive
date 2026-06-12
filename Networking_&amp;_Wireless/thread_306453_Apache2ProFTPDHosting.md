---
title: "Apache2/ProFTPD/Hosting"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by Vermyndax on 2006-11-25
Greetings!

I have a question regarding "The Right Way" to do things on a Dapper 6.06 server.

I'm building out an apache2 installation.  According to "The Way Things Are," I see that when I install some of the packages (like phpmyadmin for example) it dumps them into /usr/share/<whatever> and then symlinks it from /var/www/<whatever>

So I've followed this model in building out websites that this server will be hosting.

Now I need to open some of the websites to users via proftpd so they can be edited.

What's The Right Way to go about this and permission it correctly?  Proftpd is installed and users can get into it, but I guess I'm concerned about permissions and the like... especially since permissions in /usr/share/ are root:root drwxr-xr-x.

Any insight on what I should be doing here?

Thanks!

---

