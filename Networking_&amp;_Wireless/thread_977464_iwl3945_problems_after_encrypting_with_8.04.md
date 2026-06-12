---
title: "iwl3945 problems after encrypting with 8.04"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by sidestrand on 2008-11-10
Last weekend I upgraded to Ubuntu 8.10 and felt pleased with myself - it all went smoothly.  I then found that I had a problem with ruby / rails which meant downgrading.  To cut a long story short I decided to reinstall 8.04 but to use the alternative CD and encrypt while I was at it.  Again this went OK except that my iwl3945 no longer sees any wireless networks.

The card is recognised by the system, but it won't work.  If I choose 'Connect to another wireless network' and enter all the details, the nice little indicator spins round and round but neither of the lights light up, after a while it will prompt me for the network name, WEP etc.  The odd thing is that my wireless network then appears, but never with any signal strength, and it won't connect.

It was all working perfectly before under both 8.04 and 8.10.

I've tried ifdown wlan0 / ifup wlan0 / iwconfig etc.  I get the message "ignoring unknown interface wlan0=wlan0" with ifup and 'unconfigured interface with ifdown.

This morning I tried running the 8.04 live cd which used to bring up wireless no problem, but today it didn't work.  I then tried a live Mint CD from May 2008 and it worked perfectly.  I installed Mint and it still worked perfectly.

I then tried the Ubuntu 8.04 both live and as an install but nothing doing.

When I boot I am getting a message I can barely read (goes past too quickly) but is like ... cannot terminate rx iwl3945

Any offers for help?  This is really, really frustrating! :confused:

Thank you.

Richard

PS: I'm using Ubuntu on my laptop, which is where the problem is.  The laptop is a Samsung Q45 - I've overcome the install etc. problems before and had it working fine.

---

