---
title: "Trying to forward port over internet with ufw"
date: 2018-06-08
forum: Networking &amp; Wireless
---

### Post by strange on 2018-06-08
hey guys im trying to connect from box A to box C through box B
box A is a cableboxtop box so is box C, i need them to interact with each other but i can only reach box C from a certain IP that ip is box B so i would like any traffic going to box B on port 15500 to go to box C port 14000.
and all traffic that box c responds i would like to end up back to the connecting box. also i would like to use ufw so i can add ips that are allowed to connect to port 15500.

help is greatly appreciated

---

### Post by TheFu on 2018-06-13
[https://askubuntu.com/questions/660972/port-forwarding-with-ufw](https://askubuntu.com/questions/660972/port-forwarding-with-ufw) found by google.
I've never tried to use UFW for anything more than trivial client firewall needs.  When something more is needed, that has me purge ufw and switch to iptables for firewall management.  I'm looking forward to using firewalld when that becomes available.  Simple things are easy like ufw, but harder things are possible too.

---

