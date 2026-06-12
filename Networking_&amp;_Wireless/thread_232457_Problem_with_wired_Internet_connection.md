---
title: "Problem with wired Internet connection"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by austinkjaa on 2006-08-08
[SIZE="3"]I'm trying to set up an ex-windows machine at my school with Dapper Drake Kubuntu. However, I'm having some difficulty connecting to my school's internet. As far as I know, my school uses static ip addresses (no DHCP), and connects straight to the internet (no router, switch, or server - don't ask me why, but we're trying to fix that).

Anyway, I copied the old windows ip information (address, netmask, gateway, dns server) and set it up the same under Linux, but I am still unable to connect to the internet. Here are the results from ifconfig:
[INDENT]
admin@JCA-Lab-2:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:4F:78:04:A0
          inet addr:172.20.1.18  Bcast:172.20.1.63  Mask:255.255.255.192
          inet6 addr: fe80::2c0:4fff:fe78:4a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18769 errors:1 dropped:0 overruns:0 frame:1
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1539166 (1.4 MiB)  TX bytes:13844 (13.5 KiB)
          Interrupt:11 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9516 (9.2 KiB)  TX bytes:9516 (9.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/INDENT]

I did notice one difference from the ifconfig output of most other posts, but am not sure of the significance, if any. It's under eth0:

[INDENT]RX packets:18769 errors:1 dropped:0 overruns:0 frame:1
[/INDENT]
Most other posts had "errors:0" and "frame:0".

When I try to ping, etc. I get "connect: Network is unreachable".

Anyway, any help would be appreciated. Thanks[/SIZE]

---

### Post by ohgod on 2006-08-09
Are you sure you're connected straight into the internet and that there's no DHCP?  The IP address that your card has ( 172.20.1.18 ) is a private address (not valid on the internet).  So I'm guessing you are actually behind a router.  You might want to contact your local tech support/ network admin/ whatever and ask them what settings you should be using.

---

### Post by austinkjaa on 2006-08-09
> **ohgod said:**
> The IP address that your card has ( 172.20.1.18 ) is a private address (not valid on the internet).  So I'm guessing you are actually behind a router.  You might want to contact your local tech support/ network admin/ whatever and ask them what settings you should be using.

Thanks. That at least gives me an idea of which direction to look in. The only problem is that I'm kinda the local tech support. Yeah, that's right - a noob. They couldn't afford to hire anybody that knew what they were doing, so they got me. Ha!

> **ohgod said:**
> Are you sure you're connected straight into the internet and that there's no DHCP?

See, here's what made me think there was no router. This is how it's wired.

Outside world -> Satellite on roof -> box next to satellite (router?) -> wire down through roof to hub in computer lab -> wire to wireless router in office.

I have Linux installed on my laptop with a wireless card. I can connect to the internet through the wireless card on my laptop. It goes through the router in the office, picks up DHCP, and works fine. But, when I plug straight into the hub (the same hub that the wireless router is connected to) I get no access.

Either my wired card isn't set up right, I've got some settings wrong, or there's no router/DHCP between the hub and the satellite (or maybe I'm missing something else). The thing is, it worked fine under Windows, so why not in Linux? The wiring is all the same. I'm missing something in the software setup. Arg!

Anyway, I'll try to get in touch with our ISP and see what they can tell me about how we're connected. I may even crawl up on the roof and see what the box is all about. It's frustrating being in charge of something and not knowing what you're doing yet. I'll probably be back. Thanks.

---

### Post by RedBoot on 2006-08-09
> admin@JCA-Lab-2:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:C0:4F:78:04:A0
inet addr:172.20.1.18 Bcast:172.20.1.63 Mask:255.255.255.192
inet6 addr: fe80::2c0:4fff:fe78:4a0/64 Scope:Link
ohgod is correct. The IP you listed is considered a private IP and cannot be an internet IP. You can have host IPs of 172.20.1.1 - 172.20.1.62 and the broadcast IP is the next one, 172.20.1.63. FWIW, if you want to know your internet IP, go to the working PC and go to the web site [ipchicken.com]("http://ipchicken.com") and it will tell you.

Not that any of that info gets you hooked up! But it would be helpful to try these steps:
[LIST=1]
[*]Does it appear that you have good lights at each end: NIC and hub?
[*]Can you ping 127.0.0.1? 172.20.1.18?
[*]Can you ping the gateway IP (you've not listed that here, but I'd guess it's 172.20.1.1)
[/LIST]
I've set up about 5 PCs of Ubuntu in my school, too, so I can relate!

---

### Post by ohgod on 2006-08-10
So, your wireless router is plugged into the same hub that you plug into when you have trouble connecting, right?  You might want to login to the wireless router to check out what settings it's using to get an IP address (whether it's DHCP or static, etc).  If you ape the settings the wireless router is using, it might help you out.

To connect to the wireless router's interface you'll want to connect to it via your wireless nic.  Then fire up a browser and type in it's address like so:  [http://192.168.0.1](http://192.168.0.1) (it might be 192.168.1.1 or something similar...check out the routers documentation to find out).

Hope that helps!

---

### Post by austinkjaa on 2006-08-10
Alright, still trying to get in touch with the guys that set up our "network." But, in the mean time, here's what I've learned:

1. I've got good lights on both the NIC and the hub.
2. I can ping 127.0.0.1 and 172.20.1.18.
3. I can't ping the gateway IP (172.20.1.254) which is the same default gateway the Windows computers are set up with.

4. The wireless router is using a static IP address (172.20.1.31) with a subnet mask of 255.255.255.192, and an ISP gateway address of 172.20.1.31. Why is the IP address the same as the gateway?
 
5. And, our internet ip is 207.70.191.118 - from any of the windows computers in the lab - so there must be some sort of router or switch or something up on the roof. I'll know more when I can get in touch with our network guys.

Thanks for the help so far.

---

### Post by RedBoot on 2006-08-10
Due to your use of the subnet mask 255.255.255.192, I mentioned in a previous post:
> You can have host IPs of 172.20.1.1 - 172.20.1.62 and the broadcast IP is the next one, 172.20.1.63.
Therefore, you _cannot _have a gateway of 172.20.1.254 since it is out of that range. (If you want to see why, try [subnet-calculator.com]("http://subnet-calculator.com"))

I would suggest you try to setup a static IP of 172.20.1.30 using the same gateway as the shown below, 172.20.1.31 and, if possible, the DNS addresses for your ISP.

---

