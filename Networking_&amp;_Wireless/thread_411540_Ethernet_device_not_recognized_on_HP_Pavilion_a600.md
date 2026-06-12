---
title: "Ethernet device not recognized on HP Pavilion a6000n"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by avik on 2007-04-17
I just got a new HP Pavilion a6000n PC, and of course, the first thing I wanted to do was install Ubuntu.  That part I did, but the problem is that the ethernet card is not recognized by Ubuntu.

The ethernet card is an integrated "10/100Base T-network interface."

Has anyone had any similar experiences?  No amount of searching has surfaced any links between the a6000n and GNU/Linux in general.

Let me know if you need more information.

---

### Post by josephus on 2007-04-17
which version of ubuntu are you running?

i've read a couple of posts of other computer using a similar chipset with troubles detecting hardware.  One post that I read suggests that you will have better luck with Feisty.

look for posts that have terms related to NVIDIA GeForce 6150SE nForce 430, mcp61p

[http://ubuntuforums.org/showthread.php?t=411569](http://ubuntuforums.org/showthread.php?t=411569)
[http://ubuntuforums.org/showthread.php?t=393537](http://ubuntuforums.org/showthread.php?t=393537)

---

### Post by josephus on 2007-04-17
I think this post will get your network card up and running.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346)

Just follow the instructions in the second post.  Let me know if this works.

---

### Post by dbott67 on 2007-04-17
Can you post the output of:
```
dbott@feisty:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:17

```

-Dave

---

### Post by avik on 2007-04-17
I got it to work!

> **josephus said:**
> which version of ubuntu are you running?

i've read a couple of posts of other computer using a similar chipset with troubles detecting hardware.  One post that I read suggests that you will have better luck with Feisty.

look for posts that have terms related to NVIDIA GeForce 6150SE nForce 430, mcp61p

[http://ubuntuforums.org/showthread.php?t=411569](http://ubuntuforums.org/showthread.php?t=411569)
[http://ubuntuforums.org/showthread.php?t=393537](http://ubuntuforums.org/showthread.php?t=393537)

I'm using Edgy, and I was able to fix the problem.  As a side note, the first link you posted links to the article [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).  Using that, I even got my sound device to work!

> **josephus said:**
> I think this post will get your network card up and running.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346)

Just follow the instructions in the second post.  Let me know if this works.

That did the trick.

> **dbott67 said:**
> Can you post the output of:
```
dbott@feisty:~$ sudo lshw -C network
--snip--
```

Actually, it was coming up completely blank at first, but after fixing the problem, the output is similar to yours in that it came up with an Ethernet interface.  Obviously, the exact details are different, but at this point, it doesn't matter.

Thank you *so* much everybody!  This is exactly why I chose Ubuntu!

---

