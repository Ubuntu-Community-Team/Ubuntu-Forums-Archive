---
title: "setting up wireless from the start"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by ohyeah12321 on 2008-08-02
okay, so i'm a total starter at ubuntu. in fact, for the sake of this thread, lets pretend i installed ubuntu yesterday. okay, you got me, i installed ubuntu yesterday. i love it and it works great...except for the internet. i'm dual-booting with osx, hence me typing this. i have wireless internet in my house. i've looked through tons of threads, and found nothing that has been able to get me started (and finished :)) i know it's a broad question, but...where do i start?

---

### Post by rokytnji on 2008-08-02
Start by opening a Terminal and type

ifconfig  -----------        should show you all of the cards you have

Next type

iwconfig -------------         should show you which of those are wireless

Copy and paste the results in your next post

---

### Post by ohyeah12321 on 2008-08-02
from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1f:5b:e8:06:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1544 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1544 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:77392 (75.5 KB)  TX bytes:77392 (75.5 KB) 


from iwconfig:

lo        no wireless extensions. 

eth0      no wireless extensions.

---

### Post by prshah on 2008-08-02
> **ohyeah12321 said:**
> 
 i have wireless internet in my house. i've looked through tons of threads, and found nothing that has been able to get me started (and finished :)) 

[Here's a step-by-step guide to check/install wireless]("http://ubuntuforums.org/showpost.php?p=4723545&postcount=1"). It includes expected outputs to each command, so you can know when something goes wrong.

Post back here if you run into any trouble. Note that you can check if your adapter is recognized with the command iwconfig, as mentioned by the earlier poster. If iwconfig finds a wireless capable adapter, you can jump straight to step 9.

---

### Post by cdtech on 2008-08-02
First we need to know which wireless device your using:
```
lshw -C network
```

Thanks.....

**P.S.**
You wont be able to use any iw or ifconfig's until it gets configured

---

