---
title: "OpenDNS problems"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by teumima on 2006-11-14
Hi 

I entered into my /etc/resolv.conf the DNS nameservers of [www.opendns.com](www.opendns.com).

It worked great.

Then I decided to do a fresh install of edgy. So I erased the whole HD.

Now no matter what I do, I can't get it to work.

my /etc/resolv.conf looks like this:

nameserver 208.67.222.222
nameserver 208.67.220.220

That's right.

Then when I go through Gnome to Networks: 

I see:

208.67.222.222
208.67.220.220

But when I go to the OpenDns test site:

[http://welcome.opendns.com/](http://welcome.opendns.com/)

I get Oops you're not using OpenDNS.

Now I'm behind a router. However, I have a Mac OS X also and no problems with OpenDNS, no oops page.

I contacted OpenDNS and they were fast to help, but I think they're kind of stuck too, as they're not replying much anymore. 

Any ideas, would be greatly appreciated.

a.t.

---

### Post by kerry_s on 2006-11-14
Have you tried doing it manually?

sudo gedit /etc/dhcp3/dhclient.conf

change this->
#prepend domain-name-servers 127.0.0.1;
To this->
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

Then restart the network->
sudo /etc/init.d/networking restart

---

### Post by teumima on 2006-11-14
yes man i did that too.

However, I changed it back, as I have a static IP, so my resolv.conf isn't updated automatically.

Unless you think it needs to be that way regardless?

---

### Post by teumima on 2006-11-14
ok issue is solved.

I entered the DNS in my router as well. 
So in resolv.conf and in my router.

All works great!

---

### Post by teumima on 2006-11-15
Ok this is pathetic. Issue not solved. And OpenDNS not helping me troubleshoot.

I have screenshots if anyone is interested.

I'm using OpenDNS accordin to dig, but not according to that stupid welcome.opendns.com page.

It won't block phising sites or complete misspelled .cm and it's slow as a dying turtle.

Any ideas?

I got it working, then all of a suddent it stopped.

My /etc/resolv.conf still has:

nameserver 208.67.222.222
nameserver 208.67.220.220

Which is right. Damn it.

Any ideas appreciated.

---

### Post by jhaykage on 2007-12-18
> **kerry_s said:**
> Have you tried doing it manually?

sudo gedit /etc/dhcp3/dhclient.conf

change this->
#prepend domain-name-servers 127.0.0.1;
To this->
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

Then restart the network->
sudo /etc/init.d/networking restart

I've been trying to use OpenDNS with Gutsy, when I edit the dhclient.conf file,

do I really have to remove the "#" before the "prepend domain-name-servers 208.67.222.222, 208.67.220.220" ?

Please help

---

