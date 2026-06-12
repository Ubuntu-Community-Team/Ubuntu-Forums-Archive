---
title: "I need to have an IPv6 address, but my PC doesn't have one(?)"
date: 2015-06-01
forum: Networking &amp; Wireless
---

### Post by blasej on 2015-06-01
I need to port forward my router for my Ubuntu PC so that I can connect to its server. My router will not allow me to port forward for any device unless it has an IPv6 address, and it does not have my Ubuntu PC listed as having one. 

How can I check for an IPv6 address and/or add one to my PC? 

I have some Xfinity router.

---

### Post by the_kernel2 on 2015-06-01
Your router may not be advertising, if this is the case then you can try to add it manually (an IPv6 Addr)

ip -6 addr add 2002:b000:201::1/64 dev eth0 
or something like that. 

If you have an IPv4 addr, and your router probably has IPv6 assignments handy and you can just edit interfaces 

Something like 

auto 6to4
iface 6to4 inet6 6to4 
     local x.x.x.x  <-- your IPv4 Addr. 
Or something like that. 

Try that.

---

### Post by blasej on 2015-06-01
I went back to try port forwarding again, and I found something strange.

On my router's homepage, there are two "connected devices" for my PC: the computer name (username@string of stuff) and a row of groups of two symbols separated by colons. The latter has an IPv6 associated with it, but the former does not. I tried to port forward port 22 for the latter, but I just keep getting an error message? Any idea how to help, or should I just ask my ISP?

---

### Post by blasej on 2015-06-01
Thanks for the help, but I was able to port forward and connect to my server successfully. At least for now.

---

