---
title: "resolv.conf"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by sagasha on 2006-11-11
When I boot up my computer my resolv.conf is:

search Belkin
nameserver 192.168.2.1
nameserver 68.87.77.130
nameserver 68.87.72.130

With those settings surfing is very slow. Spped is very good if I edit file to:

search Camcast.net
nameserver 68.87.77.130
nameserver 68.87.72.130

But when I boot again it re-writes to

search Belkin
nameserver 192.168.2.1
nameserver 68.87.77.130
nameserver 68.87.72.130

Help and thanks in advance.

---

### Post by NetworkGuy on 2006-11-11
Looks like the problem to me is coming from your Belkin router.   Are you running the latest firmware for your Belkin router?

---

### Post by deanlinkous on 2006-11-11
Sounds like your belkin router is handing out that info so adjust that and you should be fine. Or I guess you could edit that file and then make it read only and that may work also.

---

### Post by sagasha on 2006-11-11
Thanks for the quick replies. I was able to tell router to change the line:
search Belkin to search Comcast.net
but the problem seems to be the:

nameserver 192.168.2.1. 

How can I stop that from being added? I tried changing to read only but it still over-writes?

---

### Post by stream303 on 2006-11-12
I found that by hardcoding my isp's dns nameservers in my router's web-based setup page, they would be listed first in my /etc/resolv.conf.

Alternately you could edit (as root) **/etc/dhcp3/dhclient.conf** and find the line that reads:

#prepend domain-name-servers 127.0.0.1;

and uncomment it, and change it to:
[B]
prepend domain-name-servers 68.87.77.130, 68.87.72.130;[/B]

Note the lack of the beginning hash mark, servers with an "s", a comma between addresses, and a semicolon at the end.

This isn't elegant as it places multiple copies of your nameservers in the file, but at least they will be listed again at the very beginning.

reboot or restart networking.

What rewrites /etc/resolv.conf is dhclient, so the instruction in dhclient.conf will ensure that those dns addresses will prepend anything it automatically finds.  Making it read-only is useless.

---

