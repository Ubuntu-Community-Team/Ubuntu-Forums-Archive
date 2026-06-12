---
title: "How to set a static ip?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-21
Hello,

I want to connect to the internet using a static ip in order to later connect to a vpn. I found the network utility on which I set things like this: 
static ip: 192.168.1.7
Subnetmask: 255.255.255.0
gateway address: 192.168.1.1

I also went into my router and I set a static ip for 
Begin port: 7777
End port: 7777
Server ip address: 192.168.1.7

I didn't really know what the ports had to be so I just made something up. When I do this however, I cannot connect to the internet anymore..

What am I doing wrong here?

---

### Post by billgoldberg on 2009-01-21
The static ip you refer to is the ip of your pc in the local network.

If you want a static ip, you'll have to ask your ISP.

---

### Post by kramer65 on 2009-01-21
ah ok.. 

What I want is that I can connect to a vpn. I thought I had to get a static ip for that...

Any tips or hints? I am kinda lost..:?

---

### Post by hyper_ch on 2009-01-21
well, when you gave yourself a static IP in your lan then you very likely did not set a nameserver in the resolv.conf. Add

```

nameserver 192.168.1.1

```

to /etc/resolv.conf

---

### Post by kramer65 on 2009-01-21
Alright, done. But that doesn't help anything..

More ideas?

---

### Post by hyper_ch on 2009-01-21
change to dhcp, run
```

ifconfig

```

post the output here.

---

### Post by theozzlives on 2009-01-21
For now set it back to dynamic, get the IP and other info from your ISP. Then set it up in your router and let your router act as DHCP, use port forwarding to forward your IP to whichever computer you're using. Like my web site is on computer 192.168.1.3, my static IP is 68.15.116.126 and HTTP (but you can do VPN) is being forwarded in my router to 192.168.1.3. You understand now?

---

### Post by kramer65 on 2009-01-21
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:a4:92:3d  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fea4:923d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91464 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:136660267 (130.3 MB)  TX bytes:10527995 (10.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3933 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:197300 (192.6 KB)  TX bytes:197300 (192.6 KB)
```


@theozzlives
sorry, but your tips are a bit too advanced for me.. could you explain it a bit more..? How do I forward the http in my router to my pc?

---

### Post by abyssius on 2009-01-21
> **theozzlives said:**
> For now set it back to dynamic, get the IP and other info from your ISP. Then set it up in your router and let your router act as DHCP, use port forwarding to forward your IP to whichever computer you're using. Like my web site is on computer 192.168.1.3, my static IP is 68.15.116.126 and HTTP (but you can do VPN) is being forwarded in my router to 192.168.1.3. You understand now?

Hi Ozzie

I'd like to try what you suggest (providing a web site from a private IP address). I'm confused by some of your points.

(a) My Internet access is via a cable operator, which provides a public IP to my cable modem via DHCP. Will this IP change even though I never turn it off, or do I have to actually purchase a static IP?

(b) My router (DLINK wireless) doesn't seem to have a specific option for "port forwarding". It does have something called "virtual server" that claims: *Virtual Server is used to allow Internet users access to LAN services.*. It requires entires for: private IP; protocol type; private port; public port and schedule. Is this what I would use?

(c) How do you handle the DNS for your web site? I visited it via your posted IP address. However, I saw you do have a regular domain name as well.

---

### Post by kramer65 on 2009-01-21
I am totally confused here. Do I need the port forward in order to connect to the vpn (which I ultimately want)?

---

### Post by abyssius on 2009-01-21
> **kramer65 said:**
> Hello,

I want to connect to the internet using a static ip in order to later connect to a vpn. I found the network utility on which I set things like this: 
static ip: 192.168.1.7
Subnetmask: 255.255.255.0
gateway address: 192.168.1.1

I also went into my router and I set a static ip for 
Begin port: 7777
End port: 7777
Server ip address: 192.168.1.7

I didn't really know what the ports had to be so I just made something up. When I do this however, I cannot connect to the internet anymore..

What am I doing wrong here?

Hi kramer

There are somethings you need to understand about IP's. First there are public IPs and private IP's. Public IP's are valid on the Internet, Private IP's are for LAN use only - and subsequently are NOT valid on the Internet. An example of a private IP is 192.169.1.7. This IP can never be used on the Internet.

Your router requires two IP addresses one for WAN (Internet) connectivity and another for LAN (local network connectivity).

The WAN (or public) IP address is provided to you by your Internet Access provider. You cannot change this IP address. It belongs to the ISP. Your ISP could assign a static IP to you (meaning that you have a permanent lease of a specific address), but usually for home connections your ISP provides you with an dynamic (changeable) address via DHCP (since static IP's are becoming a precious resource). This means that you cannot always count on this public address remaining the same.

The private IP address of your router is also called the gateway address. This is usually 192.168.1.1 or 192.168.0.1, depending on your router. A typical setup for a computer on your local network might be what you posted:

static ip: 192.168.1.7
Subnetmask: 255.255.255.0
gateway address: 192.168.1.1

This IP address can be set by you manually, or automatically assigned to your computer via your router's DHCP function. If you set IP's manually on your local network, you usually have to disable DHCP on your router.

Also, you can't really assign ports arbitrarily.

I know this doesn't help you with your specific problem, but I hope it gives you a better understanding of what you're trying to do.

If you plan to connect to a VPN, then the VPN provider should furnish you with the instructions on how to access their VPN from your home. This should not require you to change any of your home TCP/IP settings,

I am assuming you are connected to the Internet if you made this post. However, you did say you could no longer access the internet. Based on what you said you did (changed the router's IP address to 192.168.1.7), be aware that if a computer on your network stopped accessing the internet after you did this, it is probably because that computer's gateway address is set to 192.168.1.1 and you changed the gateway address to 192.168.1.7. If this is the case, then I recommend that you change the router's address back to 192.168.1.1 (or whatever it was originally)

---

### Post by cek on 2009-01-21
> **kramer65 said:**
> I am totally confused here. Do I need the port forward in order to connect to the vpn (which I ultimately want)?

I don't know specifically what VPN software you are using, but static IPs and port forwarding GENERALLY aren't necessary.

I connect to my work through a VPN.  My router does NAT, but no port forwarding, no (specific) opened ports in the firewall, and I connect without issue.

---

