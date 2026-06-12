---
title: "[SOLVED] Cannot connect to internet but can ping"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by htmlland on 2008-11-20
Hello all,

I have a small home network and for this I built my own server running ubuntu server edition (8.04). Computers can connect to the internet though the server so it works perfectly as a router and firewall. However when the server itself trys to connect to the internet it fails. The firewall is set to allow any connection from lo.

I can ping google.com and its IP version with 100% success but then if i try to wget a webpage or apt-get install/update it just timesout connecting.

Any ideas/suggestions would be excellent.

Michael

---

### Post by htmlland on 2008-11-20
Here is my output to ifconfig if it helps:
```

root@server:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:b0:c2:02:54:24  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2b0:c2ff:fe02:5424/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7404929 (7.0 MB)  TX bytes:201667834 (192.3 MB)
          Interrupt:20 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1f:d0:5b:59:37  
          inet addr:82.**.***.**  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::***:****:****:5937/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:204414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204767970 (195.2 MB)  TX bytes:7007924 (6.6 MB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5077 (4.9 KB)  TX bytes:5077 (4.9 KB)

```
BTW I have starred out my external IP address' it wasn't what it output!

---

### Post by superprash2003 on 2008-11-20
post output of cat /etc/resolv.conf .. also open firefox and instead of typing google.com type 64.233.187.99 .. does the google page open?

---

### Post by htmlland on 2008-11-20
```
root@server:/# cat /etc/resolv.conf
nameserver 194.168.4.100
nameserver 194.168.8.100

```

plus [http://64.233.187.99](http://64.233.187.99) works in ff on a client that connects through the server but the server does not have ff as its terminal based :(

---

### Post by lintoolman on 2008-11-20
Check to see if your default gateway is on the correct interface.

---

### Post by htmlland on 2008-11-20
> **lintoolman said:**
> Check to see if your default gateway is on the correct interface.

how would i do this?

Ihave had a look at my webmin config and I do not have a router (i.e gateway) set. When i tryed to set it to 192.168.1.2 (itself) eth0 (the internal network) then it looped and crashed the networking :(

---

### Post by lintoolman on 2008-11-20
I don't have access to an Linux box at the moment, but I believe the command is "route."  It may require a switch.

---

### Post by htmlland on 2008-11-20
I also have apache set up on another linux machine within the inner network so i thought i would try wgeting that and it worked but it did take a while waiting on the "*Connecting to 192.168.1.50:80*" part; since they are physicly 3 feet away from each other its a bit worrying.

```
root@server:/# wget 192.168.1.50
--19:27:01--  http://192.168.1.50/
           => `index.html.1'
Connecting to 192.168.1.50:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3 [text/html]

100%[=================================================================================================>] 3             --.--K/s             

19:27:06 (478.32 KB/s) - `index.html.1' saved [3/3]

```

---

### Post by htmlland on 2008-11-20
> **lintoolman said:**
> I don't have access to an Linux box at the moment, but I believe the command is "route."  It may require a switch.

I did see something on another webiste while i was googling the problem:

> Your machine is not by any chance configured as firewall?

What happens if you add the route for your loopback back into the routing table? (because without it, it won't use the loopback interface but the default route). from [http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1227208032262+28353475&threadId=342829](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1227208032262+28353475&threadId=342829).

It made no sense to me so if anyone has any ideas I will give that a shot :)

---

### Post by htmlland on 2008-11-29
Sorry for "bumping" this topic up but I was wondering if anyone has any ideas what this means:

> Your machine is not by any chance configured as firewall?

What happens if you add the route for your loopback back into the routing table? (because without it, it won't use the loopback interface but the default route).

Without this problem fixed I have no way to install/upgrade my server making it useless!

Any help really appreciated
Michael

---

### Post by htmlland on 2008-12-03
Anyone with any ideas!? Just to outline the problem and known things:
[LIST]
[*]Can ping localhost / 127.0.0.1 and 192.168.1.2 (itself)
[*]Can wget the same above list
[*]Can ping google.com and ubuntu.com etc.
[*]CANNOT wget google.com
[*]CANNOT use the apt-get tool as it will not connect
[*]CANNOT access [ftp://ftp.gimp.org](ftp://ftp.gimp.org) using ftp
[/LIST]

The server is the gateway/router/firewall for a small network who can all access the internet/server fully.

Michael

---

### Post by lintoolman on 2008-12-04
Have you checked to see if there are any helpful messages in the logs (/var/log/messages)?

Not that this should matter, but have you uninstalled apparmour?  I'm not sure what all needs to be removed.  Sometimes this program get's in the way of troubleshooting or is the cause of the issue.

---

### Post by jonobr on 2008-12-04
have you tried doing an nslookup of your sites,
google.com pingplotter.com etc


when you do w3m google.com from a terminal what do you get,

does your /etc/hosts file have any entries which may be monkeying around with your name resolution?

when you cat /etc/nsswitch.conf what results does it give for hosts 
does it have dns it in there?
It should by default.

Failing all that you are going to have to get some network sniffer running 
(wireshark or tcpdump) to see whats up with your traffic

---

### Post by htmlland on 2008-12-06
Hey guys thanks for the help,

Firstly:
> Not that this should matter, but have you uninstalled apparmour? I'm not sure what all needs to be removed. Sometimes this program get's in the way of troubleshooting or is the cause of the issue. I dont belive i have it installed in the first place :(

As for looking in /var/log/messages it only shows information reguarding the DHCP software nothing out of the ordinary

When i do w3m google.com in terminal it jsut comes up with "Opening socket..." and then just sits there waiting

/etc/hosts contains:
> michael@server:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/nsswitch.conf:
> michael@server:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:	files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
which contains the "dns" bit under hosts i belive you were talking about.

> Failing all that you are going to have to get some network sniffer running
(wireshark or tcpdump) to see whats up with your traffic ill have a look at these and get back to you.

Thanks,
Michael

---

### Post by htmlland on 2008-12-06
after 2 seconds of running tcpdump -i eth1 (the device connected to the internet) while apt-get install was trying to connect showed no lines relating to the ubuntu servers. I carnt post the output as its too much to post :). I also redid this experiment with tcpdump -i lo and nothing came up.

Michael

---

### Post by nickdbliss on 2008-12-06
Try disabling IPv6. It might be causing the problem. 
gksudo gedit /etc/modprobe.d/aliases

Change the following line:

alias net-pf-10 ipv6
to
alias net-pf-10 off

Then reboot.

Validate with
lsmod | grep v6
Should return nothing

Hope it solves the issue.

---

### Post by htmlland on 2008-12-07
Ok have made the changes but cannot kill the server just yet (they might not be too happy with me); will restart it when i can and get back to you with the results :)

Thanks,
Michael

---

### Post by htmlland on 2008-12-07
Turns out noone was on the internet at the time :P; I changed the config and the output of
> root@server:/# lsmod | grep v6
root@server:/# 

Did change from something to nothing but the problem still remains; thanks anyway :).

---

### Post by htmlland on 2008-12-27
Really do not like to "bump" my post back up again but the problem still continues! I can now install .deb files by downloading them on another computer, copying them over and dpkg'ing them but I really need my computer to be able to "talk" to the internet as I have PHP scripts and other software that need the internet! I think the problem is either the firewall or a DNS problem. I have managed to install traceroute if that will help diagnose.

I will try anything to help diagnose the problem :)

Thanks,
Michael

---

### Post by htmlland on 2008-12-27
I dont belive that the problem is a DNS one now as traceroute just worked perfectly.

```
michael@server:~$ traceroute google.com
traceroute to google.com (74.125.45.100), 30 hops max, 40 byte packets
 1  10.57.128.1 (10.57.128.1)  11.988 ms  12.042 ms  14.079 ms  <--- This is the modem for my internet provider

..... after many routers around the world ...

12  209.85.253.145 (209.85.253.145)  126.943 ms  97.514 ms 209.85.253.137 (209.85.253.137)  105.849 ms
13  yx-in-f100.google.com (74.125.45.100)  105.740 ms  98.524 ms  104.343 ms

```

Now im even more puzzled! Its making me think more now that its a firewall issue even though i have allowed all INPUT from LO :confused:

---

### Post by lintoolman on 2008-12-29
Are you allowing "established" and "related" connections on the appropriate chain?

---

### Post by rjmatthews62 on 2008-12-29
I've been chasing this problem myself, and it's quite a common one.

It's almost certainly DNS related.

First, how are you connected to the internet? Through a router?

There seems to be a bug in 8.10 in talking to a nameserver on a local network.
If you manually edited /etc/resolv.conf and add the line:
nameserver *your isps nameserver*

then try again.
Warning: NetworkManager will overwrite this next time you boot, but it might get you going. If you make resolv.conf read only, this will stop nm from taking over.

The try running "host", "dig", "nslookup" or "dnsget" to confirm your dns is actually running.
If you run host with the -v parameter and post the results here, this will help confirm.

ie:
host -v google.com

also, you can monitor just the dns requests using:
sudo tcpdump -i eth1 -X -vvv -n -l port 53

---

### Post by rjmatthews62 on 2008-12-29
> **htmlland said:**
> I dont belive that the problem is a DNS one now as traceroute just worked perfectly.Now im even more puzzled! Its making me think more now that its a firewall issue even though i have allowed all INPUT from LO :confused:

Still not ruling out DNS issue I previously mentioned, as it *sometimes works anyway*... just to be even more annoying.

---

### Post by htmlland on 2009-01-01
My setup is something like this:
(Internal Network)  -- (My Server) -- (Virgin Media Modem Box) -- (The Internet). Its the server with the problem every computer within the internal network can access the network!

> There seems to be a bug in 8.10 in talking to a nameserver on a local network.
If you manually edited /etc/resolv.conf and add the line:
nameserver your isps nameserver
Output of "cat /etc/resolv.conf"
```
nameserver 194.168.4.100
nameserver 194.168.8.100
```
These seem to be the right DNS servers for virgin media already set.

> The try running "host", "dig", "nslookup" or "dnsget" to confirm your dns is actually running.
If you run host with the -v parameter and post the results here, this will help confirm.

ie:
host -v google.com

Output of "host -v google.com:"
```
michael@server:~$ host -v google.com
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64387
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		137	IN	A	72.14.205.100
google.com.		137	IN	A	74.125.45.100
google.com.		137	IN	A	209.85.171.100

Received 76 bytes from 194.168.4.100#53 in 8 ms
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50001
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	AAAA

;; AUTHORITY SECTION:
google.com.		300	IN	SOA	ns1.google.com. dns-admin.google.com. 2008122201 7200 1800 1209600 300

Received 78 bytes from 194.168.4.100#53 in 8 ms
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17976
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.			IN	MX

;; ANSWER SECTION:
google.com.		623	IN	MX	10 smtp4.google.com.
google.com.		623	IN	MX	10 smtp1.google.com.
google.com.		623	IN	MX	10 smtp2.google.com.
google.com.		623	IN	MX	10 smtp3.google.com.

;; ADDITIONAL SECTION:
smtp1.google.com.	1836	IN	A	209.85.237.25
smtp2.google.com.	2069	IN	A	64.233.165.25
smtp3.google.com.	26	IN	A	64.233.183.25
smtp4.google.com.	1952	IN	A	72.14.221.25

Received 180 bytes from 194.168.4.100#53 in 7 ms

```

> Are you allowing "established" and "related" connections on the appropriate chain?
Not sure what chain you mean but all except for input on the external nic are set to accept always.

The external rule is like this:
If protocol is TCP and input interface is eth1 and destination port is not 80 		
Accept 	If input interface is lo

---

### Post by rjmatthews62 on 2009-01-01
That does look OK...
I have seen that there are sometimes issues with ipv6, you might try disabling that.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by htmlland on 2009-01-01
Yep already been suggested 
> 
Try disabling IPv6. It might be causing the problem.
gksudo gedit /etc/modprobe.d/aliases

Change the following line:

alias net-pf-10 ipv6
to
alias net-pf-10 off


Made no diffrence :p.

thanks for you help so far anyway :)

---

### Post by rjmatthews62 on 2009-01-01
> **htmlland said:**
> Yep already been suggested 


Made no diffrence :p.

thanks for you help so far anyway :)

Poot. 

Tell you what might give some useful results:
```
sudo tcpdump -i eth1 -vvv -n port 80
```

And then try wget to see what happens. You *should* see activity both ways... if not, it might give us a clue...

---

### Post by htmlland on 2009-01-01
I should be the only one using the internet at this time at night so what I get should be me.
I have two terminals open both ssh to my server:

On one terminal I used ```
sudo tcpdump -i eth1 -vvv -n port 80
``` to listen

I used ```
lynx google.com

``` as a connection test.

The result still no lynx connection and the tcpdump:
```
23:07:04.147241 IP (tos 0x0, ttl 64, id 18499, offset 0, flags [DF], proto TCP (6), length 60) 82.34.139.58.46589 > 209.85.171.100.80: S, cksum 0xe82f (correct), 2340516183:2340516183(0) win 5840 <mss 1460,sackOK,timestamp 45103380 0,nop,wscale 6>
23:07:04.307090 IP (tos 0x0, ttl 45, id 55982, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0x0ace (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997014291 45103380,nop,wscale 6>
23:07:04.694290 IP (tos 0x0, ttl 45, id 55983, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0x094b (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997014678 45103380,nop,wscale 6>
23:07:05.297468 IP (tos 0x0, ttl 45, id 55984, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0x06f0 (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997015281 45103380,nop,wscale 6>
23:07:06.499123 IP (tos 0x0, ttl 45, id 55985, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0x0240 (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997016481 45103380,nop,wscale 6>
23:07:07.143454 IP (tos 0x0, ttl 64, id 18500, offset 0, flags [DF], proto TCP (6), length 60) 82.34.139.58.46589 > 209.85.171.100.80: S, cksum 0xe703 (correct), 2340516183:2340516183(0) win 5840 <mss 1460,sackOK,timestamp 45103680 0,nop,wscale 6>
23:07:07.302773 IP (tos 0x0, ttl 45, id 55986, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0xff19 (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997017287 45103380,nop,wscale 6>
23:07:08.897735 IP (tos 0x0, ttl 45, id 55987, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0xf8df (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997018881 45103380,nop,wscale 6>
23:07:13.143460 IP (tos 0x0, ttl 64, id 18501, offset 0, flags [DF], proto TCP (6), length 60) 82.34.139.58.46589 > 209.85.171.100.80: S, cksum 0xe4ab (correct), 2340516183:2340516183(0) win 5840 <mss 1460,sackOK,timestamp 45104280 0,nop,wscale 6>
23:07:13.304857 IP (tos 0x0, ttl 45, id 55988, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0xe7a6 (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997023290 45103380,nop,wscale 6>
23:07:13.696291 IP (tos 0x0, ttl 45, id 55989, offset 0, flags [none], proto TCP (6), length 60) 209.85.171.100.80 > 82.34.139.58.46589: S, cksum 0xe61f (correct), 3840900363:3840900363(0) ack 2340516184 win 5672 <mss 1430,sackOK,timestamp 1997023681 45103380,nop,wscale 6>

```

---

### Post by rjmatthews62 on 2009-01-01
> **htmlland said:**
> I should be the only one using the internet at this time at night so what I get should be me.
I have two terminals open both ssh to my server:

On one terminal I used ```
sudo tcpdump -i eth1 -vvv -n port 80
``` to listen

I used ```
lynx google.com

``` as a connection test.

That really looks like it's doing what it's meant to.

Try this:
sudo tcpdump -i eth1 -vvv -n -s256 -X port 80

Should show us a bit more detail.

Have you trying disabling your firewall completely, to see if that makes a difference?

---

### Post by htmlland on 2009-01-01
Ithink disabaling the firewall is going to have to be the next thing :(

output:
```

tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 256 bytes
23:30:10.554984 IP (tos 0x0, ttl 64, id 47044, offset 0, flags [DF], proto TCP (6), length 60) 82.34.139.58.50920 > 72.14.205.100.80: S, cksum 0xa11f (correct), 2605769057:2605769057(0) win 5840 <mss 1460,sackOK,timestamp 45242021 0,nop,wscale 6>
	0x0000:  4500 003c b7c4 4000 4006 9028 5222 8b3a  E..<..@.@..(R".:
	0x0010:  480e cd64 c6e8 0050 9b50 e161 0000 0000  H..d...P.P.a....
	0x0020:  a002 16d0 a11f 0000 0204 05b4 0402 080a  ................
	0x0030:  02b2 56a5 0000 0000 0103 0306            ..V.........
23:30:10.650385 IP (tos 0x0, ttl 52, id 45284, offset 0, flags [none], proto TCP (6), length 60) 72.14.205.100.80 > 82.34.139.58.50920: S, cksum 0x6c9d (correct), 1922020131:1922020131(0) ack 2605769058 win 5672 <mss 1430,sackOK,timestamp 3704304312 45242021,nop,wscale 6>
	0x0000:  4500 003c b0e4 0000 3406 e308 480e cd64  E..<....4...H..d
	0x0010:  5222 8b3a 0050 c6e8 728f b323 9b50 e162  R".:.P..r..#.P.b
	0x0020:  a012 1628 6c9d 0000 0204 0596 0402 080a  ...(l...........
	0x0030:  dccb 32b8 02b2 56a5 0103 0306            ..2...V.....
23:30:11.100447 IP (tos 0x0, ttl 52, id 45285, offset 0, flags [none], proto TCP (6), length 60) 72.14.205.100.80 > 82.34.139.58.50920: S, cksum 0x6adc (correct), 1922020131:1922020131(0) ack 2605769058 win 5672 <mss 1430,sackOK,timestamp 3704304761 45242021,nop,wscale 6>
	0x0000:  4500 003c b0e5 0000 3406 e307 480e cd64  E..<....4...H..d
	0x0010:  5222 8b3a 0050 c6e8 728f b323 9b50 e162  R".:.P..r..#.P.b
	0x0020:  a012 1628 6adc 0000 0204 0596 0402 080a  ...(j...........
	0x0030:  dccb 3479 02b2 56a5 0103 0306            ..4y..V.....
23:30:11.701029 IP (tos 0x0, ttl 52, id 45286, offset 0, flags [none], proto TCP (6), length 60) 72.14.205.100.80 > 82.34.139.58.50920: S, cksum 0x6884 (correct), 1922020131:1922020131(0) ack 2605769058 win 5672 <mss 1430,sackOK,timestamp 3704305361 45242021,nop,wscale 6>
	0x0000:  4500 003c b0e6 0000 3406 e306 480e cd64  E..<....4...H..d
	0x0010:  5222 8b3a 0050 c6e8 728f b323 9b50 e162  R".:.P..r..#.P.b
	0x0020:  a012 1628 6884 0000 0204 0596 0402 080a  ...(h...........
	0x0030:  dccb 36d1 02b2 56a5 0103 0306            ..6...V.....
23:30:12.900213 IP (tos 0x0, ttl 52, id 45287, offset 0, flags [none], proto TCP (6), length 60) 72.14.205.100.80 > 82.34.139.58.50920: S, cksum 0x63d4 (correct), 1922020131:1922020131(0) ack 2605769058 win 5672 <mss 1430,sackOK,timestamp 3704306561 45242021,nop,wscale 6>
	0x0000:  4500 003c b0e7 0000 3406 e305 480e cd64  E..<....4...H..d
	0x0010:  5222 8b3a 0050 c6e8 728f b323 9b50 e162  R".:.P..r..#.P.b
	0x0020:  a012 1628 63d4 0000 0204 0596 0402 080a  ...(c...........
	0x0030:  dccb 3b81 02b2 56a5 0103 0306            ..;...V.....
23:30:13.553459 IP (tos 0x0, ttl 64, id 47045, offset 0, flags [DF], proto TCP (6), length 60) 82.34.139.58.50920 > 72.14.205.100.80: S, cksum 0x9ff3 (correct), 2605769057:2605769057(0) win 5840 <mss 1460,sackOK,timestamp 45242321 0,nop,wscale 6>
	0x0000:  4500 003c b7c5 4000 4006 9027 5222 8b3a  E..<..@.@..'R".:
	0x0010:  480e cd64 c6e8 0050 9b50 e161 0000 0000  H..d...P.P.a....
	0x0020:  a002 16d0 9ff3 0000 0204 05b4 0402 080a  ................
	0x0030:  02b2 57d1 0000 0000 0103 0306            ..W.........
23:30:13.649549 IP (tos 0x0, ttl 52, id 45288, offset 0, flags [none], proto TCP (6), length 60) 72.14.205.100.80 > 82.34.139.58.50920: S, cksum 0x60e6 (correct), 1922020131:1922020131(0) ack 2605769058 win 5672 <mss 1430,sackOK,timestamp 3704307311 45242021,nop,wscale 6>
	0x0000:  4500 003c b0e8 0000 3406 e304 480e cd64  E..<....4...H..d
	0x0010:  5222 8b3a 0050 c6e8 728f b323 9b50 e162  R".:.P..r..#.P.b
	0x0020:  a012 1628 60e6 0000 0204 0596 0402 080a  ...(`...........
	0x0030:  dccb 3e6f 02b2 56a5 0103 0306            ..>o..V.....
23:30:14.500656 IP (tos 0x0, ttl 52, id 45289, offset 0, flags [none], proto TCP (6), length 60) 72.14.205.100.80 > 82.34.139.58.50920: S, cksum 0x5d94 (correct), 1922020131:1922020131(0) ack 2605769058 win 5672 <mss 1430,sackOK,timestamp 3704308161 45242021,nop,wscale 6>
	0x0000:  4500 003c b0e9 0000 3406 e303 480e cd64  E..<....4...H..d
	0x0010:  5222 8b3a 0050 c6e8 728f b323 9b50 e162  R".:.P..r..#.P.b
	0x0020:  a012 1628 5d94 0000 0204 0596 0402 080a  ...(]...........
	0x0030:  dccb 41c1 02b2 56a5 0103 0306            ..A...V.....

```

---

### Post by htmlland on 2009-01-01
Disabled the firewall and it all worked fine :@ the problem is the one rule i removed i tryed putting back but missed one important feature locking me out so im going to tinker around locally on the machine to see what i get.

---

### Post by rjmatthews62 on 2009-01-01
Ok. Handshake is failing.

The connection request is going out, the initial response is coming back, and then nada.

Well, retrying happens, but it's clear that your end is just not seeing the incoming packets, although they clearly arrive.

This means something is getting in the way, which to me means firewall. Unfortunately I know almost nothing about how Ubuntu does its firewalls. I'd try disabling it completely, at least eliminate it as a culprit.
That's about reached the limits of my knowledge, I'm afraid... :")

---

### Post by rjmatthews62 on 2009-01-01
> **htmlland said:**
> Disabled the firewall and it all worked fine :@ the problem is the one rule i removed i tryed putting back but missed one important feature locking me out so im going to tinker around locally on the machine to see what i get.

Yay! I like it when I'm right (eventually.... :") )

---

### Post by htmlland on 2009-01-01
Finally fixed my firwall and a word of advice to anyone doing any sort of firewal work over ssh.. have a backup plan in case you lock yourself out :D


Thanks to everyone for you help

---

