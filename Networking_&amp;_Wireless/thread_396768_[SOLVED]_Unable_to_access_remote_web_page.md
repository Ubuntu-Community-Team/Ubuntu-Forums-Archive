---
title: "[SOLVED] Unable to access remote web page"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by stalker145 on 2007-03-29
I don't even know where to begin with this one...

I have a three computer network that sits behind a NetGear WGR614 v6. I am able to access my web page via the **private** IP, but I am unable to access via the **public** IP. Even the server itself can't get to the page via the **public** IP. I can ping my **public** IP, I've double and triple checked the port forwarding, so I'm positive that those are correct. 

I can confidently say that they are *definitely* correct because, get this, people from the outside world can get to my web site. :confused: 

So, does anyone have any sort of idea as to what could possibly be amiss here? Thanks for looking and thanks for your help.

---

### Post by stefan.ciobaca on 2007-03-30
My guess is: it's a firewall issue.

From the spec:
"Firewall:
    * Stateful Packet Inspection (SPI), DoS Attack Protection"

Maybe you get filtered out because of overly engineered firewall rules. You could begin by trying to disable the firewall (or checking its rules) on the router.

---

### Post by Mr. C. on 2007-03-30
Many consumer routers do not provide support for NAT loopback.  If your router does not support this, you cannot access the WAN inteface address via the LAN.  You must use LAN IP addresses to communicate with your server.

MrC

---

### Post by stalker145 on 2007-03-31
> **stefan.ciobaca said:**
> My guess is: it's a firewall issue.

From the spec:
"Firewall:
    * Stateful Packet Inspection (SPI), DoS Attack Protection"

Maybe you get filtered out because of overly engineered firewall rules. You could begin by trying to disable the firewall (or checking its rules) on the router.

My router defaulted to SPI disabled. Just for fun I tried to enable the SPI and received the same error... go figure. Reinstate the disabled SPI and lo and behold, still can't get to my web page. That and the block services/sites settings are the only real things on my router that I can think of that May effect this and neither of those are being used. (We really need to get a smiley that scratches its head... lol)

> **Mr. C. said:**
> Many consumer routers do not provide support for NAT loopback.  If your router does not support this, you cannot access the WAN inteface address via the LAN.  You must use LAN IP addresses to communicate with your server.

MrC

It's not technically a NAT loopback. The router sends my domain name out to the DNS servers which send the request back to my router, translate to NAT/Port Forward and the connection is made... in theory
The odd thing is that I was previously able to type my web domain into FireFox and access my page. I seriously can't figure this out. There aren't that many settings in this lil' old router and I think I've tried them all. I guess I'll just live with using the private IP from my LAN and the public from outside.

---

### Post by Mr. C. on 2007-04-01
> **stalker145 said:**
> 
It's not technically a NAT loopback. The router sends my domain name out to the DNS servers which send the request back to my router, translate to NAT/Port Forward and the connection is made... in theory

It is.  Let's clarify. Your router does not send out your domain name directly.  Your linux system's resolver creates a query, and asks the name server in /etc/resolv.conf to perform a lookup.  The router just sends IP payloads.  That lookup occurs using a public DNS server.  That server returns an A record, which would be your WAN IP (the address provided by your ISP; unless you have mis-configured DNS to have a public DNS server return a private IP).

I will repeat... if your router does not support the ability to address your LAN IP via its WAN IP, this will not work.  And guess what, your router does not.  From page 6-6 of your router's documentation:

```
Local computers must access the local server using the computers&#8217; local LAN address
(192.168.1.33 in this example). Attempts by local computers to access the server using the
external IP address (172.16.1.23 in this example) will fail.
```

> **stalker145 said:**
> 
My router defaulted to SPI disabled.
No, it does not.  SPI is enabled by default on virtually all routers that support SPI, and this is true of your WGR614v6 router.  Your manual clearly indicates not to disable SPI unless there are special circumstances.

> **stalker145 said:**
> 
The odd thing is that I was previously able to type my web domain into FireFox and access my page. I seriously can't figure this out. There aren't that many settings in this lil' old router and I think I've tried them all. I guess I'll just live with using the private IP from my LAN and the public from outside.
I think by and large, you are a bit confused by how these things work.  Read your manual cover-to-cover; this may help clarify some things.

MrC

---

### Post by stalker145 on 2007-04-01
> **Mr. C. said:**
> It is.  Let's clarify. Your router does not send out your domain name directly.  Your linux system's resolver creates a query, and asks the name server in /etc/resolv.conf to perform a lookup.  The router just sends IP payloads.  That lookup occurs using a public DNS server.  That server returns an A record, which would be your WAN IP (the address provided by your ISP).

OK, so what you're saying is that Firefox sends my domain name to the DNS servers asking where to find it. The DNS servers then direct FF back to my router... right, just what I said.

> **Mr. C. said:**
> I will repeat... if your router does not support the ability to address your LAN IP via its WAN IP, this will not work.  And guess what, your router does not.  From page 6-6 of your router's documentation:

```
Local computers must access the local server using the computers’ local LAN address
(192.168.1.33 in this example). Attempts by local computers to access the server using the
external IP address (172.16.1.23 in this example) will fail.
```

OK, so, basically, a couple of weeks ago when I was typing my domain name into Firefox and it was resolving to my web page, I was doing something that was not possible? Odd thing, that. Kinda makes me wonder if Habib in India updated my router firmware when he was troubleshooting my router a couple of weeks ago...

> **Mr. C. said:**
> No, it does not.  SPI is enabled by default on virtually all routers that support SPI, and this is true of your WGR614v6 router.  Your manual clearly indicates not to disable SPI unless there are special circumstances.

Well, I don't recall disabling SPI about a year ago when I bought this router. May have happened, but I don't remember. Since the manual states that it's defaulted to on, I guess it must be me making the mistake... Thanks for taking the time to sharpshoot my post instead of offering some sort of fix... Big help.

> **Mr. C. said:**
> I think by and large, you are a bit confused by how these things work.  Read your manual cover-to-cover; this may help clarify some things.MrC

I think you're right about me not understanding **"how these things work"**. I've taken the afternoon as you suggested and read *most* of the manual. I have successfully wasted my time. The need to understand *how* something works is not something that is important to me. Knowing *that* it works and how to get it to *that* state is what is important to me. I can't say that I've really learned anything useful from reading the manual and may actually be shorter a few brain cells.
:lolflag:

---

