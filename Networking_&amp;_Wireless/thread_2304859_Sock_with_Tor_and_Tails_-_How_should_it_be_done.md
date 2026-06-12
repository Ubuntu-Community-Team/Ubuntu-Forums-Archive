---
title: "Sock with Tor and Tails - How should it be done?"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by mail2toronionservi on 2015-11-30
Hi,
 
 Goal: Tor Browser -> Socks5 proxy
 OS: Tails
 
 For testing purposes I have chosen a socks proxy from here (e.g. 159.253.191.110:61111).
 
 I installed proxychains, then edited the config file:
 
     sudo apt-get update
     sudo apt-get install proxychains
     nano /etc/proxychains.conf
 
 There I added my proxy below the Tor prox
y:
 
     socks4 127.0.0.1 9050
     socks5 159.253.191.110 61111
 
 Now I wanted to run proxychains
 
     proxychains tor
 
 I was shown this  ...
 
 
ControlPort is open, but no authentication method has been
 
This means that any program on your computer can reconfigure your Tor.   
That's bad!  You should upgrade your Tor controller as soon as  
possible. Nov 30 18:33:23.480 [notice] Opening Socks listener on  
127.0.0.1:9050 Nov 30 18:33:23.480 [warn] Could not bind to  
127.0.0.1:9050: Address already in use. Is Tor already running? Nov 30  
18: 
33:23.480 [notice] Opening Socks listener on 127.0.0.1:9061 
Nov 30 18:33:23.480 [warn] Could not bind to 127.0.0.1:9061:  
Address already in use. Is Tor already running? 
Nov 30 18:33:23.480 [notice] Opening Socks listener on  
127.0.0.1:9062 
Nov 30 18:33:23.480 [warn] Could not bind to 127.0.0.1:9062:  
Address already in use. Is Tor already running? 
Nov 30 18:33:23.480 [notice] Opening Socks listener on 127.0.0.1:9150  
Nov 30 18:33:23.480 [warn] Could not bind to 127.0.0.1:9150: Address  
already in use. Is Tor already running 
#etc. 
 ... so I decided to 'sudo killall tor' and run 'proxychains tor' again:
 
 
root@amnesia:/home/amnesia# proxychains tor 
ProxyChains-3.1 ([http://proxychains.sf.net](http://proxychains.sf.net)) 
Nov 30 18:45:40.215 [notice] Tor v0.2.7.4-rc  
(git-6c4f0850146d706c)running  
on Linux with Libevent 2.0.19-stable, OpenSSL 1.0.1e and Zlib 1.2.7.  
Nov 30 18:45:40.215 [notice] Tor can't help you if you use it wrong!  
Learn how to be safe at [https://www.torproject.org/download](https://www.torproject.org/download) 
/download#warning  
Nov 30 18:45:40.215 [notice] Read configuration file "/etc/tor/torrc".  
Nov 30 18:45:40.218 [warn] ControlPort is open, but no authentication   
method  
has been configured.  This means that any program on your computer can   
reconfigure your Tor.  That's bad!  You should upgrade your Tor   
controller as soon as possible.  
Nov 30 18:45:40.218 [notice] Opening Socks listener on 127.0.0.1:9050  
Nov 30 18:45:40.218 [notice] Opening Socks listener on 127.0.0.1:9061  
Nov 30 18:45:40.218 [notice] Opening Socks listener on 127.0.0.1:9062  
Nov 30 18:45:40.218 [notice] Opening Socks listener on 127.0.0.1:9150  
Nov 30 18:45:40.219 [notice] Opening DNS listener on 127.0.0.1:5353  
Nov 30 18:45:40.219 [notice] Opening Transparent pf/netfilter listener on  
127.0.0.1:9040  
Nov 30 18:45:40.219 [notice] Opening Control listener on 127.0.0.1:9051  
Nov 30 18:45:40.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/g
eoip.  
Nov 30 18:45:40.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/g
eoip6.  
Nov 30 18:45:40.000 [warn] You are running Tor as root. You don't need to,  
and you probably shouldn't.  
|DNS-response|: amnesia is not exist  
|DNS-response|: amnesia is not exist  
|DNS-response|: amnesia is not exist  
Nov 30 18:45:40.000 [notice] Bootstrapped 0%: Starting     
Nov 30 18:45:41.000 [notice] Bootstrapped 5%: Connecting to server 
============================================================
   
T=1448909141  
(Sandbox) Caught a bad syscall attempt (syscall fcntl64)  
tor(+0x1587d9)[0xf764f7d9]  
/lib/i386-linux-gnu/libc.so.6(fcntl+0x36)[0xf61f8036]  
/lib/i386-linux-gnu/libc.so.6(fcntl+0x36)[0xf61f8036]  
/usr/lib/libproxychains.so.3(connect+0x1a3)[0xf65440f3]  
tor(+0xdfa69)[0xf75d6a69]  
root@amnesia:/home/amnesia#   
Obviously now Socks Listener is working, but how do I resolve the other things like "Caught a syscall attemp" 
 I am desperately trying to get this working and really would appreciate any help (the easier explained the better as I am starting with Tails).
 
 How do I get it done so that my socks adress is actually shown as ip?
 
 I am looking forward to your answers!

---

