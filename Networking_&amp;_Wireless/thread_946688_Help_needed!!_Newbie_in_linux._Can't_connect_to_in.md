---
title: "Help needed!! Newbie in linux. Can't connect to internet."
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Riffat on 2008-10-13
I am totally unfamiliar with linux. Using for the first time. I can connect to internet. I am using broadband line from local provider. i need to enter ip, gateway, mac etc. I hv entered ip gatewaysubnet mask. But cant find where to put mac address. plus how can i see if my LAN card is working or not??
I am using on board lan card Intel(R) 82566DC Gigabit Network Connection and my motherboard is Intel DG965RY.
By the way I also have xp installed.

---

### Post by puppywhacker on 2008-10-13
All network cards have leds at the connector-side ... solid orange means the link is up, green blinking means you have some form of traffic.

You should never have to set your the MAC address. To the right top of the screen you have a clock. If it also tells you the temperature you have an internet connection. You should also have an icon with two black monitors behind each other. click it for manual configuration. (and choose unlock) Otherwise the same network menu can be found under "system/administration/network" ...

In a terminal you could run these commands for some clues.
lsmod       (and look for the module e1000)
sudo mii-tool
ifconfig
route
ping [www.google.com](www.google.com)

---

### Post by Riffat on 2008-10-13
but without MAC even my xp cant connect to internet. so i thought may b i need that in linux too. By the way havent entered mac address. 

One more thing, how can i know if my LAN card driver is properly installed and working??

---

### Post by Iowan on 2008-10-13
> **Riffat said:**
> I am totally unfamiliar with linux. We can fix that...
Open a terminal, issue the command **ifconfig -a**. That displays the results of your interfaces. You should also be able to find your MAC address in the results.  Copy/paste (or copy down and enter) results here.
Another command to try is **lspci |grep eth**. That one lists your PCI devices, then filters the results for lines containing "eth".

Now you're not "totally" unfamilar with linux. :)

---

### Post by Riffat on 2008-10-13
@puppywhacker
module e1000 used by 0.

@Iowan
See if u can understand this.

eth0      Link encap:Ethernet  HWaddr 00:19:d1:ee:34:d2  
          inet addr:10.11.24.32  Bcast:10.11.24.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:feee:34d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:33649 (32.8 KB)  TX bytes:6019 (5.8 KB)
          Base address:0x30c0 Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

got from lspci:
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)

---

### Post by Riffat on 2008-10-13
By the way whats physical adress?? In xp if u use ipconfig /all it shows ip gateway physical adress etc. this physical address wa given to me by my service provider. where do i put this address in ubuntu??

---

### Post by Iowan on 2008-10-13
My interpretation of a physical address would be the MAC (Hw) address - but your ISP can't just assign one - that's built into the NIC. Ubuntu doesn't need that info - it just reads it from the "card".  If you've been instructed to use a static address, the other potentially missing piece would be the gateway. I presume 10.11.24.32 is the address you were assigned. Did they give you a gateway?  Besides the manual configuration page, another place to look (should have the same information) is **/etc/network/interfaces**. Posting that might be helpful.

---

### Post by Riffat on 2008-10-13
it says bash permision denied. i am administrator then why permission denied??

u r saying i cant give mac but i entered this number myself. network connections>properties>configure>Advance>Logically Administrated address, here i entered this number which my service provider gave me. I am nt sure if its my real one or not. how can i check my REAL mac number(in xp or ubuntu)??

Btw i did gave the gateway.

---

### Post by Iowan on 2008-10-13
Sorry - my bad... **/etc/network/interfaces** is a file - not a command.  You could **less /etc/network/interfaces** or **cat /etc/network/interfaces** and post results. **Sudo** is generally required to actually get administrator rights - but it won't help in this case.
What number did you enter? 10.11.24.32  is an IP address (which you *could* enter.  00:19:d1:ee:34:d2 is your hardware address (AKA MAC address) which generally is not modifiable. That information was included in the results of **ifconfig** (the -a option listed all interfaces - configured or not.)

---

### Post by Riffat on 2008-10-14
those two comand shows file or directory not found.

the MAC address i m talking about is a virtual MAC address it doesnt change  the real one. is there any way to use virtual MAC in ubuntu??

---

### Post by puppywhacker on 2008-10-14
In short:
  ifconfig eth0 hw ether 00:11:22:33:44:55

In long:
1. lspci | grep Eth
   is the list of devices on the PCI bus.
   your 82566DC is on PCI location 00:19.0 (useless info :-)
2. lsmod | grep e1000
   is a list of modules using these devices
   e1000 is the driver to use for your interface
   used by 0 means there are no other modules depending on it, that is OK!
3. sudo mii-tool eth0
   probes if the network link is up
4. ifconfig eth0
   shows the configuration for the eth0
   tx / rx show counters. you are sending/receiving packet.
   your ip-address seems configured. it's just not communicating properly
5. arp -an
   shows which mac-address linux has learnt.
6. ifconfig eth0 hw ether 00:11:22:33:44:55
   sets the mac-address to the virtual address until you reboot


7. sudo tcpdump -i eth0 -qn
   will show you the packets flowing over the line.

I have never seen an internet provider to require you to set a mac address. congratulations, you're the first =)

---

### Post by Iowan on 2008-10-14
As fate would have it, I stumbled on a thread about randomizing a MAC address. [This]("https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses") help page references a package called **macchanger** that may be what you're looking for.

---

