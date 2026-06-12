---
title: "[SOLVED] HELP Trying to connect to the internet ...."
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by cfynn on 2008-09-02
I've just downloaded UBUNTU from MS Windows & installed with no problem except I can't establish connection to the internet 

I connect to my ISP through an ethernet connection. This goes up to my roof & from there via a wireless device to my ISP and from there via a sattelite connection to the world.. 

In MS Windows all I have to do is enter my IP address (static), Subnet mask, and the IP address of default Gateway, and DNS servers under TCIP properties and I'm connected - simple as that.

I don't need a password or anything else to connect.

In UBUNTU I've entered the same addresses' in Network Settings under "Wired Connections" and "DNS" ~ but I cant connect properly to the internet. What else do I need to do?

When Update Manager tries to download packages I get message like failed to fetch ..... .deb Could not connect to ..... (113 no route to host)

In Firefox "Firefox can't establish a connection to the server at ..."

UBUNTU seems to recognize my card OK ~ I can even "see" a couple of other machines, obviously connected to the same ISP gateway, under "Network, Places" 

What else do I need to do???

Thanks 

- chris

---

### Post by pytheas22 on 2008-09-02
Please post the outputs of these commands:

In Ubuntu (from Applications>Accessories>Terminal):
```

cat /etc/network/interfaces
lshw -C Network
ifconfig
host google.com
```

In Windows (open up a command prompt by pressing windows key-R):

```
ipconfig /all
```

That should help us figure out the problem.

---

### Post by cfynn on 2008-09-02
> **pytheas22 said:**
> Please post the outputs of these commands:

In Ubuntu (from Applications>Accessories>Terminal):
```

cat /etc/network/interfaces
lshw -C Network
ifconfig
host google.com
```

In Windows (open up a command prompt by pressing windows key-R):

```
ipconfig /all
```

That should help us figure out the problem.



OK. Here are the results of those commands...

MS WINDOWS:

C:\>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : padma-2ai7rq
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connecti
on
        Physical Address. . . . . . . . . : 00-07-E9-93-AB-04
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 202.89.26.71
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 202.89.26.254
        DNS Servers . . . . . . . . . . . : 202.144.128.200
                                            202.89.26.9

UBUNTU:

chris@chris-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 202.89.26.71
netmask 255.255.255.0
gateway 202.89.26.254

auto eth0
chris@chris-desktop:~$ 
chris@chris-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:07:e9:93:ab:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=202.89.26.71 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:93:ab:04  
          inet addr:202.89.26.71  Bcast:202.89.26.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe93:ab04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4287 errors:418 dropped:0 overruns:0 frame:418
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:413636 (403.9 KB)  TX bytes:50931 (49.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96300 (94.0 KB)  TX bytes:96300 (94.0 KB)

chris@chris-desktop:~$ host google.com
google.com has address 64.233.167.99
google.com has address 64.233.187.99
google.com has address 72.14.207.99
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
chris@chris-desktop:~$ 



- Chris

---

### Post by pytheas22 on 2008-09-02
Well, you can resolve domain names (as indicated by the output of the "host" command), so you're connected to something.  Did you try using a different web browser?  Perhaps the issue lies with Firefox and not the connection in general, or maybe it's just a problem with the http port.  Did you modify the firewall settings at all (using 'iptables' from the command line or a GUI like Firestarter)?

What's the output of:
```

wget google.com
wget ubuntu.com
```

Also, see if you can ftp or ssh or vnc into a remote server.  If you don't have any servers to connect to, private-message me and I'll give you credentials to an ssh server.

---

### Post by cfynn on 2008-09-03
> **pytheas22 said:**
> Well, you can resolve domain names (as indicated by the output of the "host" command), so you're connected to something.  Did you try using a different web browser?  Perhaps the issue lies with Firefox and not the connection in general, or maybe it's just a problem with the http port.  Did you modify the firewall settings at all (using 'iptables' from the command line or a GUI like Firestarter)?

What's the output of:
```

wget google.com
wget ubuntu.com
```

Also, see if you can ftp or ssh or vnc into a remote server.  If you don't have any servers to connect to, private-message me and I'll give you credentials to an ssh server.

First, many thanksfor your help.

Here is what I get with wget & ftp :

```

chris@chris-desktop:~$ wget google.com
--12:22:07--  http://google.com/
           => `index.html'
Resolving google.com... failed: Name or service not known.
chris@chris-desktop:~$ wget ubuntu.com
--12:22:22--  http://ubuntu.com/
           => `index.html'
Resolving ubuntu.com... failed: Name or service not known.
chris@chris-desktop:~$ wget bt.net
--12:22:41--  http://bt.net/
           => `index.html'
Resolving bt.net... 193.113.211.125
Connecting to bt.net|193.113.211.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 115 [text/html]

100%[==============================================================================================================>] 115           --.--K/s             

12:22:43 (7.41 MB/s) - `index.html' saved [115/115]

chris@chris-desktop:~$ wget google.com
--12:23:25--  http://google.com/
           => `index.html.1'
Resolving google.com... failed: Name or service not known.
chris@chris-desktop:~$ wget ubuntu.net


chris@chris-desktop:~$ ftp ftp.ubuntu.com
ftp: ftp.ubuntu.com: Unknown host
ftp> exit
chris@chris-desktop:~$ ftp ftp.bt.net
Connected to ftp.bt.net.
220 ftp.bt.net FTP server ready.
Name (ftp.bt.net:chris): login
331 Password required for login.
Password:
530 Login incorrect.
Login failed.
ftp> exit
221 Goodbye.
chris@chris-desktop:~$ ftp 202.144.128.220
Connected to 202.144.128.220.
220 Welcome to DrukNet's FTP server; please log in using the ftp password and username provided by DrukNet, if you have any problem contact us at DrukNet.
Name (202.144.128.220:chris): 

chris@chris-desktop:~$ 
chris@chris-desktop:~$ wget ftp.druknet.bt
--12:36:25--  http://ftp.druknet.bt/
           => `index.html.1'
Resolving ftp.druknet.bt... 202.144.128.223
Connecting to ftp.druknet.bt|202.144.128.223|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [  <=>                                                                                                          ] 7,715         21.93K/s             

12:36:27 (21.93 KB/s) - `index.html.1' saved [7715]

chris@chris-desktop:~$ wget google.com
--12:36:50--  http://google.com/
           => `index.html.2'
Resolving google.com... failed: Name or service not known.
chris@chris-desktop:~$ wget pages.google.com
--12:37:06--  http://pages.google.com/
           => `index.html.2'
Resolving pages.google.com... failed: Name or service not known.
chris@chris-desktop:~$ 
chris@chris-desktop:~$


```

These things seem to *partly* work .... which seems puzzling.

> 
Perhaps the issue lies with Firefox and not the connection in general, or maybe it's just a problem with the http port.  


Maybe, but when Ubuntu tries to download some security updates this is not working either.
 
> 
Did you modify the firewall settings at all (using 'iptables' from the command line or a GUI like Firestarter)?


I haven't modified anything - and there is not much installed. This is a brand new install on a clean partition from an iso image I downloaded yesterday. Nothing added.

Don't know how to use iptables and it seems firestrter is not installed.

From MS Windows I get:

```


C:\>ping ubuntu.com

Pinging ubuntu.com [91.189.94.250] with 32 bytes of data:

Reply from 91.189.94.250: bytes=32 time=248ms TTL=52
Reply from 91.189.94.250: bytes=32 time=314ms TTL=52
Reply from 91.189.94.250: bytes=32 time=305ms TTL=52
Reply from 91.189.94.250: bytes=32 time=278ms TTL=52

Ping statistics for 91.189.94.250:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 248ms, Maximum = 314ms, Average = 286ms

C:\>ping google.com

Pinging google.com [64.233.187.99] with 32 bytes of data:

Reply from 64.233.187.99: bytes=32 time=401ms TTL=243
Reply from 64.233.187.99: bytes=32 time=351ms TTL=243
Reply from 64.233.187.99: bytes=32 time=355ms TTL=243
Reply from 64.233.187.99: bytes=32 time=379ms TTL=243

Ping statistics for 64.233.187.99:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 351ms, Maximum = 401ms, Average = 371ms

C:\>ftp ftp.ubuntu.com
Connected to ftp.ubuntu.com.
220 (vsFTPd 2.0.6)
User (ftp.ubuntu.com:(none)):
530 This FTP server is anonymous only.
Login failed.
ftp>


```

but pinging "google.com" and "ubuntu.com" from UBUNTU doesn't seem to work - though "google.net" & "ubuntu.net" do!!! : 

```

chris@chris-desktop:~$ 
chris@chris-desktop:~$ ping google.com
ping: unknown host google.com
chris@chris-desktop:~$ ping ubuntu.com
ping: unknown host ubuntu.com
chris@chris-desktop:~$ ping microsoft.com
ping: unknown host microsoft.com
chris@chris-desktop:~$ ping google.net
PING google.net (209.85.171.99) 56(84) bytes of data.
64 bytes from 209.85.171.99: icmp_seq=2 ttl=240 time=450 ms
64 bytes from 209.85.171.99: icmp_seq=3 ttl=240 time=398 ms
64 bytes from 209.85.171.99: icmp_seq=4 ttl=240 time=458 ms

[8]+  Stopped                 ping google.net
chris@chris-desktop:~$ ping ubuntu.net
PING ubuntu.net (91.189.94.249) 56(84) bytes of data.
64 bytes from 91.189.94.249: icmp_seq=1 ttl=51 time=232 ms
64 bytes from 91.189.94.249: icmp_seq=2 ttl=51 time=217 ms
64 bytes from 91.189.94.249: icmp_seq=3 ttl=51 time=241 ms

[9]+  Stopped                 ping ubuntu.net
chris@chris-desktop:~$ 

```

don't know anything about vnc or ssh

- Chris

---

### Post by pytheas22 on 2008-09-03
hmmm, there's some really strange stuff going on here.  It looks like you can't resolve .com domains, but .net and .bt seem to work fine.  To add to the confusion, yesterday you were able to resolve google.com ('host google.com') without a problem.

Because this looks like a DNS issue, please post the output of:
```

cat /etc/resolv.conf
host google.com
ping google.com
dig google.com
```

Perhaps your DNS servers in Ubuntu are configured incorrectly.

Also, do you get connected to anything if you put these addresses in your browser:
```

72.14.207.99
91.189.94.249
```

---

### Post by cfynn on 2008-09-03
> **pytheas22 said:**
> hmmm, there's some really strange stuff going on here.  It looks like you can't resolve .com domains, but .net and .bt seem to work fine.  To add to the confusion, yesterday you were able to resolve google.com ('host google.com') without a problem.

Because this looks like a DNS issue, please post the output of:
```

cat /etc/resolv.conf
host google.com
ping google.com
dig google.com
```

Perhaps your DNS servers in Ubuntu are configured incorrectly.



OK - here are the results of the commands above:
```

chris@chris-desktop:~$ cat /etc/resolv.conf
nameserver 202.144.128.200
nameserver 202.89.26.9

chris@chris-desktop:~$ host google.com
google.com has address 64.233.187.99
google.com has address 72.14.207.99
google.com has address 64.233.167.99
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.

chris@chris-desktop:~$ ping google.com
ping: unknown host google.com

chris@chris-desktop:~$ dig google.com

; <<>> DiG 9.4.2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53119
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 13, ADDITIONAL: 14
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;google.com.                    IN      A

;; AUTHORITY SECTION:
.			508897	IN	NS	D.ROOT-SERVERS.NET.
.			508897	IN	NS	J.ROOT-SERVERS.NET.
.			508897	IN	NS	L.ROOT-SERVERS.NET.
.			508897	IN	NS	E.ROOT-SERVERS.NET.
.			508897	IN	NS	I.ROOT-SERVERS.NET.
.			508897	IN	NS	F.ROOT-SERVERS.NET.
.			508897	IN	NS	H.ROOT-SERVERS.NET.
.			508897	IN	NS	C.ROOT-SERVERS.NET.
.			508897	IN	NS	M.ROOT-SERVERS.NET.
.			508897	IN	NS	A.ROOT-SERVERS.NET.
.			508897	IN	NS	G.ROOT-SERVERS.NET.
.			508897	IN	NS	K.ROOT-SERVERS.NET.
.			508897	IN	NS	B.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
A.ROOT-SERVERS.NET.	595297	IN	A	198.41.0.4
A.ROOT-SERVERS.NET.	595297	IN	AAAA	2001:503:ba3e::2:30
B.ROOT-SERVERS.NET.	595297	IN	A	192.228.79.201
C.ROOT-SERVERS.NET.	595297	IN	A	192.33.4.12
D.ROOT-SERVERS.NET.	595297	IN	A	128.8.10.90
E.ROOT-SERVERS.NET.	595297	IN	A	192.203.230.10
F.ROOT-SERVERS.NET.	595297	IN	A	192.5.5.241
F.ROOT-SERVERS.NET.	595297	IN	AAAA	2001:500:2f::f
G.ROOT-SERVERS.NET.	595297	IN	A	192.112.36.4
H.ROOT-SERVERS.NET.	595297	IN	A	128.63.2.53
H.ROOT-SERVERS.NET.	595297	IN	AAAA	2001:500:1::803f:235
I.ROOT-SERVERS.NET.	595297	IN	A	192.36.148.17
J.ROOT-SERVERS.NET.	595297	IN	A	192.58.128.30
J.ROOT-SERVERS.NET.	595297	IN	AAAA	2001:503:c27::2:30

;; Query time: 29 msec
;; SERVER: 202.144.128.200#53(202.144.128.200)
;; WHEN: Wed Sep  3 20:18:26 2008
;; MSG SIZE  rcvd: 511

chris@chris-desktop:~$ 

```

The DNS servers listed in /etc/resolv.conf are the same as I have in MS Windows.

I gather "google.com" is being resolved when "host" & "dig" commands are  used but not when "ping" command is used.

 
> **pytheas22 said:**
> 

Also, do you get connected to anything if you put these addresses in your browser:
```

72.14.207.99
91.189.94.249
```


O.K. The first address gives me what is apparently a simple Google search page. The address remains as a numeric IP address in Firefox address bar:

"http://72.14.207.99/"


However, when I type in the second address (91.189.94.249) it seems to get resolved and changed in the address bar to a name:

"http://www.canonical.com/"

But then Firefox only gives me a "page load error", "Address Not Found", "Firefox cannot find the server at www.canonical.com" etc. 

However when I type  the same 91.189.94.249 into Firefox under MS Windows using the same internet connection the address gets changed to [http://www.canonical.com/](http://www.canonical.com/)  and the canonical welcome page loads without an error.

All this seems extremely odd...

I guess there must be something going wrong somewhere in the communication between Ubuntu setup on my machine and the DNS server. 


- Chris

---

### Post by pytheas22 on 2008-09-03
Yes, it's very bizarre.  In the output above, you can resolve google.com without a problem (using both 'host' and 'dig') but you can't ping it.  I don't understand!

One possible thing to try is [to switch your DNS servers to opendns]("https://www.opendns.com/start?device=ubuntu").

If that doesn't help, you might want to contact your ISP and ask them if they have any idea what's going on.  Tell them you can resolve all hostnames, but you don't seem to be able to access any services (ping, ftp, http) on .com domains, even though .net and .bt work.  Even if your ISP doesn't want to support Linux, they should still be able to tell you something, because I think this is a DNS issue more than anything operating-system specific.

---

### Post by cfynn on 2008-09-03
> **pytheas22 said:**
> Yes, it's very bizarre.  In the output above, you can resolve google.com without a problem (using both 'host' and 'dig') but you can't ping it.  I don't understand!

One possible thing to try is [to switch your DNS servers to opendns]("https://www.opendns.com/start?device=ubuntu").

If that doesn't help, you might want to contact your ISP and ask them if they have any idea what's going on.  Tell them you can resolve all hostnames, but you don't seem to be able to access any services (ping, ftp, http) on .com domains, even though .net and .bt work.  Even if your ISP doesn't want to support Linux, they should still be able to tell you something, because I think this is a DNS issue more than anything operating-system specific.

OK Changing the DNS servers to OpenDNS (208.67.222.222  & 208.67.220.220)
worked. First I just added them to the other two in /etc/resolve.conf 
- that didn't work. But when I deleted the two listed before leaving only the OpenDNS ones that worked.

Anyway this reply is now coming from  my UBUNTU Linux installation :) not from MS Windows.

I'll inform my ISP as you suggest - they are a pretty small outfit with a VSAT dish, a few computers, a few dozen clients like me connecting through them, as well as some larger clients they install VSAT dishes for. 

I think they are just running Windows Server on a couple of small machines
to handle individual clients like me - and they may not  know how to fine tune DNS. 


BTW I decided I had to install Linux when I got some kind of nasty malware infecting the MBR  of my Windows computer and hiding itself away. This wasn't picked up by my anti-virus software, or several differernt root kit detectors, but was affecting the performance and stability of the machine. - Only after I had re-formatted my HD and re-installed Windows several times, (applying all the service packs and updates etc, each time) did I finally figure out what was going on and re-partitioned my hard drive and replaced the MBR. Since I was re-partitioning I thought "better install Linux as well" and start using that as much as possible. I was already using OpenOffice, Firefox and Inkscape  - and thirty years ago used unix and xenix - so no big deal. 

Unfortunately there are still a couple of software applications I rely on that don't yet have suitable OpenSource replacements. So I'll probably have to keep Windows installed to run them.

BTW I've contributed a couple of free Tibetan script fonts (Jomolhari & Tibetan Machine Uni) that are shipped w several different Linux distributions - though not it seems Ubuntu.

Anyway thanks once more for your invaluable help.

- Chris

---

### Post by pytheas22 on 2008-09-03
I'm glad OpenDNS did the trick.

Which Windows-only applications do you still need to run?  It may be possible to run them in wine or a virtual machine, so that you could wipe Windows completely.

---

