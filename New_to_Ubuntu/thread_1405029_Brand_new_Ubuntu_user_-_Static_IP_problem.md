---
title: "Brand new Ubuntu user - Static IP problem"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by HarryNZ on 2010-02-12
[SIZE=4]Hi

I have just installed Ubuntu 9.10 on my personal computer.

I'm battling to figure out how to enable my static internet connection. As suggested on the Ubuntu help pages I have been attempting to manually type in the necessary numbers under the 'IPv4 Settings' tab, located in Network connections/Editing Auto eth0


My first problem is that I do not confidently know my IP address. After bringing up a terminal and typing the command 'ifconfig', I bring up a something similar to:

[/SIZE]eth0      Link encap:Ethernet  HWaddr 00:15:c5:82:50:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
[FONT=Arial]

[/FONT][FONT=Arial][SIZE=5]Somehow I need to find out the following:

1. IP address: (I can't connect to an online reverse IP site obviously - I'm guessing that this will be different to the 'lo' internal IP?)
2. Netmask:
3. Gateway: (I think I know this - came with the router that I am using?)
4. DNS Servers: (can I use the free GoogleDNS 8.8.8.8?)

Any help would be greatly appreciated!
[/SIZE][/FONT]

---

### Post by Grenage on 2010-02-12
I would consider adding a new connection in the network manager, and specifying your settings in there.  Sometimes the gnome network manager has... issues.

P.S: A smaller font would rock, I had to stand on the other side of the road to read your post.

---

### Post by HarryNZ on 2010-02-12
Thanks for your help - though I am still having some problems.

Perhaps the attached screen shot will better describe my difficulties. 

In this screenshot I have displayed three windows.

1. Top left window - this is of a terminal where I have typed in 'ifconfig' in an attempt to find out my IP address.

2. Middle right window - this is where I have attempted to insert what I think is my IP address + netmask into my Network Connections 
(Is Network Connections this the same as Network Manager?)
(The DNS server I have inserted here is the free GoogleDNS one - will that work for me?)

3. Bottom left window - this is of a second terminal where I have typed in 'ifconfig' after I have attempted inserting the details into Network Connections as described in 2. above.

Q. When I open Firefox and attempt to log on to something like google.com, the browser displays an message "Server not found". Would someone be able to suggest where I am going wrong?

Many thanks!

---

### Post by audiomick on 2010-02-12
Hi.
I'm wondering why you need to set up a static IP. What exactly is your setup? The "normal" setup would be a cable/dsl modem, perhaps from the Internet Service Provider, then a router then your PC. Do you have something different to this?

---

### Post by thatguruguy on 2010-02-12
> **audiomick said:**
> Hi.
I'm wondering why you need to set up a static IP. What exactly is your setup? The "normal" setup would be a cable/dsl modem, perhaps from the Internet Service Provider, then a router then your PC. Do you have something different to this?

That's my question as well.  I think the OP may be making ubuntu more difficult than it needs to be.

---

### Post by Grenage on 2010-02-13
> **HarryNZ said:**
> Perhaps the attached screen shot will better describe my difficulties.

127.x.x.x is a localhost IP address, basically that routes all traffic internally, it will not get you an external connection.  You're going to need to find out what your settings should be, ISP support?

---

### Post by The Cog on 2010-02-13
Why do you need a static IP? Doesnt't your router have an inbuilt DHCP server? I would advise using an automatically allocated (DHCP) IP address if possible.

127.0.0.1 absolutely is the wrong IP address. That's the loopback address - an address that cannot connect outside the local machine. You should remove that configuration. As I said, I recomment using automatic addresses if you're not sure.

In your top-left screenshot, the ethernet cable is not plugged in, which would explain the lack of an IP address. If an interface doesn't show the word RUNNING, you should check your hardware and cabling.

---

### Post by HarryNZ on 2010-02-15
> **audiomick said:**
> Hi.
I'm wondering why you need to set up a static IP. What exactly is your setup? The "normal" setup would be a cable/dsl modem, perhaps from the Internet Service Provider, then a router then your PC. Do you have something different to this?
Hi!

Many thanks for your message - I have finally managed to sort my problem out and finally have internet!

Turns out that my setup is not directly connected to a router as I first thought but instead to an external modem/router that the ISP installed into my apartment. Hence the static IP was needed to connect to this piece of hardware.

Thanks once again,

H

---

