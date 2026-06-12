---
title: "Wireless network not realised..."
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by paulm2008 on 2008-07-24
Hello and Good Evening

Following advice from this forum, I [hope] have now managed to install the ndiswrapper package - simply double clicking on the file on the CD - this opened an installation manager - this seems to have worked.

I also hopefully installed the wireless driver wg111v3.inf using ndiswrapper.

But there appear to be a problem.

When I go into

Windows Wireless Drivers

It does actually list the driver, namely

wg111v3

and states that the hardware is present - all good [I think !!]

However when I then go to Network, There is no wireless option, only 2 wired options + Point-to-Point connection. I guess something's not quite right. 

Also

sudo lshw -C network

Does not yield any information about anything at all

Anyhelp would be appreciated

Kind Regards

Paul

---

### Post by northern lights on 2008-07-24
> **paulm2008 said:**
> 
Also

sudo lshw -C network

Does not yield any information about anything at all

Even if there was no driver what so ever installed, that should show your ethernet device.

Can you post the output of ```
ifconfig
```

Thank you.

---

### Post by paulm2008 on 2008-07-24
Thank You for your help, Please find attached the iconfig listing.  I'm currentlu on line, via a windows laptop - so I have to keep swapping the USB pen drive over to transfer information

paul@paul-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:c9:5d:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:c9:63:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:c9:5d:f7  
          inet addr:169.254.9.217  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:221 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83100 (81.1 KB)  TX bytes:83100 (81.1 KB)

Thank you

Regards

Paul

PS when I issue the command

iwconfig

I get

lo     no wireless extensions.

eth0   no wireless extensions.   

eth1   no wireless extensions.

something's amiss somewhere

---

### Post by northern lights on 2008-07-24
Something's amiss indeed, as a wireless interface does not show up anywhere.

Does
```
lshw -C network
```
show the ethernet adapters at least? Or nothing?
If it gives you network adapters but not the wireless card, it is most likely physically disabled / broken / not present.

Laptop or desktop?

Recently added wireless device or did it work before?

---

### Post by paulm2008 on 2008-07-24
Hi,

Decktop, with a wireless adaptor.  Works when I boot the system into Vista - but doesn't work with ubuntu.  My system defn is basically

Q9540 CPU
Striker II Formula
4Gb 1066Mhz Corsair Dominator CL5 RAM,
8800GTX xfx Graphic card

Thank You for you efforts

Kind regards

Paul

---

### Post by zipperback on 2008-07-24
Could you please also provide the output from:

```
lspci
```

Thank you


-zipperback
:popcorn:

---

### Post by match002001 on 2008-07-24
Are you running 64 bit? 

If so you need to find the Marvell 8388 driver because the WG111v3 does not have a 64 bit driver. I would also highly recommend you use that driver anyway because that is the chipset that it uses

---

### Post by paulm2008 on 2008-07-24
Hello, I initially installed the 64 bit ubuntu version, but with all the problems I was having Ire-formatted my drive and installed the 32 bit.  I may actually revearse this and try the 64 bit again.  I have been tyring to fo the most simplest of tasks for a week now. I cannot even get the basics i.e. install build-essential/ndiwrapper to work via the terminal - which I would have thought would be the most logical way to install packages.  Oh well - I will try this tomorrow

thanks again for all you help

Regards

Paul

---

