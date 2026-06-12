---
title: "DNS / Bind / Dynamic IP - Please Help"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by schurtek on 2006-08-03
This is something I tried back in the days of my Windows (shudder) NT servers, now I am running all Linux servers with only one server to convert... (I will be baptising that server by the end of this month). 

Due to the kind of work my business does, I am often requiring to access files on my servers at my head office, but I might be at another office. So I am running No-IP on each server... but I have my own DNS server on the internet. It was all part of my server package I bought from the Planet (Texas, USA) for hosting my projects.

I have registered a domain name which I own... schurtek.co.za

I would like to set up an Intranet DNS server that will track allow me to access a local server by typing say damien.schurtek.co.za or even gollum.schurtek.co.za or igore.schurtek.co.za . . . you get the idea. 

Now that's suppose to be simple, but even with Windows (shudder) couldn't get it to work.

I then want to set up that same server to map dynamic IP numbers on my server in the states. I have access to my Name Records, but only via a control panel. So what I was thinking, was to setup some subdomains, with a bit of PHP code to lookup the dynamic IP address from a MySQL database and then just run the server's pages through the frame.

But I just can't get my head around this DNS/BIND thing...

Any help?

---

### Post by mips on 2006-08-03
What have you done so far. Show some files.

---

### Post by darrenm on 2006-08-03
> **schurtek said:**
> This is something I tried back in the days of my Windows (shudder) NT servers, now I am running all Linux servers with only one server to convert... (I will be baptising that server by the end of this month). 

Due to the kind of work my business does, I am often requiring to access files on my servers at my head office, but I might be at another office. So I am running No-IP on each server... but I have my own DNS server on the internet. It was all part of my server package I bought from the Planet (Texas, USA) for hosting my projects.

I have registered a domain name which I own... schurtek.co.za

I would like to set up an Intranet DNS server that will track allow me to access a local server by typing say damien.schurtek.co.za or even gollum.schurtek.co.za or igore.schurtek.co.za . . . you get the idea. 

Now that's suppose to be simple, but even with Windows (shudder) couldn't get it to work.

I then want to set up that same server to map dynamic IP numbers on my server in the states. I have access to my Name Records, but only via a control panel. So what I was thinking, was to setup some subdomains, with a bit of PHP code to lookup the dynamic IP address from a MySQL database and then just run the server's pages through the frame.

But I just can't get my head around this DNS/BIND thing...

Any help?

Don't understand what you're trying to do...

You have dynamic IPs on all your servers and you want to access them using your own domain names?

If so can you not just use dyndns and point your DNS entries for the domain you want to use to yourhostname.dyndns.org ?

I would have thought the best and easiest way would be to get a static IP for each server though and then you can have DNS properly setup for your zone.

---

### Post by schurtek on 2006-08-04
> **mips said:**
> What have you done so far. Show some files.

I haven't done anything yet... well not on my Linux box... I am building a linux box for this task... dedicated. Ultimately it will be used as a DNS/Bind Server and a Proxy Cache.

I have tried in the post with previous Linux boxes, but linux is more hands on... and since I no nothing about DNS/Bind I just loose myself...

---

### Post by schurtek on 2006-08-04
> **darrenm said:**
> Don't understand what you're trying to do...

You have dynamic IPs on all your servers and you want to access them using your own domain names?

If so can you not just use dyndns and point your DNS entries for the domain you want to use to yourhostname.dyndns.org ?

I would have thought the best and easiest way would be to get a static IP for each server though and then you can have DNS properly setup for your zone.

Okay... let me explain... I have several servers at home... which is head quarters for my business... I have wireless internet, but the guy who offers the internet connection doesn't offer Static IP cos he is connecting everyone via a couple DSL lines. 

Now Dynamic IP works, as I have been using no-ip.com, but I want to use schurtek.co.za (I have my reasons). I know it can be done... as if no-ip.com can do it, then so can I.

I have spoken to no-ip.com to handle it through my domain name, but they want to charge me more than what I am currently paying for my server at The Planet, which as DNS on it, and I have access to the DNS Records.

Thanks...

---

### Post by darrenm on 2006-08-04
OK think I get you.

You have schurtek.co.za as your domain. This is currently purchased and residing with your hosting provider (websitewelcome.com) but you have several servers all running with a single NAT'd IP address that is dynamic. You want each server to have its own hostname in your namespace i.e main.schurtek.co.za, backup.schurtek.co.za etc.

To allow your bind install to be able to dish out the correct IP for each server it would need to be authoritative for that domain which can be fairly easily done by getting your hosting provider to change their NS settings or changing them yourself but then you have the NAT problem.

Your outside IP of your NAT'd server's are all going to be the same, a public IP such as 62.59.165.34 . When your DNS server answers a query for main.schurtek.co.za it will give the inside private IP, say 192.168.0.1 as the answer. which would mean nothing to the remote client trying to connect.

You could set your bind server to reply for each name as the same outside IP address but then how would the client know which server to connect to?

I think the answer will lie in what services you need to connect to. SSH? SMB shares?

OpenVPN may be your best bet...

---

### Post by schurtek on 2006-08-05
Hey Darren, thanks... 

I understand the NAT thing, the way I understood it, was that when I connect to a PHP script, it can give me my outside IP which is usually in the 165 range. My internal IP addresses are in the 192.1.0 range, but obviously my internal DNS server will handle the query... and then redirect it to the correct server depending on the subdomain. There has to be a way for this to work... as I had it running on no-ip.com...

I am needing to get into port 80 most of the time... and also to get into my MySQL server... that is the main ones at the moment... but 23023 will soon be needed for my Seed Server. (or I think it was that one?)

---

### Post by darrenm on 2006-08-05
Still say openvpn is the best thing for you :)

---

### Post by blkish on 2006-08-05
From a quick evaluation of the situation i would agree. Look into openVPN.

blkish

---

### Post by schurtek on 2006-08-07
OpenVPN... Mmmm... Okay, I will give it a look... will it allow me to make Port 80 calls with a browser? from out side my network?

---

### Post by darrenm on 2006-08-07
You will need a cd-rom / pendrive with your openvpn config, win32/linux installer and keys. That will see you ok for any eventuality.

Once you connect with openvpn you are VPN'd into your network therefore can access any server as if you were on the LAN.

OpenVPN is awesome software, may seem a little confusing at first but read the howto's and you'll be up and running in no time

[www.openvpn.net](www.openvpn.net) for the main site and
[www.openvpn.se](www.openvpn.se) for the GUI Win32 client which is very nice.

Remember to add a config option for push dhcp option dns ;)

---

### Post by schurtek on 2006-08-08
Sounds awesome... but it restricts me in that some of my clients will need access to Port 80, and possibly even my internal MySQL database...

Okay... let's skip this part for now... will keep using No-IP.com for now... Some help on setting up DNS and Bind internally...?

---

### Post by darrenm on 2006-08-08
sudo apt-get install bind

about it ;)

get bind first, have a look at the dhcpd.conf file and then see what you need to know.

---

### Post by schurtek on 2006-08-09
okay... will give that a try... will be loading ubuntu server to replace windows 2000 server, then I will load it on my dev server... fiddle till I get it working, asking questions as I go... and when it works, I will build me a DNS server... ultimately I want one server for DNS/Bind and Squid. What spec you think I need, I have a network of about 6 computers... sometimes up to 24 connected (laptops).

---

### Post by mips on 2006-08-10
> **schurtek said:**
> ultimately I want one server for DNS/Bind and Squid. What spec you think I need, I have a network of about 6 computers... sometimes up to 24 connected (laptops).

You really don't need much in terms of horsepower for the above tasks.

---

