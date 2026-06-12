---
title: "pinger - GTK/ncurses multiping utility"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Zaggy on 2006-12-03
Author: Petr Koloros 
Website: [http://aa.vslib.cz/silk/projekty/pinger/](http://aa.vslib.cz/silk/projekty/pinger/)

Screenshot of the GTK interface:
[IMG]http://img117.imageshack.us/img117/3691/pingerhn1.png[/IMG]

Screenshot of the the ncurses interface:
[IMG]http://img217.imageshack.us/img217/8329/pingerbs8.png[/IMG]

How to get it working:

1. Get the latest version (at the moment of writing): [http://aa.vslib.cz/silk/projekty/pinger/download/pinger-0.31d.tar.gz](http://aa.vslib.cz/silk/projekty/pinger/download/pinger-0.31d.tar.gz)

2. Extract it to somewhere

3. Open a terminal and browse to the directory you extracted it to
(cd xyz)

4. Browse to the src directory and edit the arp.c file (gedit arp.c)
place this line into pinger's arp.c file:

#include <linux/netdevice.h>

right before if_arp.h so it looks like this:

#include <linux/netdevice.h>
#include <linux/if_arp.h>
#include <features.h>    /* for the glibc version number */

5. ./configure && make && sudo make install

6. It should be installed now, time to configure it:
gedit ~/.pingerrc
and change the IPs/hostnames/names as you see fit

7. start it!
'pinger --gtk' for the gtk interface
'pinger for' the ncurses interface
Also, you could add --quiet to not display messages into the console.

Perhaps this one is good for the repository? ;-)

---

### Post by silcus on 2006-12-04
Zaggy, thanks for there instruction for Ubuntu users.

I'll check the headers and if it is not an anomaly, I'll implement those changes in the pinger in the next release.

To all: if you want to enjoy better GTK behavior and look, please use svn version until there is 0.32 out (maybe this week).

---

