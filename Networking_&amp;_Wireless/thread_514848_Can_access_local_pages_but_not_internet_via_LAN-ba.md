---
title: "Can access local pages but not internet via LAN-based ISP"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by Sean Babu on 2007-08-01
Greetings all; Ubuntu newbie here. This problem is a little unusual; I will try to be both succinct and thorough.

In India, many ISP's work by simply stringing up ethernet cable along telephone poles to connect users to their servers. The user has a static IP address; no login procedure is required. My particular ISP also records MAC addresses; I couldn't get my Windows laptop to work on the internet until I assigned it the same MAC as my desktop. Until I did that, it could access local pages on the ISP's server (like [http://10.10.10.10](http://10.10.10.10) and its useless help forum) but not web pages (e.g., cnn.com, yahoo.com). I don't have a router.

I have now installed Ubuntu 7.04 on my desktop; it dual boots with Windows. I would think that it would use the hard-burned MAC adddress, but Ubuntu reported 00:00:00:00:00:00. With help from this forum, I manually tweaked the address.** ifconfig** reports the following:

```

eth0      Link encap:Ethernet  HWaddr 10:E0:8C:10:11:A0  
          inet addr:10.2.23.2  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1907405 (1.8 MiB)  TX bytes:2751 (2.6 KiB)
          Interrupt:17 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

The IP address and domain information are all correct. (I don't want to go into the networking wizard again as it tends to mess the settings up.) **Bcast** I don't know about.

The situation as it stands is very similar to the problem I had on my Windows laptop before changing the MAC address. I can access my ISP's local pages (e.g., 10.10.10.10) but nothing external (cnn.com). What's different from the laptop is that Firefox times out immediately after I type the address in; it's like it's not even trying to access the page but immediately being blocked. I also cannot ping anything outside. I saw something on this forum about problems with ipv6. I tried disabling that but it didn't help. As far as I know no firewall is running; I certainly haven't installed one.

My guesses as to what the problem might be:

1) Somehow the spoofed MAC address is getting overridden.
2) Some other network setting I, as a Linux newbie, know nothing about needs to be tweaked. (Bcast?)
3) My ISP is doing something sinister.

Any assistance anyone could provide would be immensely appreciated.

---

### Post by Steve1961 on 2007-08-01
can you ping web sites:

ping -c 3 [www.google.com](www.google.com)

---

### Post by Sean Babu on 2007-08-01
BTW the network card is Realtek RTL8139.

---

### Post by Sean Babu on 2007-08-01
> **Steve1961 said:**
> can you ping web sites:

ping -c 3 [www.google.com](www.google.com)

Nope, can't ping outside sites.

---

### Post by xiehuipiaofeng on 2007-08-01
If the windows and linux are all in your computer, and you have only one network card, i think the MAC of it in windows is as same as in linux. If the network card is work fine in windows, you could remember the mac using ipconfig /all in cmd.exe. And then, you could change the mac in linux manually. The steps are the following:
1. At the first, you must stop the eth0.
     [SIZE="2"][COLOR="Red"]sudo /sbin/ifconfig eth0 down[/COLOR][/SIZE]

2. Change the MAC address of eth0.
     [SIZE="2"][COLOR="Red"]sudo /sbin/ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE[/COLOR][/SIZE]

3. in the end, restart the eth0.
     [SIZE="2"][COLOR="Red"]sudo /sbin/ifconfig eht0 up[/COLOR][/SIZE]

Bcast of eth0 is right,because the Mask is 255.0.0.0.

---

### Post by Sean Babu on 2007-08-01
> **xiehuipiaofeng said:**
> If the windows and linux are all in your computer, and you have only one network card, i think the MAC of it in windows is as same as in linux. If the network card is work fine in windows, you could remember the mac using ipconfig /all in cmd.exe. And then, you could change the mac in linux manually. The steps are the following:
1. At the first, you must stop the eth0.
     [SIZE="2"][COLOR="Red"]sudo /sbin/ifconfig eth0 down[/COLOR][/SIZE]

2. Change the MAC address of eth0.
     [SIZE="2"][COLOR="Red"]sudo /sbin/ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE[/COLOR][/SIZE]

3. in the end, restart the eth0.
     [SIZE="2"][COLOR="Red"]sudo /sbin/ifconfig eht0 up[/COLOR][/SIZE]

Bcast of eth0 is right,because the Mask is 255.0.0.0.

Thanks. Just to be clear, I've already done this. I used ifconfig to change eth0's hwaddress while running; it didn't work. I also was able to make the change permanent by modifying some system files (/etc/iftab? /etc/rd.local? something like that/can't check now as I'm in Windows.) That too did not make the internet work.

---

### Post by Sean Babu on 2007-08-01
The before-bed bumpage of hope.

---

### Post by Sean Babu on 2007-08-01
Bump.

---

### Post by Sean Babu on 2007-08-01
When pinging outside sites from the terminal, the exact response is an immediate

connect: Network is unreachable

In the Device Manager under "System: Hardware Information," 00:00... is still shown as the address of the network card, not the spoofed address that ifconfig shows (which, ironically, is actually the physical address the card should return.)

---

### Post by Sean Babu on 2007-08-01
Fixed it! My Google-fu is strong this morning. I found something which advised me to do this:

 **netstat -nr**

Which returned:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0

I then did this:

**sudo route add -net 0.0.0.0 gw 10.0.11.1 eth0**

So **netstat -nr** now returns:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0
0.0.0.0         10.0.11.1       0.0.0.0         UG        0 0          0 eth0


With the result that I am now posting from Ubuntu!

Question: how do I make this addition permanent?

---

### Post by Sean Babu on 2007-08-01
SOLVED.

I added the **route** line to /etc/rd.local

---

