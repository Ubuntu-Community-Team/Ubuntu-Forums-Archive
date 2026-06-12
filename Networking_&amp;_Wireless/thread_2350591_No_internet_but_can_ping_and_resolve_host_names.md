---
title: "No internet but can ping and resolve host names"
date: 2017-01-25
forum: Networking &amp; Wireless
---

### Post by sushiboxdev on 2017-01-25
Using freshly installed **Ubuntu Server 16.04.1 LTS** with a wired connection on business class internet.

Hello, I have set up a static IP address for my server to use and configured the connection in /etc/network/interfaces

```

auto enp3s0
iface enp3s0 inet static
address 10.1.10.198
gateway 10.1.10.1
netmask 255.255.255.0
dns-nameservers 75.75.75.75 75.75.76.76

```

The nameservers are as provided to me by my ISP and is set in my routers admin panel as manually assigned. I am able to ping my gateway, 8.8.8.8 and even [www.google.com]("http://www.google.com"). I am also able to run host [www.google.com]("http://www.google.com") or any other domain and it resolves properly. However, if I try to wget google.com or run apt-get update - nothing.

I have browsed a ton of threads and haven't been able to resolve my issue at all. Thank you.

---

### Post by TheFu on 2017-01-25
wget google.com? Trying to download the entire internet, eh? ;)

What exactly do you mean by " I am also able to run host [www.google.com](www.google.com) or any other domain " - I hope you can't run those. Only google should be running that domain. You should only run domains that you've paid for.

I'd start by trying different DNS servers.
Also, can you post the entire "**interfaces**" file and the output (using code tags) of **ifconfig**, and **route** please.

---

### Post by justincase2 on 2017-01-25
> **sushiboxdev said:**
> Using freshly installed **Ubuntu Server 16.04.1 LTS** with a wired connection on business class internet.

Hello, I have set up a static IP address for my server to use and configured the connection in /etc/network/interfaces

```

auto enp3s0
iface enp3s0 inet static
address 10.1.10.198
gateway 10.1.10.1
netmask 255.255.255.0
dns-nameservers 75.75.75.75 75.75.76.76

```

The nameservers are as provided to me by my ISP and is set in my routers admin panel as manually assigned. I am able to ping my gateway, 8.8.8.8 and even [www.google.com]("http://www.google.com"). I am also able to run host [www.google.com]("http://www.google.com") or any other domain and it resolves properly. However, if I try to wget google.com or run apt-get update - nothing.

I have browsed a ton of threads and haven't been able to resolve my issue at all. Thank you.
It wouldn't hurt to add the "network" in there.

```

auto [FONT=Verdana]enp3s0[/FONT]
iface [FONT=Verdana]enp3s0[/FONT] inet static
    address [FONT=Verdana]10.1.10.198[/FONT]
    netmask 255.255.255.0
    network [FONT=Verdana]10.1.10.0[/FONT]
    broadcast [FONT=Verdana]10.1.10[/FONT].255
    gateway 10.1.10.1
    dns-nameservers 75.75.75.75 75.75.76.76 8.8.8.8
    #dns-domain acme.com
    #dns-search acme.com

```

I'd probably run a "tracert www.google.com" to see if my own router or another upstream of me is choking.  If I thought it were a DNS-lookup problem I might run "nslookup www.google.com." to see if those Comcast DNS servers are reachable and doing their jobs.

---

### Post by TheFu on 2017-01-26
Don't put the static IP inside the DHCP range. That can cause issues.

'network' isn't needed and if it is incorrect there will be a conflict that may not be handled as you expect.
Same for 'broadcast'. Not needed. I haven't used them in about 15 yrs.  It is best those things are not added. 

tracert isn't a Unix command. nslookup has been deprecated for years.  Use **dig** and **traceroute**. There are probably **ip** versions of those commands, but I don't like the unformatted output from ip.

Those nameservers are provided by my ISP too (also on business-class with a /29), but I don't use them. 
My only real question about the file is whether the correct device is being used and where is the loopback device (very important for Unix systems). **sudo lshw -C network** will answer one of those.

My comcast connection has been down about half an hour this week. Wrote a little script to keep logs of it - with logs, Comcast never questions my availability statements.
```
$ internet-up-summary.sh 
 Period 20170122-062611  - 20170126-073611
  Total Time: 5832 (min) 97.20 (hrs)
  Percent Up Time: 99.38 % 
  Percent Down Time: 0.62 % 
  Total Down Time: 36 min or 0.60 hrs
 Currently: UP
```
Had an issue last summer with connectivity. They tested the coax, signal, then simply replaced the 10 yr old SMC router with a new Cisco. Been fine ever since.  I use their router as a bridge and manage my public static IPs on my router. However, I have a few devices using their NAT subnet (10.1.10.x) to keep it away from my stuff - a Roku, guest wifi and SIP-ATA.

---

### Post by sushiboxdev on 2017-01-26
So, I should have been more clear about the host command. I ran that actual command to see if I could resolve the domain name and see the IP addresses. Not trying to actually "host" a copy of Google. :P
[B]
cat /etc/network/interfaces
[/B]```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
inet lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
address 10.1.10.198
gateway 10.1.10.1
netmask 255.255.255.0
dns-nameservers 75.75.75.75 75.75.76.76

```

**route**
```

default     10.1.10.1     0.0.0.0     UG     0     0     0     en3ps0
10.1.10.0     *     255.255.255.0     U     0      0     0     en3ps0

```

I have tried both Google and OpenDNS nameservers and get the same result. **nslookup** does work for me. **ifconfig** does show both my enp3s0 and lo interfaces with the correct IP assigned to it. I ran **lshw -C network** and it showed my disabled wireless adapater and my ethernet interface (not disabled) - everything looks correct there. For what it is worth I set up in my router admin portal to assign that IP statically to this device. I also tried and address outside of the DHCP range and still the same result. :(

---

### Post by sushiboxdev on 2017-01-26
So, I just got it to work finally by disabling ipv6. Does anyone have any idea why this would work?

---

### Post by wildmanne39 on 2017-01-26
> **sushiboxdev said:**
> So, I just got it to work finally by disabling ipv6. Does anyone have any idea why this would work?

We always recommend setting IPV6 to ignore because it has never worked right in linux since it was introduced.

---

### Post by TheFu on 2017-01-26
I was joking about the wget. ;) However, testing websites that are full of javascript with a tool like wget probably doesn't do what you want.  I did this:
$ wget [http://www.google.com](http://www.google.com)
and it wrote a 10Kb index.html file full of javascript. Guess it is working for me.

We really need to see the commands, not an interpretation of those commands. Sometimes we all miss things in the output. You never know.

nslookup is still deprecated. It may be working fine or it might be lying. Use **dig**, which is maintained. Also, use traceroute to see where things are getting stuck. Once in a while, remote ISPs make poor route advertisements that impact far way users.

The rest of this is just guessing, things to try.

Check that there is an empty line at the end of all config files.  Sure, it shouldn't matter, but sometimes, with some tools, it does.
Comment out the 
```
source /etc/network/interfaces.d/*
``` line. I don't have it on any of my systems. Yes, it shouldn't be an issue, but ... 

If the issue is only with apt-get update - then we should work on that. Sometimes the mirrors aren't available. Sometimes ISPs (due to govt mandate) blocks certain web traffic. Just depends on your location/country.

You didn't mention it, but is there a VPN anywhere on this?
Do other systems on the same subnet work? 
Can they visit the ubuntu repos?  
What about in a web browser?
 Can you visit the repos that way? It is just http after all.

How solid are the connections that do work?  Is speedtest normal or with huge ups/downs during the run?

I've had ipv6 disabled forever. Don't use it myself and only found that it causes issues when all the equipment doesn't fully support it.

---

### Post by sushiboxdev on 2017-01-26
Everything seems to be working and blazing fast now that I have disabled ipv6. I am happy as long as I do not run into any issues.

Our office is located very close to Chicago in the US - so I don't think any government mandates are blocking web traffic.
There is no VPN anywhere on this.
Other systems work great, they can visit the ubuntu repos and web browsers are all good.
The connections (including my now working server) are all fast with over 150mbps on speed test.

Sorry for not typing over the whole output of those commands, I cannot copy and paste so it is a major chore while I am here at the office in-between tasks (I would have done that next if it wasn't working so well now).

---

### Post by TheFu on 2017-01-26
Whoa!  You typed that?  Not good.

Use redirection dude.  Also, setup ssh quick, so you can always remote in and have select/paste from a terminal.
Don't do things the hard way.

---

