---
title: "IP Masquerading with Firestarter vs. Squid"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by pmscunha on 2008-10-04
Hi,

I'm new to linux and this is my first attempt to use Ubuntu (8.04) together with Firestarter for connection sharing.

My system consists of the following:

My Ubuntu machine is connected to the internet provided by my university. The other ethernet interface is connected to a wireless router using static IP and I then connect all of the other machines to the wireless router.

The problem is that my university does not allow me to run my own private network, nor wireless nor wired. So I thought I could use Firestarter with connection sharing to get around the problem. But a friend of mine said that that wont work because of how Firestarer keeps tracks of the packets.

He claims that Firestarter works by replacing the ipaddress (of a computer in my private network) in the packets header with the ipaddress of the gateway. But to know where the packet came from it also adds the original ipaddress somewhere in the header. So the university routers will know that the packet came from a private network because of the original ipaddress in the headers.

Is this correct or is it done by the gateway simply keeping a local table of where the packets came form?

If the former is correct then I was wondering if I could use Squid to get around this problem by setting it up as an anonymous proxy. If I can does anyone know of a good tutorial that would help me to set that up on my system?

Cheers,
Pedro

---

