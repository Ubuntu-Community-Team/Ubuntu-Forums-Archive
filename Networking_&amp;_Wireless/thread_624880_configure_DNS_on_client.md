---
title: "configure DNS on client"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by Kasparov on 2007-11-27
Hi everyone

I have a LAN with 1 router and 4 computers, each one gets an IP-address by DHCP. From the computer I'm working on (Ubuntu OS), I can ping to everyone else by ip-address but not by hostname. What do have to do? The resolv.conf file says:

```

nameserver <ip router>

```

It feels like a very simple task, but I've been searching the net for over 3 hours, and I can't find anything useful.

Regards,
Tim

---

### Post by sshahir on 2007-11-27
check [ [COLOR="Blue"]DNS How To[/COLOR]]("http://www.tldp.org/HOWTO/DNS-HOWTO.html") if you have already installed the [[COLOR="Blue"]BIND server[/COLOR]]("https://help.ubuntu.com/7.04/server/C/dns.html").

---

### Post by Kasparov on 2007-11-27
No I don't need that. 
I don't need to configure a DNS server.

I just want to do:
```

ping <hostname>

```  (result: host unknown)

instead of
```

ping <ip-address>

```   (this works)

On all the other systems in my domain (which are running Windows) I can do both. It took me 0 seconds to configure it on Windows as it went automatically.

---

### Post by moyazes on 2007-11-27
You can also add entires to match IP addresses to hostnames in

/etc/hosts

$/etc$ cat hosts
127.0.0.1 localhost

192.168.1.38 blake 
192.168.1.45 drake

Hope this helps

moyazes

---

### Post by Kasparov on 2007-11-27
Yes I know, this is only useful though when using static routing. I'm using DHCP, so ip-addresses might change when the lease time is over. 

It's just localhost in my /etc/hosts file.

---

### Post by moyazes on 2007-11-27
Then I suggest you run a DNS server locally using BIND and and have a hostname mapped to all IP addresses in your DHCP pool. 

moyazes

---

### Post by Jimmy_r on 2007-12-12
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=88206&highlight=hostname+ping](http://ubuntuforums.org/showthread.php?t=88206&highlight=hostname+ping)

---

### Post by Sagadon on 2007-12-12
Someone recently told me about a dynamic dns service:

[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

You can set it up to be jimmyr.dyndns.com or something like that, and you run a program on your local machine that tells dyndns.com every time your IP Address changes.  Handy for having a static dns entry into a dynimically assigned IPAddress machine.

You say you don't want to configure dns, but basically referring to an ip by a name involves a dns lookup (or the hosts file).

---

### Post by mrhinman on 2007-12-12
Plus, most routers can be configured for DynDNS without having to use their update software.  Works well with my Linksys router and a dynamic IP.

---

### Post by FishFilet on 2007-12-12
He does not need to set up a dns server because he already has one. obviously if his windows pc can resolve hostnames he either has a dns server running on a pc or mostlikely his cable or dsl modem or router such as linksys or dlink is running one. Most of these units have this function and it is enabled by default.

so I believe what Kasparov is asking is why cant he ping by hostname with Ubuntu. When he can with windows. and more importantly what can he do to enable this feature in Ubuntu.

He does not need a dynamic dns service like No-IP.com and the like. He is trying to resolve names on the local network. These services allow you to have a host name such as roaminghost.no-ip.com which will be updated by software you load on your pc at regular intervals. This can be handy when your isp gives you a dynamic ip address instead of a static address. This is not what he is talking about.

I have the same problem and I also have a dns server already running on my lan. My windows pc's can resolve hostnames but not my Ubuntu laptop.

does anyone know how this can be fixed?

I frequently use remote desktop to connect to servers and would like to connect by hostname instead of 20 or so ip addresses.

---

### Post by FishFilet on 2007-12-12
Try this thread it fixed it for me!

[http://ubuntuforums.org/showthread.php?t=88206&highlight=resolve+hostnames](http://ubuntuforums.org/showthread.php?t=88206&highlight=resolve+hostnames)

---

### Post by Jimmy_r on 2007-12-13
> **FishFilet said:**
> Try this thread it fixed it for me!

[http://ubuntuforums.org/showthread.php?t=88206&highlight=resolve+hostnames](http://ubuntuforums.org/showthread.php?t=88206&highlight=resolve+hostnames)

Guess I am invisible. Oh well... :p

Anyway, I discovered that, at least on a network with only ubuntu, I did not need to do the nsswitch fix.

I did a traceroute(system -> administration -> network tools) on the ip of the other computer on the network, and discovered I needed to put a .local after the hostname when I ping it.

for example 'ping jimmy-desktop.local' works fine from the laptop and vice versa.

---

### Post by FishFilet on 2007-12-13
> **Jimmy_r said:**
> Guess I am invisible. Oh well... :p

Anyway, I discovered that, at least on a network with only ubuntu, I did not need to do the nsswitch fix.

I did a traceroute(system -> administration -> network tools) on the ip of the other computer on the network, and discovered I needed to put a .local after the hostname when I ping it.

for example 'ping jimmy-desktop.local' works fine from the laptop and vice versa.

LOL, sorry i am not sure how i missed that if only i hadn't i could have saved about an hour of forum searching:)

One thing to mention is that i did try pinging my network in this fashion computer.domain.local and it did not help although I had not yet installed winbind.

Thanks.

---

### Post by jonallport on 2007-12-14
My 2 pence/2 cents/2 euro-cents worth:

Can I assume that in the resolv.conf example above <ip-router> is n actual IP address, not a bit of text?

If so this looks like a DHCP mis-config.  Your DHCP server (router?) is issuing option 5 (name server) but not option 6 (domain name).  Your windows clients will be able to get around this because by default they will use the workgroup name as the DNS suffix, but there will be no option 6 entry for dhcpcd to put into resolv.conf.  Two ways to fix/workaround:

1) Sort the DHCP server out: make sure the domain name field is populated.
2) add 'echo domain {local.domain.suffix} >> /etc/resolv.conf' to /etc/rc.local to manually put then domain suffix in at startup

---

