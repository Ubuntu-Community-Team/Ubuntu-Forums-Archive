---
title: "Is wireless network on Dial up possible, if so how?"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by skew on 2007-07-05
I am looking for some advice in regards to setting up a wireless network in my home. 

   Here are my particulars. I have one desktop and one laptop with a built in wifi card 
(see laptops lspci capture below). I don't as of yet have any wireless hardware for the desktop and was hoping for some advice in regard to hardware for that machine as well. The desktop runs dapper and the laptop feisty. Finally, the monkey wrench thrown into the works is that I don't have a broadband connection to the net or the ability to get one in my area. What this means is my net connection is dialup only. 

Questions: Can I get a wireless network working? Can I get internet connection sharing with only my dialup net access? How do I do this?

 I do also have a WRT54G v8 but it claims it will only work when a broadband connection is present. One final addition. I do currently have a wired network working between the two machines but the idea of forever dragging a ethernet wire around the house is highly undesirable.

Thanks,
Steve

Laptop

lspci capture:

05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

---

### Post by arsenic23 on 2007-07-05
Ok, I've only ever made wireless dailup once, and that was a good way back using windows PCs, but I don't think it should be very difficult with your currant setup.  You may need to buy a second wired NIC for your PC, though, if you want to keep the two networked properly.

What I did was connect to my PC with two NICs to the internet and then share the dailup though one of the NICs (you should be able to do this using firestarter).  That NIC is then pluged into the internet port on the router.  The second NIC is plugged into one of the routers network ports to keep it on the network, and that should be it.

Again, I've only tested this with window's connection sharing and a WRT54Gv2, so your milage may vary.  Should work though, I think.  Anyway, you can test it out without the seoncd NIC so it won't hurt to try.

---

