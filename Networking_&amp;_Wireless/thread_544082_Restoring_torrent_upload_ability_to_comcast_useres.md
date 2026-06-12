---
title: "Restoring torrent upload ability to comcast useres"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by faylix on 2007-09-05
From digg (and i hear slashdot too): 

[http://redhatcat.blogspot.com/2007/09/beating-sandvine-with-linux-iptables.html](http://redhatcat.blogspot.com/2007/09/beating-sandvine-with-linux-iptables.html)

supposedly a script to help defeat sandivine, or comcasts torrent throttling. 

> #!/bin/sh
#Replace 6883 with you BT port
BT_PORT=6883

#Flush the filters
iptables -F

#Apply new filters
iptables -A INPUT -j RH-Firewall-1-INPUT
iptables -A RH-Firewall-1-INPUT -i lo -j ACCEPT
iptables -A RH-Firewall-1-INPUT -p icmp --icmp-type any -j ACCEPT
#Comcast BitTorrent seeding block workaround
iptables -A RH-Firewall-1-INPUT -p tcp --dport $BT_PORT --tcp-flags RST RST -j DROP
#BitTorrent
iptables -A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport $BT_PORT -j ACCEPT
iptables -A RH-Firewall-1-INPUT -m state --state NEW -m udp -p udp --dport $BT_PORT -j ACCEPT
iptables -A RH-Firewall-1-INPUT -j REJECT --reject-with icmp-host-prohibited
iptables -A FORWARD -j REJECT --reject-with icmp-host-prohibited


The "Ubuntu version" anyway when I run it, i get 
> 
root@War-and-Peace:/home/faylix# sh torrent.sh
iptables v1.3.6: Couldn't load target `RH-Firewall-1-INPUT':/lib/iptables/libipt_RH-Firewall-1-INPUT.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name


clearly the writer was a redhat person, but i'd still like to be able to upload my Ubuntu image torrent to my fellow users... Anyone experimented?

---

### Post by mocoloco on 2007-09-06
Nice, thanks.

---

### Post by faylix on 2007-09-06
It would be nice if it worked! 

I'm fairly sure the problem is with "RH-firewalll-1 -input" but, i dont know enough about iptables to correct it... thus i'm asking here.


anyone?

---

### Post by chalewa on 2007-09-11
```
#!/bin/sh
#Replace 6883 with you BT port
BT_PORT=6883

#Flush the filters
iptables -F

#Apply new filters
iptables -A INPUT -i lo -j ACCEPT
#Comcast BitTorrent seeding block workaround
iptables -A INPUT -p tcp --dport $BT_PORT --tcp-flags RST RST -j DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#BitTorrent
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport $BT_PORT -j ACCEPT
iptables -A INPUT -m state --state NEW -m udp -p udp --dport $BT_PORT -j ACCEPT
iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited

```

---

### Post by bionnaki on 2007-12-13
to get this script running at startup, is this all I have to do?:

sudo nano /etc/rc.local

> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/home/bionnaki/.bak/sandvine.sh

exit 0


right?

---

