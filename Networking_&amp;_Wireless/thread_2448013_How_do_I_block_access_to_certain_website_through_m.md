---
title: "How do I block access to certain website through my  ubuntu server 18.04?"
date: 2020-07-30
forum: Networking &amp; Wireless
---

### Post by BlackGuyZA on 2020-07-30
I have setup an ubuntu server 18.04 as a network router at a high school through which internet is being accessed by everyone in the school community. I now want to block access to certain websites like facebook.com, youtube.com as well as all adult content websites for obvious reasons.

Thank you

---

### Post by TheFu on 2020-07-30
> **BlackGuyZA said:**
> I have setup an ubuntu server 18.04 as a network router at a high school through which internet is being accessed by everyone in the school community. I now want to block access to certain websites like facebook.com, youtube.com as well as all adult content websites for obvious reasons.

Thank you

There are ways around this unless you do some other network things to force all connections through the system.  While you can get all the subnets for facebook.com, youtube.com, and others around the world, then add them to a firewall ipset (you'll have thousands you need to block) soon, this is a whack-a-mole method.  You probably want to do some content filtering too.

The best case would be to get white lists of approved websites that are specifically allowed, then only allow those.  So you'd have a default rule that drops all outbound connection attempts except those needed for the specific, white-listed sites and the support includes those sites use.

You'll probably want a transparent proxy running - squid - and you'll need to prevent all default routes to the internet for all systems that are on the student subnet. If you allow DNS from the student subnet, they will use that to tunnel out passed your blocks - so you need to block all traffic trying to leave that isn't using the proxy.

For almost all blocking, you probably want to setup a pi-hole. This can use regex to block domains.  New domains spin up all the time, so this will be whack-a-mole, but other schools may have lists they block.

If you do anything less, computer smart students will find ways around what you are doing.

Let me try to summarize.[LIST]
[*]Block all traffic from student subnets to the outside. Nothing gets through.
[*]Setup a transparent proxy that gets DNS lookups from ... 
[*]Setup a pi-hole for use by proxy server which does aggressive blocking using regex
[*]All client machines would see the transparent proxy as the only way to the internet.  
[*]Only the proxy server should be allowed to hit the DNS server or the internet. Block any traffic of any sort IPv4, IPv6, ICMP, and all the other 16 types of the header "version" allows. People forget that part.
[/LIST]

It has been a long time since I setup a transparent proxy - at least 15 yrs. It was surprisingly simple. No client-side changes were needed.

If there is a plan to allow teachers more access or to run servers that need to allow inbound, that will make this complex.

Really, there are excellent router distros which handle most of this stuff in a fairly great way.  The key for those distros is that the configurations can be downloaded - the entire machine (or a new machine) reloaded - then the old config can be restored and in about 3 minutes, you have a all your settings running on the new system.  pfSense and OPNSense do this, these are BSD-based, not Linux.  openWRT does as well and there are commercial versions that will easily handle Gbps connections for not much money.  Then you can use that "server" for lots of more interesting things than just being a router/firewall.

IMHO, the WAN router needs to run on dedicated hardware. Not on a mixed use computer or inside a virtual machine.  Sure, people do run their WAN routers on VMs and you can find thousands of "how-tos" for doing that too, but it is a really bad idea.  One tiny mistake - a careless command - and the entire network is down. Someone will have an assignment due or paper research necessary and it will be 100% your fault.  People will come to depend on the connection working, unless you make a point about it being for learning and routinely take it down at random times for hours.

I've worked at a few companies where all our traffic had to go through a proxy - including all SSL traffic - which was opened, inspected, and passed/refused based on the content. I've also worked in places with large networks that were air-gapped from anything outside the building.  That was initially frustrating, but once the entire network became production, it was clearly the right choice for that control center.

Can't wait to read what others suggest. Perhaps someone has a great, easier, method?

Are you in South Africa?  I spoke to a Linux group in Cape Town years ago on optimizing virtualization settings.

---

### Post by BlackGuyZA on 2020-07-30
Thank you for the reply. I just want to confess though that my network administration skills are very limited. I am only a Science teacher. I was only able to setup two web based applications on the server, a router and samba file sharing. 

I am looking for a very simple and basic setup to block certain websites and adult based websites. I am aware that you can block websites on a Linux machine by editing /etc/hosts file and I am not sure if this will block those websites for all computers on the network if I do it on the server. 

My students are often under constant supervision while they are on the internet so I do not mind to manually block each domain as we discover it. 

Yes, I am from a small town in the Free State, South Africa.

---

### Post by TheFu on 2020-07-31
Thanks for showing Linux to your students!  I volunteer taught Linux at a local University here. They knew very little about Linux, but a few would eat it up.

> I am looking for a very simple and basic setup to block certain websites and adult based websites. I am aware that you can block websites on a Linux machine by editing /etc/hosts file and I am not sure if this will block those websites for all computers on the network if I do it on the server. 
Only if that server is also the mandated, required, transparent proxy.  Otherwise, nope.

If wifi connections are allowed, then you won't actually be supervising them.  They will step outside and use a phone or tablet to go anywhere they like on the internet. 

There's no way to prevent access to unallowed content if they learn how to override DNS settings on their devices, unless all DNS traffic is blocked EXCEPT by the proxy server.  With more and more websites going HTTPS, you won't be able to block by the content on the webpage, just by the URL.  

I run a few websites. All are HTTPS encrypted.  The connect from those servers to the client browser is fully encrypted, but the URL is not.  Squid, a proxy server can filter based on URL and for HTTP connections, content.

Blocking by running a filtered DNS and mandating that it be used by all devices on your network is the other key. A pi-hole setup does exactly that. Most of the time, a pi-hole is used to block advertising on the web. On my tiny network, over 50% of the DNS queries are for either advertising or tracking links. There have been just under 30,000 DNS queries.  over 15,000 of those were blocked, to give you an idea.

There are millions of sites you'll need to block. Millions.

Nothing you do will be perfect.  Few organizations, including middle-sized companies, have the skills and resources to block all offensive, adult, content. Risks definitely exist. OTOH, we have the "internet" which is full of all sorts of great information in little pockets that shouldn't be blocked.

[https://community.spiceworks.com/topic/2204939-school-web-blocker-free](https://community.spiceworks.com/topic/2204939-school-web-blocker-free) discussions about content blocking in schools.

[https://www.youtube.com/watch?v=mNXJ616Kl8Q](https://www.youtube.com/watch?v=mNXJ616Kl8Q) Pi-Hole setup on a r-pi (45min), but it is really easy in an LXD container on Ubuntu. That's how I run mine. Then just patch it weekly like any Ubuntu Server, run the pi-hole update at the same time ```

$ pihole -up
  [i] Checking for updates...
  [i] Pi-hole Core:     up to date
  [i] Web Interface:    up to date
  [i] FTL:              up to date

  [&#10003;] Everything is up to date!
```
There are curated, free, lists to block almost any sort of content you like. Once you select those lists, updating them every few weeks is useful.  Of course, you don't need to memorize these commands. There are webGUI ways to do this too, I just prefer scripting it, so I don't have to waste time watching.
```
$ pihole -g
```

---

### Post by BlackGuyZA on 2020-07-31
> **TheFu said:**
> Thanks for showing Linux to your students!  I volunteer taught Linux at a local University here. They knew very little about Linux, but a few would eat it up.


I do not introduce Linux to students but all our client PC's are windows based. It is only our main server that is Linux based. 


> **TheFu said:**
> 
[https://community.spiceworks.com/top...b-blocker-free]("https://community.spiceworks.com/topic/2204939-school-web-blocker-free") discussions about content blocking in schools.
 

If I use use this does it mean I can simply replace the Google public DNS servers 8.8.8.8 and 8.8.4.4  with FamilyShield DNS servers: 208.67.222.123 and 208.67.220.123 ?

---

### Post by TheFu on 2020-07-31
> **BlackGuyZA said:**
> I do not introduce Linux to students but all our client PC's are windows based. It is only our main server that is Linux based. 

Too bad. Opportunity lost. Perhaps a lab or computer club could use it? For a business, Unix/Linux knowledge is very important. Even just knowing that other OSes exist would be something.

> **BlackGuyZA said:**
> If I use use this does it mean I can simply replace the Google public DNS servers 8.8.8.8 and 8.8.4.4  with FamilyShield DNS servers: 208.67.222.123 and 208.67.220.123 ?

Just because we provide a DNS in the DHCP return values, that doesn't mean the clients have to use it. I don't know anything about "FamilyShield", but if any external DNS is used and the firewall isn't specifically setup to block all other DNS server queries anywhere else, I'd say no.

Additionally, you don't have control over what extra stuff needs to be blocked.  

There are multiple reasons I suggested using a pi-hole and proxy server. You can only do what you can do. Hopefully, it doesn't turn out badly like it would in my part of the world. If a school here didn't meet the legal requirements for content filtering, it would be bad.

---

### Post by BlackGuyZA on 2020-08-01
Thanks for the advice. I will try the pi-hole.

---

### Post by BlackGuyZA on 2020-08-02
> **TheFu said:**
> 

[https://www.youtube.com/watch?v=mNXJ616Kl8Q](https://www.youtube.com/watch?v=mNXJ616Kl8Q)  

I am currently watching this video. It's very helpful. Thanks a lot!

---

### Post by TheFu on 2020-08-02
> **BlackGuyZA said:**
> I am currently watching this video. It's very helpful. Thanks a lot!

No need to get a raspberry pi.

You can run the pi-hole software inside an LXD container with very little overhead to your server, while keeping the software segmented away from the router, which I think is mandatory.  I did this a few months ago and put links for how-tos in these forums.  

[https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337](https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337)
First, setup a bridge to be used by LXD containers and make that bridge (not NAT) the default for your lxd subsystem.  'lxc' is the LXD controller - and it has an unfortunate, confusing, name. There is a different project, lxc.  ;(
```
lxc launch ubuntu:18.04 pihole
lxc exec pihole -- /bin/bash
dpkg-reconfigure tzdata
```

[https://github.com/pi-hole/pi-hole/#one-step-automated-install](https://github.com/pi-hole/pi-hole/#one-step-automated-install)  Install the pi-hole software.
**# Notes:**
[LIST]
[*]*  pi-hole wasn't providing DNS on the LAN interface, had to manually enable that in the [http://pihole/admin](http://pihole/admin) webpage. 
[*]*  set a static ip for the container. Did that in the netplan file like any other server.
[*]* Spent a little time messing with the webapp, then modified the LAN DHCP servers to point all DHCP clients at the pi-hole for DNS.
[*]* Refresh all the block lists
[*]**  Restarted those wifi devices. Life was fine.
[*]* Added a few regex patterns to block - twitter, facebook,  google-tracking stuff.
[/LIST]

[https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533](https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533)
By this point, I didn't need many notes.  Just this 1 thing.  Each record in the forward DNS lookup table must have at least 3 entries.
```

# IP, localname, FQDN
172.22.22.1 rt1 rt1.thefu.lan
172.22.22.2 rt2 rt2.thefu.com
```
If you leave off any of these or get the order wrong, it isn't good.  Other host aliases can come at the end of each line, as you like.

I did it on a 16.04 server, so things will be similar, but the bridge network setup will definitely be different and will 95% likely require changes to your router unless you have a spare NIC port.

The hardest part was setting up LXD to use the bridge. Bridges are on the same subnet as the host machine. They are not NAT'd.  On 18.04 and 20.04, setting up a bridge is different than on 16.04 thanks to the change to netplan by those releases.  These links may be helpful.  I've not tested any, but each is supposed to create a bridge under netplan.  The last 2 are LXD specific.
[LIST]
[*][https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/)
[*][https://bayton.org/docs/linux/lxd/lxd-zfs-and-bridged-networking-on-ubuntu-16-04-lts](https://bayton.org/docs/linux/lxd/lxd-zfs-and-bridged-networking-on-ubuntu-16-04-lts) but updated for netplan (17.10+).
[*][https://lxadm.com/Bridge_with_a_static_IP_with_netplan](https://lxadm.com/Bridge_with_a_static_IP_with_netplan) another example.
[/LIST]
Good luck.

---

### Post by BlackGuyZA on 2020-08-08
I  did install pi-hole on the server using:

```
sudo curl -sSL https://install.pi-hole.net | bash
```

I then setup the static ip on one of the unused network interface with a new IP address 192.168.9.1/24 and my current server LAP IP address of 192.168.8.1. Everything seemed to work before I rebooted the server. I could open a web interface and I also changed my router DNS settings to 192.168.9.1. But after I rebooted the server I could not get DNS server running again. 

The following is what I got when trying to restart the DNS:

[[IMG]https://www.4shared.com/img/g1hlIzJ-ea/s25/173cf870458/restartdns[/IMG]](https://www.4shared.com/photo/g1hlIzJ-ea/restartdns.html)

I then tried this [https://discourse.pi-hole.net/t/dns-service-is-not-running-2019-02-10/17103](https://discourse.pi-hole.net/t/dns-service-is-not-running-2019-02-10/17103) but without success.

Why is pi-hole not starting after reboot?

---

### Post by TheFu on 2020-08-08
I didn't have the issue you've hit.  Is the pi-hole software installed into an LXD container or virtual machine?

---

### Post by BlackGuyZA on 2020-08-09
> **TheFu said:**
> I didn't have the issue you've hit.  Is the pi-hole software installed into an LXD container or virtual machine?

I installed it on ubuntu server 18.04 physical machine. I don't have LXD container installed.

Maybe I should remove the installation and follow the LXD container process.

---

### Post by TheFu on 2020-08-09
As stated above:
> IMHO, the WAN router needs to run on dedicated hardware. Not on a mixed use computer or inside a virtual machine. Sure, people do run their WAN routers on VMs and you can find thousands of "how-tos" for doing that too, but it is a really bad idea. One tiny mistake - a careless command - and the entire network is down.

There are reasons for writing everything above, but we all go our own way sometimes. Perhaps you can make it work, but my 25+ yrs doing admin work has taught me to keep things separate. It is easier now than ever.  But I don't know how you'll get the bridge working on the same system where the router runs. Perhaps you are better at networking than me.

---

### Post by BlackGuyZA on 2020-08-09
> **TheFu said:**
> As stated above:


There are reasons for writing everything above, but we all go our own way sometimes. Perhaps you can make it work, but my 25+ yrs doing admin work has taught me to keep things separate. It is easier now than ever.  But I don't know how you'll get the bridge working on the same system where the router runs. Perhaps you are better at networking than me.

Do you suggest then that I install pi-hole on a separate machine from the main server? To tell you the truth I don't know nothing about network or ubuntu. I am novice. Most of the terms I heard  for the first time here.

---

### Post by TheFu on 2020-08-09
> **BlackGuyZA said:**
> Do you suggest then that I install pi-hole on a separate machine from the main server?

I'd rather you used a real router, perhaps from Ubiquiti or Mikrotik (not some consumer brand) and used this Linux server as a VM/LXD host for other services like pi-hole, squid, file storage, and with an extra HDD, backups. Each of those things would run in separate VMs or LXD containers.

Both Ubiquiti and Mikrotik have good histories providing patches.  The video about the pi-hole - that guy did a series about using a Mikrotik router in the last few months.

I've not used either Mikrotik or Ubiquiti routers, but I have deployed Ubiquiti WAPs for clients. They make the best, cheapest, enterprise stuff.  When I do this sort of work (routers), I deploy specialized router HW and load pfSense or OPNSense. For a small environment where home routers are completely inadequate, those really are the only choices. All the others are too expensive or don't provide solid security. 

A little ER-X router is much better than anything from cisco/linksys, tp-link, d-link, netgear, asus, for about $60. Ubiquiti's software is based off a different sort of software, so the learning curve will be higher. 
Same for the Mikrotik hEX RB750Gr3 - great value for the price.  All RB models use the same software, so the lowest end version scales up to their $450+ stuff. Nothing new to learn.

If you plan to add wifi, keep that separate from the router.  Get a Ubiquiti WAP or 2 or 10 or 20, if that's what you need. The Ubiquiti WAPs all have a web interface or you can run a central controller via free software (use a VM) to control them all together. This is how large hotels manage their wifi grid stuff.

I've got to do some hardware changes here for the next few hours. Won't be available.  Swapping disk controllers and RAID HDDs in 2 different systems. Not my idea of fun, but I've put it off as long as I can. ;( Good luck.

---

### Post by BlackGuyZA on 2020-08-09
> **TheFu said:**
> I'd rather you used a real router, perhaps from Ubiquiti or Mikrotik (not some consumer brand) and used this Linux server as a VM/LXD host for other services like pi-hole, squid, file storage, and with an extra HDD, backups. Each of those things would run in separate VMs or LXD containers.

Both Ubiquiti and Mikrotik have good histories providing patches.  The video about the pi-hole - that guy did a series about using a Mikrotik router in the last few months.

I've not used either Mikrotik or Ubiquiti routers, but I have deployed Ubiquiti WAPs for clients. They make the best, cheapest, enterprise stuff.  When I do this sort of work (routers), I deploy specialized router HW and load pfSense or OPNSense. For a small environment where home routers are completely inadequate, those really are the only choices. All the others are too expensive or don't provide solid security. 

A little ER-X router is much better than anything from cisco/linksys, tp-link, d-link, netgear, asus, for about $60. Ubiquiti's software is based off a different sort of software, so the learning curve will be higher. 
Same for the Mikrotik hEX RB750Gr3 - great value for the price.  All RB models use the same software, so the lowest end version scales up to their $450+ stuff. Nothing new to learn.

If you plan to add wifi, keep that separate from the router.  Get a Ubiquiti WAP or 2 or 10 or 20, if that's what you need. The Ubiquiti WAPs all have a web interface or you can run a central controller via free software (use a VM) to control them all together. This is how large hotels manage their wifi grid stuff.

I've got to do some hardware changes here for the next few hours. Won't be available.  Swapping disk controllers and RAID HDDs in 2 different systems. Not my idea of fun, but I've put it off as long as I can. ;( Good luck.

I run my home network through Ubiquiti router because that is the device I get my internet and I found it easier to work with than Mikrotik which one of my friends uses at his house.

---

