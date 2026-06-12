---
title: "nginx fails to serve up web page for my web site"
date: 2022-06-25
forum: Networking &amp; Wireless
---

### Post by johnaaronrose on 2022-06-25
nginx fails to serve up web page for my web site. My web site ([https://rose.mywire.org](https://rose.mywire.org)) runs under nginx on my Xubuntu 20.04 server. ping fails to the server from another computer. I have the firewall ports 443 & 80 open on my Xubuntu server with my router's  port forwarding to the server's NAT ip address of the server. nginx status shows it's active. wget [http://roseserver.mywire.org](http://roseserver.mywire.org) hangs as shown below.

manager@Server:~$ wget [https://roseserver.mywire.org](https://roseserver.mywire.org)
--2022-06-23 17:14:23--  [https://roseserver.mywire.org/](https://roseserver.mywire.org/)
Resolving roseserver.mywire.org (roseserver.mywire.org)... 2.99.53.254
Connecting to roseserver.mywire.org (roseserver.mywire.org)|2.99.53.254|:443...

I have used LetsEncrypt to generate a certificate etc: certificate etc are valid on [https://www.ssllabs.com/ssltest/anal...ver.mywire.org]("https://www.ssllabs.com/ssltest/analyze.html?d=roseserver.mywire.org")
Ping to roseserver.mywire.org doesn't work, nor does ping to2.99.53.254  work. According to dynu.com, roseserver.mywire.org is Ok.
ddclient runs Ok for roseserver.mywire.org. 				 

ddclient.conf:
> 
# ddclient configuration for Dynu
#
# /etc/ddclient.conf
daemon=60                                                # Check every 60 seconds.
syslog=yes                                               # Log update msgs to syslog.
mail=root                                                # Mail all msgs to root.
mail-failure=root                                        # Mail failed update msgs to root.
pid=/var/run/ddclient.pid                                # Record PID in file.                                      
use=web, web=checkip.dynu.com/, web-skip='IP Address'    # Get ip from server.
server=api.dynu.com                                      # IP update server.
protocol=dyndns2                        
login=JohnRose                                           # Your username.
password=********                                        # Password or MD5/SHA256 of password.
roseserver.mywire.org                                    # List one or more hostnames one on each line.

PS I was not able to upload either roseserver.mywire.org or nginx.conf or ddclient.conf as this site's 'uploader' said that they are invalid files.

---

### Post by The Cog on 2022-06-25
```
$ curl  roseserver.mywire.org
Welcome to the Rose Server. This is the dummy index page.
```
This looks as though the certificate is OK to me. Perhaps wget is looking for some content that the served response doesn't contain?

---

