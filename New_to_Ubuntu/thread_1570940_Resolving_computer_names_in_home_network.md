---
title: "Resolving computer names in home network"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by gldearman on 2010-09-08
Hi, everyone,

I'm trying to set up my home network so that my computers can share files and printers.  Since, in addition to my Ubuntu computers, I have some that run on Windows 7, I need to use Samba to do this.  I am very inexperienced at networking, and need some very basic help with some elementary stuff to get started.

I found a Samba tutorial, and got as far as Step 1 before I encountered a problem:

[INDENT]*... it is assumed that you have a working TCP/IP network. This meaning that all pc's are on the same subnet, IP range, and that you are able to ping all your pc's by name and IP. If your network does not meet these conditions, there is no sense in proceeding further as Samba requires a properly configured TCP/IP network in order to function properly. *[/INDENT]

OK, I'm pretty sure all the computers are on the same subnet; I got the IP address and subnet mask of each, used an online subnet calculator, and got the same subnet ID for each.

All the computers are in the same IP range.

Every computer can ping every other computer on the network by IP address (once firewalls are disabled).

But ... most of my computers cannot ping any other computer by hostname.  Neither Ubuntu computer could do this at all.  The Win7 computers could ping each other by name, but could only sometimes ping the Ubuntu computers by name.

How do I get this resolved, so that the computers on my network recognize each other's names?

Some of the computers are netbooks, and are frequently connected to public networks as well.

Thanks!

---

### Post by jtarin on 2010-09-08
Just edit /etc/hosts and insert the ip and hostname

here is my /etc/hosts file

```
127.0.0.1	localhost
127.0.1.1	godzilla.net
```
This is good for static IP's

Or you can try with Samba...first make sure the samba client is installed and then try: 

```
smbclient -L a.b.c.d
```

I don't use Samba so the last command your on your own.:p

---

### Post by gldearman on 2010-09-08
I thought about /etc/hosts.  But wouldn't that mean that my computer would *always* resolve the IP address to that particular host? No matter what network I was on?

That wouldn't be so bad for my desktop.  But my netbooks get connected to public networks all the time.  If I put 192.168.1.2 in my netbook's hosts file with the hostname of my desktop, what happens when I log in at a coffee shop and it identifies someone else's laptop as my desktop?

Thanks!

---

### Post by sandyd on 2010-09-08
> **gldearman said:**
> I thought about /etc/hosts.  But wouldn't that mean that my computer would *always* resolve the IP address to that particular host? No matter what network I was on?

That wouldn't be so bad for my desktop.  But my netbooks get connected to public networks all the time.  If I put 192.168.1.2 in my netbook's hosts file with the hostname of my desktop, what happens when I log in at a coffee shop and it identifies someone else's laptop as my desktop?

Thanks!
this is currently an ongoing discussion, it seems that something changed in lucid.
just install the "winbind" package for a quick and dirty fix.

---

### Post by gldearman on 2010-09-08
What does winbind do and how do you use it?  I found that advice when I was searching the forum for answers.  So, I installed the package.  It seemed to make things worse &#8212; I couldn't even connect to my NAS via smbclient with winbind installed, and I didn't see any performance problems solved.  So, I uninstalled it again.  Maybe I had it configured wrong?

---

### Post by CharlesA on 2010-09-08
You'd need a DNS server on the network to resolve names to ip addresses between windows and linux.

Windows to windows just use broadcasting/NetBIOS.

It's either that or edit the hosts file on each machine.. which only works if all machines have static addresses.

---

### Post by bobstro on 2010-09-08
From your description, I am understanding that you are NOT issuing addresses to your PCs via DHCP. Is that correct?

I had this same problem, and found that dnsmasq is a simple solution. dnsmasq is described as "a small caching DNS proxy and DHCP/TFTP server". You don't have to use the DHCP functions, though I use it, even for machines with fixed addresses, simply to speed up rebuilding a machine.

For every internal machine, create an address entry in the dnsmasq.conf file (e.g. address=/pc1.mydomain.com/172.16.16.1). Then configure each machine to point to the machine running dnsmasq as the first DNS server. dnsmasq will resolve any addresses it has, whether fixed address entries as above, or that it issued via DHCP, and pass others on to upstream DNS servers.

Be sure to enter the search DNS parameter set to yourdomain so you don't have to type the fully-qualified domain name each time (e.g. pc1 instead of pc1.mydomain.com).

- Bob

---

### Post by bodhi.zazen on 2010-09-08
You can either use your router (depending on your router of course) or on a small LAN I use dnsmasq

[http://www.enterprisenetworkingplanet.com/nethub/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm](http://www.enterprisenetworkingplanet.com/nethub/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm)

---

### Post by gldearman on 2010-09-09
> **bobstro said:**
> From your description, I am understanding that you are NOT issuing addresses to your PCs via DHCP. Is that correct?

No, I am using the router's DHCP functions to assign fixed IP addresses.

> **bobstro said:**
> 
I had this same problem, and found that dnsmasq is a simple solution. dnsmasq is described as "a small caching DNS proxy and DHCP/TFTP server". You don't have to use the DHCP functions, though I use it, even for machines with fixed addresses, simply to speed up rebuilding a machine.

For every internal machine, create an address entry in the dnsmasq.conf file (e.g. address=/pc1.mydomain.com/172.16.16.1). Then configure each machine to point to the machine running dnsmasq as the first DNS server. dnsmasq will resolve any addresses it has, whether fixed address entries as above, or that it issued via DHCP, and pass others on to upstream DNS servers.

Be sure to enter the search DNS parameter set to yourdomain so you don't have to type the fully-qualified domain name each time (e.g. pc1 instead of pc1.mydomain.com).
- Bob

> **bodhi.zazen said:**
> You can either use your router (depending on your router of course) or on a small LAN I use dnsmasq

[http://www.enterprisenetworkingplanet.com/nethub/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm](http://www.enterprisenetworkingplanet.com/nethub/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm)

After doing a little investigating, dnsmasq looks like the perfect solution for me.  I've got an extra box that I've been meaning to set up and play around with as a file server, and this would be a great use for it.

And, though my router does not support any DNS server functions now, a little googling of "dnsmasq" has revealed that, if I flash it to DD-WRT, I can run dnsmasq directly on the router.

Thanks!

---

### Post by bobstro on 2010-09-09
Finding the documentation for configuring dnsmasq in DD-WRT can take a little work, but yes, it does support all of the options. I originally started with DD-WRT on my Linksys router and was very pleased with it. It certainly takes less power than a full computer!

- Bob

---

