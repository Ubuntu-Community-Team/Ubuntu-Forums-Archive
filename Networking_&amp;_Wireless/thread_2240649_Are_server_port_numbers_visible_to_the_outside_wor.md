---
title: "Are server port numbers visible to the outside world ?"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by Omnipresence on 2014-08-21
Noobie here,

I have searched the forums but can't seem to find an answer,

I'm using a dell 1950 server running ubuntu and virtual box. A browser is used in virtual box for internet access. 

The server port numbers that are being used on the server are the standard numbers (9001 etc) These numbers are seen as being commonly used by a server. 

My question is: Are server port numbers visible to external websites while surfing the web or will it appear as though I'm accessing via my standard PC ?


Thanks

---

### Post by sandyd on 2014-08-21
> **Omnipresence said:**
> Noobie here,

I have searched the forums but can't seem to find an answer,

I'm using a dell 1950 server running ubuntu and virtual box. A browser is used in virtual box for internet access. 

The server port numbers that are being used on the server are the standard numbers (9001 etc) These numbers are seen as being commonly used by a server. 

My question is: Are server port numbers visible to external websites while surfing the web or will it appear as though I'm accessing via my standard PC ?


Thanks[B]
Moved to Networking And Wireless[/B]

I dont know what you mean by standard numbers, but ports above 1024 are seen as unallocated service ports - which means they can be used by any application.

Of course, if you are behind a NAT device such as a home router, then that point is moot as NAT translates your internal port to something else entirely.

---

### Post by Omnipresence on 2014-08-21
> **sandyd said:**
> 
 ports above 1024 are seen as unallocated service ports

What are ports below 1024 commonly seen as ? Server ports ?

I was under the impression that port numbers around the 9001 mark are seen as commonly used by servers as I'm guessing that port numbers used on standard PC's are in a different region of numbers.

I access the server from my home router but the server uses a wireless dongle for internet access - I was wondering if port numbers are visible to the outside world in this scenario.

---

### Post by matt_symes on 2014-08-21
Hi

To clarify sandyd's point, ports below 1024 are privileged ports and require elevated privileges (sudo or root) to open them.

Ports above 1024 have no such restriction and can be opened by any service and this is why they are being used by virtual box (or any other VM software).

The point about being behind a NAT is very pertinent because if the VM is using NAT or the host machine is behind a NAT, then the listening ports can be mapped to other ports that will be visible to the outside world. 

This kind of what you generally want. Most web servers want to be listening on port 80 even if they are in a VM on a host machine.

Take a look at this website 

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Kind regards

---

### Post by Lars Noodén on 2014-08-21
> **Omnipresence said:**
> What are ports below 1024 commonly seen as ? Server ports ?

Ports below 1024 need root level access to bind services to listen.  Regular users are free to bind services to listen to anything above that.  The IANA maintains a list of what is generally agreed upon as to [which ports are used by which service](http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.txt).  So port 80 is usually used for HTTP and port 443 usually for HTTPS and 22 for SSH and so on.  Of course you could always run a service on a non-standard port but then you could not connect to it without the client application being pointed to that non-standard port.

---

### Post by SeijiSensei on 2014-08-21
Install **nmap** on a machine and use it to scan a remote machine.  You'll see all or most of the open ports.  For instance, my server would reveal
```

[Seiji@GhostWorld ~]$ sudo nmap myserver.example.com

Starting Nmap 5.51 ( http://nmap.org ) at 2014-08-21 13:23 EDT
Nmap scan report for myserver.example.com (50.116.11.117)
Host is up (0.11s latency).
Not shown: 995 filtered ports
PORT    STATE SERVICE
25/tcp  open  smtp
80/tcp  open  http
110/tcp open  pop3
143/tcp open  imap
443/tcp open  https

```
An extensive list of ports appears in /etc/services.  Programs like nmap sometimes include larger lists of services.

---

### Post by Omnipresence on 2014-08-22
Thank you for your replies,

Unfortunately I am a newbie and much of what is written above is way over my head.

Could someone please explain in layman terms.


I connect to my server through my router. My server has an internet broadband dongle through which I connect to the internet with a browser on a Vm. The server does not share the same internet connection as that router.

My question is: Will the server port number that the server is using be reported to a website that I visit ? Or is the sever port number only used and visible inside my home network ? ( Server - Router Router - Server )

What I am trying to establish is whether a website is aware I am accessing it from a server because of the port numbers used or whether the website thinks its a standard PC or laptop.


Thanks

---

### Post by ian-weisser on 2014-08-23
The concept of 'servers use a port range' is incorrect. Many *services*  use specific ports. Often those services are provided by servers. Many  of those services are clustered below 1024. But many of the same  services are provided by non-servers and use the same port numbers.


The website will have no idea if the query comes from a server, desktop, laptop, tablet, phone, whatever *from the port number*. Regardless of the platform, all queries to the website will use the same port number. All webservers, running or all platforms, default to listen on port 80. And all web browsers default to sending http requests to that port. That's how they connect. Responses are a little more complicated, but suffice it to say that nobody can guess the platform of the web browser from that port number either.

But...the website *can* tell what kind of platform you are using...a different way. Your operating system and browser are included in the http request created by your web browser. The kind of server software that the website uses is included in the http response.

---

### Post by SeijiSensei on 2014-08-23
Every IP packet includes a source address and source port number along with the destination IP and port number. The destination port number is determined by the service you wish to access.  If you're connecting to the HTTP service, you'll send packets to the server's port 80, or 443 if SSL is used.  If you are connecting to an IMAP server to read mail, you'd connect to port 143.  

Ports number 0 through 1023 can only be used the "root" or administrative user.  Anyone can use the remaining ports from 1024 to 65565.  When your browser sends a request to a web server, it randomly selects an unused port from the 1024-65535 range as the source and sends a packet with your IP and that randomly-selected port number addressed to the server's IP and port 80.  So far the server knows your IP and the random port number and a [few other administrative things]("http://www.diablotin.com/librairie/networking/firewall/ch06_03.htm").

All of that happens at what's called the "[transport layer]("http://en.wikipedia.org/wiki/OSI_model#Layer_4:_transport_layer")" in the standard model of network communications.  However applications like browsers have the ability to share any information they want, and the HTTP standard enables both ends of the connection to exchange significant amounts of information.  The server tells the browser what language and character encoding to use for display, whether the browser can cache the object locally, and also provides information about the object like the date it was last updated.  Browsers tell servers which operating system and browser they are using in something called a "[User-Agent]("http://en.wikipedia.org/wiki/User_agent")" string.  Most browsers let you [spoof]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") this item and claim to be connecting with an operating system or browser different from the one you are actually using.  I tell Netflix I'm on Windows so it won't block my connection arbitrarily for using an unsupported operating system.

So the answer to your question is both yes and no.  From the point of view of the transport layer, all the server knows is your IP and the random port your browser selected when it initiated the connection.  Depending on the application you use, the server can learn quite a bit of information about you or hardly any at all.

If you're asking about how a virtual machine appears to a remote server, it depends on what networking model the VM uses.  If it uses "NAT," then packets will appear to come from the host's IP address.  If you use "bridged" networking, where the guest VM has an address on the same network as the host, then requests will come from the guest's address.  If there is an upstream router that also uses NAT to masquerade the entire network behind it, then all requests will carry the publicly-facing IP address of the router.  This is probably the most common situation in offices and homes.  If you're running virtual machines at places like Linode or Amazon you'll have a public IP address.

---

