---
title: "Installing NIC driver from CD"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Tsega on 2007-05-04
I bought a new Ethernet PCI Adapter and apparently it has drivers for Linux. There seems to be two versions for Linux, 1. linux22x-8139cp and 2. linux24x-8139cp. I opened the two folders and all I cloud find where these files. 
1 kern_compat.h, readm.txt, rtl8139.c
2 8139too.c , Makefile, readme.txt 

what should I do? I tried to read the readme file but it says nothing about installation. I know for sure I just have the sources and I might need to compile them (".c" file a C program), how do I do that and if I'm wrong please, you would be doing me a favor in correcting me. Thanks. 

P.S If it makes a difference I'm using Ubuntu 6.06 LTS.

---

### Post by chili555 on 2007-05-04
> If it makes a difference I'm using Ubuntu 6.06 LTS.It makes a great deal of difference! 6.06 has a driver built-in, 8139too, which should work perfectly with your new adapter. Stick the card in, issue a command in the terminal:```
sudo modprobe 8139too
```and then see if ```
ifconfig -a
```shows your ethernet interface. Connect the cable, do:```
sudo dhclient eth0
```Enjoy.

OR: post back and tell Chili he has lost his touch.

---

### Post by Tsega on 2007-05-05
Hey Chilli I'm getting the following error but before that I want to tell you something. I'm using my Ubuntu desktop PC to connect to to my Windows Xp laptop. Now what I want to do is share a dial-up  internet connection. Is that possible?
 
I ran the commands and here's what I got for the "ifconfig -a " 

io          Link encap:Local loopback
            inet addr:127.0.0.1 Maks:255.0.0.0
            inet6 addr: ::1/128 Scope:Host  
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            RX packets:5 errors:0 dropper:0 overruns:0 frame:0
            TX packets:5 errors:0 dropper:0 overruns:0 carriers:0
            collisions:0 txqueuelen:0

sit0       Link encap:IPv6-in-IPv4
            NOARP MTU:1480 Metric:1
            RX packets:5 errors:0 dropper:0 overruns:0 frame:0
            TX packets:5 errors:0 dropper:0 overruns:0 carriers:0
            RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

and when I ran the command "sudo  dhclient eth0" here's what came out:

Internet Systems Consortium DHCP Client v3.0.3
Copyright 2004-2005 Internet System Consortium
All rights reserved.
For info, please visit [http://ww.isc.org/products/DHCP](http://ww.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth0: error while getting interface flags: No such device
eth0: error while getting interface flags: No such device
Bind socket to interface: No such device

I'll have to admit that I really don't know much or I don't care to do so about networking but I guess what we are tying to do here is get the DHCP server or something. But I don't think I've configured my system the right way.

In short I would really appreciate it if you take me by the hand and help me go through this step by step. I know it's a lot to ask. Please keep in mind that I just want to share the internet connection on my Windows Xp machine. That's all. Thanks for reading this!

---

### Post by chili555 on 2007-05-05
> Now what I want to do is share a dial-up internet connection. Is that possible?
Absolutely! But I have no experience with such things. Let's get your ethernet working first, then I suggest you post a new question on the forum; something like: Connection Sharing Ubuntu <> XP.

What happened when you did the command:```
sudo modprobe 8139too
```Nothing? Good! That means it stuck. Let's do:```
sudo ifconfig eth0 up
ifconfig -a
```Did your ethernet interface appear? If so, please again try:```
sudo dhclient eth0
```Post back and let me know how you get along.

---

### Post by Tsega on 2007-05-06
Hey Chilli thanks for your help but I'm still having problems. 
```
sudo ifconfig eth0 up
            if config -a 
```
gives me the following error message 
```
eth0: ERROR while getting interface flags: No such device
           ifconfig: Host name lookup failure
           ifconfig: '--help' gives usage information 
```

Just to let you know I have properly installed my NIC and when I connect the computer with a cable I get LAN connection active on my windows. What next man?

---

### Post by chili555 on 2007-05-06
Perhaps I did not explain myself well. Please do:```
sudo modprobe 8139too
```Tell me what happens; maybe nothing. Do:```
sudo ifconfig eth0 up
```Tell me what happens; maybe nothing. Do:```
ifconfig -a
```What is the output?

Each of these are separate commands with Enter pressed after each one.

---

### Post by Tsega on 2007-05-07
Hey Chilli I'm sorry if I seemed really foolish but I did try it seprately and her's what I got.
 for the code 
```
sudo modprobe 8139too
```
nothing happened
for
```
sudo ifconfig eth0 up 
```
I got this
```
eth0: ERROR while getting interface flags: No such device 
```
and for 
```
ifconfig -a
```
I got
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:213.55.69.27  P-t-P:213.55.89.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:2 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1442 (1.4 KiB)  TX bytes:1533 (1.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Thanks a lot for your patience!

---

### Post by chili555 on 2007-05-11
Sorry for the delay in replying. I am surprised this thing doesn't just spring to life. With the card installed in the slot, what does:```
lspci -v | grep -i Network
```tell us about it? Also try:```
sudo lshw -C network
```Thanks.

---

### Post by chili555 on 2007-05-11
Could I also take a look at:```
cat /etc/iftab
```Thanks.

---

### Post by Tsega on 2007-05-12
Hey Chilli thanks for the reply and here's what I got for
```
lspci -v | grep -i  Network
```
I got nothing!
but for 
```
sudo lshw -C network
```
I got this
```
*-network UNCLAIMED
description: Ethernet controller
product: Sundance Technology Inc
Vendor: Sundance Technology Inc
physical id: 0
bus info: pci@01:00.0
version: 31
width: 32 bits
clock: 33MHZ
capabilities: bus_master cap_list
resources: ioport:3000-307f iomemory:f4110000-f41101ff irq:11    
```
for the last one
```
#This file assigns persistent names to network interfaces.
# See iftab(5) for syntax  
```

Well there you go

---

### Post by chili555 on 2007-05-12
Oops! I mada a mistake. I meant to ask for:```
lspci -v | grep Ethernet
```Sorry.

---

### Post by Tsega on 2007-05-13
Hey Chilli guess what I just upgraded to Fiesty (7.04) and it has recognized my NIC. It's working now! THANKS A LOTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! for all your help, I really appreciate it. I know you were very much into the challenge but I have another one for you, How I do I connect to Win Xp PC through a  peer-to-peer network to share a dial-up internet connection. I'm going to post a new thread right now. Thanks again.  :)

---

