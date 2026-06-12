---
title: "Using 2 network interfaces 192.168.1.x"
date: 2020-10-04
forum: Networking &amp; Wireless
---

### Post by ubun567 on 2020-10-04
Hello,

I am trying to install a ZoneMinder server on my network and am having trouble getting it to work. I have successfully made it work on Windows 10 using Blue Iris (found camera straight away), but have spent a few days (and tried everything) without success using Ubuntu. 

- The computer is connected to the internet via Wifi on a 192.168.1.x network. 
- The POE camera has a fixed IP address of 192.168.1.10 and is connected to the computer via wired ethernet. The wired interface has a manual IP address set to 192.168.1.20 (both IPs unused on the wifi network)
- Network diagram below.

- The camera can be found (via internet browser) when ONLY the wired connection is enabled. Once the wireless is turned on the camera can't be found. 

I have tried bridging the networks, setting custom routing tables, but nothing works. 

Could someone please tell me the easiest way to make this work?

Thanks

[IMG]https://i.imgur.com/oA2jlJN.jpg?1[/IMG]

---

### Post by TheFu on 2020-10-04
To learn about IPv4 networking, there's a 3-part podcast series called "how the internet works" here: 
[https://www.grc.com/sn/past/2006.htm](https://www.grc.com/sn/past/2006.htm) There are transcripts or you can listen to the extremely long-winded, podcast.  #25-#27.

Easy networking setups require the interfaces to be on different subnets for routing to work or to be connected to the same router, somehow.  A $5 switch would work for that connection. If one of the wired connections isn't 1000 base tx, then you'll need a cross-over cable for the system-to-IPCam connection. The wiring is different.  The 1000 base tx standard automatically recognizes this and handles it. 100 base-tx and earlier do not.

---

### Post by SeijiSensei on 2020-10-04
The camera and the interface to which it connects need to be in a different subnet, say 192.168.2.0/24. Then if you enable IPv4 packet forwarding in /etc/sysctl.conf and reboot, the Ubuntu box will act as a router and pass packets between the camera and the router.

You might need to enable masquerading on the Ubuntu box with
```
sudo iptables -t nat -A POSTROUTING -o [wifi interface on Ubuntu] -j MASQUERADE
```
The entry for -o should be something like wlan0 or one of the much longer interface names Ubuntu now uses.  This way all the traffic from the camera appears to be coming from the wifi interface on the Ubuntu box, and the router will recognize it and masquerade it again out to the internet.

---

### Post by ubun567 on 2020-10-05
> **TheFu said:**
> 
Easy networking setups require the interfaces to be on different subnets for routing to work or to be connected to the same router, somehow. A $5 switch would work for that connection.


A wired connection between the router and Ubuntu computer would be very difficult. The camera and computer are close, but router is many rooms/brick walls away. 


> **TheFu said:**
> 
To learn about IPv4 networking, there's a 3-part podcast series called "how the internet works" here:
[https://www.grc.com/sn/past/2006.htm](https://www.grc.com/sn/past/2006.htm) There are transcripts or you can listen to the extremely long-winded, podcast. #25-#27.


I was listening weekly when that 3 part series came out. Haven't listened for a few years though. Proud owner of SpinRite. 


> **SeijiSensei said:**
> The camera and the interface to which it connects need to be in a different subnet, say 192.168.2.0/24.


Unfortunately the IP address is hard coded into the camera. (192.168.1.10)

---

### Post by TheFu on 2020-10-05
> **ubun567 said:**
>  Unfortunately the IP address is hard coded into the camera. (192.168.1.10)

Then you need to change the router's subnet to NOT be 192.168.1.x.  I'd be surprised if you couldn't setup DHCP reservation for that device and give it a different IP/subnet/gateway.  My networked TV tuners support that and I use it.

**Or **
to get everything connected on the same subnet, you could use power-line ethernet.  
I use that to connect my wiring closet upstairs to the downstairs switch.  Of course, it depends on the house wiring. I see about 10% of the claimed bandwidth on the box.  It is a 600 Mbps Powerline kit, so between 2 floors, I'm seeing a stable 60 Mbps, which is more than the true bandwidth I'd see using wifi.  People often confuse wifi connection speeds with that they truly achieve.  A 300 Mbps wifi connection might really provide about 80 Mbps and it isn't stable. The bandwidth jumps all over the place.

There are a few other options. But they all require different subnets for the 2 NICs on the PC. That's how networking ... er ... works.

---

### Post by SeijiSensei on 2020-10-05
> **ubun567 said:**
> Unfortunately the IP address is hard coded into the camera. (192.168.1.10)
Then use 192.168.2.0/24 on the wifi side and assign the network interface on the Ubuntu box an address in 192.168.1.0/24.  It doesn't matter what they are so long as they are different subnets.

---

### Post by ubun567 on 2020-10-06
Changing the wifi side to 192.168.2.x will be the the way to go. Thanks for the help guys. 

I was initially thrown by how this arrangement works so well in Windows 10. It may be unreliable or may break if there is a conflict IP on the wifi side.

---

