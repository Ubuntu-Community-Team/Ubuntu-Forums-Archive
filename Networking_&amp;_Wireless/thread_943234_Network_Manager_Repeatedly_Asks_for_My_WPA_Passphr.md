---
title: "Network Manager Repeatedly Asks for My WPA Passphrase w/o connecting"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by meenman on 2008-10-10
Hi, I am kind of new to linux (using ubuntu 8.04), but am picking it up relatively fast.  However, I just installed a new wireless USB device (netgear wg111t), and the network manager keeps asking me to enter the passphrase for my wpa wireless network.

I can see all the networks around my house (including mine).  I can even connect to unsecured networks.  

However, I enter my password in for my network, it acts like it is connecting, and 10 seconds later it ask for my password again, and repeats this loop almost infinitely until it finally gives up.

Please let me know if you have any ideas, I have been trying to google for answers for the past two days and have almost pulled all my hair out.

-Nick

---

### Post by sh_son on 2008-10-10
To start with, I am not a technical person so I can not guarantee that my solution will solve your problem.

I had exactly same problem but found a solution to it;
All I did was change the driver to its native driver from Ralink, of course I was using modified version for RFMON and injection support.

After loading new driver, I could see all the network + the Network Manager did not ask me for password.

1. creating profile in N/work Manager
2. try change driver for your wireless device

Sorry for my bad English; hope it helped;

---

