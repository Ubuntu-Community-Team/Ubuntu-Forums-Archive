---
title: "My trouble with tunneling and tsocks because of bad local Internet"
date: 2013-11-14
forum: Networking &amp; Wireless
---

### Post by shestero on 2013-11-14
I have both practical and theoretical difficulties with tsocks (and with tunneling and socks proxy).


My geographically closest download mirrors (in different systems, including Unintu) are sometimes not working. This thing is quite annoying – I have to go to and download each package manually through my browser from different mirror (now I think about sourceforge).
Also sometimes some sites not reachable at all. Sometimes it's because ISP failures. Some sites are blocked by government... Recently I found that download.microsoft.com (taken as just example, but it was my real task to install something into Wine using winetricks) are totally unreachable. This perhaps it happened because of failures at local mirror (to which I redirected automatically through DNS).


I tried to solve the problem using HTTPTunnel ( [http://http-tunnel.sourceforge.net](http://http-tunnel.sourceforge.net) ). I install the server part into hosting I have (in another country) and run the tunnel_client.pl script on my PC. Then I configure konqueror to use socks proxy localhost:1080 and (great!) I am able to reach all what I need through this browser.


But still this isn't too handy sometimes, especially with such things as winetricks.
And I tried to make work wget or something also work through the tunnel.


I discovered that socks-proxy support was deleted in wget 1.9.
So I installed the tsocks and my questions began.
At first it doesn't work with SOCKS5, although HTTPTunnel 1.2.1 should support it (or am I wrong?). The output is:
libtsocks Need a password in tsocks.conf or $TSOCKS_PASSWORD to authenticate withfailed: Connection refused
(Meanwhile I use no password at local socks-proxy).
Ok, set the SOCKS v4 mode in /etc/tsocks.conf ... Seems thats all right... I open sites through tsocks lynx (text mode browser) and can see that the sites detect my location in the country of my hostings (so tunnel is working). I can also see the tunnel-client-log file grows. But! I still cannot download anything that I cannot download directly! Nor through tsocks wget, nor using tsocks curl, nor tsocks lynx. Why?
They just failed with timeout. I can see tunnel-client-log that they yet tried to use the tunnel.
For example through konqueror I can download the file:
[http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe](http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe)
But through tsocks lynx or wget I cannot!


Why so?
This is my question.


Also what I shell to do to use command-line tools such as wget through tunnel?


May be somebody can advice me something also than HTTPTunnel?


In fact I dream to wrap all my traffic into a secure tunnel.


PS Does qBittorent can download/upload through such tunnel?

---

### Post by Lars Noodén on 2013-11-15
If you use lynx or wget you usually set the environment variable *http_proxy* to point to the proxy.  lynx should work with a SOCKS proxy but not wget.  

I've used apt-get with regular proxies but not SOCKS.  Have you tried proxychain?

---

### Post by shestero on 2013-11-15
Than you for proxychains. I'll try. Can it provide a localhost HTTP-proxy working through SOCKS-proxy? (Or may be some another software?)


But what about tsocks? Why I cannot download file through it? 
I have an idea why that I haven't checked yet:
If I use tsocks through HTTPTunnel where domain names are resolved through DNS? On my PC locally (using direct connection) or at remote host where tunnel_server.pl are run?
I need them to resolve remotely!

---

### Post by Lars Noodén on 2013-11-16
I've only read of proxychains.  It will capture tcp output (maybe not udp) from a program and run it through a proxy, including a SOCKS proxy.  You'll have to read the instructions thoroughly.  But many of the examples include wget, like you are asking about.

---

### Post by shestero on 2013-11-25
It is clear about tsocks. It indeed don't resolve DNS: [https://trac.torproject.org/projects/tor/wiki/doc/SupportPrograms#AboutDNSandtsocks](https://trac.torproject.org/projects/tor/wiki/doc/SupportPrograms#AboutDNSandtsocks)
I downloaded the latest source tsocks-1.8beta5.tar.gz and configured it with --enable-hostnames option and now it seems to be working.

But the HTTPTunnel_v1.2.1 works bad. :-( The client side falls with messages like: Caught SIGPIPE - Restarting ...Server socket on port 1080: bind() failed: Address already in use
while downloading some files.
I'm sad about it, because for me it looks like very useful tool. Are there any other such tools allows tunneling having only web-script access on the server?

---

