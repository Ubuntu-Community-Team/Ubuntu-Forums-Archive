---
title: "Finding LAN but not Internet"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by njord3 on 2007-04-26
I am new to linux and recently set up an old computer on Linux Ubuntu 6.06 wired to ADSL Belkin Modem/router. I already have a Windows Vista laptop, and a Windows XP Desktop successfully connected to the Internet and on a home network.My Ubuntu machine can access the home network but not the internet. Eth0 is enabled and set for DHCP.
 ifconfig gives the following:
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:D5:6F:C5
          inet addr:192.168.2.4  Bcast:192.168.2.255 
 Mask:255.255.255.0
          inet6 addr: fe80::207:95ff:fed5:6fc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000

          RX bytes:19635 (19.1 KiB)  TX bytes:1494 (1.4 KiB)
          Interrupt:11 Base address:0xc000
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 
carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9160 (8.9 KiB)  TX bytes:9160 (8.9 KiB)
I'm completely at sea,can anyone help please!

---

### Post by lloyd_b on 2007-04-26
You're getting believable values for IP address and netmask, so I'm guessing that either you're not getting a default route (gateway), or you're not getting good addresses for DNS nameservers.

First off, could you post the output of the command "route -n" (from a terminal window)?  This will show us what routes are defined. 

Second, could you post the contents of the file "/etc/resolv.conf"?  This will show us what nameservers have been defined.

It would also help if you could post the IP address, gateway, and DNS info from one of the Windows machines (sorry - I have no clue where to look for this info - I haven't used Windows in years).

Now for some testing.  In a terminal window:
```
ping 66.102.7.147
```
This is an IP address for "www.google.com".  If it fails, then it's most likely a routing issue.  If it fails, please post the results of the command - it will give us a clue as to what exactly is going wrong.

If it succeeds, then try
```
nslookup www.google.com
```
This *should* respond with something like this:
```
lloyd@laptop:~$ nslookup www.google.com
Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
www.google.com  canonical name = www.l.google.com.
Name:   www.l.google.com
Address: 66.102.7.104
Name:   www.l.google.com
Address: 66.102.7.147
Name:   www.l.google.com
Address: 66.102.7.99

```
If this fails, then you've got a DNS issue - most likely you're not gettting a correct nameserver.

Lloyd B.

---

### Post by njord3 on 2007-04-26
Hi Lloyd 
Thanks for your response . 
Here is the result of your suggestions.
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.	192.168.2.1     0.0.0.0         UG    0      0        0 eth0

 /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied /etc/resolv.conf

 When I do ping 66.102.7 147 I get the following repeatedly and I can only stop it by closing terminal 
64 bytes from 66.102.7.147: icmp_seq=1 ttl=245 time=161 m
 nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

The windows machine is set to 'obtain IP address automatically',  'obtain DNS server address automatically', and the default gateway is blank.
Sorry if this is not too much help, but if you can guide me at all I'll be very grateful.

Regards Nev

---

### Post by lloyd_b on 2007-04-26
> 
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.	192.168.2.1     0.0.0.0         UG    0      0        0 eth0

This looks fine.  You are getting a proper default route, with the gateway at 192.168.2.1, which is believable given your IP address.

> /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied /etc/resolv.conf

I guess I confused you with this one - "/etc/resolv.conf" is a data file, not a command.  What I'm interested in seeing the contents of this file.  This can be done by using the terminal command "cat /etc/resolv.conf", or opening the file with an editor.

> 
 When I do ping 66.102.7 147 I get the following repeatedly and I can only stop it by closing terminal 
64 bytes from 66.102.7.147: icmp_seq=1 ttl=245 time=161 m

That is the normal behavior of the "ping" command.  This means that you *are* able to reach the google servers by IP address.

> nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

Bingo - you have an internet connection, but no reachable DNS nameservers.  This means that you can potentially reach things like Google, but your machine can't do a lookup to determine that "www.google.com" is at IP address "66.102.7.147".  Think of it as having a working phone, but no phone book...

> The windows machine is set to 'obtain IP address automatically',  'obtain DNS server address automatically', and the default gateway is blank.
Sorry if this is not too much help, but if you can guide me at all I'll be very grateful.
It would be nice to know what the Windows machines are using for a nameserver, but I have no clue how to go about getting that info.  Oh well.

If you could post the info from "/etc/resolv.conf", it will tell us what (if any) nameservers are being defined.  If there are no "nameserver" lines in that file, then try adding this one:
```
nameserver 192.168.2.1
```
That's just a guess, but it may resolve the problem.
Note: To edit that particular file, you'll need to "sudo" or "gksudo" the editor command.  For instance:
```
sudo nano /etc/resolv.conf
```
will give you root permission, and then edit the file using the "nano" editor.

Lloyd B.

---

### Post by .rdg on 2007-04-26
From what I've seen in your response - you are correctly routed to the Internet (ping goes through to google's host). The problem lays in your DNS configuration - you are not allowed to read the contents of /etc/resolv.conf. That's why the nslookup command failed for you.

Please do the following:

ls -l /etc/resolv.conf and post the result (just to be extra sure - if my entire message doesn't help).

On my machine it's:

-rw-r--r-- 1 root root 96 2007-04-26 16:47 /etc/resolv.conf

Which means: root user and root group are the owners of the file; the root user is allowed to Read and Write, the root group can only read and all other users/groups are allowed to read only.

Your file rights are most certainly wrong - something like:

-rw-r----- 1 root root 96 2007-04-26 16:47 /etc/resolv.conf

The last 3 dashes would mean all other people are NOT ALLOWED TO READ IT so it means you're not set up with DNS. If so please use the command:

sudo chmod 644 /etc/resolv.conf

So your file can be read by all users of your system and do a check if it works. If not - post what's in the resol.conf file (in terminal type: cat /etc/resolv.conf). It should be set up by the dhcp client automatically, but it might not. If not - check what are your DNS settings on Windows machines (ipconfig /all in command line) and set the contents of the resolv.conf file to something like this:

search thedomain.you.use
nameserver IP.of.your.primary.DNS
nameserver IP.of.your.secondary.DNS
nameserver IP.of.your.tertiary.DNS

That should help for sure (but shouldn't be required at all if your dhcp server is set up correct - if your Windows PCs work ok than it most likely is only the Ubuntu file rights problem).

Hope this helps.

PS: in terminal ctrl-c should stop anything - like ping you couldn't stop.

---

### Post by njord3 on 2007-04-26
Thank you both for your help . /etc/resolv.conf had 'search Type address'. I put in another line 'nameserver 192.168.2.1 and Eureka I've got internet access .
As a matter of interest when I typed "ls -l /etc/resolv.conf"' I got "ls: invalid option --?Anyway I'm on!
Thanks again guys!
Nev

---

### Post by .rdg on 2007-04-26
Perhaps you didn't copy-paste the commands I gave and instead of small L you typed in capital i in the ls command - that would explain why you got the error.

Anyways glad you have Ubuntu working now.

---

### Post by macabro22 on 2007-04-26
Cool. I will try that as well. I have the same bloddy problem.

---

### Post by gcordoba on 2007-04-28
Hi, I have a similar problem.
I think it is some bug kind problem.
I installed Drapper some moths ago in a two computers (a laptop and a PC) as the only OS. My home internet is by dhcp and worked fine. However, I instaled a dual OS in an other laptops (vaio and dell) and in both cases ubuntu seems to detect the connection but it can not use. 
It is like Drapper can not find any ip offer from the internet provider. On the Dell laptop I move to Edgy and the same problem remains. On both laptops the networking facility report connection and find the network card.
ifconfig -a semms to find the card and report: UP BROADCAST RUNNING MULTICAST ...
However 
nortiz$ route -n :
Destination    Gateway   Genmask   Flgs  Metric   Ref   Use Iface
nortiz$

Then Ubuntu semms to think that there is no ip offer, which is not true.
If I deffine by hand the dns server the problem remains as internet can not be reached.
As the problem seem to appear only in dual OS installations, it could be a bug.
Any idea?

---

### Post by .rdg on 2007-05-06
In your case gcordoba I guess it's the lack of any IP address that permits you to connect to Internet - not the DNS. There's no route because there's no IP at all and your dhcp client did not recieve any info from dhcp server. Could you give an info if the other OS (Windows perhaps) gets the IP by dhcp without problem? Also did you try to run (from console) dhclient - it's verbose in its actions, so you could have a good info if all works fine then. Also check if your /etc/network/interfaces file is set up correctly to use dhcp. It should contain something like:

auto eth0
iface eth0 inet dhcp

To be honest - I haven't really ran into problems such as described here. Dhcp client works fine, sets up the DNS in /etc/resolv.conf and routes. The networking part of GNU/Linux is really great, surpassess Windows by miles imho (well at least in normal cases like here).

Regards,
.rdg

---

### Post by macabro22 on 2007-05-06
> The networking part of GNU/Linux is really great, surpassess Windows by miles imho (well at least in normal cases like here).


Is that so? Then I suppose it shouldn´t be a problem when I switch my static ip config at work and at home. Unfortunatelly, as a matter of fact, Ubuntu seems to randomly accept my changes after some reboots but not promptly, right after the config change.   

To make things worse, sometimes (I fail to perceive a pattern) it just wont connect to the internet inspite of me not changing a thing.

I also have a problem automounting my IEEE external HD. Whenever Ubuntu is in the mood it plays pranks on me. Its really pissing me off.

I can´t avoid cursing it. Its a love-hate relationSHIT.

Will anyone PLEASE help me on the LAN-internet erratic behavior issue? I will post any command outputs you wish.

Merci!

---

### Post by gcordoba on 2007-05-07
thanks .rdg,
Currently I am at the office, and the problem is at home.
I will try your advice and other tips  this afternoon,
Regards,
Gustavo

---

