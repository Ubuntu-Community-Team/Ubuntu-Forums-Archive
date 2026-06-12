---
title: "DNS server? (BIND9) or not needed..."
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by mhouston100 on 2008-06-13
Hi guys, I'm having a bit of trouble nailing down exactly what I need to do, and it may be that I've bitten off more then I can chew.

Basically, I have a static IP address assigned to my router 202.76.140.### and all my PC's connected via that.  I have a webserver running on one, accessed via a temporary domain name from NO-IP.com and port 80 forwarded through the router.  I have several other services (SSH FTP etc) working through port forwarding as well.

No I just registered a domain name example.com.au and what I want to achieve is example.com.au:80 to go to the webserver, example.com.au:22 go to SSH etc but I also want to be able to access each individual PC e.g server.example.com.au, laptop.example.com.au for ftp and VNC sessions etc.

No will I need to set up my own DNS server for this?  From my readings it would seem so, though all of the tutorials I have seen seem to offer more then I need (DNS mirroring etc).

Can someone point me in the right direction and maybe even some hints on how to start.

I have BIND9 install and administer it via webmin, though I'm a bit at a loss as to how to point my example.com.au to my 202.76.140.### address, and what to do from there.

Here is my guess so far.  

1. Setup the DNS pointer through [http://www.intaserve.com/](http://www.intaserve.com/) (registrar) to point to my address 202.76.140.###

2. Setup my router's DNS settings to point to my server on 192.168.1.68

3. Setup a BIND9 server with a zone example.com.au

4. add all of the hosts in as pointers e.g server.example.com.au

5. END?!?!?

I'm guessing I wont need port forwarding etc anymore as using DNS entries would forward all ports for say laptop.example.com.au to the IP address specified in the pointer?

Thanks in advance for your help guys.

-Matt

---

### Post by kidders on 2008-06-15
Hi there,

> **mhouston100 said:**
> I also want to be able to access each individual PC e.g server.example.com.au, laptop.example.com.au for ftp and VNC sessions etc.That'll work fine internally, but since you only have one public IP address, none of the subdomains will work from outside your LAN, because you only have one place to point them.

The best you'll be able to achieve is to point *.example.com.au to 202.76.140.xxx, and forward packets to the correct internal IP based on the service being accessed. So, for instance, if you're running two SSH servers behind your router on port 22, there is no way to make them both accessible from the public side on the same port (because you can't bind more than one server to the same port/IP).

> **mhouston100 said:**
> will I need to set up my own DNS server for this?No, but it can be handy. It's much easier to make changes when you have a single point of control over name resolution.

> **mhouston100 said:**
> I'm a bit at a loss as to how to point my example.com.au to my 202.76.140.### addressYour domain registrar should have set that up for you. A local DNS server will only be of use to people inside your router, so if you don't already use one, there's no reason to set one up now. Having said that, if you *do* want to run one, the steps you outlined seem fine.

> **mhouston100 said:**
> I'm guessing I wont need port forwarding etc anymoreIP doesn't work that way. Basically, it's impossible to address a packet to a hostname. Let's imagine I open a terminal (here in Ireland) and run "ftp laptop.example.com.au". My computer will perform a lookup, and assuming your DNS is correctly configured, laptop.example.com.au will resolve to 202.76.140.xxx. My computer will then start sending packets on port 21 to your router, which will have to decide where to route them, based solely on the information they contain (eg origin/destination IP, origin/destination port number, etc).

I hope that helps.

---

### Post by mhouston100 on 2008-06-16
> **kidders said:**
> 

IP doesn't work that way. Basically, it's impossible to address a packet to a hostname. Let's imagine I open a terminal (here in Ireland) and run "ftp laptop.example.com.au". My computer will perform a lookup, and assuming your DNS is correctly configured, laptop.example.com.au will resolve to 202.76.140.xxx. My computer will then start sending packets on port 21 to your router, which will have to decide where to route them, based solely on the information they contain (eg origin/destination IP, origin/destination port number, etc).

I hope that helps.

Thanks for the comprehensive reply!

The way I worked it out in my preliminary research was that I would assign my server the outside address, so 202.76.140.xxx would become the external address of my server (dns server / router that is, by putting a modem into the server directly, or setting an external one to bridge mode) and that address would be assigned example.com.au.  So then all DNS queries for *.example.com.au would come to MY DNS server, from there I could assign laptop.example.com.au to 192.168.1.60 and MY router / DNS would know how to get it there.... so even though it would need to go to a 192.168.*.* address, in the routing tables it would know that it needs to go through the 202.76.140.xxx address first...

I'm not sure if i'm explaining myself well here but basically I thought that everything inside of my DNS server would be reachable because my DNS server knows where it is and it can be reached by the outside world.  I guess this is what you were saying would not work because packets are addressed to the IP and not the hostname so therefore everything would just come to the 202.76.140.xxx address???

I guess what im saying is that if my server receives a query for laptop.example.com.au it knows that its 192.168.1.60 and therefore knows how to complete the route and vice versa, your computer knows that *.example.com.au is located at 202.76.140.xxx  so it just send it all to my router to take care of the details?

Thanks again for the reply, hope you can help me out with some more info :)

---

### Post by kidders on 2008-06-17
> **mhouston100 said:**
> all DNS queries for *.example.com.au would come to MY DNS server, from there I could assign laptop.example.com.au to 192.168.1.60There's a small flaw in your idea ... 192.168.1.60 is a reserved IP, for use only on private networks, so packets destined for that address will never make it to your router.

Unfortunately, there's just no getting around the fact that a computer must have a unique IP in order to be addressable. Depending on what kind of internet connection you have, you could possibly ask your service provider for more IP addresses. Failing that, using port forwarding to create the illusion that there's a single PC at your public IP address is your best alternative, I'd say.

---

### Post by mhouston100 on 2008-06-18
Kidders::

The more I thought about it and the more I read about it the more your information made sense.  So basically I will be just forwarding the domain to my router and continuing to use port forwarding...

Thanks for clearing that up for me man!

---

