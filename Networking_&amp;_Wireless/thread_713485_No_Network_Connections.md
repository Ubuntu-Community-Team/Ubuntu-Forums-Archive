---
title: "No Network Connections"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by t-a-g on 2008-03-02
Hello,

I am new to ubuntu and linux.

I just installed ubuntu 7.10 - the Gutsy Gibbon.
I can not connect to my home network.

When I typed ifconfig 
I only see this  (all typed no cut/paste so pardon if I mistyped something):
lo    Link encap:Local Loopback
      inett addr:127.0.0.1 Mask:225.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU 16436 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      Collisions:0 txqueuelin:0
      RX bytes:0 (0.0 b) TX bytes: (0.0 b)

Also I only see a "Modem connectection" from System \ Administration \ Network.
***Red flag:  Shouldn't there also be something for my network card?
 
Also seems odd but in the upper right hand corner of the screen (next to the no network connection icon) I see the alert telling me that there are 196 updates available.   Impressive how does my install of ubuntu know that if I dont have a network connection.  When I double click the alert, I see the list of the 196 updates and the Install Updates button.  When I try to install them I get message that says Failed to fetch (the item)  Could not resolve 'us.archive.ubuntu.com'  

***Red flag: How does my install know about these updates if I do not have a network connection?

Thanks for anyones help!!

---

### Post by tman elite on 2008-03-02
I have no idea about the network thing, sorry.

As for the updates, I'm guessing here but it's possible that when Ubuntu is installed those 196 updates are already on the update list.  Has the number ever changed?

---

### Post by scottro on 2008-03-02
The fact that you're only seeing lo (the loopback or local interface) isn't a good sign, I'm afraid.  Your redflag alert is correct, it should be seeing the network card and have something for eth0.  

(I'm assuming this is wired and not wireless.)

How to solve it?  We don't have enough information yet.  :)  
Can you let us know if you are talking about wired internet?
If so, do you know the model of your card.  (Usually, lspci will give the answer, or, if you're in Windows when you see this, WIndows device manager.)

---

### Post by t-a-g on 2008-03-03
I don't see anything specific to the either net card.
I know it is an on board unit.

Is there another command I can use?
Or is there a way to "Scan for new Hardware" (to borrow a phrase from windows)?

Or do I just need to crack the case?

---

### Post by superprash2003 on 2008-03-03
try to find out the model and make of the ethernet card of your motherboard.. it could be mentioned in the motherboard manual itself..then go to google and search for the linux drivers for it..

---

### Post by Iowan on 2008-03-03
From a terminal, you can try ```
lspci |grep Eth
``` but I suspect nothing will turn up.

---

### Post by t-a-g on 2008-03-03
I am confused with the command
I tried "lspci<space>|{PIPE)grep Eth"

Nothing came up, but trying that I also tried lspci -v
This is what I got:

01:00.0 VGS compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA])
Subsystem Eletegroup Computer Systems Unknown device 1623
Flags: bus master 66MHZ, medium devsel, latency 64, IRQ 10
Memory at f0000000 (32bit, prefetchable) [size=64M]
Memory at f0000000 (32bit, non-prefetchable) [size=16M]
Expasion ROM at feaf0000 [disabled] [size=64k]
Capabilities: <access denied>

I am looking for my book on the MB.  I think I still have it???

---

### Post by froy02 on 2008-03-03
If you do not have your mb manual, go to the ECS website to get a pdf copy of the manual.

---

### Post by schmildo on 2008-03-03
ifconfig will only show interfaces that are 'up', make sure you try:

*ifconfig -a*

(this will show all interfaces)

If you see your card listed then things should be pretty easy after that.

---

