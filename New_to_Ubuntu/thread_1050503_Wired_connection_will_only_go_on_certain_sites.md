---
title: "Wired connection will only go on certain sites"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by stormtrooprdave on 2009-01-25
I have been using a wireless connection on Hardy and then Intrepid with no problems what so ever. I need to now use a wired connection but cannot get it to work. When I try to browse websites using the wired connection I can only access google sites such as picassa, google news, gmail, etc, but no other site will load. It just keeps loading.... for as long as I leave it.

I have tried all sorts of solutions on these forums but none have worked. I will outline what I have tried already below:

Added blacklist ipv6 to etc/modprobe.d/blacklist - no effect
Made adjustments to etc/ppp/options and the mtu level - no effect
Added my ISP's dns servers to resolv.conf - no effect
Added the lines auto eth0, iface eth0 inet dhcp to eth/network/interface - no effect (in fact it does not boot when I do this)
Also tried changing ifupdown:managed=false to true in /etc/NetworkManager/nm-system-settings.conf = no effect

The wired connection does have a connection then as it will browse google related pages with no problem, other pages hang indefinitely. It also will not access the router settings or my NAS drive. Wireless works perfectly. Wired also works perfectly on XP and Windows 7 Beta.

I;ve been searching a lot on these forums and have run out of ideas - please help!

results from ifconfig -

eth0 Link encap:Ethernet HWaddr 00:50:8d:98:57:25
inet addr:192.168.1.69 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::250:8dff:fe98:5725/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:459 errors:36 dropped:0 overruns:0 frame:36
TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:141928 (141.9 KB) TX bytes:53759 (53.7 KB)
Interrupt:19 Base address:0xdead

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1184 (1.1 KB) TX bytes:1184 (1.1 KB)

wlan0 Link encap:Ethernet HWaddr 00:17:3f:b1:a5:54
inet6 addr: fe80::217:3fff:feb1:a554/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:28 errors:0 dropped:0 overruns:0 frame:0
TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3395 (3.3 KB) TX bytes:5563 (5.5 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-17-3F-B1-A5-54-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by HermanAB on 2009-01-25
Hmm, looks like you have a DNS problem.

First test your DNS settings:
$ dig [www.yahoo.com](www.yahoo.com)

If it resolves, test port 80 (web) access to Yahoo:
$ telnet [www.yahoo.com](www.yahoo.com) 80

---

### Post by stormtrooprdave on 2009-01-27
dig [www.yahoo.com](www.yahoo.com)

; <<>> DiG 9.5.0-P2 <<>> [www.yahoo.com](www.yahoo.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12369
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 9, ADDITIONAL: 9

;; QUESTION SECTION:
;[www.yahoo.com](www.yahoo.com).			IN	A

;; ANSWER SECTION:
[www.yahoo.com](www.yahoo.com).		112	IN	CNAME	[www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
[www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net). 4	IN	A	87.248.113.14

;; AUTHORITY SECTION:
akadns.net.		113659	IN	NS	eur1.akadns.net.
akadns.net.		113659	IN	NS	use3.akadns.net.
akadns.net.		113659	IN	NS	use4.akadns.net.
akadns.net.		113659	IN	NS	usw2.akadns.net.
akadns.net.		113659	IN	NS	asia9.akadns.net.
akadns.net.		113659	IN	NS	za.akadns.org.
akadns.net.		113659	IN	NS	zb.akadns.org.
akadns.net.		113659	IN	NS	zc.akadns.org.
akadns.net.		113659	IN	NS	zd.akadns.org.

;; ADDITIONAL SECTION:
za.akadns.org.		2391	IN	A	195.219.3.169
zb.akadns.org.		2460	IN	A	12.183.125.5
zc.akadns.org.		1376	IN	A	124.211.40.4
zd.akadns.org.		2009	IN	A	204.2.178.133
eur1.akadns.net.	67719	IN	A	195.59.44.134
use3.akadns.net.	67719	IN	A	204.2.178.133
use4.akadns.net.	58504	IN	A	208.44.108.137
usw2.akadns.net.	64062	IN	A	12.183.125.5
asia9.akadns.net.	67719	IN	A	220.73.220.4

;; Query time: 36 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Tue Jan 27 17:40:46 2009
;; MSG SIZE  rcvd: 403

telnet [www.yahoo.com](www.yahoo.com) 80
Trying 87.248.113.14...
Connected to [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
Escape character is '^]'.

I have no idea what any of this means lol

---

### Post by stormtrooprdave on 2009-02-01
bump

---

### Post by HermanAB on 2009-02-01
The two tests that you have done show that your network access works properly.

Your DNS works:
 ANSWER: 2
 Query time: 36 msec

and your web access works too:
 Connected to [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
 Escape character is '^]

So if you would use a web browser like firefox and type [www.yahoo.com](www.yahoo.com) in the address box, then it should work.

If you still have a real problem, then the issue is something else, not the network settings, because that has been proven to work.

Cheers,

Herman

---

### Post by stormtrooprdave on 2009-02-05
can anyone help on this or suggest something I can try?

---

### Post by HermanAB on 2009-02-05
You proved that your networking works.  Use another browser.

Cheers,

Herman

---

### Post by stormtrooprdave on 2009-02-06
> **HermanAB said:**
> You proved that your networking works.  Use another browser.

Cheers,

Herman
It's not a browser issue.  I've already tried it with Opera and Konqueror, and also update manager, synaptic, pidgin, etc will not connect.  It is a networking issue.

---

### Post by HermanAB on 2009-02-06
Use telnet to connect to my simple web site:

$ telnet aeronetworks.ca 80
get index.html  (you got to type that 'blind', don't make a mistake)

If you get html scrolling over the screen then the network works properly and the problem lies somewhere else.

Cheers,

Herman

---

### Post by newbee70 on 2009-02-06
> **stormtrooprdave said:**
> can anyone help on this or suggest something I can try?

Have you tried to completely remove and purge your browser and then reloading it from scratch.

---

### Post by HermanAB on 2009-02-06
Do you have a default route pointing to the gateway of your ISP?

Check it with the route command (it may take a while to come back with a complete list):

$ sudo route

It should show a 'gw' entry with the IP address of your ISP gateway.

If not, then you can manually add it with something like:
$ sudo route add default gw w.x.y.z


Cheers,

Herman

---

### Post by stormtrooprdave on 2009-02-08
sudo route has the name of my router as the default so I presume thats that is correct.

Funnily enough I just tried the livecd of jaunty alpha 4 and it has exactly the same issue.  It must be a hardware issue.

---

