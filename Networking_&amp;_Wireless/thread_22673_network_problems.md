---
title: "network problems"
date: 2005-03-29
forum: Networking &amp; Wireless
---

### Post by charizan on 2005-03-29
i have just installed ubuntu linux in my computer and im having problems with the ethernet connection.
i m able to work to the local area network but i cant get in the internet.
I have double checked the ip,dns ,gateway and subnet mask and they are all ok!!
Any suggestions????
Thanx

---

### Post by localzuk on 2005-03-29
Have you tried running 'ping ubuntulinux.com' in a terminal? What does that say?

It should resolve a IP address as such:
user@host:~$ ping ubuntulinux.com
PING ubuntulinux.com (82.211.81.130) 56(84) bytes of data.
64 bytes from 82.211.81.130: icmp_seq=1 ttl=53 time=33.8 ms
64 bytes from 82.211.81.130: icmp_seq=2 ttl=53 time=35.1 ms

--- ubuntulinux.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 33.884/34.520/35.157/0.663 ms

---

### Post by m4ng0 on 2005-03-29
... and if ping does not work as localzuk said, check your /etc/resolv.conf

---

### Post by orion_114 on 2005-03-29
What machine are you using as your gateway ? (the one to connect to the net)
If you are connecting to a Windows XP machine that connects to the net try checking your windows xp firewall.

---

### Post by linuxNewb on 2005-03-30
I know that is sounds obvious, but have you tried reseting (unplugging/plugging-in) your modem?

---

### Post by arctic on 2005-03-30
check this howto. if the tips in there do not help, report back.
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)
good luck :)

---

