---
title: "Auto-repair script"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Prefix100 on 2008-05-03
I want to write a script that executes another script when i lose my Internet connection - it will act as an auto repair. 

Can anyone help me do this?

I have the repair script already, its just that I have no clue about how to make it execute when i lose my connection. 

I know I could just schedule it with cron to do it every hour or so, but this isn't the same.

Cheers,
Prefix

---

### Post by Prefix100 on 2008-05-04
Bump.

---

### Post by Prefix100 on 2008-05-05
Bump :/

---

### Post by Monicker on 2008-05-05
You could add a function which pings an external site, and if you don't receive a normal ping response, proceed with the repair.

---

### Post by Bez625 on 2009-02-19
> #!/bin/bash
while [ 1 ]
do
  sleep 10s
  if ! ping -c 2 192.168.1.1 > /dev/null
  then
     wall "network down"
     sudo /etc/init.d/networking restart
  fi
done


I wrote this, it pings my router twice every 10s (a bit excessive i know) and evaluates the response. Im not sure how well it works as its a relatively new script. If anyone wants to comment/change/improve etc feel free :)

---

### Post by superprash2003 on 2009-02-19
nice.. you  could also add the dhclient command to get an ip incase its an ip address issue. like sudo dhclient eth0

---

### Post by jtmedin on 2009-06-26
Would be interested in the repair script. I have a wireless connection that hangs & would like to repair rather than reboot. TIA

---

