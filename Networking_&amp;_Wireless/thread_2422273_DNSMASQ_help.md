---
title: "DNSMASQ help"
date: 2019-07-04
forum: Networking &amp; Wireless
---

### Post by thomas-soum on 2019-07-04
Hello, and sorry if my writing is bad. I would like someone to guide me on how to set correctly dnsmasq in order to achieve one thing. I have a raspberry pi model 3B+ running a few websites and I have installed on it dnsmasq. I also have one pc running proxmox for virtualization. In order to connect to the proxmox web guide you need to type the ip of the machine followed by the port number 8006. The thing that I am trying to achieve is(not sure if I am gonna say it correctly) to be able to give the proxmox a domain name so when I have another PC or Phone and have as a DNS server the raspberry and search on google for a specific domain let's say proxmox.home.net to be redirect to my proxmox machine.

Thanks in advance

---

### Post by houstonbofh on 2019-07-04
This is usually handled in your router or Internet gateway device.  It needs to be set on a place when you can actually create DNS entries, not just proxy them.

---

### Post by lensman3 on 2019-07-06
I think you want a setup like "PI-hole", the DNS server that strips out advertisements to browsers.  Pi-hole uses dnsmask to identify the advertisement servers and insert a 127.0.0.1, one pixel wide advertisement.  

I also think you will have to rent an static IP address from a company like "DynDNS" so that a random assigned IP address from your gets assigned to a top level DNS server. There is NO way for you to advertise your  IP number to Google and search for it.  DynDNS has a script that runs when a session is started on your IP that adds the number into DynDNS dns database.

Your setup would be easier if you setup your own firewall and put dnsmask on the firewall.  Set your existing modem and existing firewall to pass through mode. Dnsmask can be setup to supply local DNS IP and IPv6 numbers for your small network.

Hope this gives you a place to start.   (A Raspberry PI will work nicely as a firewall if you buy a USB Ethernet dongle for the second Ethernet port).

---

### Post by TheFu on 2019-07-06
You need 3 things for a website to work on the internet for others to use.
[LIST=1]
[*]Bought domain-name from a "registrar"
[*]Authoritative DNS for the domain, tied to the registrar record
[*]web server or web host
[/LIST]

I keep these 3 things with separate companies. You can get them all from 1, but then you end up trapped with that single company constantly trying to up-sell you.

You cannot just make up a domain name and expect google to find it.  It must be purchased from an approved domainname vendor. They run from $1.95/yr to $200/yr.  Most are about $10/yr.

Then you'll need a public DNS service. It is best for non-professionals NOT to try running a public DNS. DNS is often hacked. I pay $20/yr for a reputable DNS provider. I was hacked when running my own DNS about 20 yrs ago. You can use no-ip or dyndns or almost any hosting provider will give you DNS if you host there.  If your home IP is in a dhcp range from the ISP, then you'll want to either have your WAN router manage updates or use something like ddclient to do that.

The DNS points the domain and subdomains to the different IPs you have. It can be static or dynamic, but static works best for many reasons.  Static IPs are required for smtp services. For web servers, it isn't that important, provided the DNS records are probably updated after every IP address change.  There are automatic tools for that.

If you drop the google requirement, then you can just run the website using your public IP and put that IP-to-name mapping in the /etc/hosts on all the machines involved.  If you have 5 or fewer machines, that is usually much easier than all the DNS and registrar stuff.

---

