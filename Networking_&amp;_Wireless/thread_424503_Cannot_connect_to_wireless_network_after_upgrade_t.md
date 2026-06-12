---
title: "Cannot connect to wireless network after upgrade to Feisty"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by cracker on 2007-04-26
I have two laptops, and a wireless network with 64-bit WEP encryption. Both laptops connected to the wireless network just fine under Edgy, but after upgrading to Feisty, neither can connect. One laptop was upgraded using update manager, the other was reformatted with the Desktop CD. Both cards have native linux drivers; one is a Linksys WPC54G that uses the acx111 driver, the other is an internal card that uses the r2500 driver. I've tried both using the roaming mode with automatic connection and manually configuring it in the Network program in System > Administration (the same way I did it in Edgy), and I simply can't connect. The network is visible, and it has signal strength, but I can't get any packets through, and can't get an IP address. I'll post here with some debug output from NetworkManager in a moment. This is quite disappointing--no wireless networking is a deal-breaker in my book.

---

### Post by dubiousmike on 2007-04-26
I did a fresh install last night and my internal card that used r2500 drivers did the same thing.  But I noticed it is trying to use IPV6 and not 4.  There are other threads that posted the following to disable IPV6:

sudo gedit /etc/modprobe.d/aliases

Then scroll down to where you see alias net-pf-10. Comment out alias net-pf-10 ipv6, and add a few lines so it looks like this:


Code:
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

I haven't gotten home yet to try, but hopefully this works...

---

### Post by cracker on 2007-04-26
Here's the debug info. The first file, r2500.txt, is the internal card, using the r2500 driver. It's interface is ra0. The second file, acx.txt, is the Linksys card with the acx111 driver. It's interface is wlan0. My other laptop's broadcom card doesn't work either, but I didn't expect it too, I've had to use ndiswrapper in the past. I had to put them in a tarball because they're too big to attach or post raw.

---

### Post by cracker on 2007-04-26
I tried disabling ipv6 like you suggested, but there is no difference. I know ipv6 was running under Edgy before, too, because it would always assign an ipv6 APIPA address instead of an ipv4 one when disconnected. I don't think this should be that big of a deal. I mean, I don't have a WPA network or anything, just an old, standard 64-bit WEP.

---

