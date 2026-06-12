---
title: "finding your dns from command line"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by showe1966 on 2006-12-07
The other day I was wanting to find out what my dns was from the command line.
I googled a bit and used the command dig.
But, then I discovered that a "dig" from the command line will only try to look up whatever you have set up in the dns tab of your networking configuration.
So, what I'd like to know is supposing my dns is set wrong and I don't know the right one but I am connected to the internet okay.
What command should I do from the command line to find out the right dns to use ?
Once I have the dns, obviously I just put it in my network configuration and I can surf away as much as I like.
cheeersssss

---

### Post by mips on 2006-12-07
> **showe1966 said:**
> 
What command should I do from the command line to find out the right dns to use ?


Uhm, logical reasoning tells me this is kinda impossible. What you could do is look at what DNS server addresses your router receives via DHCP from your ISP. Your router will most likely pass on it's own IP address as the DNS server. YOur PC will forward request to the router, the router forwards the request to the specified DNS server and then it comes all the way back to your PC.

Another option is to go to your ISPs web site and get the primary & secondary DNS server IP addresses from there.

---

