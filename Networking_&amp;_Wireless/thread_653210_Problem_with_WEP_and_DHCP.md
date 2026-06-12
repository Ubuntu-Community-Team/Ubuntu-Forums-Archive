---
title: "Problem with WEP and DHCP"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by prensing on 2007-12-29
I got a new laptop and installed Gutsy (64-bit) from scratch. This is a Thinkpad with the Intel wireless. The wireless worked fine in a couple of different situations (WEP, no WEP), but after a few weeks stopped working.

The setup is a simple 802.11g network with a shared 128-bit WEP key. The wireless driver is ipw3945. I have two different wireless routers at home (a SMC box and one on my DSL modem). I also tried at work against a Linksys and had the same problem.

When I bring up the interface, I see the network light flash a bit as it scans for the station. It then goes solid on. Looking at iwconfig, it has associated with the desired network with excellent signal (I am about two feet away when experimenting ;-). However, nothing I tried would get it to give me a DHCP address.

I did finally "fix" the problem. On a whim, I disabled dhcp3-client and install dhcpcd. That seems to work, but I don't really understand why. Now, the card associates with my access point and gets an address pretty much right away. 

If anyone has a thought on what the really problem might be, I would love know try to figure it out.

---

### Post by spd106 on 2007-12-31
Maybe there was a problem with dhcp3. To learn what was going wrong you'd probably have to inspect the dhcp packet exchange with Wireshark. It's not going to be trivial to do, but it could be a great learning experience.

It might be worth collecting as much information as you can, such as steps to repeat. Then file a bug report on launchpad.

---

### Post by prensing on 2008-01-02
Unfortunately, it stopped working the next day. I am thinking that the real problem is fundamentally noise in the packet stream. Even when it was working, I would get about 8-10% packet loss (with ping). If I sniffed with Wireshark, there were frequent bad packets on the interface, usually around 100 byte long; they appeared to be junk.

Thanks for any suggestions.

---

### Post by prensing on 2008-01-05
Well, I think I have at least some of the solution. I discovered that there is a firmware upgrade for my Westell DSL/Wireless modem. I have applied that, and I can now get my wireless to work, at least for a bit. Hopefully this will continue.

For reference, the following link helped:

[http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&docid=125CFDEB0AFE10E1E0401E0A55174E79&journalid=BC50966C27EA11DB96E995E8363E7F84&l=en&s=gen&~f=lg](http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&docid=125CFDEB0AFE10E1E0401E0A55174E79&journalid=BC50966C27EA11DB96E995E8363E7F84&l=en&s=gen&~f=lg)

---

