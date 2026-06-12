---
title: "Sharing internet connection with windows XP"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by fibra on 2007-07-07
Hello everyone.

First of all, I'd like to thank you for reading this thread, next, I'd like to say that i've read a lot of these "Share internet connection", tried them, but neither worked, so I'd like to explain my particular case to see what i'm doing wrong, and to see if anyone can help me.

So, here's the thing.

I have an ubuntu 7.04 machine, with 2 devices.

Eth1 -- connects to the internet --

IP: 10.2.54.115
Subnet:  255.255.255.0
Gateway: 10.2.54.1

Eth0 -- Connected with a WinXP Notebook --
IP: 192.168.0.1
Subnet: 255.255.255.0
Gateway : 10.2.54.115

And in my notebook, with WinXP, I have the following configuration

IP: 192.168.0.2
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1

Now, I have tried all those fancy scripts some kind experts have taken their time to write and share, but they didn't work. I also have installed firestarter, and when I run the wizard and share my internet connection with eth0 and DHCP, it says eth0 is not ready, or that "Theres been an internal error". If I don't use DHCP, it starts just fine, but I still get no response when pinging 192.168.0.2 from my ubuntu machine, and no response from 192.168.0.1 when I ping it from my notebook.

Also, as a native Spanish speaker (I'm from Argentina) I decided to get some help in the spanish ubuntu forums, but the only response I got (which I also appreciated) was to change the gateway of eth0 to 192.168.0.2, which didn't make any sense to me... but hey, i'm the one with the problem, so I decided to try it, but still, no luck.

So if anyone could help me, I'd be very grateful :D

Thanks in advance!

Fibra.

---

### Post by SpiritIsReality on 2007-11-09
howdy
I think eth0 should have no gateway listed.
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
Please see if this helps your network
[http://ubuntuforums.org/showthread.php?t=604104&highlight=internet+connection+sharing](http://ubuntuforums.org/showthread.php?t=604104&highlight=internet+connection+sharing)
trails

---

