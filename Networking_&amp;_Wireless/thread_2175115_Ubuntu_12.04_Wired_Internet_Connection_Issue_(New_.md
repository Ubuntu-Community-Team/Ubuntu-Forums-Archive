---
title: "Ubuntu 12.04 Wired Internet Connection Issue (New Linux User)"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by matthew10 on 2013-09-17
So I'm in a bit of a tricky spot. I downloaded Ubuntu 12.04 for my new build and for some reason I'm not able to connect to the internet. I think it's a problem with how I have (or haven't) configured the wired network. The connection says that it's established and should be working, but when I go to open a page in firefox it can't find the server. I tried pinging [www.google.com](www.google.com) and I get nothing so I'm wondering what I can do to fix this. I'm a bit new to Linux and just slightly above the bar with computers in general so some layman's terms would be nice. I'm still figuring out the command terminal so if you guys can give me what I should input for my network config, I can give you the readouts. I have tried reinstalling and even installed Mint to see if the problem would resolve itself but I ran into the exact same problem. Thanks for schooling me in advance.

---

### Post by lukeiamyourfather on 2013-09-17
Are you using the server or desktop version? What's the network setup like, connected directly to the internet or behind a router? Please post the output of this command which will return information about the network adapters.

```
ifconfig -a
```

Also this which will list any network adapters installed in the system regardless of whether they are configured or not.

```
lspci
```

---

### Post by matthew10 on 2013-09-17
> **lukeiamyourfather said:**
> Are you using the server or desktop version? What's the network setup like, connected directly to the internet or behind a router? Please post the output of this command which will return information about the network adapters.

```
ifconfig -a
```

Also this which will list any network adapters installed in the system regardless of whether they are configured or not.

```
lspci
```

Desktop version. I'm connected to a router which runs everything else in the house as well. Another thing that might be important to know is that this is the first time OS for this computer. I just got the thing all together last week. Don't know if that's important or not. Also, to clarify, I'm just on the trial mode for Ubuntu because I didn't have an internet connection for the install.

ifconfig -a  returns
```
eth0      Link encap:Ethernet  HWaddr 94:de:80:bf:3f:20
          inet6 addr: fe80::96de:80ff:febf:3f20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:141 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7120 (7.1 KB)  TX bytes:7120 (7.1 KB)lspci returns
```

lspci returns
```
05:00.0 Ethernet controller: Realtek Semiconductor co., Ltud. RTL8111/8168B PCI E
Xpress Gigabit Ethernet controller (rev 06)
```

---

### Post by matthew10 on 2013-09-17
Update: I booted up again because I left to do something and now the connection isn't established at all. The above outputs are current. So I'm not getting anything at all now and I'm totally lost.

---

### Post by ashish_belwase on 2013-09-18
[COLOR=#000000][FONT=Sans Serif]I think there is problem with your routing. Try adding following routing path[/FONT][/COLOR]
route add default gw 192.168.1.1 eth0
here 192.168.1.1 is your router address and eth0 is ethernet interface.

---

### Post by lukeiamyourfather on 2013-09-18
It looks like the device drivers are functional because it shows up as eth0. By default the adapter should get an IP address using DHCP unless you specifically changed this. Do you know if the router is serving IP addresses with DHCP? Or is the network configured using manual IP addresses? Is there any extra security on the router like a MAC address filter? Tried another port on the router and another network cable?

---

### Post by Robert Neuron on 2014-03-22
I have the same problem, and I have some experience with Ubuntu. I haven't dared to try the solutions offered because I can get a wired internet connection by going to "recovery mode" and I am afraid of making things worse. When you have a black screen with a little line blinking in the upper left corner, press key "F12" and hold it. It should give you a menu where you will find "network". Use the "down" key to there and press "enter". You then will go back to the menu with "normal startup". Press "enter" and the same with the following windows that appear.

You may need to shut off your machine and try a second or third time. I know that this is a temporary solution, at least it works for me. The error that I get if I don't do this is "ignore eth0=eth0". I don't know why it does that. I also get "initctl failed". This never happened before 12.04.

I know this is long but I try to explain it in the clearest words possible. If anyone can explain my problem, I would be very appreciative.

---

