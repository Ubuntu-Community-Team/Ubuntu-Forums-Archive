---
title: "Web Server : internet ok - Windows Stations : firefox doesn' t work - any idea ? Thks"
date: 2005-04-01
forum: Networking &amp; Wireless
---

### Post by Spear on 2005-04-01
Hi !

I had a big server problem on the filesystem (Debian Woody), and i thought it was a nice occasion to try Ubuntu.
I installed everything and upgraded to the required modules. But, after hours spent searching , i can' t find a way to surf on internet from the stations (running Windows XP) using it as a gateway.

The server is running ubuntu, it is a webserver, and a gateway for 3 stations running Windows.

The network is using static IPs ; the server' s ip is used as the gateway for the stations.

I unsettled in /etc/peers/dsl-provider : #usepeerdns , because that option asks the dns to the provider and changes resolv.conf. Resolv.conf is okay with it' s nameservers, and the same dns names are being used in the workstations.

The connection to the internet works okay, and i can surf from the server without any problem. From the stations, i can ping external ips, even names, i can use IRC client ... but ! if i launch thunderbird : it sees the mails but tries undefinitely to get them (my server isn' t a mail server). If i run Firefox i can' t reach websites from the stations ... in fact, if i type " google " i reach the google page ... but if i type " [http://www.google.fr](http://www.google.fr) " it doesn' t work. I managed to reach another linux page and that' s all. I took the same masquerading configuration i used under debian woody, i re-read the Masquerading guide, but didn' t find any solution.

Thanks !

---

### Post by bihe on 2005-04-02
my setup is allmost the same. but i'm using bind on the gateway, so
there is less dns lookup traffic. bind on the gateway only acts as a 
caching nameserver and forwards requests to the isp nameserver.

my iptables setup is fairly simple:

  COMMAND="/sbin/iptables"
  /sbin/modprobe ip_tables
  /sbin/modprobe ip_conntrack
  /sbin/modprobe ip_conntrack_ftp
  /sbin/modprobe iptable_nat
  /sbin/modprobe ip_nat_ftp
  /sbin/modprobe ipt_state
  /sbin/modprobe ipt_limit
  /sbin/modprobe ipt_LOG

  echo 1 > /proc/sys/net/ipv4/ip_forward
  ## masquerade
  $COMMAND -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
  ## FORWARD rules
  $COMMAND -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
  ... # other forward rules

maybe this helps

---

### Post by Spear on 2005-04-02
Thanks for the bind idea ! I' ll try it, and even if it doesn' t work to solve this case, i' ll work on that  for the gateway !

So, i' m bringing here the last tests ...

Today, i took the hoary-live-cd and booted from a workstation ... i configured :
In disorder :)

- i used the same iptables ruleset i used on the server
- pppoeconf (with no modification at all)
- the network address (same as the server, same mask)

of course, i stopped the server ...

and it worked !

I took the hoary-live-cd and used it with the same parameters on the server ... and it doesn' t work. So something is wrong with the hardware ... i changed the network cards between the server and the workstation (server has a Netgear FA311 and i already had some problems with it). But it doesn' t change anything (in the Warty usual configuration) : doesn' t work.
I' ll try the Hoary Live CD again later today and tell you the results on the server, and on the workstation with the netgear card.

---

### Post by Spear on 2005-04-04
The Hoary Live CD works with the station's network card once it' s in the server, i have a normal access on the stations. So, today morning, i upgraded the Warty to Hoary ... and ... it doesn' t work once upgraded.

As i absolutly need to restart the server, i had to reinstall a Debian Woody. It works.
I' ll try to backport old packages from woody and try with ubuntu.

---

