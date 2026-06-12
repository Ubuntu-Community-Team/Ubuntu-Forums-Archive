---
title: "can't ping"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by arxontas on 2006-11-06
hi guys!!
i have 2 problems :
1)i have two pcs connected with ethernet cards connected via crossover cable
(winxp and dapper drake) and i can't ping neither from winxp nor dapper to each other.In winxp it shows me the icon local area connection that it is enabled and connected but i can't ping to my linux machine.
I understand that there is a link somehow but it is useless because i can't do anything
My configuration for winxp is:
ip:192.168.0.1
subnet mask:255.255.255.0

My configuration for linux is:
> 
 ifconfig -a
eth1      Link encap:Ethernet  HWaddr ffffffffff:EE
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967292 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xe000
when i issue the netstat -rn
> 192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1

what is the problem? should i have a gateway and what it should be its ip both in the two machines!!

2)SECOND PROBLEM

I can't ssh to my linux machine via internet nor view my web page although i can ping to its ip provided by the isp(dial-up connection)when i issue netstat -a |grep tlp:

> sudo netstat -tlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:4450          *:*                     LISTEN     4251/python
tcp        0      0 localhost:mysql         *:*                     LISTEN     4523/mysqld
tcp        0      0 *:www                   *:*                     LISTEN     4803/apache2
tcp        0      0 localhost:4692          *:*                     LISTEN     4247/hpiod
tcp        0      0 *:ssh                   *:*                     LISTEN     4648/sshd


i can ssh locally to the internet address 
example:
> ssh 72.103.100.98
The authenticity of host '72.103.100.98 (72.103.100.98)' can't be established.
RSA key fingerprint is c6:84:d0:73:1e:59:a2:68:27:9b:6f:38:b7:cb:70:39.
Are you sure you want to continue connecting (yes/no)?


Please HELP!!

---

### Post by DaveBorealis on 2006-11-06
> **arxontas said:**
> 
I can't ssh to my linux machine via internet

Does this mean that you can ssh out of the linux box but not ssh into it?  If so, you either need to install sshd or start it up if you do have it installed.  'ps axx | grep sshd' should list '/usr/sbin/sshd' if it's installed and launched.

Best regards,
Dave

---

### Post by arxontas on 2006-11-07
dave thanks for your reply
the ps -axx |grep sshd gives  > 4601 ?        Ss     0:00 /usr/sbin/sshd

and i haven't found a machine to ssh into so i can't answer all the questions!!

if you have any other ideas!!

please post them :) 

thanks in advance

---

### Post by arxontas on 2006-11-09
guys first problem solved!!!
The problem was that in the network card of the winxp machine it was by default the speed between the ethernet cards in auto-negotiation.
So it was connecting always at 100 Mbps full-duplex(I don't know why though...)and it worked when i manually changed to 10Mbps full-duplex or 10 Mbps half-duplex.NOW i can ssh from winxp to ubuntu machine and view my web page which i made setting up LAMP.

But i need help with the second problem.
Now that i verified that all services in ubuntu are configured correctly since they work in the home-lan i can't figure out yet
why i can't ssh via internet to my linux machine nor view my web page since i can ping to its ip (I have dial-up connection:mad: )!!!

I welcome all the ideas you can give me!!
thanks

---

### Post by FrodoB on 2006-11-09
Do you have the ssh server installed on Ubuntu? 

If not:

$ sudo apt-get install openssh-server

---

### Post by arxontas on 2006-11-09
Yes i have installed openssh-server
please read carefully my last post
i wrote that i can ssh locally from my home -lan but not from the internet

---

### Post by FrodoB on 2006-11-09
Likely your router is protecting you from the internet. Some routers let you put a specific host on the internet, but if you have dynamic IP addresses they will always be changing on you. Look for dynamic dns on the search engines.

---

### Post by dbott67 on 2006-11-09
Please describe how your LAMP computer is connected to the internet.  Is it connected directly via dial-up?  Or is it behind some sort of router? Or are you using some sort of "internet connection sharing"?

Please post the output from your LAMP computer of:
```
ifconfig -a
```

Just the first few lines of:
```
tracepath www.google.com
```

Or, if you have traceroute installed (just the first few lines):
```
traceroute www.google.com
```

As FrodoB mentioned, it could be a router/firewall issue.  Are you running iptables on the LAMP computer?

Need more info, please.  :)

-Dave

---

### Post by dannyboy79 on 2006-11-09
> **arxontas said:**
> Yes i have installed openssh-server
please read carefully my last post
i wrote that i can ssh locally from my home -lan but not from the internet

it's either that your router is blocking you from connecting, so you need to forward port 23 i think it is, or 22. or if you;re talking about what you posted previously, "ssh 72.103.100.98
The authenticity of host '72.103.100.98 (72.103.100.9' can't be established.
RSA key fingerprint is c6:84:d0:73:1e:59:a2:68:27:9b:6f:38:b7:cb:70:39.
Are you sure you want to continue connecting (yes/no)?" 

than simply say yes, you want to connect. i think you have to type out the word yes and you can't just put y.

or if you don't have a router and you enabled some rules within iptables than thats what is blocking youm ipables is the default fireall in most linux distro but ubuntu doesn't have any rules setup by default so if you didn;t set any than that's NOT the isuse. i can tell you once you are able to ssh in from outside it's awesome.

---

### Post by arxontas on 2006-11-10
wow guys thanks a lot for your answers!!
Here some info that you asked

My lamp-server is connected directly via dial-up.So as you understand **i don't use** any kind of router,also i don't use internet connection sharing with the winxp machine yet.I wan't to get it right first with ssh and the web page and maybe later i will ask for help regarding ICS :) .
**I haven't** setup any kind of firewall (ex.Firestarter) or IPTABLES and as danny said none of them is installed by default!!
Dave these are for you my friend!!

>  ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:14:78:05:34:EE
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2560 (2.5 KiB)  TX bytes:942 (942.0 b)
          Interrupt:9 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2800 (2.7 KiB)  TX bytes:2800 (2.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:195.167.106.209  P-t-P:62.103.3.138  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:777019 (758.8 KiB)  TX bytes:270558 (264.2 KiB)


> 
 tracepath [www.google.com](www.google.com)
 1:  athe530-k209.otenet.gr (195.167.106.209)               0.568ms pmtu 1500
 1:  athe530k-l0.otenet.net (62.103.3.138 )                299.331ms
 2:  athe6509k2-vlan40.otenet.net (62.103.4.1)            287.628ms
 3:  62.103.6.145 (62.103.6.145)                          267.914ms
 4:  athe-GSRb-po1.otenet.net (62.103.6.4)                275.013ms
 5:  gig4-0-0-cr02-otenet.ath.OTEGlobe.net (62.75.3.5)    asymm  6 267.594ms
 6:  pos6-0-0-cr02.lon.OTEGlobe.net (62.75.4.82)          asymm  7 335.276ms
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply

and a tracepath to [www.cisco.com](www.cisco.com) might help of a better understanding(i think)

> tracepath [www.cisco.com](www.cisco.com)
 1:  athe530-k209.otenet.gr (195.167.106.209)               0.586ms pmtu 1500
 1:  athe530k-l0.otenet.net (62.103.3.138 )                295.795ms
 2:  athe6509k2-vlan40.otenet.net (62.103.4.1)            287.821ms
 3:  62.103.6.145 (62.103.6.145)                          267.894ms
 4:  athe-GSRb-po1.otenet.net (62.103.6.4)                266.835ms
 5:  gig4-0-0-cr02-otenet.ath.OTEGlobe.net (62.75.3.5)    asymm  6 295.838ms
 6:  pos6-0-0-cr02.lon.OTEGlobe.net (62.75.4.82)          asymm  7 339.801ms
 7:  ex1-g9-0-0.linxuk.sbcglobal.net (195.66.226.210)     asymm  8 347.135ms
 8:  bb1-p5-0.linxuk.sbcglobal.net (151.164.41.245)       asymm  9 339.655ms
 9:  bb1-p2-0.amsxnl.sbcglobal.net (151.164.40.87)        asymm 10 327.843ms
10:  bb2-p9-0.hrndva.sbcglobal.net (151.164.41.208 )       427.904ms
11:  ex2-p5-1.eqabva.sbcglobal.net (151.164.40.53)        asymm 12 450.826ms
12:  151.164.92.241 (151.164.92.241)                      asymm 23 487.858ms
13:  ded-p1-0.pltn13.sbcglobal.net (151.164.191.245)      asymm 23 494.828ms
14:  VIP-Cisco-Systems-1112812.cust-rtr.pacbell.net (71.133.200.198 ) asymm 24 487.773ms
15:  sjc5-dmzbb-gw1.cisco.com (128.107.224.105)           asymm 25 487.877ms
16:  sjce-dmzbb-gw1.cisco.com (128.107.224.2)             asymm 26 487.893ms
17:  sjck-dmzdc-gw1.cisco.com (128.107.224.69)            asymm 27 487.709ms
18:  no reply
19:  no reply
20:  no reply

frodo i didn't forget you,i have setup Dyndns which works great since I can ping using the domain name but what's the point since i can't ssh or view my web page both ways [by domain name-->the same everytime ,by ip-->changes every time because i use dial-up]

thanks a lot guys

---

### Post by dannyboy79 on 2006-11-10
ok wait a second, you say you don't have a router? well then how in the heck is your internal lan ip's 192.168.blah blah. It is my understanding that if you are connected straight to the internet than you should have an ip that meets the wan ip standards so to speak, so you say you can ssh locally to the internet address 
example:
Quote:
ssh 72.103.100.98
The authenticity of host '72.103.100.98 (72.103.100.9' can't be established.
RSA key fingerprint is c6:84:d0:73:1e:59:a2:68:27:9b:6f:38:b7:cb:70:39.
Are you sure you want to continue connecting (yes/no)? 

so then what are using to forward port 23 from ip 72.103.100.98 to the ip of your lamp server, which you have told us is  192.168.0.2. I am just a newbie so maybe I may be missing something here but something doesn't seem correct here with the info your giving us?

---

### Post by dbott67 on 2006-11-10
Dannyboy79, the 192.168.x.y IP address is for eth1 (which is the LAN NIC).  The ppp adapter is the dial-up modem (195.x.y.z).  Also SSH is port 22 (FTP is 21, telnet 23).

FYI, 192.168.x.y is considered a private non-routable Class C network.  It is reserved for *any* organization that wants to use it on a 'closed system' (i.e. not directly connected to the internet).  In order for this address to work, you would need a NAT router that could translate the traffic from the INTERNAL network (private) to the EXTERNAL network (internet).  D-Link, Linksys, Netgear and others make home cable/DSL routers to do this.

Give me a few minutes and I'll post more...


QUESTION: Does LAMP ask to bind to a particular interface?  **If so, it may be bound to eth1, but also needs to be bound to ppp0.**

-Dave

---

### Post by arxontas on 2006-11-10
when i use tracert it seems to work great in winxp but in linux it can't make a complete trace(see previous post of mine ).Here is what i mean!!
I was wondering if mtu(max transfer unit)has anything to do with this difference-problem.

> C:\Documents and Settings\Nick>tracert [www.google.com](www.google.com)

Tracing route to [www.l.google.com](www.l.google.com) [66.102.9.104]
over a maximum of 30 hops:

  1   291 ms   277 ms   619 ms  athe530i-l0.otenet.net [62.103.3.136]
  2   264 ms   238 ms   238 ms  athe6509k2-vlan40.otenet.net [62.103.4.1]
  3   353 ms   238 ms   238 ms  62.103.6.145
  4   350 ms   237 ms   238 ms  athe-GSRb-po1.otenet.net [62.103.6.4]
  5   347 ms   217 ms   238 ms  gig4-0-0-cr02-otenet.ath.OTEGlobe.net [62.75.3.5]
  6   354 ms   277 ms   298 ms  pos2-0-cr02.lon.OTEGlobe.net [62.75.4.78]
  7   432 ms   298 ms   297 ms  195.66.224.125
  8   447 ms   319 ms   337 ms  216.239.49.254
  9   444 ms   319 ms   316 ms  72.14.232.233
 10   453 ms   319 ms   316 ms  72.14.232.239
 11   447 ms   319 ms   319 ms  64.233.174.18
 12   426 ms   319 ms   298 ms  66.102.9.104

Trace complete.

Dave LAMP doesn't ask me to bind to a particular interface.
I downloaded and install the packages myself in order to setup the lamp(i used alternate-cd for installation instead of the server-edition)keeping in mind to get more familiar with ubuntu.
To be honest i don't remember something like that in the configuration procedure of the lamp server.You may be right with the binding with ppp0 but when I test the web page from the same machine it works and with the internet address.
Here is what i mean:
http://127.0.0.1-->works great
http://195.66.224.125-->works great

i hope these information that will help

---

### Post by dbott67 on 2006-11-10
After a little checking, I think that the issue might be that SSH (and possibly the other services) are bound to 'eth1' and not 'ppp0'.

I'm not terribly familiar with setting up LAMP (I've done it, but only on a system with one interface --- eth0).  The /etc/ssh/sshd_config file does have a section as to which interface to listen on:
```
dbott@thedrake:/etc/ssh$ cat sshd_config
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
**[COLOR="Red"]#ListenAddress 0.0.0.0[/COLOR]**
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes
<snip>

```

Perhaps, the line in red above needs to be UNcommented (just guessing).

Let me know if it works.

-Dave

---

### Post by dannyboy79 on 2006-11-10
> **dbott67 said:**
>  Dannyboy79, the 192.168.x.y IP address is for eth1 (which is the LAN NIC).  The ppp adapter is the dial-up modem (195.x.y.z).  Also SSH is port 22 (FTP is 21, telnet 23). 
That's exactly my point, how does the traffic know how to go from the ppp adapter to eth1? On the port numbers, yeah, I just mistyped. I am not familar with dial-up modems and linux, I have a cable modem, then a router, then a switch, then 1 ethernet adapter in my ubuntu server. So if I mispoke about something than i apologize and I probably shouldn't speak about stuff I don't know about.

> **dbott67 said:**
> FYI, 192.168.x.y is considered a private non-routable Class C network.  It is reserved for *any* organization that wants to use it on a 'closed system' (i.e. not directly connected to the internet).  In order for this address to work, you would need a NAT router that could translate the traffic from the INTERNAL network (private) to the EXTERNAL network (internet).  D-Link, Linksys, Netgear and others make home cable/DSL routers to do this.
Again, that's exactly what I was saying. You even state yourself, "In order for this address to work, you would need a NAT router that could translate the traffic from the INTERNAL network (private) to the EXTERNAL network (internet).  D-Link, Linksys, Netgear and others make home cable/DSL routers to do this."


I didn't notice that he posted the ip of his ppp adapter (195.167.106.209 ) why is he trying to ssh to 72.103.100.98 if his ip is 195. blah blah???

---

### Post by arxontas on 2006-11-10
danny
the ssh to 72.103.100.98 was just an example to show tha ssh works fine.I used the ip that i had at that time i posted the message.
Having dial-up means that the internet address **changes every time **you login.For start i wan't to login only in the linux machine which is the machine that is connected directly to internet.i don't need NAT Router because **i am referring only in one machine**
Danny i hope that i answered to your questions.I am also a newbie and we all try to learn!!!

dave i will test your idea and we will see what will happen!!!
thanks

---

### Post by dbott67 on 2006-11-10
Hi Dannyboy79,

Please don't misinterpret my explantations as implying that you don't know or understand something. I generally like to try to be as explicit and detailed as possible so that:

a) The steps are clear for the people reading the thread, regardless of their experience.
b) They include an explanation explaining why something might be happening (so that they will be able to understand what they are doing, rather than just typing in a bunch of commands that some guy on the internet told them).
c) Provide clear instructions for people that find this thread via google or search.  Again, it's hard to know the esperience level of the person, so I try to err on the side of being explicit with my instructions.

It must be the former teacher in me (5 years teaching networking at a college).

Anyhow, the eth1 issue (192.168.x.y) for clarification (for all parties):

The LAMP services can be configured to 'listen' on multiple interfaces (eth0, eth1, ppp0, etc).  If the service was only set to listen on one interface, we would need to somehow get the traffic from ppp0 to eth1 (create a static route).  

The other option is to set the service to listen on multiple interfaces (see my post above about the **/etc/ssh/sshd_config** file).  In this case, you wouldn't need to worry about NAT because the service would be listening on both eth1 and ppp0.

-Dave

---

### Post by dannyboy79 on 2006-11-10
here's a website for setting up NAT using PPP with Dial-Up modem.

[http://www-jerry.oit.duke.edu/linux/bluedevil/HOWTO/ipmasquerade_with_ppp_howto.html](http://www-jerry.oit.duke.edu/linux/bluedevil/HOWTO/ipmasquerade_with_ppp_howto.html)

i think you are saying that you don't want to have the computers on your internal lan to have internet access so maybe you could just disregard this part but this should allow you to be able to ssh into your box I would think, if not, sorry. I am trying to help and maybe I shouldn't since I am new to linux. Good luck

---

### Post by arxontas on 2006-11-10
danny
I couldn't describe it better myself.Now we have an understanding!!:) and as i said all the ideas are welcome.
I think that the fact that you are willing to help is that counts the most.As for my problem i am sure that it will be solved since the community of ubuntu is superb;) and it is responding very fast!!

dave I try to find a pc from which i will ssh via internet into my linux machine.
thanks guys

---

### Post by dbott67 on 2006-11-10
arxontas,

PM me your IP address --- I'll just see if I can get an ssh login prompt.  No need for me to login.

-Dave

---

### Post by arxontas on 2006-11-14
Guys FINALLY SUCCESS!!!!

The reason i couldn't ssh into my linux machine nor view my web page over internet was that the damn ISP:evil: had blocked some ports so it wasn't possible to get this done.
When i used a connection from another ISP it worked just fine!!!
I would like to thank especially Dave for his significant help.
Please other members of the forum don't get offended;) 

Thank you all for the help

PROBLEM SOLVED

---

