---
title: "ethernet in laptop does not work"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by vinthund on 2005-07-27
hello,

I am just starting to use hp compaq nx 7000 laptop. Of course the first thing to do was installing ubuntu and it went fine, set correct resolution by itself (even though it is not typical, 1680x1050). Well, anyway, there is however a problem with networking. It does not work. :>

In my network setting I have activated two interfaces: wireless and "normal" ethernet. I do not know whether wireless works as I had no opportunity to check this, but ethernet does not. Both are set to be configured with DHCP and both are activated. There is a flashing network icon on my upper panel and when I click on it it says: "connection: lo" (and no alternative). It DOES DO something as below I see: received 7544 packages, sent 7544 packages and some KBs with it. But that is not whai I need because there is still no response from the outside world.

During installation net (DHCP) did not work. And it is the same with every boot - I have to wait when my computer tries to connect for a minute or so byt anyway if fails to connect and continues with loading system.
I am using the very same internet cable on my desktop computer at the moment and as you can see it works fine both in Ubuntu and in Win98SE.
Maybe it is a hardware problem? When I boot my laptop reports: 
```
- ide 2 I/O resource 0x3EE - 0x3EE not free
- ide2 ports already in use, skipping probe

```
I did not see it on my other machine so maybe thet has something to so with my problem?

I hope you can help me because if it turns out to be a hardware failure the I shall have to bring it back to vedor,

regards,

Marek

---

### Post by spd106 on 2005-07-29
These NICs should work out of the box. 

Check the output from lspci. It should let you know what's been detected. Also check your router is set up to give out ip addresses and they are available. 

If you're using crossover cable or manual ip config make sure they are on the same subnet.

Can you ping the local network machine? if not an outside domain, such as cisco.com? 

It might be useful to post the ifconfig output and maybe some details as to you setup plus what you've already tried. Also try looking in the /etc/network/interfaces file.

Good luck

---

