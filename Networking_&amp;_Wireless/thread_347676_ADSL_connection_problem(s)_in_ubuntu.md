---
title: "ADSL connection problem(s) in ubuntu"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by skannloh on 2007-01-27
Hi, I am new in both ubuntu and this forum. I install ubuntu 6.06 alongside winxp in my desktop but i just could not configure pppoe to connect to the net in ubuntu while the same hardware setup working fine in winxp. When i type sudo pppoe in the termial, it recongizes the eth0 but fails the scan of "access concentractor" of the ISP. I have contacted my ISP and they said they do not support Linux. Could anyone help to work around this problem.

---

### Post by q3_abhi on 2007-01-27
Facing exactly the same problem..anyone out with a solution ?

---

### Post by pyrofire on 2007-01-28
Third!

---

### Post by q3_abhi on 2007-01-29
Whereas i popped in the dyne-bolic disc (live version) and i had no probs in getting DSL detected...but ubuntu fails to do so.

---

### Post by TheGeneralsLounge on 2007-01-30
I was having the same problem and after some (semi) extensive Googling i typed this into the terminal

sudo sed -i -e 's/^alias *net-pf-10 *ipv6/alias net-pf-10 off/'
/etc/modprobe.d/aliases

all as one line and hit the enter key, waited a minute until a message popped up and then rebooted. It works although im not sure if it's the "right" thing to do (because i don't know what it DOES exactly lol)

Credits to Matt Zimmerman from web page [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/9160](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/9160)

hope it helps.

---

### Post by skannloh on 2007-01-30
To: TheGeneralsLounge

Thankyou for the advice. I have done what you suggested and no luck. The same message appeared when I "sudo pppoeconf"  in the terminal.

---

### Post by alibaba73 on 2007-08-23
Hi all!

I faced the same problem with my ADSL, i tried many many time's but nothing works,   
So, I decide to reinstall Ubuntu.

after i reinstall it it worked fine:

    [HTML]sudo pppoeconf[/HTML]

---

