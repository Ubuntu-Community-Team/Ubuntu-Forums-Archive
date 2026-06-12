---
title: "Yet Another Wireless Problem"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by mr_stabby on 2005-08-03
Hello,

I seem to be having bit of a wlan problem. My dongle is setup alright and I can see everything's alright when I ifconfig and iwconfig and can ping other PC's and my router. However, I can't do much else. My thoughts are that it must be a WEP/ESSID setting problem but I can't seem to identify what's wrong. I don't want to have to change the key because 3 other desktops are dependent on the router pretty much all the time and I'm lazy. The key is a 26-character numerical string - how does this need to be specified for iwconfig (it's already in hexadecimal isn't it?)

Anything else I'm doing wrong?

Thanks,
Louis

---

### Post by ProNoblem on 2005-08-03
If you can ping your internal network, the wireless connection seems to be working so the problem is probably in your wireless ip configuration.

It looks like you haven't set your gateway or subnet mask correct (the gateway is the 'door' to other networks like the internet and the subnet mask sets the range of your internal network)

For instance, if you have an internal IP 192.168.1.1, with a subnet mask of 255.255.255.0, it thinks that all the 192.168.1.X adresses are internal. (If the subnet mask was 255.255.0.0 then all the 192.168.X.X adresses were internal)
If you tried to reach a system with the IP-adress 192.168.[COLOR=Red]2[/COLOR].1, it recognizes that adress as being outside of your internal network, and tries to go through the gateway (the 'door' to other networks).

That said: Try to compare the output of ifconfig with a working PC's output of ipconfig (windows) or ifconfig and make sure that you have the same values set for DNS, Gateway and subnet mask.

---

### Post by mr_stabby on 2005-08-03
ProNoblem,

Thanks for your reply. Fairly sure my IP configuration is alright - I'm static on 192.168.1.7 and the gateway is set to 192.168.1.1 with the subnet as 255.255.255.0 and all other PC's follow suit.

Think it might be that I haven't provided my WEP in hexadecimal format - I've spent ages trying to find a utility to convert a 26-char decimal to hex so I'll give that a go when I get home.

Cheers.

---

### Post by ProNoblem on 2005-08-03
My understanding of a WEP/WPA/etc. key is that it should be correct if you can reach the other PC's, it (kinda) acts as a normal ethernet cable only then through the air.

The situation would be like this:
[Computer]----[ethernet cable]----[router]----[internet]
And with a wireless connection it would be:
[Computer]----[WiFi connection]----[router]----[internet]

So if you can ping the other computers, you can reach the router, because that router would send the signal through to the other computers. Because you can ping the other computers: Your wireless connection is set up correctly.

Another option you could check is the possibility that there are different profiles in your router for wired and wireless connections. My router (Asus WL500G) also has this, ment for extra protection so that open wireless laptops cannot access some parts of the network. It could be that the wireless configuration is not set-up correct.

P.s. Does your router use DHCP (automatic IP-adresses), or do you assign them manually on your clients?

---

### Post by mr_stabby on 2005-08-03
Ah, I thought that the WEP key was only used to provide encryption for transmitted data and a connection (or at least communication) could be present without the correct key.
[In your example, how do you connect to an unsecured wlan?]

I assign the IP addresses myself - but only so that I know what's what instantly. Unsure about router profiles, only ever plugged anything into the ethernet ports once.

---

### Post by gruepig on 2005-08-03
WEP keys provide *both* authentication to access the wireless network and encryption.  I agree with what has been said previously; if you have any IP level connectivity (e.g., can ping your router), it's not a WEP issue.

It sounds like a routes problem.  Run 'route -n' to see your route table.  You should have two routes.  Something like:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

What happens when you ping a host outside of your network by IP address?  Try  'ping 64.21.33.9'.  If that works, you have IP connectivity and most likely your problem is a DNS problem (check /etc/resolv.conf and make sure you have a nameserver listed and can ping it).

If ping fails, try 'traceroute 64.21.33.9'.  What's the last host you get a response from?

---

### Post by mr_stabby on 2005-08-04
[QUOTE=gruepig]WEP keys provide *both* authentication to access the wireless network and encryption.  I agree with what has been said previously; if you have any IP level connectivity (e.g., can ping your router), it's not a WEP issue.

It sounds like a routes problem.  Run 'route -n' to see your route table.  You should have two routes.  Something like:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

What happens when you ping a host outside of your network by IP address?  Try  'ping 64.21.33.9'.  If that works, you have IP connectivity and most likely your problem is a DNS problem (check /etc/resolv.conf and make sure you have a nameserver listed and can ping it).

If ping fails, try 'traceroute 64.21.33.9'.  What's the last host you get a response from?[/QUOTE]
 Ok, my routing tables seem ok, I can ping external IPs and I have a pingable nameserver listed in /etc/resolv.conf.

It seems like it pretty much works then but I can't get it to work with any of my other apps and do anything useful. Think I'm being quite a spacker here. Do I have to set a default gateway or anything?

---

### Post by mr_stabby on 2005-08-05
*bump*

Anyone got any ideas on what I'm doing wrong? Still no further. What DNS entries should be in my resolv.conf?

Thanks,
Louis

---

### Post by blakamin on 2005-08-05
dont know if this will help but this is where i go for wireless problems...

[http://forum.remote-exploit.org/](http://forum.remote-exploit.org/)

knoppix based

---

### Post by mr_stabby on 2005-08-05
[QUOTE=blakamin]dont know if this will help but this is where i go for wireless problems...

[http://forum.remote-exploit.org/](http://forum.remote-exploit.org/)

knoppix based[/QUOTE]
 Cheers, can't browse it at work though :(

---

### Post by ProNoblem on 2005-08-05
Check if you have the following line in your /etc/resolv.conf:
```
nameserver 192.168.1.1
```
(replace 192.168.1.1 with your router IP)

Most routers also work as a DNS, so if the DNS settings are correct in the router (which is likely, because your other PC's can resolve domainnames) then you'll be able to resolve domainnames and use the internet.

[QUOTE=blakamin]dont know if this will help but this is where i go for wireless problems...

[http://forum.remote-exploit.org/](http://forum.remote-exploit.org/)

knoppix based[/QUOTE]
I should say that we're past the wireless problem (there never was a wireless problem), this is a global network setting-problem instead :)

---

### Post by mr_stabby on 2005-08-06
[QUOTE=ProNoblem]Check if you have the following line in your /etc/resolv.conf:
```
nameserver 192.168.1.1
```
(replace 192.168.1.1 with your router IP)

Most routers also work as a DNS, so if the DNS settings are correct in the router (which is likely, because your other PC's can resolve domainnames) then you'll be able to resolve domainnames and use the internet.


I should say that we're past the wireless problem (there never was a wireless problem), this is a global network setting-problem instead :)[/QUOTE]
 My router's IP (which incidentially is 192.168.1.1) is listed in my resolv.conf. I can get it to assign me an IP via DHCP etc. but it still doesn't want to do anything useful.

Are there any other network settings which I hve not yet played with? Is there any possibility that I need to set up or even enable my eth0 interface as well as my wireless eth1 interface? I just can't think of any reason for this not to be working since, as you say, the connection seems to be alright.

Any ideas greatly appreciated.

---

### Post by gruepig on 2005-08-08
[QUOTE=mr_stabby]Ok, my routing tables seem ok, I can ping external IPs and I have a pingable nameserver listed in /etc/resolv.conf.

It seems like it pretty much works then but I can't get it to work with any of my other apps and do anything useful. Think I'm being quite a spacker here. Do I have to set a default gateway or anything?[/QUOTE]

If you can ping external IPs, you already have a default gateway.  It sounds like everything is working except DNS resolution (translation from hostnames to IP addresses and vice versa).

Since you can ping the nameserver listed in /etc/resolv.conf, that means it's on the network and accessible.  But is it running a nameserver?  Nameservers run on port 53, so you can use 'telnet <nameserver> 53' to verify that a nameserver is running.  If you get a "connection refused" message, the host listed in /etc/resolv.conf is not a nameserver, and you need to modify the file so it contains the IP address of a nameserver which is valid for you to use. If the host is running a nameserver, you should see a message indicating that you are connected.  (Use control-] to disconnect.)  

Just because there's a nameserver running, that does not mean you have access to run DNS queries against it.  So the next thing you need to test is whether you can resolve hostnames.  To test this, you'll want to use a program like 'host' or 'nslookup'.  For example, try 'host ubuntuforums.org' or 'nslookup ubuntuforums.org'.  If DNS is working properly, this should return the IP address 64.21.33.9.  If it doesn't, post the error.

---

