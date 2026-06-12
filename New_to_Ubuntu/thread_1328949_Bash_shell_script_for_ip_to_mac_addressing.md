---
title: "Bash shell script for ip to mac addressing"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by abraves247 on 2009-11-16
I just started using Ubuntu and I was wondering if there is a script that I can give an ip address and it will find the mac address on my network?

---

### Post by teward on 2009-11-16
IPs and MAC addresses are not super-directly connected.  This sounds, however, like someone trying to clone a MAC address to gain access to something (sorry for my paranoia, but I am a tech, and this sounds suspicious).

---

### Post by wingnut59 on 2009-11-17
you can try this, as long as the other address is in the same subnet, it should work.

#!/bin/bash
ping -q -c 4 $1 >/dev/null
/usr/sbin/arp -an | /bin/grep $1 | /usr/bin/cut -d " " -f 4

---

### Post by abraves247 on 2009-11-18
Thank you Wingnut59 that helped a lot I work at a school and we want to be able collect all the mac addresses in all the labs without doing it one by one.

---

