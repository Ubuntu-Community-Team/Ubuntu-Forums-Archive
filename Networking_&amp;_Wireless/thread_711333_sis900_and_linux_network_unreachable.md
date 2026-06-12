---
title: "sis900 and linux: network unreachable"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by edonan on 2008-02-29
Hi, I have an issue with my sis900 ethernet card: it behaves like there is no cable pugged in it.
You should know that:
- The card is correctly recognized ("lspci" reports it) and its drivers are correctly loaded (i can see eth0 in ifconfig, and I see that "sis900" is the driver in use for that interface by typing "ethtools -i eth0" in terminal)
- I tried other distributions (mandriva, puppy linux, knoppix) and i always got the same problem
- I disabled the ACPI at boot time, since i read someone had similar issues and solved by doing this (at startup, before disabling it, I had an ACPI warning)
- I tried both dhcp and static ip to connect to the LAN, but i always got responses like "netkwork unreachable" or "destination host unreachable" when pinging my router's ip (I know the router is working fine because other PCs are connected)
- I can successfully ping my local host (127.0.0.1)

Any helps would be much appreciated.

If you have a (working) sis900 ethernet card, please tell me wich linux kenel are you using (i'm thinking it's a matter of kernel... but i may be wrong).

Thank you!

---

### Post by Iowan on 2008-02-29
What other info does **ifconfig **provide?
I presume you've tried switching cables?

---

### Post by deep75 on 2008-04-14
:( same problem

---

### Post by sursata on 2008-07-22
Hey buddy,
Try turning off the acpi. 

[http://howtoxyz.blogspot.com/2008/07/netdev-watchdog-eth0-transmit-timed-out.html]("http://howtoxyz.blogspot.com/2008/07/netdev-watchdog-eth0-transmit-timed-out.html")

Now i can surf without any problem.

---

