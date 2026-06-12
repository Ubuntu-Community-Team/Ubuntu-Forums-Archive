---
title: "dyndns and no access to the server"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by uantuzri on 2006-10-17
Hi, 

I installed a LAMP server on an old box recently, now i'm configureing it and I'm having some problems when I try to reach it outside my network.

I followed this [guide]("https://help.ubuntu.com/community/ApacheMySQLPHP") to configure the server, I installed a wiki and everything works when I access it both from the server and other machines on my network as long as I use the servers static IP in the browser. My router has the option to use dyndns.org to make my dynamic IP a static one. So far, everything ok. 

The problem is that when I try to connect to my server with the address configured with dyndns, no connection is made. When I ping it, an IP is found, but I recieve the message:
```
From 192.168.153.1 icmp_seq=1 Destination Net Unreachable
```

Do I have to forward the ports from the router to the server? Do I need something like ddclient even though the router options? Is it something on the Apache config? :( 

As always, I really appreciate any help...

---

### Post by dannyboy79 on 2006-10-17
you need to forward the ports to the server. also, you will want to use the ip of the router, normally given to you by your isp or you can find it by going to a website that tells you waht your ip is or by going into the configuration of the router normally. you are trying to use a lan ip not a wan ip!! you don't need to ddclient if you router supports dyndns.

---

### Post by uantuzri on 2006-10-17
> **dannyboy79 said:**
> you need to forward the ports to the server.

But is it going to be possible to access the internet from the other machines if I redirec the port 80 to the server? I supose the only thing I have to do is redirect the income data.

> **dannyboy79 said:**
>  also, you will want to use the ip of the router, normally given to you by your isp or you can find it by going to a website that tells you waht your ip is or by going into the configuration of the router normally. you are trying to use a lan ip not a wan ip!! you don't need to ddclient if you router supports dyndns.

Ok, I know my ip looking it up into the router's config, but whatfor do I need it?

This is the first server I install and I'm learning networking as problems come... maybe the awnsers are too obvious... Thanks anyway!

---

### Post by uantuzri on 2006-10-17
Ok, I forwarded the port 80 to 192.168.1.88, which is my server's IP. Now, when I type the address dyndns gave me, I access to my router, but not to the server. Any ideas? I know it must be a basic thing, but I don't find it looking up the router's user guide.

---

### Post by uantuzri on 2006-10-18
I did it!

I looked up in forums about my router and after redirecting the router's remote control to another port different to the 80, I had to enter to the router's command line via telnet (I didn't know it had one) and enter "ip nat loopback on". This made my server visible. I don't know what that loopback stuff means, but it is magic for my server :KS

---

### Post by dannyboy79 on 2006-10-18
> **uantuzri said:**
> Ok, I know my ip looking it up into the router's config, but whatfor do I need it?

well if you didn't have dyndns than that's the ip you have to enter into firefox or ie to get to your website. you can't enter a 192.x.x.x because that is an internal ip, lan, Local Area Network, which can't been seen from the outside, that's why you enter the router's ip and forward port 80 to your internal ip, which is your server. 

apparently you got it working, something doesn't sound right though, i have never heard of this setting you're talking about but if you got it working than great. well, i think if you registered your internal ip with dyndns and not your external ip than that's maybe why you had to do this loopback thingy. oh well, it's good you got it working at least.

---

