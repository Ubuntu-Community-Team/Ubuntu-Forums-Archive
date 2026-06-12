---
title: "PCMCIA Wireless Card Doesn't Power up on Laptop"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by Daz902 on 2006-11-09
Hi there, 

Brand new to Ubuntu and I installed it without any issues - wired lan works fine. But for some reason it didn't 'turn on' my PCMCIA wireless card. It's not recognizing it as an ethernet card. It's as if there's no driver for it. Is there a way I can install a driver for my wireless card? It's a NetworkEverywhere Notebook Adapter 802.11b model NWP11B. 

Here's the output from ifconfig, for what it's worth. 

eth0      Link encap:Ethernet  HWaddr 00:0D:9D:43:59:9B  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe43:599b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2041 errors:1 dropped:0 overruns:1 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1856538 (1.7 MiB)  TX bytes:295714 (288.7 KiB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:804 (804.0 b)  TX bytes:804 (804.0 b)

---

### Post by FrodoB on 2006-11-09
See this thread:

[http://ubuntuforums.org/showthread.php?t=149148](http://ubuntuforums.org/showthread.php?t=149148)

You either need to get 6.06 or get the driver and compile it perhaps. If you decide that you want to compile the drive on Edgy you will need to get the kernel source:

$ sudo apt-get install linux-source-2.6.17

---

### Post by Daz902 on 2006-11-09
Sorry - but remember I am a newb. :) How do I 'get' 6.0.6?

Thanks,
Darryl

---

### Post by dhughes on 2006-11-09
I think what he was referring to was a person in the post at the link he gave mentioning "*there is a working driver that is shipped with the dapper drake 6.06.*" for the piece of hardware you're trying to get to work.

 6.06 being Dappper Drake Ubuntu, the newest one is Edgy Eft 6.10, so I guess that means wiping your drive and reinstalling 6.06 or upgrade it.

 You're on your own, I not much better at this than you are.

---

### Post by Daz902 on 2006-11-09
Running 'uname -a', reveals that I've got 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux which appears to be much later than the 6.0.6 one mentioned. I followed the link and actually found info on installing an acx driver [http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)  but unfortunately it appears to be written by folks who know what they're doing. 

It doesn't explain what to do with the driver beyond downloading it and renaming it. And even that much is me guessing. Can anyone throw me a bone? If I understand what I am reading, this support should be already built in. So how do I turn it on?

Thanks!

---

### Post by FrodoB on 2006-11-10
Well, looking at the driver, I would suggest getting the Ubuntu 6.06 (Dapper Drake) CD and installing it.  

The driver wants you to patch the kernel and that is definitely not something the average user wants to do.

So it's either download it:
[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Or get it shipped to you:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

If it did not require a kernel patch, or if I had such a device and could do it here, I would suggest that you try compiling the driver.

The other option if Edgy Eft does not recognize it is to try ndiswrapper. There are no guarantees, but there seem to be a lot of threads that cover it fairly well.

---

