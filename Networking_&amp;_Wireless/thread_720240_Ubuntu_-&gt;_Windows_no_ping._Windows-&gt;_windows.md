---
title: "Ubuntu -&gt; Windows no ping. Windows-&gt; windows ping !"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2008-03-10
HI guys,

weird one for y'all !

My home network has 3 PCs :

192.168.1.1 : Wireless router
192.168.1.100 : Windows XP &  Ubuntu Dual boot
192.168.1.101 : Windows XP
192.168.1.102 : Ubuntu

Now 100(XP) can happily ping and RDP into 101. And 100(Ubuntu) can happily NXCLient into 102.

However 100(Ubuntu) can't ping or RDP into 101. Which is weird enough in itself. However the more intriguing thing is it used to ! So clearly something has changed, but I can't think what it is which would stop a PING across operating systems.

btw, I am using IP addresses, not machine names, so it's not a hosts issue.
And ALL machines can access the internet at all times. So I know networking is working ...

anyone any ideas ?

---

### Post by superprash2003 on 2008-03-10
are they all on the same subnet?

---

### Post by Jethro_uk on 2008-03-10
Aha ! Since I have to answer "How do I check ?" in Ubuntu (10 years plus experience in Windows. The windows subnet is 0.0.0.0) then this could be a clue ....

---

### Post by superprash2003 on 2008-03-10
go to ubuntu terminal and type ifconfig .. under your network adapter .. you should find something called as "Mask:" .. there will be an ip sorta number there... make sure its the same for all your pcs!!!

---

### Post by Jethro_uk on 2008-03-10
Thanks, I'll try that tonight (when I get home). If I find they are different, then it raises the question, what changed them ?

---

### Post by ATIuser on 2008-03-10
you've manually configured the IP addresses on these machines correct?


with a class C IP address such as the 192.168.1.X scheme you have, the subnet mask is generally 255.255.255.0. unless you have it subnetted down even further. If three devices (four counting the router)is all you intend to ever have on the network, you could use a subnet mask of 255.255.255.248. but the router needs to be configured into the same subnet using that mask as well.

ex:
192.168.1.249 255.255.255.248 router
192.168.1.250 255.255.255.248 xp/ubuntu dual boot machine
192.168.1.251 255.255.255.248 xp machine
192.168.1.252 255.255.255.248 ubuntu machine

---

### Post by Jethro_uk on 2008-03-10
I've half configured the IP addresses !

I've set the router to act as a DHCP server, and assign IP address from 192.168.100 upwards.

I've then fiddled with it's DHCP table to link the MAC addresses to a sepcific IP addres. That way I know that whatever a particular machine is running (XP, Ubuntu) it will get the "correct" IP address ("correct" as in I will always know what machine 192.168.1.101 is).

I take the point on the subnet - the XP one will be whatever Windows assigns by default. However because all my machines are set to use DHCP, then I can't (yet) speak for what's going on with Ubuntu.

I'll post more later, when I'm home & able to check.

---

### Post by terazen on 2008-03-10
Can 100 Ubuntu ping 102?  

Also, from 100 Ubuntu, if you ping both 101 and 102 and then type 'arp -a' does it show mac addresses of both 101 and 102?

---

### Post by Jethro_uk on 2008-03-10
yes.


here's the output of arp -a 

media-server.local (192.168.1.102) at 08:10:74:13:E2: D0 [ether] on eth0
? (192.168.1.101) at 08:10:74:14:78:AD [ether] on eth0
? (192.168.1.1) at 08:10:74:14:71:3C [ether] on eth0


so it seems 100 is *aware* of 101 ... hmmm

any ideas anyone ?

---

### Post by superprash2003 on 2008-03-10
have you configured your gateway correctly?? do all your pcs have the router ip as the gateway??

---

### Post by Jethro_uk on 2008-03-11
all PCs are configured to use DHCP automatically, so I'm presuming they are all picking up the gateway settings from there, as they can all access the internet, I'll check later (I'm at work again).

---

### Post by ATIuser on 2008-03-11
do you have firewalls running on the Windows machines? I know it sounds like a crack shot since the same machine can RDP into .101 when using Windows, and not Ubuntu. Perhaps give it a try by disabling any firewalls on .101 or configuring it to trust the network.

---

### Post by terazen on 2008-03-14
Interesting, it got the mac address from 101.  That should mean that your pc sent a broadcast saying "what's the mac address for 101" and the 101 pc answered "here it is".  The next thing it does is send a ping request to the windows 101 box's ip/mac with it's own ip/mac as source.

As far as I know if the `arp -a` from windows 101 matches the `ifconfig` ip/mac of ubuntu 100 and the `arp -a` of ubuntu 100 matches the `ipconfig/all` ip/mac of windows 101 then it should work.  But I don't see how the ubuntu 102 box would have the correct information and the windows box wouldn't so I doubt this is the case, you can check though.

You may need to download something like ethereal/wireshark on the ubuntu 100 box and then try to ping it from the 101 and 102 boxes.

---

