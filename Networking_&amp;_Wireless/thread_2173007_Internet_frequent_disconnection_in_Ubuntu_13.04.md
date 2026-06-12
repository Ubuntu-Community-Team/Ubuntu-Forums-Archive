---
title: "Internet frequent disconnection in Ubuntu 13.04"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by giridhar2 on 2013-09-07
Recently installed Ubuntu 13.04. The internet gets frequently disconnected - Ethernet. I read somewhere to check output of the command 'traceroute'. 

Hence,I typed the following command at the terminal: 

**traceroute -n 8.8.8.8**

& obtained the **following output:**

traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.1.1  0.577 ms  0.958 ms  1.357 ms
 2  10.9.240.137  23.072 ms  23.192 ms  24.674 ms
 3  115.255.236.57  38.079 ms  39.985 ms  40.253 ms
 4  115.255.236.49  42.664 ms  43.067 ms  44.100 ms
 5  115.255.239.45  81.916 ms  83.507 ms  83.909 ms
 6  72.14.212.118  92.147 ms  92.029 ms  92.944 ms
 7  209.85.241.52  95.596 ms 72.14.232.202  76.696 ms 209.85.241.52  78.849 ms
 8  72.14.232.100  124.427 ms  111.549 ms 209.85.251.95  93.315 ms
 9  72.14.239.20  92.343 ms 66.249.94.74  96.551 ms  96.705 ms
10  209.85.242.243  107.004 ms  99.829 ms  104.939 ms
11  209.85.242.125  99.384 ms 209.85.250.237  102.419 ms 209.85.250.255  103.762 ms
12  * * *
13  8.8.8.8  105.638 ms  101.120 ms  105.358 ms


[B]1) I can not understand anything out of it. Can someone please help me? 

2) Also, what should be the addresses etc entered in Settings->Network ??? 
[/B]
Kindly answer the above two questions.

I have dual boot - Ubuntu 13.04 & Windows 7. Windows does not have problem connecting to the internet but Ubuntu has. Where is the problem, then? Please explain in a way that a novice like me can understand. 

Tx a ton, in advance !

Regards

---

### Post by ian-weisser on 2013-09-07
1) Traceroute simply tells you the IP addresses of the gateways that relay your packet to/from the destination server.
Wherever you read that, they were likely trying to fix something unrelated to your problem.
For the problem you have described, I see no useful information.

2) Depends on your router's configuration. For example, in a DHCP network, you would enter nothing.

I have found that Windows disconnects take longer to show up than Ubuntu disconnects - Windows tries to reconnect, and only admits to the disconnection upon failure. Ubuntu tells you every time.

If you have frequent disconnects using wired ethernet, the fault can be in several places. You need to narrow the possibilities.

1) Router or upstream ethernet card
2) Ethernet cable
3) Your ethernet port/card
4) Upstream server (that's the only one traceroute is used for, and the least likely)
5) Something in Ubuntu

In my experience, squashed cables, dying routers, and failing ethernet hardware are the most likely culprits. Happily, it's not difficult to narrow those down.

Look in /var/log/syslog for the disconnect and reconnect messages. Post a few here.

If you have one handy, try a different ethernet cable. Be sure to use the *same* ethernet ports on your local system and upstream router. Only change one thing at a time.

---

### Post by giridhar2 on 2013-09-08
> **ian-weisser said:**
> 

2) Depends on your router's configuration. For example, in a DHCP network, you would enter nothing.



 I have observed that whenever it disconnects, when i changed ipv4 settings from automatic DHCP to manual, it reconnects. When after sometime, it disconnects, i change the settings to manual, it reconnects. The last few days, it has been set to Automatic DHCP . It disconnects & reconnects on its own. So, i understood, the change from manual to automatic & vice versa is not helping.. 

> **ian-weisser said:**
> 

If you have frequent disconnects using wired ethernet, the fault can be in several places. You need to narrow the possibilities.

1) Router or upstream ethernet card
2) Ethernet cable
3) Your ethernet port/card
4) Upstream server (that's the only one traceroute is used for, and the least likely)
5) Something in Ubuntu

In my experience, squashed cables, dying routers, and failing ethernet hardware are the most likely culprits. Happily, it's not difficult to narrow those down.
 

  The hardware faults are ruled out. For, as soon as i boot into windows, it has NO problems connecting to the internet !! I am sure that i am missing out on some settings - something to do with configuration. What details could i give you for that - kindly tell me please?

> **ian-weisser said:**
> 
Look in /var/log/syslog for the disconnect and reconnect messages. Post a few here.


& how do i do that ? I am new to Ubuntu !! :(

> **ian-weisser said:**
> 
If you have one handy, try a different ethernet cable. Be sure to use the *same* ethernet ports on your local system and upstream router. Only change one thing at a time.

What did you mean by the last 2 lines above ?

Thanks for your replies !

Regards

---

### Post by ian-weisser on 2013-09-08
> **giridhar2 said:**
> & how do i do that ? I am new to Ubuntu !! 

Open your dash.
Look for "gedit" or any other text editor. Start it.
Open the file /var/log/syslog.
Scroll through the file looking for entries that include "Network Manager:"
Copy and paste several of those entries here, inside CODE tags (the #-button on the screen -not keyboard- when you write an entry in this forum)

---

