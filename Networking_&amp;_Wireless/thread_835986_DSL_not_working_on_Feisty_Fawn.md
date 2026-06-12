---
title: "DSL not working on Feisty Fawn"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by hackapelite on 2008-06-21
I booted up Feisty Fawn off the LiveCD (didn't install), but the internet's not working. It says that I'm connected to a wired network, DHCP is enabled, but whenever I try to access a website, Firefox comes up with the "Server not found" message. 

The DSL modem is Siemens SpeedStream 4200 hooked up via an Ethernet Cable. I run and installed the same distro on a virtual machine under XP, and the internet worked just fine. Is it necessary to install?

Would downloading the newest distro help (I'm currently speedlimited, so I have to wait a few weeks before being able to download anything), or am I doing something wrong?

---

### Post by hackapelite on 2008-06-21
*bump*

Just wanted to add that I'm a 100% noob when it comes to Linux... I had a look at a few threads but most of this console-stuff&whatnot doesn't make too much sense to me... please assume that I'm an idiot and need to be told every slightest detail.

---

### Post by superprash2003 on 2008-06-21
in windows did you require to use a dialer to connect to the internet? or internet works as soon as you swtich on modem?.. go to the terminal(Applications->Accessories>Terminal) and type ifconfig and post output here..

---

### Post by lisati on 2008-06-21
> **hackapelite said:**
> I booted up Feisty Fawn off the LiveCD (didn't install), but the internet's not working. It says that I'm connected to a wired network, DHCP is enabled, but whenever I try to access a website, Firefox comes up with the "Server not found" message. 

The DSL modem is Siemens SpeedStream 4200 hooked up via an Ethernet Cable. I run and installed the same distro on a virtual machine under XP, and the internet worked just fine. Is it necessary to install?

Would downloading the newest distro help (I'm currently speedlimited, so I have to wait a few weeks before being able to download anything), or am I doing something wrong?

You might also want to check if your wired connection is enabled. You can find it on the System->Network menu.

---

### Post by hackapelite on 2008-06-21
ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:13: D3:0F:78:AF [COLOR="Blue"]<-- That space wasn't there; only put it there to keep that smiley from popping up[/COLOR]
          inet addr:58.109.98.209  Bcast:58.109.98.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe0f:78af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3348 (3.2 KiB)  TX bytes:4303 (4.2 KiB)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

@superprash - No, I've never needed a dialer, the connection is always on. 
@lisati - I did make sure that the wired connection is enabled.

---

### Post by hackapelite on 2008-06-21
*bump*

I've tried different configurations, DHCP, IPv4 LL, both with Roaming enabled and disabled (and I don't even know what it does)... still no luck. Is it possible that my NIC (Realtek RTL8139 Family PCI Fast Ethernet NIC) isn't supported?

---

### Post by superprash2003 on 2008-06-21
what is your modem's ip address?? also type ping google.com in your terminal and post output!!

---

### Post by hackapelite on 2008-06-21
My IP's 58.109.98.209, will be back with ping results in a few minutes.

---

### Post by hackapelite on 2008-06-21
I tried pinging google.com and several other sites, but every time it comes up with the message "Unknown host: blahblah.com" or something along those lines, with no delay.

---

### Post by superprash2003 on 2008-06-22
is 58.x.x.x.x your internal ip address?? whats your modem's ip address?? the one you mentioned is your ip address.. because i saw it under ifconfig output

---

