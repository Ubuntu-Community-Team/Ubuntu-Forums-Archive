---
title: "Conection problem with RTL8139, ISP wont help :("
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Messiah25 on 2008-07-29
i just installed the latest Ubuntu
And I've tried for hours to connect to the internet.
I called my isp for help and they told they only do windows help support, they said that it's possible to connect to them via Ubuntu but none of them knows how. they gave me a link on their website that's been done by one of their employees, but he is not working there anymore. so they cant help me

I'm a noob at this and cannot figure out what to do.
Event with the instruction on the link they gave me...
Please help me

here is the link that my isp gave me:
[http://217.22.112.120/support/linux/LinuxCableScript.htm]("http://217.22.112.120/support/linux/LinuxCableScript.htm")

My pc:
Intel(R) Pentium 4 
CPU: 3.00Ghz
512ram

---

### Post by Messiah25 on 2008-07-29
Anyone?
Please...

---

### Post by VyReN on 2008-07-29
I know why you have no replies, so let me help you a little bit here:

What steps have you taken so far?
What "doesn't work"? 
Do you see the router or any wireless signal?  If so, do you get a reply from the DHCP?
Have you tried anything from [http://ubuntuforums.org/showthread.php?t=564419]("http://ubuntuforums.org/showthread.php?t=564419")?

---

### Post by Messiah25 on 2008-07-29
I don't have a wireless modem or a router.
I have an onboard RTL8139.
I've tried to do the stuff on the link that my ISP gave me, but it wont work or i do something wrong...

Here is my ifconfig (if it helps):
eth0      Link encap:Ethernet  HWaddr 00:13:d4:27:8d:93   
          inet addr:172.26.156.155  Bcast:255.255.255.255  Mask:255.255.248.0 
          inet6 addr: fe80::213:d4ff:fe27:8d93/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1061 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:363945 (355.4 KB)  TX bytes:20666 (20.1 KB) 
          Interrupt:20 Base address:0xe400  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2234 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2234 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:111700 (109.0 KB)  TX bytes:111700 (109.0 KB)

---

### Post by VyReN on 2008-07-29
Looks like everything is right.

What happens when you:
ping -c 3 64.233.167.99

and if you get a reply, do you get the same results with:
ping -c 3 google.com

---

