---
title: "network after Gutsy"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by anv on 2007-12-11
after change to Gutsy G. I have found some odd internet problem. I can go to web with my dyne:bolic linux but Ubuntu resists. It gets connection to router which has received IP but when I try firefox and updatas they wont connect to web. this has not happened before, and after couple of days after some late updates the prolem has become more resistant, often when I logout from x and back again or restart machine it fixes itself, (not very practical move but...) I  found some other same kind of questions without answer.

:confused:

---

### Post by Original Brownster on 2007-12-11
Hi,
You say it gets an ip ok from the router, I think I read about a problem with some routers not liking the new ipv6 used by gutsy as standard, try disabling ipv6

[this thread]("http://ubuntuforums.org/archive/index.php/t-87798.html") discusses how to disable it.

---

### Post by anv on 2007-12-11
Indeed after: 

"

gksudo gedit /etc/modprobe.d/aliases

Change

alias net-pf-10 ipv6
to
alias net-pf-10 off

Reboot.

Validate with
lsmod | grep v6
Should return nothing.

                                        "

it didn't just enable to browse the internet but did it much much faster than before, thank you so much.

---

