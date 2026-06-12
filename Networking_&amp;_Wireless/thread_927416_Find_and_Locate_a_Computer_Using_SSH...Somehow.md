---
title: "Find and Locate a Computer Using SSH...Somehow"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by mlissner on 2008-09-22
This seems possible, but I lack the vocabulary to find what I'm looking for. I'd like to be able to SSH into my laptop from my server without having to set a static IP on my laptop, or having to guess at what the DHCP IP might be of my laptop.

So, for example, I'd like to come home, and allow wireless on my laptop to hook itself up via DHCP to the network. At this point, I'd like to go to my server, and somehow find my laptop without leaving the internal network (that they are both on), or having to guess at IP addresses...such as 192.168.1.1....192.168.1.2.....192.168.1.3, etc.

I'm guessing there is a way to do this, but I don't know what it's called. Any help?

---

### Post by AndrewTheArt on 2008-09-23
I guess the terminology for this is "update client" - but normally update clients are used for updating a service like DynDNS when your *public* IP changes. It also works for internal IP addresses though - I just tested it (it's sort of cool!)

One of the most popular update clients is **ddclient**, should be in the repos.

The workflow would be - 

(1) Make an account on DynDNS.com, and get a domain there. After signing up, find the "My Account" button, then click "Add Host Services". Make a hostname (whatever you want), but write it down. When it asks for an "IP Address" to hook to the domain, just use the auto detected one it offers (at least for the time being)
(2) sudo apt-get install ddclient
(3) Answer all the config questions for ddclient. Remember to use the domain name you just set up when asked. When it asks for an "interface", you are going to want to type either eth0 or wlan0 (depending on what interface you're using on your laptop, probably wlan0 for wireless. If you're not sure just run ifconfig).
(4) Set the update interval to whatever you want, mine is like 2 days.
(5) If all goes well, your DynDNS domain will be hooked up to the laptop's local ip (192.168.1.whatever), and you should be able to use the domain your registered to redirect to your laptop.

---

### Post by Aearenda on 2008-09-23
I use dnsmasq on my local server for this (the server is multipurpose and runs Ubuntu). Dnsmasq is a simple DNS and DHCP server. It manages the DHCP service on my local network instead of BIND (or the router), and any client which advises its name is dynamically linked into the local DNS domain when DHCP grants an address. Windows clients send their names, and so do Ubuntu clients so long as /etc/dhcp3/dhclient.conf tells it to using the 'send host-name' entry. For the record, this is what my dhclient.conf contains: ```
send host-name "tc1100";
request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;

```

Then I can pick up the machine by name anywhere on my local network, for SSH or other uses.

I also use DynDNS for finding my network over the internet, but that's another story.

---

### Post by mlissner on 2008-09-23
@AndrewTheArt: I've set up ddclient before with DynDNS. I'm confused why this would work. Why would this update dyndns with my internal IP rather than my external one as it usually does? Did I not see a relevant config change you suggested above that would make that change? 

The other thing is, I'd like for this to work without need for the Internet to be up. Though I suppose if a DNS lookup is completed prior to SSH working only internally, that's not the end of the world. I'm using this in a backup script though, so if the backup happens over the Internet rather than the Intranet, that would be too slow.

I would have expeted my laptop to be able to broadcast itself to the network somehow, but this is an interesting thought as well.

@Aerenda: that seems quite effective, but I'm not sure I'm ready for that kind of maintenance overhead. I don't know enough about setting up DNS to feel confident with that...

Surely there is an easier way, right?

---

### Post by AndrewTheArt on 2008-09-23
> @AndrewTheArt: I've set up ddclient before with DynDNS. I'm confused why this would work. Why would this update dyndns with my internal IP rather than my external one as it usually does? Did I not see a relevant config change you suggested above that would make that change?The interface you specify makes the difference. You can choose to look up your external IP on a website or using a script, or you can use the laptop's hardware interface to get the IP. The hardware interface contains your local IP. Run ifconfig and looks for the interface you want the IP of. You can feed ddclient the name of the interface in the config file and it knows how to parse the IP out of that.

You can either edit the config files for ddclient manually or do a sudo dpkg-reconfigure ddclient. 

[https://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](https://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html)

This setup is not necessarily common but it's perfectly valid and is a built in feature of ddclient.

---

### Post by mlissner on 2008-09-23
Hmmmm...I reinstalled ddclient, and set up the config file as below. It doesn't seem to be working. I found a forum entry that seems to indicate that I have things set up correctly, so I don't really know why it's not working.  It's neither updating my IP to be my internal one, nor is it updating to indicate my external one.

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

daemon=150
syslog=yes
mail-failure=xxxxxx@xxxx.com

pid=/var/run/ddclient.pid
protocol=dyndns2
use=if, if=eth1
server=members.dyndns.org
login=xxxxxxxx
password=xxxxxxx
xxxx.boldlygoingnowhere.org

```

---

### Post by AndrewTheArt on 2008-09-23
> **mlissner said:**
> Hmmmm...I reinstalled ddclient, and set up the config file as below. It doesn't seem to be working. I found a forum entry that seems to indicate that I have things set up correctly, so I don't really know why it's not working.  It's neither updating my IP to be my internal one, nor is it updating to indicate my external one.

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

daemon=150
syslog=yes
mail-failure=xxxxxx@xxxx.com

pid=/var/run/ddclient.pid
protocol=dyndns2
use=if, if=eth1
server=members.dyndns.org
login=xxxxxxxx
password=xxxxxxx
xxxx.boldlygoingnowhere.org

```

Mine looks similar, and it's working - 

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

pid=/var/run/ddclient.pid
protocol=dyndns2
use=if, if=wlan0
server=members.dyndns.org
login=andrewtheart
password='*****'
*****.is-a-geek.com
```Did you try a dpkg-reconfigure? You might also want to restart the ddclient daemon(?)

---

