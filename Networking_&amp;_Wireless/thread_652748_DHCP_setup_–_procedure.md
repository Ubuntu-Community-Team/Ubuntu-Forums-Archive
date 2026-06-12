---
title: "DHCP setup – procedure"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by expatCM on 2007-12-29
Just getting a little out of depth ....  I am setting up a dhcp server to split my lan traffic from the Internet interface.

So I have set up eth0 and eth1 as separate ranges / subnets which looks fine.  

When I start the server I cannot find the Internet at all from the clients which makes me wonder if I have got the process wrong.  I think perhaps I need to turn off the dhcp function on the router which I have only just wondered about.  Is that correct?  Competing dhcp services does not sound so good to me ..... 

My concern is that access to the router may become a problem if this is wrong since a gui is needed to access the router setup and if I make a mess and loose the IP access then I am basically toast since the server is cli only ....

And .... do I need to set up shorewall before dhcp so that NAT is there?

---

### Post by mellowd on 2007-12-29
It doesn't really matter that there are 2 dhcp servers on the network, all clients will simply use the address they get first even if both dhcp servers responded. Having said that, it's much easier to manage a network with the minimum amount of dhcp servers. What you could do is set up the router so it recognises only one network card and gives it the same ip address everytime (i.e. reserve an ip for one mac address, ignore all other dhcp requests)

That way you can be sure that your clients will be one 1 subnet, while the server and router will be on the second.

Having a look at your original request again though, essentially the router itself will split your lan and wan, is there a reason you want your server to act as a router as well?

---

### Post by expatCM on 2007-12-29
What I am trying to do is to put some distance from the modem router.  

The Internet often fails or is really bad performance so I put Squid up to help with the traffic.  I would like to also manage some form of security by putting a firewall in place but with focus on the Internet.

So my intention is to separate the Internet and the Lan. In doing so I am told that it is necessary to run a dhcp server to dish up the IP's,  certainly for the local network.  I am also told that I will probably need to enable NAT and to do this through the firewall.  

Since my children think any games are cool I would like to be able to manage the local and Internet traffic a bit just so that I can see what is really happening.

The tutorials / configuration guides out there are great but written by those who know.  I do not know and it is painful to follow the big picture let alone the details :)

---

### Post by mellowd on 2007-12-29
Okay, is it possible but I must warn you that I myself haven't actually set up a server as a router before, so it can be a learning experience for both of us.

Essentially what you are saying is correct. What you would want to do is use the second network card in the server to hand out IP's to your internal network. That network would need to be on a seperate subnet to your external connection (just use 192.168, 10.0, etc) Therefore dhcp needs to be configured on the second interface.

This is where I sort of hit a brick wall for now, I haven't done the setup yet to enable the server to route the traffic from that interface, through the firewall and then out the first network card. I'll have to investigate.

When the server filters though it should automatically NAT any address, if not it will be part of the setup of the routing. Obviously you can't have 192.168.0.1 routing to the internet, it simpy won't work.

---

### Post by mellowd on 2007-12-29
Setting up dhcp. Coudl you run this command first? I want to see what dhcp packages you have installed:

```
sudo dpkg --list | grep dhcp
```

---

### Post by expatCM on 2007-12-29
I have no problem to have a few disasters here and there ....  what I tend to do is to start dhcp, have a crisis, stop it and then work normally ....

I installed the standard from apt-get install dhcp3-server

> dpkg --list | grep dhcp
ii  dhcp3-client                          3.0.5-3ubuntu4                 DHCP client
ii  dhcp3-common                          3.0.5-3ubuntu4                 common files used by all the dhcp3* packages
ii  dhcp3-server                          3.0.5-3ubuntu4                 DHCP server for automatic IP address assignm

You say "Obviously you can't have 192.168.0.1 routing to the internet, it simply won't work."  Perhaps this is my problem .....  

I set up eth0 directly to the router with 192.168.0.1 as the gateway address.  eth1 I use for the lan and here I used 10.0.0.0 .....

If I start the dhcp server and then on a client run ifconfig then I see an IP in the 10.0.0.x range whereas without the server running the address is in the 192.168.x.x range.

---

### Post by mellowd on 2007-12-29
That's perfect then. Remember 192.168.0.1 is still actually internal to your network. Once it gets to your router it'll NAT the 192 address to your external address. Remember you now have 2 routers, and 3 networks.

You could try and setup your router in bridge mode if its avalible, that will then simply send your internet connection straight to your server without first changing the subnet. Your server would then get the external IP. It's not needed though.

Anyways, you say that your clients have already got an address in the 10 range. What OS is on these clients? Is your servers IP 10.0.0.1? Are you able to ping the server? Can you ping the 192.168.0.1 address from a client?

---

### Post by expatCM on 2007-12-29
The server is running Ubuntu 7.10 Server Edition and the clients are all running Ubuntu 7.10 Desktop. The clients only return the 10.0.x.x address when I reboot the client and also have started the dhcp server.  I also change the cable to connect the lan hub to eth1 and remove the link from the router to the lan hub.

I access the server from a client either with Webmin or with PuTTY depending on my need for pain. As soon as I change to eth1 the access goes.  With the Internet I think this may be due to needing to change the Squid ACL but webmin should connect since it does not run through the proxy.  Never thought that the server IP might have changed ... I will check.  Also skype does not find the service so something is not quite right.

Just looked round the router and yes, there is a Bridge mode.  

I will post back in a few hours with details of the ping and server IP ...  sorry to say but I may not be too popular to take out the server right at the present moment ...  (would have to do that to bring up the 10.0.x.x range)

---

### Post by mellowd on 2007-12-29
No problem.

what would also be helpful is a couple of trace's from the clients.

Unfortuantely traceroute is not installed by default so do this first:

```
sudo aptitude install traceroute
```

on the clients and its good to install it on the server as well. Once that is installed you can do this:

```
traceroute www.google.com
```

Is should show all the hops along the way. what you should be seeing therefore from the clients would be this:

10.0.0.1 (first hop)
192.168.0.1 (second hop)
x.x.x.x (your isp's gateway)
and so on...

if it doest go any further then we know where the problem lies. if it gets to 10.0 but no further there is an issue with the setup. if its goes to the routers ip of 192 then we know we are getting that far

---

### Post by expatCM on 2007-12-30
Slight side track but an interesting result .....

Start dhcp server.

Edit hosts file on client to change the IP to the host.  Reboot client.

**On the client - **

Confirmed that dhcp had allocated an IP in the correct range.

Was able to PuTTY to the server using the IP on eth1.  Worked after accepting new certificate.

tracert to google.com failed totally.  The following error message appeared - 

```
tracert google.com

google.com: Name or service not known

Cannot handle "host" cmdline arg `google.com' on position 1 (argc 1)
```

**On the server - **

ifconfig showed the correct IP address for both eth0 and eth1

tracert to google.com was no problem ... it ran to the router and then to the ISP and so on.

---

### Post by expatCM on 2007-12-30
still looking and find the following ...

**on the client -**

cat /etc/resolv.conf correctly states the two DNS servers.  No other information in the file.

tracert and ping by IP address or domain name only gives Network is unreachable.

ping - gateway - unreachable
ping - eth0 - unreachable
ping - eth1 - ok

nslookup google.com - timed out, No servers could be reached.


**on the server**

ping - gateway - ok
ping - eth0 - ok
ping - eth1 - ok

---

### Post by mellowd on 2007-12-31
thats odd, can you ping 127.0.0.1 on the clients? What IP address are you getting on the clients?

---

### Post by expatCM on 2008-01-01
I think I made a mistake in using webmin to set this up.  I have now tidied up the dhcpd.conf  but it still does not work which is annoying but no idea why not.  Is the broadcast address correct for eth1?  

The network card on the client and the corresponding card on the server are using different ranges so this must be the problem.

I have tried changing the network card settings on the client from the roaming default to DHCP to giving a fixed address but nothing seems to make any difference.

The dhcpd.conf now is this

```

option routers 192.168.1.1;

option domain-name-servers 208.67.222.222, 208.67.220.220;

default-lease-time 600;
max-lease-time 7200;


# Internet Access
subnet 192.168.16.0 netmask 255.255.255.0 {
	option domain-name-servers 208.67.222.222 , 208.67.220.220;
	option routers 192.168.1.1;
	range 192.168.1.70 192.168.1.80;
	}
# Local Network
subnet 10.0.0.0 netmask 255.255.255.0 {
	option domain-name-servers 208.67.222.222 , 208.67.220.220;
	option routers 192.168.1.1;
	range 10.0.0.80 10.0.0.100;
	}


```

The service ifconfig is this

```

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:49:AB:45:7D  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:49ff:feab:457d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24989655 (23.8 MB)  TX bytes:33955819 (32.3 MB)
          Interrupt:20 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:13:49:AB:CE:A3  
          inet addr:10.0.0.88  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:49ff:feab:cea3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107709 (105.1 KB)  TX bytes:270219 (263.8 KB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5192 (5.0 KB)  TX bytes:5192 (5.0 KB)

```

But the Client gives a message of Network is Unreacheable.

The ifconfig is this
```

eth0      Link encap:Ethernet  HWaddr 00:16:E6:82:54:D6  

          inet addr:10.0.0.100  Bcast:10.0.255.255  Mask:255.255.0.0

          inet6 addr: fe80::216:e6ff:fe82:54d6/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:397 errors:0 dropped:0 overruns:0 frame:0

          TX packets:467 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:149605 (146.0 KB)  TX bytes:56732 (55.4 KB)

          Interrupt:10 Base address:0xc000 


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:411 errors:0 dropped:0 overruns:0 frame:0

          TX packets:411 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:21436 (20.9 KB)  TX bytes:21436 (20.9 KB)

```

---

