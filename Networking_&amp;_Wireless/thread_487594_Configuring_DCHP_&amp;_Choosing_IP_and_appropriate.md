---
title: "Configuring DCHP &amp; Choosing IP and appropriate subnet mask"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by frogotronic on 2007-06-29
Hello,

  DCHP3 was installed as a dependency and always comes up as "failed!".  So I'm trying to set-up DCHP properly.  I have an ethernet port eth0 and a wireless wlan0 card.  I'm using GDHCPd to configure the two internet devices.

My problem is that I can't seem to figure out how to choose the appropriate subnet mask that correlates to the IP address of the device. I don't understand the rules.

Here's the output of the "ifconfig" command:
```

eth0      Link encap:Ethernet  HWaddr 00:04:76:50:62:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2c00 

eth0:avah Link encap:Ethernet  HWaddr 00:04:76:50:62:80  
          inet addr:169.254.5.233  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2164 (2.1 KiB)  TX bytes:2164 (2.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0D:3A:25:58:AE  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:3aff:fe25:58ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1556 errors:0 dropped:64 overruns:0 frame:0
          TX packets:2029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1261070 (1.2 MiB)  TX bytes:175290 (171.1 KiB)
          Interrupt:10 
```

Any help,or links would be appreciated.

- CH

---

### Post by kidders on 2007-06-30
Hi there,

Are you trying to configure a DHCP client or server?

You've sort of got the rules backwards, in a way. Normally, you choose IP addresses to match a netmask ... not the other way around. The netmask describes (among other things) the parts of an IP address that are significant, so there is no way to guess the "right" one by looking at an IP.

For a home network, the most important rule is that you *absolutely must* choose a subnet that is reserved for private use. For instance, the whole of 10/8 and 192.168/16 are reserved, along with  172.16/12. Because it's relatively small, and easy to work with, many opt for addresses in the 192.168/16 range. As a "for instance", my LAN is set up like this...

The whole of 192.168/16 is waaaay to big for my needs, so all my machines have addresses in the 192.168.7/24 range. Essentially, that means that the "192.168.7" part is used to identify my network, while the final digit combination (1-255, give or take) identifies the individual computer within it, giving me space for about 250 of them ... well in excess of my requirements. The computer I'm using at the moment has 192.168.7.**203**, with a netmask of 255.255.255.0.

Hypothetically speaking, the address space I'm using allows me to set up another 250-ish similar networks, at 192.168.**0**/24, 192.168.**1**/24, 192.168.**2**/24...

So, step 1 is basically to describe a network. In my case, that's 192.168.7/24. That tells you what IPs are legal (so your DHCP server can begin dispensing them), and gives you a corresponding netmask (which in my case is 255.255.255.0). The other important piece of information distributed by DHCP servers is the default route (often called a gateway), which is normally the address of your connection to the internet. Data destined for an unrecognised network (eg something other than 192.168.7/24) is typically routed there, in the hope that whatever's at that location (eg a router) knows what to do with it.

I hope that helps a little.

---

