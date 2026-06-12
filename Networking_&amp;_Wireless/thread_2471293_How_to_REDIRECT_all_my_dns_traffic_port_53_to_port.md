---
title: "How to REDIRECT all my dns traffic port 53 to port 9053 (tor-dns)?"
date: 2022-01-25
forum: Networking &amp; Wireless
---

### Post by han85 on 2022-01-25
Hi guys!

What must be the rule for iptables to forward all my dns traffic on port 53 to port 9053?

Is it even necessary if I have PIHOLE running which listens on port 53?

I tried this:

iptables -t nat -A OUTPUT -d 127.0.0.1/32 -p udp -m udp --dport 53 -j REDIRECT --to-ports 9053
iptables -t nat -I PREROUTING --src 0/0 --dst 192.168.10.10 -p udp --dport 53 -j REDIRECT --to-ports 9053


I could not notice any difference.

PIHOLE dns listens on UDP port 53. tor dns on port 9053 (tcp)

I would like to know how to do this with dns forwarding with iptables. 

Please help, thanks!

---

### Post by SeijiSensei on 2022-01-26
I'd leave the source and destination fields empty, but if the tor server expects TCP this will never work. Usually TCP for DNS is used only to transfer domains between servers; queries are handled using UDP. Is there no UDP listener for the tor server?

---

### Post by han85 on 2022-01-27
**@  SeijiSensei**,

tor dns is on localhost active and added tor dns port to PIHOLE **/etc/dnsmasq.d/01-pihole.conf**

added:
server=127.0.0.1#[B]tor-dns-port-here

[/B]Now the name resolution works with PIHOLE via tor-dns when I check dnsleaktest.com (shows me tor-dns server, or web browsing)

I thought I had to add the iptables and forward port 53 to port "tor-dns" in the iptables.It seems that PIHOLE is taking over. I hope I am right ;-)By the way,
I have tested **tor-resolve 'domain-here'** and it does not work.[B]

*tor-resolve ecosia.org*

[/B]Jan 27 12:25:19.181 [err][B] _Error while connecting to SOCKS host: Connection refused_
[/B]
Maybe you can help me to find out what the problem is.

tcp        0      0 127.0.0.1:9150          0.0.0.0:*               LISTEN      812/tor             
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1264/lighttpd       
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      1254/pihole-FTL     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1264/lighttpd       
tcp        0      0 127.0.0.1:4711          0.0.0.0:*               LISTEN      1254/pihole-FTL     
udp        0      0 0.0.0.0:53              0.0.0.0:*                           1254/pihole-FTL     
udp        0      0 127.0.0.1:9053          0.0.0.0:*                           812/tor

[B]nmap localhost

[/B]PORT    STATE SERVICE
53/tcp  open  domain
80/tcp  open  http
443/tcp open  https

---

### Post by han85 on 2022-01-27
**@  SeijiSensei**,

Is it even possible to use tor as a dns server with PIHOLE?

Strangely, my name resolution works with PIHOLE and tor-dns when I call websites or run apt update for example.

---

### Post by SeijiSensei on 2022-01-27
I have never used tor.  I see no reason for using it in the case you're describing. The usual method for setting up a DNS server is to run BIND9.  

[https://www.linuxtechi.com/install-configure-bind-9-dns-server-ubuntu-debian/](https://www.linuxtechi.com/install-configure-bind-9-dns-server-ubuntu-debian/)

Then you would specify that machine's network IP as the DNS server in all clients. If you use DHCP, you can add the server's address there and have it distributed automatically.

---

### Post by han85 on 2022-01-27
Found solution here:
[B][https://docs.pi-hole.net/guides/misc/tor/setup/](https://docs.pi-hole.net/guides/misc/tor/setup/)

"SOLVED" :-)
[/B]

---

