---
title: "bind9 to domain name"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by shanep-server on 2009-09-07
I setup a server running hardy desktop. I'm trying to set up a DNS server to point my domain name shanes-spot.info to my web server. I'm setting up my server to host a web site. I am setting up email server, dns server, ssh server, web server all on the same machine. My goal is to host my web site, host my own email, an use DNS to point my URL to my webserver. I am fairly new to all of this an just jumping right in.

I'm trying to set up DNS server using Bind9 

I'm following a tutorial from [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

What I don't quite understand is the serial # on my zone files an how or when too increment them.

Also when I try to ping my server it comes back with the following - 

64 bytes from parkwebwin-v01.prod.mesa1.secureserver.net (68.178.232.100): icmp_seq=2 ttl=108 time=157 ms

And when I try this

named-checkzone shanes-spot.info /etc/bind/db.shanes-spot.info

it returns with the following

zone shanes-spot.info/IN: NS 'ns.shanes-spot.info' has no address records (A or AAAA)
zone shanes-spot.info/IN: loaded serial 2
OK

named-checkzone shanes-spot.info /etc/bind/db.192

it returns with the following

zone shanes-spot.info/IN: loaded serial 1
OK

when I try this 

shane@shane-desktop:~$ dig 192.168.0.in-addr.arpa. AXFR

the following is recieved

;; Connection to 192.168.0.1#53(192.168.0.1) for 192.168.0.in-addr.arpa. failed: connection refused.

Any help would be great cuz i'm kind of lost at the moment.

---

### Post by Ocxic on 2009-09-07
the best way would be to use webmin to configure your server, it makes it much easier. just create a master zone, add the address and corresponding IP and your done.

please note Bind9 on your system will not allow the internet to see your domain, for that you could use DynDNS as a free service, for that.

---

### Post by shanep-server on 2009-09-07
ok i'm an idiot i have to setup 2 dns servers on my computer then switch settings at godaddy so it forwards to my DNS servers. I'll come back with more info in a few hours hopefully

---

### Post by shanep-server on 2009-09-07
So bind9 only works for local Domains on a local network? I guess I don't understand what the point of having a DNS server is then lol

---

### Post by Ocxic on 2009-09-07
You could use a dns server to provide local name resolution on your home network like i do. makes it easer then remembering ip addresses, tho all my computers use static IP's so i don't have to setup a DHCP that will update my dns server.

like i said if you want the Internet to be able to access your web page you could use DynDNS a free service that will give you the name resolution the will point your [www.whatever.com](www.whatever.com) to your computer, i use it everyday at work to get around the filter.

---

### Post by cariboo on 2009-09-08
You really have no need for a local dns server, use Godaddy's utility to setup dns. The many server tutorials that include setting up a dns server just create a lot of extra work when setting up your server.

---

