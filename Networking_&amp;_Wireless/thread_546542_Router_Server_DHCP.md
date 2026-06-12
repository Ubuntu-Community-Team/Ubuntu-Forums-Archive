---
title: "Router Server DHCP"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by rapollon on 2007-09-09
My apt complex offers free internet, can I configure my desktop to be a dhcp server to provide internet for my router?  

thx,
rudy

---

### Post by x64Jimbo on 2007-09-09
Huh? Routers have their own DHCP server built in. Why would you need (or even want) to run a second one? How does the complex offer the internet connection? If it's an ethernet jack in the wall, just disable DHCP on the router, plug a cable from one of the numbered ports on the back of the router into the wall, and then enjoy the other ports as additional connections to the complex's network. If you want to run your own subnet, you can do that too, but that requires a different setup. If your router is a Linksys, there's a good chance that the DD-WRT firmware will work in it, and that firmware supports all kinds of cool functionality that does not come with the factory firmware.

---

### Post by rapollon on 2007-09-09
Its not an ethernet, its wireless...  I theory I think it can work, I don't have the hardware in front of me to try it yet.  The desktop would provide the wireless internet and I would use my NIC card from the same desktop to the router.  The other computers would then use the same local network to share printers, files and such rather than the community internet.

---

### Post by rapollon on 2007-09-09
:lolflag: Anyone?

---

### Post by x64Jimbo on 2007-09-09
Ok, I think I understand the question now. You want to bridge the wireless network of your complex into a wired network for your own PCs. Correct? 
If so, you should use a Linksys WRT54 series router and install that DD-WRT firmware. It allows bridging local ethernet connections onto a wireless network. Then you don't have to have your main PC turned on in order to connect the other computers to the internet.
The way you are suggesting would work as well - you'd need to look up bridging network connections in Linux.

---

