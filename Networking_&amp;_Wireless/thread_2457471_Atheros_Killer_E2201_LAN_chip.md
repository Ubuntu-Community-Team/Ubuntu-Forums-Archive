---
title: "Atheros Killer E2201 LAN chip"
date: 2021-02-02
forum: Networking &amp; Wireless
---

### Post by gividen on 2021-02-02
Please give me instructions as if I was a child who knows nothing of linux.

I just downloaded ubuntu-20.04.1-desktop-amd64 today.
I installed it on my PC with a gigabyte g1.Sniper H6 that uses the Qualcomm[SUP]®[/SUP] Atheros Killer E2201 LAN chip (10/100/1000 Mbit)
The installation seems to have gone fine with the exception that ubuntu says my ethernet cable is unplugged. Which it is not.
I  have read that the e2200 series is a pain to get working.  Can anyone  link me to a thread that shows how to get it up and running for Ubuntu  20.04.1?

I have no way of accessing the internet with the PC in question.
I do have access to a laptop running windows 10, which I am using to make this post.

I see chili555 fixed this problem for version 13.04
[https://ubuntuforums.org/showthread.php?t=2166562&highlight=E2200](https://ubuntuforums.org/showthread.php?t=2166562&highlight=E2200)

ples halp meh. .

---

### Post by CelticWarrior on 2021-02-02
Welcome.

That hardware isn't new. It was back in 2013 as your link shows but support for that chip was added years ago. And if it recognizes an Ethernet connection albeit with the "unplugged" status then the device is recognized.

Have you tested with another cable and/or checked both connections?
And where is it connecting to?

---

### Post by chili555 on 2021-02-02
Let's start by gathering some data. Please open a terminal Ctrl+Alt+t and run:

```
lspci -nnk | grep 0200 -A3
ip addr show
```Next, post  the result in your reply.

We will probably need more depending on the results above.

---

### Post by QIII on 2021-02-02
Moved to Networking & Wireless as a more appropriate sub-forum.

---

