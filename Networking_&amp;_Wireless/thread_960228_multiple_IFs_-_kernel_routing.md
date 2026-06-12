---
title: "multiple I/Fs - kernel routing"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by showe1966 on 2008-10-27
Dear All,

Ok I am sure we are all very appreciative of kevins hard work in letting us use the  command line, not the network manager GUI.

However, what i need is a quick and dirty fix.

Strikes me what is going wrong with the GUI and multiple interfaces is the routing.

I would therefore like to add a line to my /etc/network/interfaces that tells my computer which is the default interface to use for accessing the "big wide world".

So, how do I do that if I am using a wireless network ath0 , wpa and the network address is set via dhcp ?

I will be wanting to use my other wired interface, eth0, for all addresses on my internal network that is of the type 192.168.1.X

I recall from previous experience how it is all supposed to work:-

You need to sell the computer to look on eth0 for all network addresses in the 192.168.1.X subnet .
Then you need to tell the computer to look on ath0 for all the other addresses you can think of.

Apropos to the dns gui overwriting your manually set DNS list, would it be possible to chmod the dns file so it couldn't overwrite it ?
That might be handy in certain circumstances.

---

