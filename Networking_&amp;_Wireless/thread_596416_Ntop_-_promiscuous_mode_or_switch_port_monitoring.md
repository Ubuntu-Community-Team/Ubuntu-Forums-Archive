---
title: "Ntop - promiscuous mode or switch port monitoring"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by Sgurd on 2007-10-29
I'd like to use ntop to monitor the Internet bandwidth used by one of the VLANs/subnets on my network (300+ users).

This is all new to me.

Would it be better/the same/worse to:
Have the ntop computer's card set to promiscious 
or 
Change the settings on the HP switch to make the computer's port the monitoring port for other ports?

I recall seeing someone else set a monitoring port on an HP switch when they were using ethereal to track down a problem.

Thoughts?  Thanks in advance - JD

----

Bonus question: How can I password protect the entire [http://ip.add.re.ss:3000?](http://ip.add.re.ss:3000?)  The box will be on a public IP and I want make sure I'm the only one accessing it.

---

### Post by Sgurd on 2007-10-30
It looks like the port monitoring setting for the switch is at least similar to the promiscuous mode of a NIC card and should accomplish what I'm looking for.

I read a bit of Question/Answer # 22 from here:
[http://www.winpcap.org/misc/faq.htm](http://www.winpcap.org/misc/faq.htm)

And then read parts of the manual for the HP switch.

Bonus question answered here:
[http://ubuntuforums.org/showthread.php?t=596429](http://ubuntuforums.org/showthread.php?t=596429)

I don't like reading . . .;)  - JD

---

