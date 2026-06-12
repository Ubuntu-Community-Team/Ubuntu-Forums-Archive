---
title: "How do I know if the network uses WEP, WPA, etc.?"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by oldcpu on 2007-07-07
How do I check if the network uses WEP or WPA or anything at all?

The cable guy is the one that setted up the network.  So I do not know anything.

What does it mean if the network does not use WEP or WPA?  Not secure, I assume, but in what way?

---

### Post by ugm6hr on 2007-07-07
First principles - is it a wifi network?

If someone else set it up for you, but didn't change anything on your computer, it will be unsecured.  This must be true, since a secure network would require some form of password (that you would have had to enter).  The only exception is MAC filtering (which filters on the basis of hardware identifiers - and is debatable if this offers any serious security)

If they did change some settings on your computer, you can just look at your wifi settings (whichever program you use).  Or scan for wireless access points from a wifi computer - it will tell you what security it uses.

This is obviously independent of whether you use Windows / Linux etc.

If your network is unsecured - it means anyone can join the network, and access any shared facilities that you have - generally internet, but also shared files, printers etc.

---

### Post by oldcpu on 2007-07-07
On a wireless network.

No changes where made in the computer.  I can connect right off the bat.

So the Internet, shared files and printer would be accessed by anyone.  But what about the computers themselves?

---

### Post by ugm6hr on 2007-07-07
I'm no networking expert, but whether other network users can "control" your computer is dependent on how your computer firewall etc and network is set up.

The main problem is that if someone hijacks your internet connection to do anything illegal, any criminal investigation will lead to you.  In a more real-world scenario, they are using bandwidth that you pay for...

I'd suggest at least a minimum WEP to dissuade casual internet hijackers, and reading around suggests that WPA is significantly better.  You should be able to set this up easily yourself - just look at the manual for your router/gateway.  Often just a case of going to the router ip (e.g. 192.168.0.1) and changing the encryption.

---

