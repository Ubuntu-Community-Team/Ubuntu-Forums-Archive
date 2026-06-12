---
title: "Dsl setup help"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by Swshaun on 2010-05-30
Hello there folks,

First time poster here, so please be gentle with me.

Firstly, I am using Ubuntu 10.04 and am trying in vain to set up a modem/router with a view to
making a wireless network.

I have a D Link 2640R combined modem and router, which connected to computer via the Ethernet port.

The instructions state that I should go to 192.168.1.1 in Firefox to get to the router config menu, but FF states that it can not find the server at this address.

I have searched high and low, disabled ipv6 addresses as that appears to be a problem, but this does not help. A ifconfig run produces this output:

eth0 Link encap: Ethernet HWAddr: 00:11:85:e6:36:ff
UP BROADCAST MULTICAST MTU: 1500 Metric:1
Rx packets:0 errors: 6 dropped: 0 overruns: 0 frame: 44
Tx packets:2 errors: 0 dropped; 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 0
Rx bytes: 0 (0.0 B) Tx bytes: 410 (410.0 B)

and then info for the loopbavk adaptor.

What am I doing wrong? I've bern at this all morning and am steadily losing my marbles!

I have also tried using ndiswrapper to no avail.

Thanks in advance

Shaun

---

### Post by lkraemer on 2010-05-30
Ref:
[ftp://ftp.dlink.co.uk/dsl.../dsl-2640r/DSL-2640R_QIG_v1.0.pdf](ftp://ftp.dlink.co.uk/dsl.../dsl-2640r/DSL-2640R_QIG_v1.0.pdf)

The manual (DSL-2640R_QIG_v1.0.pdf) states:
1. How do I configure my DSL-2640R router without the CD, or check my
  Wireless Network Name (SSID) and Wireless Encryption Key?
  • Connect your PC to the router using an Ethernet cable.
  • Open a web browser and enter the address [http://192.168.1.1](http://192.168.1.1)
  • The default username is ‘admin’. The default password is also ‘admin’.
  • If you have changed the password and can not remember it, you will need to reset the router to the factory default setting (steps in question 2), which will set the password back to ‘admin’.

It might be worth a few minutes to read the Quick Install Guide & Users
Manual.....

lk

---

### Post by Swshaun on 2010-05-30
Hello there,

thanks for this but I have this about twenty times and am stumped!

Please help as this is driving mad!

Shaun

---

### Post by roger_1960 on 2010-05-30
Hi

I think the address should be 198.162.1.1; not 192 etc

On second thoughts it may be coincidence that this address asks for a username and password.  Now I've checked with WHOIS, its East Kootenay Community College - apologies!

---

### Post by Swshaun on 2010-05-30
Think I have this resolved now, we were supplied with a duff cable!

---

