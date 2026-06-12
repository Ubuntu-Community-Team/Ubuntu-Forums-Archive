---
title: "Internet Connection Sharing -- Can this be done through a bridge?"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by kevdog on 2008-03-24
I want to share an internet connection -- or so I've been asked how to do this.  The following is the setup

```

                  Internet
                       |
                       |
                  Computer #1  <-----patch or crossover cable---------->Computer #2
                        eth0                                                                                  eth0
                        eth1

```
Ive seen this article of Ubuntugeek how to enable the connection:
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

My question is can this be done through use of a network bridge.  Bridges seen easy to setup.  How do I allow the bridge computer (#1) to access the internet.  Is this method better than that referenced by ubuntugeek?

---

### Post by SpaceTeddy on 2008-03-24
this can only be done through a bridge if you have more than one ip address from the internet. If your computer acts like a bridge, it would act like a switch/hub. 

Also, any broadcast that is done between the two computers (samba/windows shares/dhcp) would be forwarded into the internet - somethig that might not be desired.

as for the tutorial, i've read it before. I've also [written down]("http://ubuntuforums.org/showthread.php?t=713874") a few steps myself on how to do this (same way as in the tutorial).

In the end, i would NOT use bridging to the second computer online - use internet sharing (ip-forwarding and nat). this way, you do not need multiple ip's from your isp - and anything that is in the internal network stays there (broadcasts and such things)

---

### Post by kevdog on 2008-03-24
What if there was a router between computer #1 and the internet in the diagram.  Would a bridge be appropriate?

---

### Post by SpaceTeddy on 2008-03-25
with a router between the computer#1 and the internet, broadcasts would stop at the router and would not reach the net anymore. also, the router would then supply a basic firewall and do the nat. In this case, thre would only be one external address needed. 

so, yes, if there is a router in that position, bridging is as much a possibilty as routing is - no worries to use it then. 

But why use the bridge in this scenario at all ? can't computer2 connect to the router directly, then (thus eliminating the need of a bridge) ?

---

### Post by kevdog on 2008-03-25
I know the scenario isn't practical, I just want to try a few things to learn about bridging.  Really between the router and Computer #1 there is no wire -- its a wireless connection.  

Ive read about creating a bridge.  I assume for Comp #2 to Comp #1 you need a crossover cable for 100Mb/sec NIC or less -- with Gigabyte card no specific cable is necessary.

If a server is to be run from Computer #1, how do I assign a static IP to Comp #1 but let Comp#2 be configured by DHCP with the IP address handed out by the router?  Beyond creation of the bridge with the bridge-utils package, I dont believe I have to change any routing statements.  Do I need to modify anything with Computer #1 IP Tables to allow passthrough?  Im assuming the bridge, comp #1 and comp #2 will each have a separate IP address.

---

### Post by SpaceTeddy on 2008-03-25
mhm - learning is always good :)

when you create a bridge, you need to unconfigure your physical network cards (the ones that get bridged).

lets say you have eth0 (wired nic) and eth1 (wifi card). if you bridge them together, you will end up with a device called br0. This will hold both network cards (eth0 and eth1). since briding is on mac layer, anything will be forwarded between the two interfaces, regardless if the ip confguration of br0.

so, after having br0 up and having eth0 and eth1 unconfigured (you might also want to put them in promisc mode) you can then assign any ip address to br0 without affecting the traffic between eth0 and eth1... 

or so it worked for me (i used to use bridges to paste together two buildings over vpn that did not have a direct connection)

---

### Post by kevdog on 2008-03-25
I'll go ahead and try,  no routing or gateway statements need to be configured on the computer #2?  Its still possible to use the internet on the bridged computer?

So
#1. Get the bridge configured, and up
#2. Set parameters (static IPs) of any network cards in the bridge
#3. I suppose that's it.

Just having a hard time visualizing how the packets are going to be router, Ill try to draw what I mean

 Router
      |
      |
    wlan0<--bridge br0--->eth0------------------eth0(Computer #2)
      |
    Comp #1

Does that seem right?  Since a bridge works on level 2, I guess a packet coming in from the router destined for MAC Comp #2, would pass through the bridge, but would also be seen by Computer #1?

---

### Post by SpaceTeddy on 2008-03-25
yep, your assumption about the passing is right. Computer#1 can see any paket flowing through it, but will also forward layer 2.

i think the commands you need to run are
```
sudo su
apt-get install bridge-utils
brctl addbr br0
brctl addif br0 wlan0
brctl addif br0 eth0
ifconfig wlan0 0.0.0.0 promisc
ifconfig eth0 0.0.0.0 promisc

```

this will configure the bridge (first line is to become root - so i can omit the sudo on every command)
you should now be able to pass traffic thought the computer, so #2 should be able to obtain dhcp-leases through #1 now

to configutre #1 staticially, you could use
```
sudo ifconfig br0 192.168.0.4
sudo route add default gw 192.168.0.1
```
of course you will need to fix the ips

and add a dns server in the /etc/resolv.conf...

just tried this on my computer with a vm - works perfect :)

---

### Post by regomodo on 2008-03-25
i wish network bridging was as painless as in XP. I have a wired connection and wifi card in my PC but can't create an AP for my laptop with it in Ubuntu. One day maybe,

---

### Post by SpaceTeddy on 2008-03-25
mhm - that just means you have to run iwconfig with the needed options for your wireless... i.e. to attach the network "mynetwork" you would run

```
sudo iwconfig wlan0 essid "mynetwork" key s:mypassword
```

and you are connected... it'sjust nm start blows hard in this setup :)

---

### Post by kevdog on 2008-03-25
> to configutre #1 staticially, you could use

Code:
sudo ifconfig br0 192.168.0.4
sudo route add default gw 192.168.0.1of course you will need to fix the ips

and add a dns server in the /etc/resolv.conf...

just tried this on my computer with a vm - works perfect 

I think I want wlan0 to have a static IP address?? I'm only assuming this since lets say a server is running on computer#1.  In this case after I create the bridge, wouldnt I want to proceed and then assign the wlan0 interface a static IP.

Something like this 
sudo su
brctl addbr br0
brctl addif br0 wlan0
brctl addif br0 eth0
ifconfig wlan0 0.0.0.0 promisc
ifconfig eth0 0.0.0.0 promisc
ifconfig wlan0 192.168.1.5

Although from what I am typing this doesnt seem to make any sense.  I guess my question is as follows.  If Im running an ssh server on Computer #1, and I port forward port 22 from the router -- I need a static IP address to port forward it to.  If I assign a static IP to the bridge, that really doesnt get me anywhere since the bridge is virtual and it doesnt have listening ports.  I need to pass requests on to port 22 on computer #1 -- which I think requires a specific IP address.  I know the bridge only filters by MAC rather than IP address or port.

I think something like running a server on computer #1 is possible, since it can be done such as on a ddwrt router since you I know you can create a bridge but still run a server on the router itself. 

Any further direction you could provide would be helpful.

---

### Post by SpaceTeddy on 2008-03-25
of course - but you do not assign the ip to wlan0 anymore - you assign it to br0. br0 is not your one network device - anything assigned to it will be handed down to wlan0 and eth0 at the same time (since they are bridged, they act as one)

so, once you have assigned a static ip to br0, and configured wlan0 though iwconfig to be in the right wifi network - you can go ahead and just forward to the ip of br0

in your commands - just switch wlan0 in the last command with br0 - and it should work fine :)

---

### Post by kevdog on 2008-03-25
So if I understand from what you are telling me, it wouldn't be possible for computer #1, computer #2 or any other computer connected to the bridge to run a server on the same ports -- ie ports 22 couldn't be open on the multiple computers (I wonder what would happen if this were the case -- interesting)!

---

### Post by SpaceTeddy on 2008-03-25
why could you not run multiple ssh servers ? now i am confused. Of course you can run as many servers (even of the same type) as you have computers. since computer #2 is assigned a different ip than computer #1 this does not pose a problem... 

i think now i am getting lost here...

[EDIT]
The bridge runs on layer 2 and does plain paket forwarding. anything that comes in on one network card goes out the other - unless it is directed towards the machine itself.
All servers based on IP (thus using TCP, UDP, or whatever protocol based on IP) will NOT be affected by the bridge, since they run in layer 3 and higher... 

This is your physical setup

Router <-->  wlan0 <--> Comp #1 <--> eth0 <--> eth0(Computer #2)

while, when you have the bridge enabled, your logical setup would look like this

Router
|
(wlan0,eth0) <--> eth0(Comp#2)
 |
 \--> br0 <--> Computer #1

so in other words, the bridge acts like a two port hub while the network interface of computer #1 is now br0.

---

### Post by kevdog on 2008-03-26
Thanks for the drawing, its now clear to me what is going on.  That's a great explanation -- possibly a how-to is in order.

---

### Post by kevdog on 2008-03-26
Any disadvantage/advantage of sharing the internet connection this way as compared to the other way of allowing passthrough (as referenced in the other post)?

---

### Post by SpaceTeddy on 2008-03-26
like i said earlier, this way your cards act as if they are a hub. anything going in the one card will come out the other (unless it is for your computer). So, if you were to use this for sharing the internet without the router beforehand, any broadcast any computer makes on your network will be forwarded to the internet. How far it goes there nobody knows, but ultimativly you could be broadcasting a lof ot things into the interent. 

An example for this are windows share (they broadcast like crazy), DHCP-servers or requests (when your clients are trying to pull a network configuration), or any game that "autmaticially" finds other players. This is all done via broadcasts - and all of them will be run into the internet. 

i find bridges usefull when it comes to attaching networks together that do not share a direct connection. for example, you have an office in a City A and another in a  City B. connecting the Networks of the two offices together to make them one could be a desire so that people do not have to think about where the computers are. As soon as they are in either office, they are "in the network".

Also bridges are usefull when you acctually do need to forward on layer 2 (IP broadcasts, or even worse, protocolls like IPX) which do not operate on IP. 

In all other cases i would always use rounting instead of briding. It makes sure that only what you want to pass acctually does pass.

As a sidepoint i would also like to point out, that if you use a bridge to share your internet, it would result in the need of two IP's from the internet, since the bridge acts as a hub. If your ISP only gives you one IP, then the second computer, althought physicially connected to the interenet, cannot access due to the lack of a valid Configuration. With routing and NAT, you do not have that problem.

did i make some sense ?

---

### Post by kevdog on 2008-03-26
Yes you did make sense if you have the hub directly connected to the internet.  Again if the hub is behind a router, then this shouldn't be an issue.  

Im more concerned with speed of connection, however this probably isn't an issue.  With only 6 computers in the house this probably isnt an issue.

My main goal was this exercise was to share the internet through a wireless connected laptop to a desktop, but still be able to use the internet on both.  Yes I guess I could just as well go out and buy a wireless NIC for the desktop, however that wouldn't be any fun :).

---

### Post by SpaceTeddy on 2008-03-27
mhm - speed. Not, i don't think that speed is an issue in this setup. although any traffic will be running over the two network cars, you should not experience reduced network speed unless you are really starting to go to the limits of the network cards themselves (i.e. copying as fast as you can through the bridge from multiple sources to multiple destiantions... then it probably would slow you down - but if that is noticable is an entirely different questions :)

---

