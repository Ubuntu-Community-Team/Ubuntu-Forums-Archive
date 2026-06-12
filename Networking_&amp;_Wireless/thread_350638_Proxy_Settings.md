---
title: "Proxy Settings"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by pride_chang on 2007-01-31
Hi there !
My Network Admins use ISA SERVER, it's like SQUID. It provides us with internet.
My local IP is 10.0.0.204 and Server IP is 10.0.0.1
For HTTP proxy, 8080 port is used.
And for Socks4, they use 1080.
They don't have Socks5 proxy.

Now, in Windows, I set my Firefox to HTTP proxy, 10.0.0.1;8080.
And for MSN, YAHOO I use Socks4 proxy, 10.0.0.1:1080.
It works, and for other applications those which don't have support for usable of Proxies, I use ISA Firewall Client, it's like a small application resides in Tray, it provides internet to these apps, even it can provide to Firefox, if I tick "I am using Direct connection".
This ISA Client is also provided with ISA Server.
Those applications which have Proxy support, I use them with Socks4 10.0.0.1:1080 in Windows.

I searched on Net for ISA Client for Linux, nothing found.
So I thought Proxy woud do the trick.
I went to
Main Menu>System>Preferences>Network Proxy
And wrote 10.0.0.1 and desired ports.

Now I can run Synaptic Package Manager, it runs well, downloads packages. 
I can run "wget", it also runs.
But other applications don't run. like FTP, TELNET, even applications with GUI.
I tried GAIM, and set options to "USE ENVIROMENT SETTINGS" for proxy, then I tried writing my own, like USE HTTP PROXY 10.0.0.1:8080
Didn't run at all :(

Now many of applications don't run, like CVS :(

Any tips, hints ?
Firefox runs well, as I set it to 10.0.0.1:8080, like I do in Windows.

---

### Post by pride_chang on 2007-02-04
**No reply** :s

---

### Post by pride_chang on 2007-02-13
Hello ? Anyone ?
Please help !!!!!!!!!

---

### Post by koenn on 2007-02-14
try putting them through Socks

---

### Post by pride_chang on 2007-02-14
I tried to use SOCKS4(10.0.0.1:1080) in GAIM, here's the output in Debug Window


dns: Successfully sent DNS request to child 5243
dns: Got response for '10.0.0.1'
socks4 proxy: Connecting to scs.msg.yahoo.com:5050 via 10.0.0.1:1080 using SOCKS4
socks4 proxy: Connect would have blocked.
socks4 proxy: Connected.
account: Disconnecting account 0x81c9858
connection: Disconnecting connection 0x84f8848

---

### Post by pride_chang on 2007-02-14
And when I tried HTTP Proxy in Gaim, Server:10.0.0.1 and port : 8080 the same I use in Firefox. The debug windows showed

http proxy: Connecting to scs.msg.yahoo.com:5050 via 10.0.0.1:8080 using HTTP
http proxy: Connect would have blocked.
http proxy: Connected.
proxy: using CONNECT tunnelling for scs.msg.yahoo.com:5050
proxy: Proxy server replied with:
HTTP/1.1 502 Proxy Error ( The specified Secure Sockets Layer (SSL) port is not allowed. ISA Server is not configured to allow SSL requests from this port. Most Web browsers use port 443 for SSL requests.  )

Via:1.1 SERVER

Connection: close

Proxy-Connection: close

Pragma: no-cache

Cache-Control: no-cache

Content-Type: text/html

Content-Length: 3814  
account: Disconnecting account 0x81c9858
connection: Disconnecting connection 0x84f0178
connection: Destroying connection 0x84f0178


---------------------
HTTP/1.1 502 Proxy Error ( The specified Secure Sockets Layer (SSL) port is not allowed. ISA Server is not configured to allow SSL requests from this port. Most Web browsers use port 443 for SSL requests.  )

I tried to use 10.0.0.1 and port to 443, when I do this, my GAIM completely hangs. :(
Please help me !

---

### Post by pride_chang on 2007-02-19
Please Help !!!!!!!!!!!!!!!! :(

---

### Post by colonelk on 2007-02-19
Try this

[http://www.faqs.org/docs/Linux-HOWTO/Web-Browsing-Behind-ISA-Server-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Web-Browsing-Behind-ISA-Server-HOWTO.html)

---

### Post by pride_chang on 2007-02-20
I tried that, that "NTLM Authorization Proxy Server". But doesn't work. My ISA Server doesn't use any kind of Authentication.

---

