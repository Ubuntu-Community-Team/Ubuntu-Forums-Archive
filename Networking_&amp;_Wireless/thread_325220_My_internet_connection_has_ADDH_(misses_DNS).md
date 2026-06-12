---
title: "My internet connection has ADDH (misses DNS??)"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by gfgodoy on 2006-12-25
I'm having a problem with my Internet connection... I think it has ADDH :) (Attention deficit disorder with hyperactivity)...

Here is what happens (this does NOT happen under Winblows ;( ):

I have set up an PPPOE connection as the help file suggested... and BANG: it works just fine!

But then, after a while (30mins to 1 hour) I try to enter a site and firefox gives me the "server not found" error!!

weird: my downloads keep working... and GAIM also :( which makes me wonder if it is a DNS handling problem (I acquire them automatically on connection) 

Heres what I found on log:

(daemon.log)

Dec 17 23:05:24 Hal-9000 dhclient: DHCPREQUEST on eth0 to 10.0.0.138 port 67
Dec 17 23:05:24 Hal-9000 dhclient: DHCPACK from 10.0.0.138
Dec 17 23:05:25 Hal-9000 dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Dec 17 23:05:25 Hal-9000 dhclient: bound to 10.0.0.1 -- renewal in 3366 seconds. 




The only way I can bring my connection to life is by typing:

sudo poff dsl-provider
sudo pon dsl-provider


What can I do??????

Thanks in advance

---

### Post by dbott67 on 2006-12-25
You may want to try 2 things:

1. Blacklist ipv6
2. Change default DNS servers to OpenDNS servers.

Both steps are outlined in this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747](http://www.ubuntuforums.org/showthread.php?t=323747)

-Dave

---

