---
title: "How do I setup Xubuntu to be my internet router w/2 nics?"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by murphyml on 2008-05-04
HI,

I have 2 nics in my Xubuntu laptop, and I want to use it to be my broadband router.  I have an ath0 (netgear wireless) card and an embedded eth0 in my laptop, and I want to use the wireless card as the internet interface, but share the connection with the computers attached to my wired interface.

My config is like this:

atho = 192.168.1.4 gw 192.168.1.1 (static -connected to broadband wireless)
etho = 192.168.0.1 no def gw (static - connected to wired network)

I know I need to use ipchains and/or ip masquerading, I just don't know how to set that up. I can see both networks from these nics just fine - now I want to take it to the next level and actually share the wireless connection.

Can anyone point me to information that will help me set this up?

Thanks,

Mike

---

### Post by TenPlus1 on 2008-05-04
Install Firestarter from the repository and follow the setup wizard, that's what I use to share my internet connection from my lan0 card through my wlan0 wireless...  It'll work the other way around :)

Also, make sure each pc on the hub/router has it's own ip address and is allowed access through Firestarter to connect...

---

### Post by murphyml on 2008-05-04
That couldn't have been any easier.  Thank you!

That Firestarter is quite a good program, really easy to configure.

Thanks again,

Mike

---

