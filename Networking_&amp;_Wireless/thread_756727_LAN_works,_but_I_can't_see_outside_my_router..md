---
title: "LAN works, but I can't see outside my router."
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by mr.loco on 2008-04-16
I have never had this problem before and it's really dissapointing tbh.

I can look at everything on my network (shares etc.) but when I try to look at anything outside the network it just doesn't go. I've tried pinging IP's outside of the LAN to see if it's a DNS problem but that isn't the case.

The strangest thing of all is that skype works perfectly...

any pointers?

---

### Post by mr.loco on 2008-04-16
It turns out it IS a dns problem, but I dont know why it wouldnt work as I'm putting the same DNS IP on all the machines on the network but only the ubuntu one isnt working.

---

### Post by daengbo on 2008-04-16
Check /etc/resolv.conf and look at the order of your lookups.

---

### Post by mr.loco on 2008-04-16
it's pointing to 192.168.1.1 which is the right address (works on every other machine)

---

### Post by superprash2003 on 2008-04-16
since skype works and others dont.. its usually a DNS problem.in the /etc/resolv.conf try replacing 192.168.1.1 to 208.67.222.222 which is opendns' ip.make sure that 208.67.222.222 comes first in the list.. do so by removing 192.168.1.1 and adding 208.67.222.22 and then try.. may work..

---

### Post by bradwilliamson on 2008-04-16
Is it a NetGear router?

I've had these "Work" for DNS but sometimes they are **really** slow to respond making it look like a DNS problem from Linux boxes. Windows boxes usually work because they ask for everything (_everything!_) twice and get around the delay.

I second the "Use OpenDNS"

Opendns is the way to go if you don't have any other means of local DNS server, and even then, have your local DNS forward to OpenDNS. They are typically much faster than your ISP's DNS servers.

Brad

---

### Post by mr.loco on 2008-04-16
I've actually already tried that.... sorry i should have been more specific.

I've got the same config on my macbook... so it's not a router problem.

---

### Post by bradwilliamson on 2008-04-16
Ok, so is it just web traffic that fails then?

Can you try ftp/mail/ssh/https/ etc.

What router or firewall ae you using? That may help shed some light on what's going on.

---

### Post by juan@forum on 2008-04-16
check your gateway or the dns resolver
do you use a proxy?
use wireshark to see what's going on..

---

### Post by Traffic on 2008-04-17
I have to throw in here...

I am having the same problem...  I can connect to my internal network - but, when I connect my cable modem up to just my linux machine - I cannot see/ping anything outside my network...  

I am not a nube - however, I am to the point of tossing this computer...


...

---

### Post by mr.loco on 2008-04-17
Haha I second that I am actually getting pretty pissed off.

I've got an old linksys router, and I have changed nothing since it last worked.... Ubuntu just decided (mid-session) that it doesnt feel like being on the net i guess.
:lolflag:

---

### Post by Traffic on 2008-04-18
So...

I called my cable internet provider - they were able to tell me what motherboard I had because they could see it after the cable modem...

However - I still could not even ping an outside IP address => 66.94.234.13 (Yahoo) - I also could not ping any type of domain name...

They had no advice for me because they don't support anything past their router...

route -n looks good...  I have the proper gateway/netmask/network...

ifconfig is fine - my inet_interface is correct...  I am using the EXACT same settings on my linksys router and it works perfectly...  but, when I change the cable from ending at the router to ending at my linux box - it does not work...

Am I missing something...?  Is there some obscure setting that tells Linux to use a particular inet_interface to look "outside" - I know it sounds strange, but I am grasping at straws here...

This makes absolutely no sense whatsoever...


...

---

### Post by Traffic on 2008-04-18
Ok...

So, I talked with my cable company again...  They told me that they would have to request a "flush" in their system as the IP has been cached to the linksys router...  Or, I could unplug it for an hour or more - and, that should push past the cache time...

I am going to try this tonight...


...

---

### Post by zazuge on 2008-04-19
I'm no expert but did you install some DNS caching daemon like dnsmasq or BIND?
try ping some correct ipadresse
try using nslookup on both Linux and other computers and compare the results
finaly maybe its your firewall that is blocking access to all but your subnet?
did you install firestarter?

---

### Post by mr.loco on 2008-04-19
pinging external ip's works, and I can access websites through typing in their IP, it's Definitely a DNS problem. I've tried OpenDNS as someone has already suggested and that isn't working either. All other computers work with the same DNS server.

---

### Post by kevdog on 2008-04-19
Can you tell us exactly the changes you made to try the opendns servers?  When I mean exactly -- post the results of /etc/resolv.conf and /etc/dhcp3/dhclient.conf


Thanks

---

### Post by mr.loco on 2008-04-19
OK, I'll have to type them up by hand though :S

/etc/resolv.conf
```
nameserver 207.67.222.222
nameserver 207.67.220.220

```

/etc/dhcp3/dhclient.conf is the default one (I'm not using dhcp anyway)

Cheers.

---

### Post by kevdog on 2008-04-19
Are you using wired or wireless connection?  Using NM or making modifications to the /etc/network/interfaces file?

---

### Post by mr.loco on 2008-04-19
I'm using /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.3.38
netmask 225.225.225.0
gateway 192.168.3.1
wireless key *****
wireless essid *****
```

thx.

---

### Post by kevdog on 2008-04-19
Ok,

Do the following and post the results

nslookup yahoo.com  

```

(This is what I got):
>nslookup yahoo.com
Server:  UnKnown
Address:  192.168.1.1

Non-authoritative answer:
Name:    yahoo.com
Addresses:  216.109.112.135
          66.94.234.13

```

Then do the following
>nslookup

>server 208.67.222.222

>yahoo.com

Here is what I get:

```

>nslookup
Default Server:  UnKnown
Address:  192.168.1.1

> server 208.67.222.222
Default Server:  resolver1.opendns.com
Address:  208.67.222.222

> yahoo.com
Server:  resolver1.opendns.com
Address:  208.67.222.222

Non-authoritative answer:
Name:    yahoo.com.hsd1.il.comcast.net
Address:  208.67.217.132

>exit

```

---

### Post by mr.loco on 2008-04-19
```
$ nslookup yahoo.com
Server: 208.67.220
Address: 208.67.220#53

Non-authoritative answer:
name: yahoo.com
Address: 216.109.112.135
name: yahoo.com
Address: 66.94.234.13
```

Weeeeird, seems that everything is working...

```
$ nslookup
> server 208.67.220.220
Default Server: 208.67.220.220
Address: 208.67.220.220
> yahoo.com
Server: 208.67.220
Address: 208.220#53

Non-authoritative answer:
name: yahoo.com
Address: 216.109.112.135
name: yahoo.com
Address: 66.94.234.13

```

The mind boggles.

EDIT:

I'll post what i get in OSX in case it helps.
```
mac:~ mrloco$ nslookup yahoo.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	yahoo.com
Address: 216.109.112.135
Name:	yahoo.com
Address: 66.94.234.13

```

---

### Post by daengbo on 2008-04-19
We have determines that your problem is not with lookups, eh? The problem must be with an application.

try:
wget slashdot.com

If that works, then you probably have a proxy setting messed up in Gnome or Firefox. Check 
System > Preferences > Network Proxy
and make sure you are on Direct Connection

In Firefox, check 
Edit > Preferences > Advanced
Clic on the network tab
Choose Connection Settings and make sure you are using the system proxy settings.

I hope that we can solve your issue soon

---

### Post by kevdog on 2008-04-19
Sorry I didnt give the answer away in the last post.  Take a look at the dns nameservers you have listed for the opendns servers in your previous post:

nameserver 207.67.222.222
nameserver 207.67.220.220

Those IP addresses are wrong.  

Just a hint:
The second one should be:
208.67.220.220

---

### Post by mr.loco on 2008-04-20
Resolving slashdot.com... failed: Name or service not known.

if i do nslookup slashdot.com it gives me the right ip though.... something's FuBAR

all the settings in gnome and ff are set to direct connection. (the 207.xxx.xxx.xxx was a typo because i can't copy/paste into this thread as the internet isnt working)

thx.

---

### Post by kevdog on 2008-04-20
so what is your /etc/resolv.conf file actually show?

---

### Post by mr.loco on 2008-04-20
```
nameserver 207.67.222.222
nameserver 208.67.220.220
```

thx.

---

### Post by kevdog on 2008-04-20
I think it should be:

nameserver 208.67.222.222
nameserver 208.67.220.220

As directed by the OpenDNS page:

> 
The straight dope

Our nameservers are 208.67.222.222 and 208.67.220.220.


---

### Post by mr.loco on 2008-04-22
Still doesn't work mate... besides, that typo wouldnt have mattered because the secondary ip was right.

Also, OSX and Windows both work with the same DNS settings... what the **** (excuse my french) is going on?

---

### Post by mr.loco on 2008-04-23
(bump)^2

---

### Post by bradwilliamson on 2008-04-24
Ok, bare-bones time:
since nslookup slashdot.org gives me:
66.35.250.150

try telnet 66.35.250.150 80
[ENTER]
type (possibly blindly)
GET /
[ENTER]
[ENTER]

If this works, then I would check two things:
1) is IPV6 enabled on the router (it shouldn't be unless you are at a big-honkin-university) 
2) is your box firewalled - run:
sudo iptables -L and see what's there.

If it doesn't:
1) is your router really your default gateway - run:
route -n 
and make sure that the 0.0.0.0 route has your router as the gateway
2) If it still doesn't work try to post your results of ifconfig and route -n, you can use a flash drive perhaps to copy the results across machines
Here is my result on a working computer:

admin@subversion:~$ nslookup slashdot.org
Server:         192.168.100.50
Address:        192.168.100.50#53

Non-authoritative answer:
Name:   slashdot.org
Address: 66.35.250.150

tmradmin@subversion:~$ telnet 66.35.250.150 80
Trying 66.35.250.150...
Connected to 66.35.250.150.
Escape character is '^]'.
GET /

HTTP/1.0 501 Not Implemented
Content-Type: text/html
Content-Length: 136

<html><head><title>501 Not Implemented</title></head><body><h1>501 Not Implemented</h1><p>This method may not be used.</p></body></html>Connection closed by foreign host.

admin@subversion:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
admin@subversion:~$route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.100.254 0.0.0.0         UG    0      0        0 eth0

---

### Post by bradwilliamson on 2008-04-25
Well, whaddya know, I rebuilt a laptop with 7.10 and have exactly the same problem. I know the Ubuntu sites are getting their tails kicked with the 8.04 release, so the apt-get updates are horribly slow, but it seems to have the same issue where nslookup works but nothing web works, or at least, very very rarely.

Ok, found it... at least on mine...

sudo /etc/init.d/avahi-daemon stop
and try things again.

And sanity returned! Of course your mileage may vary.

To permanently disable it:
sudo nano /etc/default/avahi-daemon
and change 1 to 0, save, exit, yada yada

Witness:
norman@norman-laptop:~$ wget [http://vmhost.tmr.local/](http://vmhost.tmr.local/)
--17:11:29--  [http://vmhost.tmr.local/](http://vmhost.tmr.local/)
           => `index.html'
Resolving vmhost.tmr.local... failed: Name or service not known.
norman@norman-laptop:~$ sudo /etc/init.d/avahi-daemon stop
[sudo] password for norman:
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                                                 [ OK ] 
norman@norman-laptop:~$ wget [http://vmhost.tmr.local/](http://vmhost.tmr.local/)
--17:12:27--  [http://vmhost.tmr.local/](http://vmhost.tmr.local/)
           => `index.html'
Resolving vmhost.tmr.local... 192.168.100.230
Connecting to vmhost.tmr.local|192.168.100.230|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,703 (3.6K) [text/html]
100%[=================================================================================================================>] 3,703         --.--K/s             
17:12:27 (84.27 MB/s) - `index.html' saved [3703/3703]
norman@norman-laptop:~$ sudo /etc/init.d/avahi-daemon start
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                                                                                                     [ OK ] 
norman@norman-laptop:~$ wget [http://vmhost.tmr.local/](http://vmhost.tmr.local/)
--17:12:38--  [http://vmhost.tmr.local/](http://vmhost.tmr.local/)
           => `index.html.1'
Resolving vmhost.tmr.local... failed: Name or service not known.

---

### Post by daengbo on 2008-04-25
Check your default gateway with 
> route
I recently had my default route set at 192.168.0.254, which doesn't exist on my network. I got around the problem by setting a static IP, which is not the best choice, but was the only workaround I could find.

---

### Post by mr.loco on 2008-04-27
turning off avahi-daemon doesn't seem to do anything. Here's the stuff you wanted :)

```
//////////////ifconfig////////////////


eth0      Link encap:Ethernet  HWaddr 00:50:8D:A8:13:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5658 (5.5 KB)  TX bytes:5658 (5.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:B6:5A:05:CB  
          inet addr:192.168.3.38  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe5a:5cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39776 (38.8 KB)  TX bytes:40915 (39.9 KB)
          Interrupt:16 Memory:e7000000-e7008000 


////////////route -n//////////////////

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.3.1     0.0.0.0         UG    100    0        0 wlan0


///////////iptables -L////////////////


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```

thx

---

### Post by daengbo on 2008-04-27
You don't have a default route.
try
> route add default eth0

---

### Post by mr.loco on 2008-04-27
surely it should be wlan0 since i'm using my wireless, right?

I can't get to the machine in question at the moment, but i will definately give it a go tomorrow.

cheers.

---

### Post by bradwilliamson on 2008-04-28
He has a default route:
0.0.0.0         192.168.3.1     0.0.0.0         UG    100    0        0 wlan0

That all looks good. 

Did the wget [http://slashdot.org/](http://slashdot.org/) work?

I found the avahi weirdness that way, maybe you would see the same. 

You can run:
strace wget [http://slashdot.org/](http://slashdot.org/) 
And it will give you a *LOT* of stuff scrolling by, but towards the end it should stall and drop you back to the prompt, and if you scroll back up into the trace you should hopefully see an error that would shed some light on things. 

It will be unintelligible for the most part, but somewhere in there will lie the answer. You can post the trace if you like. Mine showed the avahi daemon causing problems, and now it shows references to mdns that work, however your mileage will obviously be different since yours still fails.

---

