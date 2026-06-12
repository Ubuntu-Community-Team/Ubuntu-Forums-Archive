---
title: "Why is Ubuntu throttling down network speed when transfering in full-duplex???"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by gods on 2007-09-10
First some info.
1) My version is Ubuntu 6.06 LTS server

2) This is NOT regarding the link speed of the NIC(full-duplex). By full-duplex is i mean transfering files to and from the machine at the same time.

3) I have tested numerous machines with different hardware, turned ipv6 of, laborated with TCP window size, TCP rescieve and send buffers

THE PROBLEM IS:
when transfering files to and from Ubuntu at the same time, Ubuntu throttles down the incomming speed to ~40Mbps. (this does not happen if both machines are Ubuntu)
To illustrate the problem I have made some graphs with the IXIA Chariot([www.ixiacom.com](www.ixiacom.com)) program (similiar to ipperf). In the test, I let the machine that aren't Ubuntu start the transfer and after 5 seconds the Ubuntu machine starts it's transfer.

Graphs:
First, transfering between two Ubuntu machines.
[IMG]http://levander.se/problem/ubuntu-ubuntu.jpg[/IMG]

Second, transfering between Gentoo(red) and WinXP(green).
[IMG]http://levander.se/problem/winxp-gentoo.jpg[/IMG]

Third, and here we see the problem, transfering between two Gentoo(red) and Ubuntu(green).
[IMG]http://levander.se/problem/gentoo-ubuntu.jpg[/IMG]

Fourth, also problem, transfering between two WinXP(red) and Ubuntu(green) machines.
[IMG]http://levander.se/problem/winxp-ubuntu.jpg[/IMG]

So my question is, how do i fix this?

  //Johan Levander

---

