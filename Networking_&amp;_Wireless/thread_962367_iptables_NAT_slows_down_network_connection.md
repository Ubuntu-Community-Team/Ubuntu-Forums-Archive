---
title: "iptables NAT slows down network connection"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by Ingmar on 2008-10-29
Hello,

I've set up a Ubuntu Xen Server with some DomUs. The DomUs are building a DMZ with some server services in an own Virtual Network. Two of the DomUs are Routers for Internet and the DMZ. The following schema shows the setup:
```
Intranet <-> Router 1 <-> DMZ <-> Router 2 <-> Internet
```
**Router 1:** eth0 is connected to the Intranet-Bridge, eth1 to the DMZ-Bridge
**Router 2:** eth0 is connected to the DMZ-Bridge, ppp0 to the Internet
And both networks, the Intranet and the DMZ have a different IP-Net in form of 192.168.XYZ/24

I used the iptables-Script-Generator from [http://www.harry.homelinux.org/modules.php?name=iptables_Generator](http://www.harry.homelinux.org/modules.php?name=iptables_Generator) and go the following Skript: [http://pastebin.com/f45af782b](http://pastebin.com/f45af782b)

I use this script on both Routers but on Router 1 I commented out the following things:
[LIST]
[*]iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to- pmtu
[*]The Port Forwarding
[/LIST]

All connections seem to work and Internet is 15 Mbit/s what is ok for my Internet connection. With my old router I had about one Mbit more but it's ok. Upload also works fine. A DSL-Speedtest showed my that 1 MBit/s were uploaded.

**My main Problem is this: Transfers between a Intranet-Client and the Webserver in the DMZ are very slow.** Connecting is no Problem so only the connection speed is making me very unhappy.

For example my Webserver. I have a 200MB file on the Webserver. Wget from another host in the DMZ over the Xen Network bridge is very fast. After one time loading the file seems to be cached and I have download rates about 180 to 200 MByte/s.
When I use wget on an intranet host I get only about 15KByte/s. The same when I access the webserver from the Internet. Only about 15KByte/s. My Upload is 1MByte/s so 120KByte/s should work. Over my old router 120KByte/s up wasn't a problem.

Where could be the problem that's slowing down my Routing to the DMZ?


P.S. A little question at the iptables-Experts: What additional iptables-policy is needed that my router forwards requests to his own address (on the ppp0-Interface) from the Internal network to the DMZ-Servers like requests from the internet?

---

### Post by SpaceTeddy on 2008-10-29
mhm - the script looks fine... although pretty unreadable for me. Can you please load the thing up and then do a

```
sudo iptables -L -vnx
sudo iptables -L --table nat -vnx
```

i am way better at read that output :) Besides that, could you also try what happens if you do not load the iptables and see if the transfer is still slow ? 
The reason i am asking this that i think you are redirecting some traffic somewhere over your external interface (ppp0 ???) which is capped in one way at the speed you are getting - thus limiting your network bandwidth.

But then, i am only guessing at the moment... 

PS: echo 1 > /proc/sys/net/ipv4/ip_forward or (i think) any direct writing wo the /proc tree should be avoided. use sysctl instead...

---

### Post by Ingmar on 2008-10-29
> **SpaceTeddy said:**
> mhm - the script looks fine... although pretty unreadable for me. Can you please load the thing up and then do a

```
sudo iptables -L -vnx
sudo iptables -L --table nat -vnx
```

Heres your output. I pastebined it, because the first is very long:
*sudo iptables -L -vnx:* [http://pastebin.com/m659376d6](http://pastebin.com/m659376d6)
*sudo iptables -L --table nat -vnx:* [http://pastebin.com/m61fce5fe](http://pastebin.com/m61fce5fe)

> **SpaceTeddy said:**
> i am way better at read that output :) Besides that, could you also try what happens if you do not load the iptables and see if the transfer is still slow ? 
The reason i am asking this that i think you are redirecting some traffic somewhere over your external interface (ppp0 ???) which is capped in one way at the speed you are getting - thus limiting your network bandwidth.
If I stop the firewall my Traffic isn't routed in the DMZ so how could I test this?


> **SpaceTeddy said:**
> PS: echo 1 > /proc/sys/net/ipv4/ip_forward or (i think) any direct writing wo the /proc tree should be avoided. use sysctl instead...
OK, I'll change this the next days, but I don't think this is responsible for my problem.

---

### Post by SpaceTeddy on 2008-10-29
> **Ingmar said:**
> If I stop the firewall my Traffic isn't routed in the DMZ so how could I test this?

This is very interesting. Since your prerouting rules only apply to the ppp0 device, I'd like to know what kind of connection ppp0 is. Usually that is associated with a DSL dial-up. How fast is your internet line (up and down) - also. you can test it without the firewall if you modify the script and only leave the essential parts in. Here is the boil down that should work as a minimal setup (you need to change the forwarding IP as i do not know them)

> 
sudo su
sysctl -w net.ipv4.ip_forward=1
iptables -F
iptables -X
iptables -F --table at

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

iptables -A POSTROUTING --table nat -i ppp0 -p tcp --dport 80 --to-destination 192.168.XXX.YYY
iptables -A POSTROUTING --table nat -i ppp0 -p tcp --dport 443 --to-destination 192.168.XXX.YYY
iptables -A POSTROUTING --table nat -i ppp0 -p udp --dport 1194 --to-destination 192.168.XXX.YYY


Hopefully i got the POSTROUTING ones right - but running these commands should give you a minimal forwarding with no firewalling - i.e. - there is no matching anywhere.

Hope it helps :)

PS: the sudo su makes you root. If you do not want that, leave it out and put a sudo in front of all other commands.

---

### Post by Ingmar on 2008-10-30
> **SpaceTeddy said:**
> This is very interesting. Since your prerouting rules only apply to the ppp0 device, I'd like to know what kind of connection ppp0 is. Usually that is associated with a DSL dial-up. How fast is your internet line (up and down) - also. you can test it without the firewall if you modify the script and only leave the essential parts in. Here is the boil down that should work as a minimal setup (you need to change the forwarding IP as i do not know them)
The connection is a DSL-Line with about 15-16MBit down and 1MBit up. So 10 KByte are very slow and upload to the Internet is about 130KBytes with some speedtests.

> **SpaceTeddy said:**
> Hopefully i got the POSTROUTING ones right - but running these commands should give you a minimal forwarding with no firewalling - i.e. - there is no matching anywhere.
After executing this commands theres no traffic to the internet. I don't get any response from out of my internal network.

I just testet another thing. I added a port forwarding rule to the Intranet-Gateways firewallscript to get it routing webtraffic to my notebooks HTTP-Server. In this direction I got 11MByte/s which is limited by my 100Mbit-network.

So when it works in this direction, why doesn't it work in the other? And why has the internet traffic the speed my line is having although it's crossing the same firewall routes.

P.S. 1: At first I had a self written small script, which hasn't had this Attack protections and all this but it had the same speed problem.


P.S. 2: With this I think I can't seed ubuntu over BitTorrent today :-(

---

### Post by SpaceTeddy on 2008-10-30
yep, it doesn't work - silly me. Forgot the masquerading on the ppp0 device (only took care of the port forwarding...).

> sudo su
sysctl -w net.ipv4.ip_forward=1
iptables -F
iptables -X
iptables -F --table at

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

iptables -A POSTROUTING --table nat -i ppp0 -p tcp --dport 80 --to-destination 192.168.XXX.YYY
iptables -A POSTROUTING --table nat -i ppp0 -p tcp --dport 443 --to-destination 192.168.XXX.YYY
iptables -A POSTROUTING --table nat -i ppp0 -p udp --dport 1194 --to-destination 192.168.XXX.YYY 

[COLOR="Red"]iptables -A POSTROUTING --table nat -o ppp0 -j MASQUERADE[/COLOR]

as an idea - have you looked at the load of the network card in your computer (i.e. something like iptraf) to see of your line might be busy with something else ?

other than that... i don't really see any reason for it to be so slow... i've done setups like this a lot and are pretty dumbstruck now.
Another idea, have you loaded any QoS rules ?

---

### Post by Ingmar on 2008-10-30
OK, with the POSTROUTE masquerading it worked. I tested it on the internal firewall. But this doesn't make the connection faster. I watched the traffic while testing with wget and there were only 10-30kB/s on both interfaces.

I don't understand why only the connections with the DMZ are so slow. Isn't there anybody who have an idee?

---

### Post by Ingmar on 2008-10-31
Hi,

today I thought I test it with Debian Lenny as my firewall system. Then I remembered that xen-tools are only installing the actual kernel from my system. I manually installed the actual Kernel and copied it to my host system and configured the new VM to use this kernel. With this system all firewalling worked as it should.
Then I copied the modules folder from the Debian system to my Ubuntu firewall systems. Now after rebooting them with the Debian 2.6.26-1-xen-Kernel all firewalling also worked fine with the Ubuntu system.
I still need to test it from an external network but I hope it will also work fine.

So it seems to was a problem with the Kernel?!

Is it a problem to use the Debian Kernel extracted from a Debian system as a Kernel for the Ubuntu systems? Or may there be some problems while using this longer times?

And one last question:
Which rules are needed that I can access the nat-services also from the internal network with the external IP? I need this for example to access my internal webserver with my dyndns-Domain.

---

### Post by SpaceTeddy on 2008-10-31
if you want it to be accessible from anywhere, just take the -i option out - that will make the rules valid for any interface. Don't worry about the requests coming in on the wrong interface - it will work (always did for me anyways).

As for the Kernel. If everything is working fine, that should not be a problem then. But you will run into problems with updates from ubuntu (or maybe so). Also some stuff will not work later on since the modules/kernel might not have something compiled into it... 

But in general - if it works, use it.

Here is the modified minimal script i posted before to use the masquerading for all hosts (internal and external):
```
sudo su
sysctl -w net.ipv4.ip_forward=1
iptables -F
iptables -X
iptables -F --table at

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

iptables -A POSTROUTING --table nat -p tcp --dport 80 --to-destination 192.168.XXX.YYY
iptables -A POSTROUTING --table nat -p tcp --dport 443 --to-destination 192.168.XXX.YYY
iptables -A POSTROUTING --table nat -p udp --dport 1194 --to-destination 192.168.XXX.YYY

iptables -A POSTROUTING --table nat -o ppp0 -j MASQUERADE
```

on second thought... this will work, but all traffic will pass through the router - which is not optimal if your client is in the same subnet. If they are in the same subnet, it is acctually better to use a dns to rewrite the ip on the dns request for internal queries. That will put less stress on the firewall and will avoid another hop (that is not neccessary)

hope it helps :)

---

### Post by Ingmar on 2008-11-02
Hallo,

I'm restructering the firewall script and I'll publish this as a GPL-Script on my homepage when it's finished. I also changed the echo * > /proc/sys/... to sysctl-commands

The script will make Masquerading to the Internet, Port-Forwarding and also Traffic-Shaping.

And here is another question refering to iptables and tc Traffic-Shaping:
I use a script ([http://wiki.ubuntuusers.de/Skripte/Traffic-Shaping?highlight=traffic%20shaping](http://wiki.ubuntuusers.de/Skripte/Traffic-Shaping?highlight=traffic%20shaping)) from the German ubuntuusers-Wiki as the base for my Traffic-Shaping. There are some iptables routes like this, which mark the ip packets:
```
$IPT -A POSTROUTING -t mangle -o $DEV -p tcp -m length --length :64 -j MARK --set-mark 10
$IPT -A POSTROUTING -t mangle -o $DEV -p udp --dport 53 -j MARK --set-mark 10
$IPT -A POSTROUTING -t mangle -o $DEV -p tcp --dport 22 -j MARK --set-mark 11
```
Where should they be added? I think on a position near before the *iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE*. Is this correct?


> **SpaceTeddy said:**
> if you want it to be accessible from anywhere, just take the -i option out - that will make the rules valid for any interface. Don't worry about the requests coming in on the wrong interface - it will work (always did for me anyways).
I tested this but only with --dport 80, all my IP-Traffic which should be send to the Internet stoped. And I didn't get any response from the server. So something went wrong. But I'll test to work this out on my on this days.


> **SpaceTeddy said:**
> As for the Kernel. If everything is working fine, that should not be a problem then. But you will run into problems with updates from ubuntu (or maybe so). Also some stuff will not work later on since the modules/kernel might not have something compiled into it... 

But in general - if it works, use it.
I know this problems but I prefer working Routers and maybe I'll test it with Intrepid and when this works I'll use this. Or I change my routers to Debian Lenny when it's released. But for now this solution with the copied kernel is ok.


I didn't test the script because I need it in my script which I think is more secure.


> **SpaceTeddy said:**
> on second thought... this will work, but all traffic will pass through the router - which is not optimal if your client is in the same subnet. If they are in the same subnet, it is acctually better to use a dns to rewrite the ip on the dns request for internal queries. That will put less stress on the firewall and will avoid another hop (that is not neccessary)
I know that the additional hop isn't ideal but I have some servers which are accessible from the internet and I need working Mailserver-Connection also at home and also with firefox I want to have access to the webserver when I leave the session open when I come home with my laptop.


> **SpaceTeddy said:**
> hope it helps :)
Yes, big thanks again. You helped me to better understand iptables and get my routers working like they should.

---

### Post by SpaceTeddy on 2008-11-02
> **Ingmar said:**
> Hallo,

The script will make Masquerading to the Internet, Port-Forwarding and also Traffic-Shaping.

And here is another question refering to iptables and tc Traffic-Shaping:
I use a script ([http://wiki.ubuntuusers.de/Skripte/Traffic-Shaping?highlight=traffic%20shaping](http://wiki.ubuntuusers.de/Skripte/Traffic-Shaping?highlight=traffic%20shaping)) from the German ubuntuusers-Wiki as the base for my Traffic-Shaping. 
goot thing i read german aswell - kinda hard to understand for anyone who does not know what is says. The scripts are pretty basic, but should do the job (at least from what i could gather)
> **Ingmar said:**
> 
Where should they be added? I think on a position near before the *iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE*. Is this correct?

You can only add them in the mangle table... But - lets do some theory first. There are three tables in iptables. one is for filtering, one for NAT and one for mangle. 
The filter is where your block/pass rules go, where you store statefull/stateless rules and where you basicially "do" you firewall. 
The nat table is where you put port forwarding, port redirects (external and internal). NAT should never involve any blocking rules.
The mangle table is for packet manipulation. It will do tagging, rewriting, flagswitching - anything you want or desire. 

All the port forwarding and masquerading you do goes into the NAT table... 
All the traffic controll (QoS) goes into the mangle table... 

there is no relation in there that concers before/after - or so i understood it. They just go into the approptiate chain in the mangle table (in your case, OUTPUT, since the "normal" interfaces cannot do ingress traffic shaping.

> **Ingmar said:**
> 
I know that the additional hop isn't ideal but I have some servers which are accessible from the internet and I need working Mailserver-Connection also at home and also with firefox I want to have access to the webserver when I leave the session open when I come home with my laptop.

When a mail client fetches mail, it does not leave the session open - even imap closes the connection again. POP3 definetly does. In other words, there is no open connection that you could loose there. Any other connection (logged in websites, chat programms, etc) will get reset anyway, since the tcp session (NOT the website session - that is something different) will time out after 60-120 seconds anyway and will have to be redone aswell. 

So, essentially, there is no reason to do the redirect other than not wanting to have an internal dns overwrite some internet names. 
I am only pointing this out because it is the "clean" way of doing it (or so i think). It just means changing one dns entry (if you ever move something) instead of redoing lots of firewalls. It might not make such big difference in your case, but i've worked in company which had a really messed up way of redirecting traffic internally and externally. overwriting names is a lot easier there... 
> **Ingmar said:**
> 
Yes, big thanks again. You helped me to better understand iptables and get my routers working like they should.

Here is the (part) of my script that i use on my server to do traffic control

first, the tc part:
> 
#delete old traffic shaping
/sbin/tc qdisc del dev ppp0 root 2> /dev/null

#create root device
/sbin/tc qdisc add dev ppp0 root handle 1: htb default 22

#create root class (this should be set to the speed of the network card)
/sbin/tc class add dev ppp0 parent 1: classid 1:1 htb rate 912kbit ceil 912kbit burst 1024k

#########################
## create bandwidth classes (the sum of these cannot be bigger than the root class)
########################

#low priority class (webserver, ftp, etc)
/sbin/tc class add dev ppp0 parent 1:1  classid 1:11 htb rate 64kbit ceil 512kbit burst 30k prio 2

#internal network class (half the bandwidth to it, can burst to max, high priority)
/sbin/tc class add dev ppp0 parent 1:1  classid 1:12 htb rate 512kbit ceil 912kbit burst 1024k prio 1

#class vpn connections to other routers - this gets priority over the webserver, but has less bandwidth then the internal network
/sbin/tc class add dev ppp0 parent 1:1  classid 1:13 htb rate 336kbit ceil 600kbit burst 1024k prio 1

#create fair share handles
/sbin/tc qdisc add dev ppp0 parent 1:11 handle 11: sfq perturb 10
/sbin/tc qdisc add dev ppp0 parent 1:12 handle 12: sfq perturb 10
/sbin/tc qdisc add dev ppp0 parent 1:13 handle 13: sfq perturb 10

#now send pakets to each of the qdisks by giving them handles that can be used by iptables
/sbin/tc filter add dev ppp0 protocol ip parent 1: prio 2 handle 11 fw classid 1:11
/sbin/tc filter add dev ppp0 protocol ip parent 1: prio 1 handle 12 fw classid 1:12
/sbin/tc filter add dev ppp0 protocol ip parent 1: prio 1 handle 13 fw classid 1:13


and here are the matching iptables rules for it:

> 
#set a general tag (everything is from the internal network)
iptables -A OUTPUT -o ppp0 -j MARK --set-mark 0xc 
#if something goes out from the webserver
iptables -A OUTPUT -o ppp0 -p tcp -m tcp -m multiport --sports 80,443 -j MARK --set-mark 0xb 
#if something goes out from one of the openvpn connections, overwrite with the appropriate class
iptables -A OUTPUT -o ppp0 -p udp -m udp --sport 15000:15004 --dport 15000:15004 -j MARK --set-mark 0xd


they work for me, but i haven't touched them in almost a year.

Lastly, here is a link to a fairly good explanation on the whole tc inner workings - i have yet to finish reading it, but it seems to be really good [COLOR="Blue"][http://www.linux.com/base/ldp/howto/Traffic-Control-HOWTO/index.htmlt]("http://www.linux.com/base/ldp/howto/Traffic-Control-HOWTO/index.htmlt")[/COLOR]

cheers

---

### Post by Ingmar on 2008-11-02
OK, you are right. I think I didn't thought enough. After reading your last post I remembered, that DynDNS also supports wildcard hostnames so I can give my mailserver a own Domain Name with only one DynDNS-Account.

I've done this and added the external Domain Name to my /etc/hosts on the router and it works without any problem.

So again, thank you very much for all your help. Next week I'll try to get Traffic-Shaping working and when this works, I'll be very happy and I'll post again.

---

