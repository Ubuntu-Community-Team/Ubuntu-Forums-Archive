---
title: "Problems with wake-on-lan"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by James Wilde on 2013-09-30
I'm experimenting with wol.  so far I have configured the BIOS and run the ethtool to turn on wol on eth0.  I then entered two lines in /etc/network/interfaces, namely:

auto eth0
ethernet -wol g

What happens when I boot the machine is that it starts off with a message 'Waiting for network interface...'  This changes to 'Waiting up to 60 more seconds for network interface' and finally Starting without network functionality', at which time the machine has hung.  (Note the three messages are cited more or less accurately as I didn't write down the exact wording at the time.)  

I have now booted with the install disk and removed the two lines from /etc/network/interfaces and the machine now boots again.

My questions:  the interface was not coupled to a cable when I started the machine.  Is this a requirement every time I start the machine?

Does anyone recognize these error messages and know a) the cause and b) the solution?

I'll be very grateful for any help.

//James

---

