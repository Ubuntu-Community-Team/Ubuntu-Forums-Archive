---
title: "ssh or sftp through ipv6? how?"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by eks on 2008-11-17
My ip is NAT'ted at the ISP level. All users are inside a big fiber optic WAN. It works for everything but, obviously, I cannot set up a dynamic DNS because I cannot set port forwarding at the host router to connect from work to the home computer.

My ISP though does provide me an ipv6 address, as does my network at work. But how do I connect to another host using an ipv6 address? I've quickly tried ssh, sftp, filezilla and just using an ipv6 address instead of an ipv4 would not do the trick.

What am I missing?

And what is a tunnel broker? Do I need one?


Thanks!
eks

---

### Post by eks on 2008-11-18
bump

---

### Post by eks on 2008-11-18
So on the Ubuntu end, to access ipv6 web, installing aiccu and creating a [sixxs.net]("http://www.sixxs.net/") account did the trick.

Now I have to configure the winxp machine work. :P

(But it was a quite funny surprise to see the jumpy Google logo at ipv6.google.com!) :D

---

### Post by rgeddes on 2008-11-21
hi,

I'm also interested in learning how to connect to the ipv6 network.

After reading:

[http://tldp.org/HOWTO/Linux+IPv6-HOWTO/index.html]("http://tldp.org/HOWTO/Linux+IPv6-HOWTO/index.html") 

I got an idea of the tools involved but I still have a problem mapping the functionality of ipv4 to ipv6 addresses.

The easy one was the loopback address ::1
I could 
- ping the loopback: ping6 -I eth0 ::1
- ssh the loopback: ssh -6 ::1

assuming that all addresses with the same prefix (network address) can see each other, I assigned a ULA address to 2 machines on my network:

sudo ip -6 addr add fd0f:8b72:ac90::1/48 dev eth0
sudo ip -6 addr add fd0f:8b72:ac90::2/48 dev eth0

and tried to ping6 across the network... and got no reply.  These to hosts connect up through a DLink DI-604 broadband router which I'm pretty sure is not ipv6 capable.  I'm not sure if the address config or the router is the problem in this case.

Can you help me troubleshoot?

Thanks,
Richard

---

### Post by eks on 2008-11-22
Well, I have zero experience with it, I'm just a graphical artist trying to connect work and home machine with ipv6. :)

What I've found so far is that you still need a ipv6 tunnel broker today since most ISPs do not provide an ipv6 address. Take a look at sixxs.net, they do have tunnels on the USA:

[http://www.sixxs.net/pops/](http://www.sixxs.net/pops/)

And they have a tool for automatic configuring the tunnel for you, called AICCU. It's on the repositories. On Ubuntu I've just installed it and placed the account I've created on the site. And that's it.

On the WinXP you just need to install a TAP driver to make AICCU work. The problem I'm having there is some other network problem over the work router or firewall, which I don't have access... :P

EDIT: AFAIK, if your ISP does not automatically gives you an ipv6 address, you will need a tunnel broker: [URL="http://en.wikipedia.org/wiki/List_of_IPv6_tunnel_brokers"]http://en.wikipedia.org/wiki/List_of_IPv6_tunnel_brokers
[/URL]
And, AFAIK again, the ipv6 address should be something like this on ifconfig, for whichever adapter you might be using to connect:
```
          inet6 addr: 2001:1418:100:2be::2/64 Scope:Global
```

The important part is the Scope, which should be Global. Ubuntu, Firefox, Filezilla, open-ssh, all seem to be already ipv6 friendly. The problem mostly is still on the network.

---

### Post by rgeddes on 2008-11-23
Thanks eks,

I registered with SixXS and am waiting for confirmation.  Looks simple.  

Most of the posts I've seen about IPv6 on the Ubuntu forum are about how to disable it, giving the impression that ipv6 is inferior to ipv4, when in fact, ipv6 should provide a performance boost in general as each packet does not require crc integrity checks and the "flows" feature should make moving big blobs of data more efficient.  I think it might be the dual stack(running ipv4 and ipv6 at the same time) implementation that seems to be creating this issue or bad configuration.

Anyway, I'd like to get ipv6 going to understand how to use it... it does have it's own quirks (some of the information is already deprecated and I've seen many tutorials that just focus on the history... not enough ip numbers in ipv4... blah, blah, blah...) but nothing that maps the functionality of ipv4 to ipv6 in a common sense way... at least to me.

R

---

### Post by eks on 2008-11-24
> **rgeddes said:**
> 
Anyway, I'd like to get ipv6 going to understand how to use it... it does have it's own quirks (some of the information is already deprecated and I've seen many tutorials that just focus on the history... not enough ip numbers in ipv4... blah, blah, blah...) but nothing that maps the functionality of ipv4 to ipv6 in a common sense way... at least to me.

Yes, I agree. The lack of information "for end-users" is big. When you search you find lots of in depth information and RFCs, information usefull if you are IMPLEMENTING ipv6, but useless if you are just trying to use it.

Which really seems very simple BTW. I'm planning to write a tutorial here on the forums when I make it work, but it depends on my network administration to see where/why the ipv6 packets are being blocked on the work network... :P

---

### Post by raghu196 on 2010-12-23
Hi eks, 
     i am trying to build a test suite for testing IPv6 applications. It would be of great help to me if you could share your IPv6 tutorial.

Thanks,
Ragz

---

