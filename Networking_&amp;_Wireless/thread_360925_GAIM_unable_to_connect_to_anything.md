---
title: "GAIM unable to connect to anything"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by megalania on 2007-02-13
GAIM is able to connect on my windows computer; however, I am not so fortunate on Ubuntu.  The issue just arose today.  

Here is my debug log if that helps at all.

dwinton@Ubuntu-desktop:~$ gaim --debug | grep oscar
plugins: probing /usr/lib/gaim/liboscar.so
oscar: oscar_login: gc = 0x8203468
dns: Host 'login.oscar.aol.com' resolved
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
dns[6247]: nobody needs me... =(
oscar: Signed off.

---

### Post by megalania on 2007-02-14
An odd developement: I am able to connect from any other computer, but this one computer has been unable to connect to AIM.  I have the necessary ports down for gaim so I see no reason for this developement.  Any ideas?

---

### Post by Floppyjoe on 2007-02-14
This sounds like a DNS issue. Something I am not totally familiar with. It might be worth searching for in any case.

---

### Post by lunaz on 2007-02-14
i dunno if this helps but i have to go to system > admin > networking > DNS & delete the 192.168.0.1 from DNS services for gaim to connect.

---

