---
title: "aMule low id through Router -&gt; AP wireless client -&gt; This pc"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by daller on 2005-11-14
Hi There,

Connecting to aMule with my laptop gives me high id (wireless)

Connecting with my desktop, I get low id...

The desktop connects through an AP in Wireless Client Mode...

Any ideas?

---

### Post by tomski on 2005-11-14
this is assuming you conect to the net via a router!
if so 
do both machines recieve different IP addresses but in the same range ie: 
       192.168.0.33/255.255.255.0 & 192.168.0.34/255.255.255.0
when they are both connected at the same time?
if so make a note of both addresses.
then find the 'mac' address for each wireless (or wired) network device in both machines
then log into the router 
(type your 'default gateway' IP address into a browser)

and assign a fixed/static to each 'mac' address 
(probably in the settings for 'dhcp')

then when your desktop or laptop gets its ip it will all ways be the same..
then you can use 'port forwarding' 
(probably in the fierwall settings of the router)
to allow those amule ports (use the default ones found in the connection settings of amule)
to be forwarded to the ip address for each machine (which will never change!)

when done i think you can test the connection in the connection settings menu

---

### Post by tomski on 2005-11-14
just one off subject but what was the transistion like from hoary to dapper 

or was it a fresh install 
i ask as im still using hoary and its rock solid but i've heard there are some problems with dapper 

how was it for you

---

### Post by daller on 2005-11-14
[QUOTE=tomski]just one off subject but what was the transistion like from hoary to dapper 

or was it a fresh install 
i ask as im still using hoary and its rock solid but i've heard there are some problems with dapper 

how was it for you[/QUOTE]

Well, everything is fine if you do NOT use KDE3.5!

...I have KDE3.5 on my laptop, and KDE3.4 on my desktop... (Both dapper) - And I must say, KDE3.5 under dapper is quite buggy!

---

### Post by daller on 2005-11-14
[QUOTE=tomski]this is assuming you conect to the net via a router!
if so 
do both machines recieve different IP addresses but in the same range ie: 
       192.168.0.33/255.255.255.0 & 192.168.0.34/255.255.255.0
when they are both connected at the same time?
if so make a note of both addresses.
then find the 'mac' address for each wireless (or wired) network device in both machines
then log into the router 
(type your 'default gateway' IP address into a browser)

and assign a fixed/static to each 'mac' address 
(probably in the settings for 'dhcp')

then when your desktop or laptop gets its ip it will all ways be the same..
then you can use 'port forwarding' 
(probably in the fierwall settings of the router)
to allow those amule ports (use the default ones found in the connection settings of amule)
to be forwarded to the ip address for each machine (which will never change!)

when done i think you can test the connection in the connection settings menu[/QUOTE]

Just to be sure...

I can NOT have 4662 point at both machines?

...That is what I have now, and it doesn't work...

Another thing, is that I can't obtain an IP address from the router via. DHCP (through the AP wireless client)

...Should I activate DHCP on the Wireless Client? (Wouldn't that create a seperate submask?)

---

### Post by tomski on 2005-11-14
[QUOTE=daller]Just to be sure...

I can NOT have 4662 point at both machines?

...That is what I have now, and it doesn't work...

Another thing, is that I can't obtain an IP address from the router via. DHCP (through the AP wireless client)

...Should I activate DHCP on the Wireless Client? (Wouldn't that create a seperate submask?)[/QUOTE]

first . if both machines are on at the same time then no you will not be able to have the same ports forwarded to both so just use the next ones up or jump up 10 ports but which ever ones you use make sure amule knows.

second . you should be able to recieve dhcp via wireless
 (laptop/desktop is the client -router is the server)
make sure the router has dhcp enabled on the LAN side and make sure it is serving enough ip's in the dhcp 'pool'

third . if your router mentions a dhcp client i would say that is for the WAN(internet) side so if your isp provides ips dynamicly then enable it but if you have paid for a static (recomended for p2p) the give it the ip you paid for
 & yes you will get a different submask probaly 255.255.255.252 or 255.255.255.0 for dynamic

---

### Post by daller on 2005-11-14
Don't know if I explained it that well, but my desktop pc is not connected to the LAN-side of the router!

I assume nothing is wrong with the setup on the router, since aMule works great on my laptop.

The problem is, that I may have been an idiot setting up a Wireless Client

My desktop is not wired to the router, nor does it have a wireless-card!

The way I managed to set it up  (knowing about the difficulties of setting up wireless-cards), I both an Access Point (D-Link DWL-900AP+) and set it up as a Wireless Client.

Now I connected the LAN-side of that AP, to my netcard in my desktop...

Apparently I have managed to do it just a little well, cause I have Internet-access.

But according to a lot of people, the router should be able to address DHCP through that setup, but running "sudo ifup eth0" doesnt find anything.

Therefore it set it up static:

iface eth0 inet static
address 192.168.0.134 (the address I use to forward 4682 to)
netmask 255.255.255.0 (This is right, right?)
gateway 192.168.0.1 (The AP is .50, but the gateway should be the router, right?)

Any ideas?

---

### Post by tomski on 2005-11-14
so does the destop have a internet connection at all

is the D-link just a AP or can it route net traffic too
that would make you situation a lot better

---

### Post by tomski on 2005-11-14
check and see if the AP provides dhcp then put the settings there but you will still need to port forwarding on the router just point that to the access point ip

---

