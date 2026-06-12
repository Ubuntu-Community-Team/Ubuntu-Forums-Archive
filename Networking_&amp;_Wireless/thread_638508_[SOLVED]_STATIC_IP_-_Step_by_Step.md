---
title: "[SOLVED] STATIC IP - Step by Step?"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by Krusader3z on 2007-12-12
The last hurdle I have to overcome is setting up a static IP address for my computer. The reason I want to do this is so I can use uTorrent and similar programs from behind my firewall.

I know in windows I had to run "ipcfg" and pull some information from there, such as my IP and Subnet, then I had to log into my router and get the DNS servers. I don't remember exactly what I did from there, but I'm sure it is entirely different in Ubuntu.

I haven't found a solid answer to this, so perhaps someone can clear this up for me and future people with this need?

---

### Post by wieman01 on 2007-12-12
If you are not scared of the infamous command line :-) try this:
> [http://ubuntuforums.org/showthread.php?t=631912](http://ubuntuforums.org/showthread.php?t=631912)
It's step-by-step instructions based on my WPA tutorial.

---

### Post by Krusader3z on 2007-12-12
inet addr:192.168.10.155 
Mask:255.255.255.0  
Bcast:192.168.10.255

is the information I pulled. What is Bcast?

these are my DNS

Primary DNS Server :  	204.127.203.135
Secondary DNS Server : 	216.148.225.135

---

### Post by Krusader3z on 2007-12-12
One more thing. This is a wireless connection. Does that make a difference in the file I am editing?

wlan0     Link encap:Ethernet  HWaddr 00:1C:26:CB:AB:12  
          inet addr:192.168.10.155  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fecb:ab12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:161663563 (154.1 MB)  TX bytes:17510089 (16.6 MB)
          Interrupt:17 Memory:f9ffc000-fa000000

---

### Post by wieman01 on 2007-12-12
Oh wireless? Then you must be using Network Manager to manage your connection(s), right? It's the little applet that resides in the extreme upper right corner (task bar).

That application cannot handle static IP addresses, that's the bad news. The good news is that WICD can. Check it out:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

Unlesss you want to configure your connection manually via command line... But try WICD first.

---

### Post by SteveHillier on 2007-12-12
> **Krusader3z said:**
> 
Bcast:192.168.10.255

is the information I pulled. What is Bcast?


I am no networking expert but BCAST is the broadcast address.  In any range of IP addresses some numbers are reserved.
So if your mask is 255.255.255.0 then theoretically your should get 265 addresses on your network.  However (in your case) 192.168.10.0 and 192.168.10.255 are reserved so in effect you get only 254 addresses.  [If you but 5 fixed IPs then you are actually allocated 8 but only have 5 that you can use.]
In my limited knowledge of these things a broadcast address might be used for when a new bit of kit comes on to your network and needs to see what is out there.  If you think about it that is just what your machine needs to do if it has dynamically allocated addressing

WORD OF WARNING.  If someone else comes back and says I have got it wrong be prepared to believe they might be right.

Hope this helps

---

### Post by Krusader3z on 2007-12-12
Okay. I successfully installed wicd.

Based on the information i copied and pasted above, can you tell me what I should enter in wicd manager?

There are two buttons to enable.

1) Use Static IP 
IP=
Netmask=
Gateway=

2) Use Static DNS

-- I assume I just enter the two DNS servers that I know my ISP uses..


However, I'm confused with the readout from ifconfig. I don't see gateway or netmask

---

### Post by wieman01 on 2007-12-12
_Here we go:_

IP = Your own desired IP address (that of your PC)
Netmask = In all likelihood it is 255.255.255.0.
Gateway = The IP address of your router.
DNS = The IP address of your router.

That's it.

---

### Post by Krusader3z on 2007-12-12
Thankyou wieman01

For anyone else having to do this, here is how I solved this problem.

The first thing I did was open a terminal and run
[PHP]ifconfig[/PHP]

Then I copied and pasted the results into a document file, but the only one I needed (and suspect you will need) was the one labeled "inet addr"
in my case it was inet addr:192.168.10.155

Then, I followed THESE instructions to install wicd
[http://www.ossgeeks.co.uk/?p=166](http://www.ossgeeks.co.uk/?p=166)

*NOTE*
Once I had wicd installed i tried connecting to my wireless network and it kept getting held up at "obtaining ip address"
After a few tries I clicked that little white triangle next to my network name to expand the options, and then I clicked on "Use Encryption" and entered my WPA2 password.

From there I logged into my router (mine was [http://192.158.10.1](http://192.158.10.1)) but most are 192.168.1.1 from what I hear.

I copied the IP addresses of my two DNS servers, which were listed right on the main page in my case, into that notepad with my computer's internal IP address already in it.

From there, I went back into wicd manager, expanded my network with the white triangle,   clicked "Use static IP's"

I entered my IP that I had copied into the notepad earlier, then when I hit "TAB" wicd auto filled the next two parts, the netmask and gateway, automatically.

I then entered my two DNS servers into the "Use Static DNS" boxes below.

I restarted my network, and I was good to go.

*NOTE* 
I'm not sure i just got lucky when i entered my IP address and it autodetected the rest, or if it does this for everyone.
wieman01 said in all probability the netmask is 255.255.255.0, as it was in my case, and my gateway was the same address I used to http:// into my router, in my case [http://192.168.10.1](http://192.168.10.1)

So, hopefully this helps someone.

---

### Post by wieman01 on 2007-12-12
To find out about your router's IP address while you are connected, do:
> route
Good job & thanks for the instructions.

---

### Post by SteveHillier on 2007-12-13
> **Krusader3z said:**
> 

2) Use Static DNS

-- I assume I just enter the two DNS servers that I know my ISP uses..


Krusader3z uses this but my concern would be if your ISP is dynamically allocating your DNS servers these might change in the future and then you will loose your DNS.  If you buy a fixed IP from your ISP then you are likely to be given fixed DNS addresses, however most home networks I have come across dynamically allocate IP addresses and DNS servers.  Quite often these will not change and they will not normally change while your router/modem stays attached, but if you have to reboot your router there is no guarantee you will get the same addresses allocated.  You might get lucky, you might not.
Just a thought in case you get problems in the future.

---

### Post by wieman01 on 2007-12-13
> **SteveHillier said:**
> Krusader3z uses this but my concern would be if your ISP is dynamically allocating your DNS servers these might change in the future and then you will loose your DNS.
If that is the case, simply enter your router's IP address and you'll be fine. The router acts as a DNS for your network.

---

### Post by SteveHillier on 2007-12-13
> **Krusader3z said:**
> From there I logged into my router (mine was [http://192.158.10.1](http://192.158.10.1)) but most are 192.168.1.1 from what I hear.


I think you meant 192.168.10.1 in the line above.
The default LAN address factory set in routers depends on (varies by) manufacturer.  You will normally strike lucky by going for 192.168.0.1 or 192.168.1.1.  If you come across a router with a setting that does not match your network then you have to change the setting on one of your machines (I have a laptop I lug around just for this) to match the router and then change the internal LAN settings on the router and then reboot.  The default setting is normally marked on the base of the router or in the documentation that comes with it.

> **Krusader3z said:**
> 
*NOTE* 
I'm not sure i just got lucky when i entered my IP address and it autodetected the rest, or if it does this for everyone.
wieman01 said in all probability the netmask is 255.255.255.0, as it was in my case, and my gateway was the same address I used to http:// into my router, in my case [http://192.168.10.1](http://192.168.10.1)

As a rule of thumb you can expect the net mask on your private (LAN) address to be 255.255.255.0 which will give you 256 nodes (addresses) on your LAN.  I have not come across a router factory set to any other netmask.  
The times when you come across masks with other than 0 in the last part is if you have fixed IP addresses from your ISP.
Remember your netmask is a bit pattern with all 1s to the left and all 0s to the right so you would see
[00000000] = 0 -> 256 addresses
[10000000] = 128 -> 128 addresses
[11000000] = 192 -> 64 addresses
[11100000] = 224 -> 32 addresses
[11110000] = 240 -> 16 addresses
[11111000] = 248 -> 8 addresses
[11111100] = 252 -> 4 addresses
[11111110] = 254 -> 2 addresses

The reason that your gateway address was the same as your router is because your router IS your gateway.
These boxes are multi function kit.  Please prepend the word 'normally' in front of the following
They are a switch and switch packets around your network.
They are a router determining routes between various parts of the network
They are gateways because they sit on two networks -> your LAN [network 1] and the internet [network 2].  A gateway is anything that can sit on two networks at the same time so any computer with two network adapters can be used as a gateway.
They might also be a modem converting outgoing digital signals from your computer to analogue signals for the telephone lines and the reverse for incoming signals.  Cable routers will be different.
The problem is we all get lazy and talk about our "router" because it is quicker than saying "my router gateway modem" 

I apologise if this comes across school teacherish.  It isn't meant to but if you are able to take the ideas on board you can see that what you experienced is not unusual or unexpected.

Good luck

---

### Post by SteveHillier on 2007-12-13
> **wieman01 said:**
> If that is the case, simply enter your router's IP address and you'll be fine. The router acts as a DNS for your network.

I agree with you in the main, but in my experience that is not always enough.

---

### Post by wieman01 on 2007-12-13
> **SteveHillier said:**
> I agree with you in the main, but in my experience that is not always enough.
Is it not? What other issues could there be for instance? Just curious... :-)

---

### Post by SteveHillier on 2007-12-14
> **wieman01 said:**
> Is it not? What other issues could there be for instance? Just curious... :-)

Hi wieman01.

Just as an example here is my network.
192.168.0.200 -> Win 2003 domain server
192.168.0.? -> Ubuntu (Gutsy) workstation
192.168.0.? -> Vista Business workstation (domain member)
192.168.0.? -> Win XP workstation (domain member)
192.168.0.? -> Win XP workstation (domain member)
192.168.0.253 -> Netgear DG834 router
192.168.0.252 -> Edimax Wireless AP
192.168.0.60 -> Minolta network printer
192.168.0.50 -> DLink USB print server
192.168.0.201 -> Ubuntu (Dapper) Web Server

The ? indicates dynamically allocated addresses using DHCP from the router.  Other infrastructure uses fixed addresses.  All the fixed IP machines are set because they need to be fixed.

To get my Ubuntu workstation to go I simply put in router IP as DNS but this is not a domain member.  

The WIn 2003 machine has gateway address set, but if you leave dynamic DNS it will not connect to internet, so this has the public DNS server set.  As this is itself a DNS server it does not make sense to add itself in the list of DNS servers.  It does not like the router as a preferred DNS server.  If you tell me it is because the routing table in the DNS set up is wrong then I will listen, but given the ages it took to get this to work with the Web Server and because it does not connect to the web very often I am happy to leave well alone.

The Vista workstation needs to have the domain server address as one of the DNS servers otherwise logging on takes forever (well a long time anyway).  I presume this because if you don't set it it goes outside the local base to find the DNS server for the domain, but I cannot prove this.  It then has one of the public DNS servers as the alternative without which it still not connect to the internet.

The two XP machines are quite happily using full dynamic allocations but in the prior to the last move I have had to set the domain server and public DNS server address in the DNS boxes.

These settings are as they are because that is how I have had to set it up to make it work - empirically.  The theory behind some of this eludes me.

Other networks I maintain can have similar issues.  Set it up the way you think it should be and then parts don't work, so change it counter intuitively and it will work.

I tend these days therefore not to be dogmatic about settings.  I operate on the lines spoken reputedly by Oliver Cromwell (you know, the one who when he had his portrait painted is supposed to have said "paint it as it is - warts and all") - sorry, I digressed - Cromwell is also supposed to have said "I beseech you, in the bowels of Christ, think it possible you may be mistaken".  

If you work on that premise then you cover all bases when it goes wrong - or takes longer to fix than you thought.

If having read this you are thinking "this guy is a real plonker" then please point me towards the paths of righteousness (or in the right direction at least)

Thanks for your interest.

---

### Post by wieman01 on 2007-12-14
> **SteveHillier said:**
> These settings are as they are because that is how I have had to set it up to make it work - empirically.  The theory behind some of this eludes me.
It's odd to hear such stuff, however, as I am less aware of the theory as might seem, I can only scratch my head and acknowledge that it may be necessary in a few (hopefully rare) cases. Thanks for the input then.

Sometimes experience beats theory I guess. What can I say?! :-)

---

