---
title: "Getting my website to appear on the web?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by ZJ88 on 2009-11-16
I have finished a website and it is in my var/www folder and seems to run great. The only problem, it only shows up if you look it up on my home network.  The URL is [www.hirekriskringle.com]("http://www.hirekriskringle.com"). When an outside computer tries to access it, you get "server timed out" or something like that. What do I need to do to get it from local to global?

---

### Post by 23dornot23d on 2009-11-16
This is what I see when I try to access it

[IMG]http://i36.tinypic.com/o1zl1.jpg[/IMG]

---

### Post by ZJ88 on 2009-11-16
ok so how do I get it to stop doing that? From what I have read, you have to do something so that everybody can access it but I don't know what that is. do I need to do port forwarding of is it something in the file var/www? Like I said, you only get that error if it's on a computer outside of my home network

---

### Post by dca on 2009-11-16
If you're hosting it, make sure the domain regsitrar has it pointing to your server, then double, triple check your firewall.
 
If using ufw, @ CLI:  
 
sudo ufw allow http 
 
(and)
 
sudo ufw allow https
 
...don't quote me, not used to ufw ...

---

### Post by Bunnybugs on 2009-11-16
Well. you'll need to setup your server to be a netserver instead of a local server...

The best is to use a domainserver, suchs like webs.com, or other free solutions... it's kinda hard to setup your own website server... it needs to be an FTP, and you'll need a long line of tools to publish your site from ftp to domain!

Use a free domain/webspace... that's much cheaper then diy

---

### Post by Maheriano on 2009-11-16
Ya, where are you hosting your DNS files and where are they pointing? There's something wrong with them.

---

### Post by Joeb454 on 2009-11-16
One thing that I'm surprised hasn't been mentioned is port forwarding on your router. If port 80 isn't forwarded to your router, chances are nothing will connect

---

### Post by NullHead on 2009-11-16
> **Joeb454 said:**
> One thing that I'm surprised hasn't been mentioned is port forwarding on your router. If port 80 isn't forwarded to your router, chances are nothing will connect

You beat me to it. 

I agree, you need to make sure port 80 is open. This will allow traffic to get to your server.

---

### Post by ctyc on 2009-11-16
Here is the problem you did not set up your dns zone file entries correctly or you dont have and external IP(wan ip)

A records
HIREKRISKRINGLE.COM.	3600	IN	A	192.168.1.106
[www.HIREKRISKRINGLE.COM](www.HIREKRISKRINGLE.COM). 3600	IN	CNAME	HIREKRISKRINGLE.COM.
HIREKRISKRINGLE.COM.	3600	IN	A	192.168.1.106
ftp.HIREKRISKRINGLE.COM. 3600	IN	CNAME	HIREKRISKRINGLE.COM.
HIREKRISKRINGLE.COM.	3600	IN	A	192.168.1.106
mail.HIREKRISKRINGLE.COM. 3600	IN	CNAME	pop.secureserver.net.
smtp.HIREKRISKRINGLE.COM. 3600	IN	CNAME	smtp.secureserver.net.
pop.HIREKRISKRINGLE.COM. 3600	IN	CNAME	pop.secureserver.net.
webmail.HIREKRISKRINGLE.COM. 3600 IN	CNAME	webmail.secureserver.net.

MX and SOA Details
HIREKRISKRINGLE.COM.	3600	IN	MX	0 smtp.secureserver.net.
HIREKRISKRINGLE.COM.	3600	IN	MX	10 mailstore1.secureserver.net.
HIREKRISKRINGLE.COM.	86400 IN SOA ns13.domaincontrol.com. dns.jomax.net. (
				2009111500 ; serial
				28800      ; refresh (8 hours)
				7200       ; retry (2 hours)
				604800     ; expire (1 week)
				86400      ; minimum (1 day)
				)

Good Luck

---

### Post by ZJ88 on 2009-11-16
Ok so I am pretty sure I forwarded the port through my router but I think the problem is this, when I looked up my ip with ifconfig there were two IP's inet address and bcast address. I used the first so I'm trying the second to see if it works. Thanks for all help!

---

### Post by ZJ88 on 2009-11-16
Actually, I don't think your supposed to use the bcast ip. I got my domain name at godaddy.com and they are parked there, we used the A host thing to tell it to point to the inet ip. I think all of that is fine, I need to check my port forwarding stuff though. I went into my linksys port forward range and I said APP was WEB from 80 to 80 and ip 192.168.1.106. I think that is right...

---

### Post by alphacrucis2 on 2009-11-16
When I look up the host [www.hirekriskringle.com](www.hirekriskringle.com) on the public DNS it returns ip address 67.166.64.0. That is never going to work as it is the start of a netblock 67.166.64.0/20. You need to set the DNS to point at your router's public ip address, not a netblock.

---

### Post by ZJ88 on 2009-11-16
Yes I tried changing where it points to but that didn't work so now it's back to good ol' 192.168.1.106. I went into my router and forwarded port 80 to that ip but it's still only works in my home network. People keep saying I need to change my DNS but that is hosted on godaddy and it points back to my server. From what I have read, all I should have to do is forward port 80 to the server but that's not doing anything

---

### Post by lisati on 2009-11-16
> **ZJ88 said:**
> Yes I tried changing where it points to but that didn't work so now it's back to good ol' 192.168.1.106. I went into my router and forwarded port 80 to that ip but it's still only works in my home network. People keep saying I need to change my DNS but that is hosted on godaddy and it points back to my server. From what I have read, all I should have to do is forward port 80 to the server but that's not doing anything

I'm not sure I'm following what's happening or what's required sufficiently well to say too much. Isn't the 192.168.1.106 address what you need to use for the port redirection in your router? It looks to me like an address that would be used in a local network rather than something you'd use for DNS resolution.

---

### Post by alphacrucis2 on 2009-11-16
> **lisati said:**
> I'm not sure I'm following what's happening or what's required sufficiently well to say too much. Isn't the 192.168.1.106 address what you need to use for the port redirection in your router? It looks to me like an address that would be used in a local network rather than something you'd use for DNS resolution.

+1. 

RFC private blocks such as 192.168.x.x are not routable over the internet. He needs to set the router's public address in the DNS so that the web traffic for [www.hirekriskringle.com](www.hirekriskringle.com) actually gets delivered from the internet to his router, then the router itself must do port forwarding/DNAT to get to the web server on the private (192.168.x.x) address behind the router.

---

### Post by halitech on 2009-11-16
you need to configure the DNS info correctly. Also, if you are running this on a residential dsl or cable connection, you better check with your ISP and make sure they allow you to run a webserver on a residential connection and that port 80 isnt blocked..

If you are allowed, look into Zone edit ( [http://zoneedit.com/](http://zoneedit.com/) ) to configure your (likely dynamic) IP to be where DNS servers are looking. If you need to figure out what your External IP address it, go to [http://ipchicken.com](http://ipchicken.com) and it will tell you.

---

### Post by ZJ88 on 2009-11-17
Hey sorry for the confusion everybody, I'm confused also, I know too little about servers. But I think I may know what is going on, I found out last night that other people have had this problem with my ISP, comcast. Apparently comcast blocks incoming Port 80 connections. If I'm not mistaken, I think this is what would cause it. Does anyone know a way to work around that?

---

### Post by halitech on 2009-11-17
If they are blocking port 80 they are doing it to stop people from running webservers on residential connections. Meaning, you are not allowed to do so.

Check here to make sure port 80 is blocked
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

You should get a message like this
> Success: I can see your service on 24.xxx.xxx.xxx on port (80)
Your ISP is not blocking port 80

---

### Post by ZJ88 on 2009-11-17
I got it working! I found out that I was using the wrong External IP. Stupid huh? When I went to your links it showed me that my external IP was different than I was using. I couldn't find it anywhere but when I changed it to that, it worked! Thanks again for the help, and sorry that it was such a simple answer!

---

### Post by Maheriano on 2009-11-17
> **ZJ88 said:**
> I got it working! I found out that I was using the wrong External IP. Stupid huh? When I went to your links it showed me that my external IP was different than I was using. I couldn't find it anywhere but when I changed it to that, it worked! Thanks again for the help, and sorry that it was such a simple answer!

I was going to say this. To get your IP more easily, go to [www.whatismyipaddress.com](www.whatismyipaddress.com).

---

### Post by Cheesemill on 2009-11-17
Also bear in mind that as you have a residential connection your external IP is likely to change from time to time, either when you have to reboot your router or when the DHCP lease expires.

You can either pay extra to get a fixed IP from your ISP or look into a dynamic DNS service.

---

### Post by sandyd on 2009-11-17
> **Cheesemill said:**
> Also bear in mind that as you have a residential connection your external IP is likely to change from time to time, either when you have to reboot your router or when the DHCP lease expires.

You can either pay extra to get a fixed IP from your ISP or look into a dynamic DNS service.
use dyndns w/ dhclient.
their pretty great

---

