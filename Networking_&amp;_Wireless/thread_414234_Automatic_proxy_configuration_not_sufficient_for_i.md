---
title: "Automatic proxy configuration not sufficient for internet access."
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by fredbaluga on 2007-04-19
I am trying to get internet access (for ubuntu 7.04) through my university network.

Their support pages do not fill me with hope:
> We do not support GNU/Linux and we can only provide you with an IP address and the information you need to configure your PC to access the web via our cache.

So I add the proxy address to the network proxy dealie in preferences, and to firefox connection settings... to no avail.

I have been in this situation before, when giving 6.06 a try out (6.10 never managed to install without crashing - I must have used about 10 disks with various forms of the OS). I did essentially the same thing and managed to get online long enough to search for "easy ubuntu". I received a page of results to my query, and that was the last time I ever saw the internet work when not using Windows.

They have changed the proxy since then, it now being [http://wwwcache.nottingham.ac.uk/proxyall.pac](http://wwwcache.nottingham.ac.uk/proxyall.pac) although the old one ( [http://wwwcache.nottingham.ac.uk/proxy.pac](http://wwwcache.nottingham.ac.uk/proxy.pac) ) still works for Opera (and, I assume, my other browsers) in Windows.

When installing this version it hanged at the 'checking mirrors' stage (at 82% completion of installation) and I only got it to actually install by not having the network cable plugged in when starting up the computer.

I don't need to input any usernames or passwords to get online in Windows, it justs insists I have Avast and AdAware (or equivalents thereof) and checks for their presence sporadically (after quarantining the section of the network in which I reside).

Before I go off and trawl this forum for responses to other people's similar (i.e. identical) questions (I apologise for my laziness - it's late, and tomorrow I have 9 hours of pipetting small amounts of DNA into small tubes), I would like to know if it worth trying to get ubuntu functioning on a network that clearly doesn't want me there.

Should I delay my adventures with non-stolen operating systems until next year when I am thrust into the world of council tax paying post-graduates?

Thanks in advance

---

### Post by Austin_KW on 2007-04-19
Are you on the LAN, do you have a  valid address

> So I add the proxy address to the network proxy dealie in preferences
What network dealie, & where

---

### Post by fredbaluga on 2007-04-21
> Are you on the LAN, do you have a valid address

I am allowed on the lan using xp.

It does detect the network, although that little network icon in the tray occasionallytells me
it has disconnected, and then reconnects in less than a minute without any input from me.

The proxy address I use is the same one i use successfully when using web browsers
in xp,and their "support" pages don't give any alternate addresses to use.

> What network dealie, & where

 system > preferences > network proxy

---

### Post by Austin_KW on 2007-04-21
You first need to see if you are connected to the LAN. Getting on the LAN should not need any proxy configuration.

Open a terminal and type the command "ifconfig"
Also if you are connecting with wireless what is the output from "iwconfig"


If you are on the LAN (ifconfig will show a valid IP address) then it might we worth looking at the proxy config file.  If you enter the URL for the pac file into your browser it should download it, it should just be a text file so you can read it in an editor. 

From what I remember these are just a single java function telling your browser what proxy to use for a given address. But it is code so it could do anything. So look at the code and see if there are any windows specific code or checks. If there is you can probably make a local copy and modify it or just hand configure to use the proxy's. 
I cannot look at it because I am outside you network and the external versions will just say not to use a proxy.

---

### Post by fredbaluga on 2007-04-24
> Open a terminal and type the command "ifconfig"
eth0      
Link encap:Ethernet  HWaddr 00:13:8F:48:7F:AF  
inet addr:10.3.49.93  Bcast:10.255.255.255  Mask:255.0.0.0
inet6 addr: fe80::213:8fff:fe48:7faf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:39 errors:0 dropped:0 overruns:0 frame:0
TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:7228 (7.0 KiB)  TX bytes:6466 (6.3 KiB)
Interrupt:22 Base address:0xdead 

lo        
Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

> If you are on the LAN (ifconfig will show a valid IP address)
Trying to access 10.3.49.93 the browser times out, but to be honest the internet connection I have is iffy at best, so sometimes it does that trying to access anything I havent already cached.

> If you enter the URL for the pac file into your browser it should download it, it should just be a text file so you can read it in an editor.

[http://wwwcache.nottingham.ac.uk/proxyall.pac](http://wwwcache.nottingham.ac.uk/proxyall.pac) (the current proxy):
function FindProxyForURL(url,host){ if (dnsDomainIs(host,'windowsupdate.microsoft.com')||dnsDomainIs(host,'.unim.nottingham.ac.uk')) return 'PROXY 128.243.220.20:3128'; if (isPlainHostName(host)||dnsDomainIs(host,'.nottingham.ac.uk')||dnsDomainIs(host,'.nott.ac.uk')) return 'DIRECT'; return 'PROXY 128.243.220.20:3128';}

[http://wwwcache.nottingham.ac.uk/proxy.pac](http://wwwcache.nottingham.ac.uk/proxy.pac) (the old proxy, still works though, did work very briefly in 6.06):
function FindProxyForURL(url, host){ if ( dnsDomainIs(host, "windowsupdate.microsoft.com") ) return "PROXY 128.243.220.20:3128"; if ( dnsDomainIs(host, ".unim.nottingham.ac.uk") ) return "PROXY 128.243.220.20:3128"; if ( localHostOrDomainIs(host, "www.2heads.nottingham.ac.uk") ) return "PROXY 128.243.220.20:3128"; if ( isPlainHostName(host) || dnsDomainIs(host, ".nottingham.ac.uk") || url.substring(0,6) == "https:" || dnsDomainIs(host, ".nott.ac.uk") || isInNet(host,"127.0.0.1","255.255.255.255")) return "DIRECT"; else return "PROXY 128.243.220.20:3128"; }

These will make more sense to you than they do to me, so if anything stands out don't hesistate to mention it.

Sorry for the delay between posts, i'm not getting much free time at the moment.

---

### Post by Austin_KW on 2007-04-24
10.3.49.93 is your PC's address. You are on the LAN. Trying to access 10.3.49.93 in a browser will not respond unless you are running a web server.

The pac file says 
use the proxy 128.243.220.20:3128
unless it https or local address. Exceptions (use proxy for unim.nottingham.ac.uk or  [www.2heads.nottingham.ac.uk](www.2heads.nottingham.ac.uk))

I am no expert but I don't see anything here that would prevent internet access on linux.
The only thing is that the java code depends on being able to look-up dns. So mabe that is the problem.

Things to try,
Just set the proxy ([http://wwwcache.nottingham.ac.uk/proxy.pac](http://wwwcache.nottingham.ac.uk/proxy.pac)) in firefox and remove it from system > preferences > network proxy in case it is preventing you getting to the dns server

You could also try just manually setting the firefox proxy;  to proxy everything to  128.243.220.20:3128 in case you have somehow disabled javascript in firefox

Failing that; what is the output from the following commands
 route
cat /etc/resolv.conf
dig google.com
ping -c 3 google.com
ping -c 3 64.233.167.99
cat /etc/network/interfaces

---

### Post by fredbaluga on 2007-05-06
> Just set the proxy ([http://wwwcache.nottingham.ac.uk/proxy.pac](http://wwwcache.nottingham.ac.uk/proxy.pac)) in firefox and remove it from system > preferences > network proxy in case it is preventing you getting to the dns server

No change.

> You could also try just manually setting the firefox proxy; to proxy everything to 128.243.220.20:3128 in case you have somehow disabled javascript in firefox

Again, no change (firefox had javascript enabled).

> Failing that; what is the output from the following commands

I did these with system > preferences > network proxy set to [http://wwwcache.nottingham.ac.uk/proxyall.pac](http://wwwcache.nottingham.ac.uk/proxyall.pac)

> route 
Kernel IP routeing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0 
default         10.3.1.1        0.0.0.0         UG    0      0        0 eth0 

> cat /etc/resolv.conf
# generated by NetworkManager, do not edit! 

search sns.nottingham.ac.uk 


nameserver 128.243.40.193 
nameserver 128.243.40.192 

> dig google.com
; <<>> DiG 9.3.4 <<>> google.com 
;; global options:  printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18812 
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 4, ADDITIONAL: 4 

;; QUESTION SECTION: 
;google.com.                    IN      A 

;; ANSWER SECTION: 
google.com.             288     IN      A       72.14.207.99 
google.com.             288     IN      A       64.233.167.99 
google.com.             288     IN      A       64.233.187.99 

;; AUTHORITY SECTION: 
google.com.             27110   IN      NS      ns4.google.com. 
google.com.             27110   IN      NS      ns1.google.com. 
google.com.             27110   IN      NS      ns2.google.com. 
google.com.             27110   IN      NS      ns3.google.com. 

;; ADDITIONAL SECTION: 
ns1.google.com.         340316  IN      A       216.239.32.10 
ns2.google.com.         325970  IN      A       216.239.34.10 
ns3.google.com.         340316  IN      A       216.239.36.10 
ns4.google.com.         340316  IN      A       216.239.38.10 

;; Query time: 3 msec 
;; SERVER: 128.243.40.193#53(128.243.40.193) 
;; WHEN: Sun May  6 16:34:19 2007 
;; MSG SIZE  rcvd: 212 

> ping -c 3 google.com
PING google.com (64.233.167.99) 56(84) bytes of data. 
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=239 time=146 ms 
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=239 time=134 ms 
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=239 time=105 ms 

--- google.com ping statistics --- 
3 packets transmitted, 3 received, 0% packet loss, time 2003ms 
rtt min/avg/max/mdev = 105.231/128.648/146.642/17.337 ms 

> ping -c 3 64.233.167.99 
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data. 
64 bytes from 64.233.167.99: icmp_seq=1 ttl=239 time=107 ms 
64 bytes from 64.233.167.99: icmp_seq=2 ttl=239 time=105 ms 
64 bytes from 64.233.167.99: icmp_seq=3 ttl=239 time=102 ms 

--- 64.233.167.99 ping statistics --- 
3 packets transmitted, 3 received, 0% packet loss, time 2000ms 
rtt min/avg/max/mdev = 102.353/105.220/107.941/2.314 ms 

> cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp

---

### Post by Austin_KW on 2007-05-06
I dont see what is wrong here. You can get to the internet, and your dns is working. But your proxy is not working. 
It is possible the the proxy is checking the http request and to verify the OS version and service packs. Some browsers allow you to pretend to be a different browser on a different OS. I dont remember if firefox allows this. I think conquer (part of kde) and the opera browser allow you to set this. That is the only thing that I can think of, as everything else looks good.

---

