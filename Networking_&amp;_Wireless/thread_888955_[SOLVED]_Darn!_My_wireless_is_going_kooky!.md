---
title: "[SOLVED] Darn! My wireless is going kooky!"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by dragos240 on 2008-08-13
I had 2 hours of internet on my new ubuntu! But when i restarted it thought it was secured again!.... wierd! Help please!

---

### Post by dragos240 on 2008-08-14
Please help.

---

### Post by crutch on 2008-08-14
I probably can't help here, but I think most people would need a bit more information. What sort of wireless are you using? etc.

---

### Post by dragos240 on 2008-08-14
Well. I'm using a wireless G linksys router. I'm running on my ubuntu right now (finally). But sometimes i have to go on my cruddy windows computer for a while. Sometimes the ubuntu thinks that the linksys router is segured WPA key. It's pretty wierd. Sometimes going into my windows for a while fixes the problem. Other times i have to reset my computer and router and it doesn't even work all the time! I like the ubuntu better, and i want this to work. Thanks.

---

### Post by lordhaworth on 2008-08-14
The only thing that still gets me is my wireless... sometimes it works, sometimes it doesnt. It also has behaved differently for WEP and WPA Personal security. What I really dont understand is that mine connects (sometimes) and then after a period of time decides to disconnect and I know the problem isnt the signal because I have another laptop that works fine. 

Anyway... away from me. When I had WPA I found that using one time connect is a short term solution, allowing me to connect "properly" without any disruptions. The only problem is youll have to turn one time connect on everytime you turn on your computer. 

I might as well say it... In the terminal type:

ifconfig 

and post the results

---

### Post by dragos240 on 2008-08-14
Ok. I got the results:

```
eth0      Link encap:Ethernet  HWaddr 00:01:4a:c0:7e:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:13:ce:18:34:43  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe18:3443/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:8979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108901726 (103.8 MB)  TX bytes:6673723 (6.3 MB)
          Interrupt:22 Base address:0x6000 Memory:b0006000-b0006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:210827 (205.8 KB)  TX bytes:210827 (205.8 KB)
```

What should i do with them?

Edit: I'm now running on my ubuntu, but.... i still want to fix the problem when it happens.

---

### Post by TDragon on 2008-08-14
I could be wrong, but it looks like your driver is not currently running (or loaded) for your wireless.

[LIST]
[*]Does your motherboard have two Ethernet jacks on it?
[*]Can you tell us what kind of your wireless card is installed on your PC?
[*]Was the wireless card automatically installed when you installed Ubuntu, or did you manually load a driver through ndiswrapper or madwifi?
[*]Can you post the contents of the following file: *sudo gedit /etc/udev/rules.d/[I]70-persistent-net.rules*[/I]
[/LIST]

---

### Post by dragos240 on 2008-08-14
> **TDragon said:**
> I could be wrong, but it looks like your driver is not currently running (or loaded) for your wireless.

[LIST]
[*]Does your motherboard have two Ethernet jacks on it?
[*]Can you tell us what kind of your wireless card is installed on your PC?
[*]Was the wireless card automatically installed when you installed Ubuntu, or did you manually load a driver through ndiswrapper or madwifi?
[*]Can you post the contents of the following file: *sudo gedit /etc/udev/rules.d/[I]70-persistent-net.rules*[/I]
[/LIST]

Well, i said that i can connect through wireless, but sometimes. So i have the wireless driver running and installed. Now for your question.



1.No
2.I don't have one. I connect through the one built in.
3.I'm pretty sure it was installed when i loaded ubuntu, becuase i'm not familiar with any of those programs.
4.Nope.

---

### Post by TDragon on 2008-08-14
The reason i need some of this info, built-in wifi or not, is to determine what driver you are using and tell you how to keep it running. It is not uncommon, in this latest release of Ubuntu, to experience the wireless intermittently working. One of the is reasons is due to the drivers randomly unloading (it being installed and actively loaded/running are two different things). As far as this file goes, *sudo gedit /etc/udev/rules.d/[I]70-persistent-net.rules*[/I], you're supposed to paste that entire line into a terminal prompt and it will automatically bring up a text editor program with the file and its contents. Then just copy and paste it to here. You will need to enter your login password when using the "sudo" command.

If anything, can you at least tell us what kind of computer you are using? For example, if you are using an off-the-shelf (retail) PC and not a custom-built one, can you tell us who makes it and the model (i.e.: HP Pavillion dv6000; laptop, desktop, etc)?

---

### Post by dragos240 on 2008-08-14
> **TDragon said:**
> The reason i need some of this info, built-in wifi or not, is to determine what driver you are using and tell you how to keep it running. It is not uncommon, in this latest release of Ubuntu, to experience the wireless intermittently working. One of the is reasons is due to the drivers randomly unloading (it being installed and actively loaded/running are two different things). As far as this file goes, *sudo gedit /etc/udev/rules.d/[I]70-persistent-net.rules*[/I], you're supposed to paste that entire line into a terminal prompt and it will automatically bring up a text editor program with the file and its contents. Then just copy and paste it to here. You will need to enter your login password when using the "sudo" command.

If anything, can you at least tell us what kind of computer you are using? For example, if you are using an off-the-shelf (retail) PC and not a custom-built one, can you tell us who makes it and the model (i.e.: HP Pavillion dv6000; laptop, desktop, etc)?
OH! I'm using a sony vaio laptop.

---

### Post by lordhaworth on 2008-08-15
Hmm wireless intermittently working sounds like the trouble I was having... Ill be keeping a close eye on this thread - but dont think I can be of any more help trying to solve the problem

Good luck and my joint thanks to anyone who solves this

---

### Post by dragos240 on 2008-08-15
oh  wish you could help but if you can't it's fine. Thanks anyway.

---

### Post by TDragon on 2008-08-15
> **dragos240 said:**
> OH! I'm using a sony vaio laptop.


Can you tell me the model number? Its usually at the bottom right-hand corner of your screen (i.e: VGN-....), or you can look at the bottom of the laptop. This way I can see what wireless card you have installed.

---

### Post by dragos240 on 2008-08-15
> **TDragon said:**
> Can you tell me the model number? Its usually at the bottom right-hand corner of your screen (i.e: VGN-....), or you can look at the bottom of the laptop. This way I can see what wireless card you have installed.
I can tell you 2 days from now, the vaio computer is my mom's and she's at the cape, for 2 days. It stinks that I can't tell you right now!! It also stinks that i can't use my ubuntu, becuase dad won't let me install it on my other computer :(.

---

### Post by dragos240 on 2008-08-17
My vaio computer is version VGN FS760/W

---

### Post by dragos240 on 2008-08-17
:):KS:popcorn:Special bump!!

---

