---
title: "Xubuntu Wireless Problem"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by jdsagastume on 2008-01-27
Hello, I'm relatively new to Ubuntu (I installed it on my PC three months ago) and I am entirely new to Xubuntu. I just installed xubuntu on an old laptop my dad gave me(pentium 3, 10 GB HD, 256mb RAM) and everything workd fine, except I can't connect to the internet. I have an old 3com PCMIA card and a brandless USB wireless connector. Both work fine; they are recognized by xubuntu, but when I try to connect to the internet my wireless router doesn't respond. (By the way, my router is a 2-year old 2wire 802.11g) The computer tries to connect and the bottom half of the "wireless connection symbol," lights up (I presume this means it is trying to connect to the network), but the upper half (symbolizing the network) doesn't light up. Is this a problem with the laptop or the network? How can I fix it? Please help.

Also, I've tried to include the necessairy information for the problem, but feel free to ask for any specifications, details, etc. that you need.

Thanks

---

### Post by chewearn on 2008-01-27
Clarification: the 3Com PCMCIA is a wired ethernet card?  Does this work when connect via wired?  Where is the wireless USB in all this?

---

### Post by jdsagastume on 2008-01-29
Yes, it's a wired Ethernet card. The USB network adapter is an entirely different adapter. I had both laying around, so I decided to try the USB when the PCMIA failed. I don't know if it makes a difference which one I use, whichever is easier to make work, I guess.

---

### Post by chewearn on 2008-01-30
Wired should be easier to get going.  With the PCMCIA plugged in, run ifconfig.  Does all the necessary connectivity info (IP address, etc) present?  Can you ping the router and the internet?

---

### Post by jdsagastume on 2008-01-31
I'm sorry, but it turns out my dad (in his infinite wisdom) actually threw away the PCMIA card when I told him I couldn't  use it. It looks like we're stuck with the USB. Should I use the same steps above with the USB?

---

### Post by chewearn on 2008-01-31
Yes, run "ifconfig" and post the output.  Try also ping the router and some internet website.

---

### Post by jdsagastume on 2008-02-03
Okay I ran ifconfig and this is what it said:

eth0      Link encap:Ethernet  HWaddr 00:D0:59:31:70:B9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x1c00 

eth2      Link encap:Ethernet  HWaddr 00:02:72:4E:5F:D5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:924 (924.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Sorry, But I don't quite know how to ping (as I said before I'm horrible with networking). Maybe you could give me a command to enter into terminal. Also, I'm sorry for taking forever to respond, and thakn you for being so patient with me.

---

