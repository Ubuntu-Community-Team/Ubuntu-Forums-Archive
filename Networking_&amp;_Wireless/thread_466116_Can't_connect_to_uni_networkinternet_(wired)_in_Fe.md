---
title: "Can't connect to uni network/internet (wired) in Feisty - fine in XP"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by Mountaingod on 2007-06-06
I just started dual booting XP Home Edition and Ubuntu 7.04. *After a bit of setting up*, Firfox in _windows XP_ runs fine, fetching both internal pages and those on the internet (after authenticating with their web proxy).

This is not the case with ubuntu however. The icon near the clock in the top right tells me I am connected to the wired network fine. Going to **System>administration>network** I can see that it's detected the network's DNS IPs and the uni's domain URL.

From what I can tell from 'connection information' it appears my computer has been assigned an internal IP address and for all intents and purposes, I am connected fine.

However, contrary to this information I can't get to *anything*. It's not the web proxy that's the problem cos if that were the case I'd still be able to get to internal pages, and when I try a www one it would give me a university-redirected error page instead of asking for proxy user/password.

It's basically telling me everything is fine (similarly 'normal' things are reported with *ifconfig* in the terminal) - but behaving as if the ethernet cable isn't plugged in the back of my laptop. Of course, if I pull this plug out, Ubuntu tells me the connection is disconnected, and reconnects when I put it back in.

Now, the uni network seems a little complicated to me as a result of their megolomaniacal desire to control everything (succesfully using P2P here is a bit of a 'cat and mouse' game) but I don't think this is really to blame because everything's fine on Windows XP. Furthermore, when you first register your computer/MAC address with them (otherwise they **will** straight up prevent you from connecting), there's a list of OSes you have to choose from in which ubuntu is *specifically* mentioned, so it's unlikely they've built a Windows & Mac-centric network that's incompatible with other OSes.

My guess is that something isn't configured right in ubuntu to allow it to use the uni network. Once, I did get a session of about 2 hours where I *was* able to use the network and internet in ubuntu, but only with firefox. GAIM, synaptic etc. couldn't get through. This session was a freak occurance and it cut out after the 2nd hour just as randomly. The same settings that achieved it won't do so now.

Their instructions for connecting Windows and Macs to the network are [here](http://www.sussex.ac.uk/its/roaming/documents/resnet_online). If they could be 'translated' into ubuntu instructions for me, that might solve my problem. Sorry for such a long post, but I've been trying at this for ages and I wanted to include all the details. Thanks in advance.

---

### Post by dfreer on 2007-06-06
If your uni specifically lists ubuntu as an OS (yea!), they probably have a techie you can help you connect. short of that, it looks like you need to do 2 things here:
(1) register your ethernet MAC address on the uni server (should be ok, it is the same in windows/ubuntu)
(2) set up firefox to use the proxy to access the internet
Go to Firefox > Edit > Preferences
go to Advanced > Network > Connection > Settings....
Fill in the proxy information provided by your uni

Beyond that, don't know how to get other internet programs working, I doubt they use firefox to access. but firefox should work

---

### Post by Mountaingod on 2007-06-06
I've done (1) with XP. I tried registering again with the same MAC address but listing the OS as **ubuntu**, but they wouldn't let me register the same MAC address twice. So I changed the last digit of it and registered that MAC instead (with ubuntu as the OS), then eventually(!) set ubuntu to change the MAC address to this one at the start of every boot. Effectively all that was changed in this exercise was what my OS is listed as when my laptop is on the network booted in ubuntu, and it made no difference to the problem.

I've also done (2), but as I say it's not the proxy that's the problem, as I can't even get onto the uni *network*, let alone through to it's web proxy.

---

### Post by dfreer on 2007-06-06
(1) as I said, you probably don't need to do this again because the MAC address would stay between windows/ubuntu. prolly no need to change mac addresses, just use the same one you originally registered.


try pinging one of those internal websites you mentioned. do you get an response? also post your output of ifconfig -a
you could also try pinging your DNS server, default gateway, or try doing a traceroute to google.com to see how far it gets.

---

### Post by Mountaingod on 2007-06-06
Pinging internal websites comes up with "the address <url> cannot be found." This is the same for external websites, and my DNS & default gateway, despite the fact if I go to *network information* it tells me what the latter two's IPs are.

The same message comes up with traceroute, again with internal and external websites. Again, it's as if my computer isn't plugged into the network despite the network icon telling me everything is fine.

Although I've been having some issues with that too. Every now and again when I right click on it and go to view *'network information* it instead comes up with the error "could not find the required resources (the glade file)!". Same problem has been had by [other people](http://ubuntuforums.org/search.php?searchid=21606488) apparently, don't know if it's related.

ifconfig -a tells me:

ben@ben-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:D0:57:26:04  
          inet addr:10.0.10.251  Bcast:10.0.10.251  Mask:255.255.255.255
          inet6 addr: fe80::240:d0ff:fe57:2604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:729065 (711.9 KiB)  TX bytes:4632 (4.5 KiB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by Mountaingod on 2007-06-07
Can anybody interpret that for me?

---

### Post by Mountaingod on 2007-06-08
Looks like I'm going to have to ditch it then until I get back home :(

---

### Post by Honig on 2007-06-08
> **Mountaingod said:**
> Pinging internal websites comes up with "the address <url> cannot be found." This is the same for external websites, and my DNS & default gateway, despite the fact if I go to *network information* it tells me what the latter two's IPs are.

Might be an issue of terminology but a <URL> generally specifies a simple name of a server or domain. What you need to test is an ip address where there are four groups or octets of numbers (example: from your inet address: 10.0.10.251 is an ip address). You need the ip address of some place else preferably on the uni network to ping.

> 
ifconfig -a tells me:

ben@ben-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:D0:57:26:04  
          inet addr:10.0.10.251  Bcast:10.0.10.251  Mask:255.255.255.255
          inet6 addr: fe80::240:d0ff:fe57:2604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:729065 (711.9 KiB)  TX bytes:4632 (4.5 KiB)
          Interrupt:11 Base address:0x4000 


That looks strange because the ip address (inet) and the broadcast (bcast) address are the same. This is not generally the case, but because your subnet is listed as 255.255.255.255, I'm thinking this is because the uni uses CDIR and just gives every ip its own subnet, but I'm not sure. 

When you use windows and look at the ipconfig at a command prompt is the ip address and gateway the same or similar? 

Also when you run a traceroute to any ip address what are the results? Do you see any hops at all?

---

### Post by jvetor on 2007-06-11
I have a simular problem. Earthlink gave me two DNS server numbers to enter and until I do I am connected but can't surf. In Linux I to to network and enter them and all works fine. I save the profile but when I shut down they are lost and I have to repeat it each time I log on. I don't understand why it doesn't save them. Any ideas? Thanks

Jim Vetor

---

### Post by starNIX on 2007-06-23
I am having the same problem.  Whenever I shutdown,  I have to reenter the search domain and DNS servers.  This is happening on 2 laptops with feisty.  A bug perhaps?

---

