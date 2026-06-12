---
title: "DNS Networking Problems"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Foolness on 2007-09-27
Okay, so i just downloaded Ubuntu. But before I install it I want to be sure I can connect to the internet with it. I tried to do so while running the live CD but I failed. I connect to the internet using a DNS connection over a private server. In the Networking Options I enter my IP address, Deafult Gateway and DNS servers but I still can´t connect online. I am grateful for any help in advance.

---

### Post by Foolness on 2007-09-27
Okay... I have now installed Ubuntu but still can´t connect to the internet. Anyone?

---

### Post by noob12 on 2007-09-28
It may be more fundamental.

I'm assuming you are trying to establish a wired connection.

Can you post the output of these commands?  You can use a USB drive  to get output off the box to post until you can get hooked up.

```

lspci -nn

sudo lshw -C network

sudo ethtool eth0

ifconfig -a

route -n

```

---

### Post by Foolness on 2007-09-28
Yes, I´m using a wired connection. But there is a problem, I am unable to give you the information that I receive after entering that information because I can´t. Either it doesn´t save the information to my USB drive or when it does it is "damaged". The file is full of unreadable codes and text and what not. Any other thing I can do?

---

### Post by noob12 on 2007-09-28
I think you may just be seeing the difference in line termination between linux and Windows.  If you open the file in Wordpad in windows you may see "normal" text.

If that doesn't work, we can try stepping through some diagnostics with you being the eyes, but unless the problem is simple, we may not find it that way, and it requires pretty immediate interaction or it will take ages.

---

