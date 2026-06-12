---
title: "Can not get connected to the internet through my router"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by habtish on 2006-12-24
Just to give some background information, I had Adelphia as my ISP and been using a router(LinkSys Wired) to connect to the net without a problem. Thanks to this thread [here]("http://ubuntuforums.org/showpost.php?p=1786168&postcount=6")(ubuntuforums.org)I was also able to set a static internal IP so my internal Ip wouldn't change everytime my DHCP was renewed.
Well Adelphia was recently bought out by Comcast and I previously lost internet connection because of a DNS switch they did, which I upgraded without a problem. Today, for no reason, my internet connection was lost again and the Tech support people at Comcast were eager to help as long as I was using Windows, no one had any idea about Linux network configurations there.
Right now I had to select DCHP assigned Ip to get a connection and also have to use a direct connection from my Cable modem to my computer to be able to get connected. When I try to pass the connection through my router, I can not get connected for some reason, neither can I set my local static IP ( Which I sort of need to access my machine remotely and also my webserver)
What settings do I need to tinker with in Edgy to pass my connection through my router??
Here's an output from my current <ifconfig> if this helps in giving a better clue
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:19:09:C0  
          inet addr:71.63.52.144  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe19:9c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:393199 (383.9 KiB)  TX bytes:37230 (36.3 KiB)
          Interrupt:201 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```Please let me know if you have expertise in this area but are not able to help because my post was not clear enough, then I can provide more information...

Thanks in advance

---

### Post by gonesolo on 2006-12-24
By the sounds of things it sounds like your linksys router is just passing all the network traffic directly through to your system, acting in a bridge mode rather than router mode. I have a linksys router also (although wireless) and I let the router do all the negotiation regarding internet connection and stuff and then me/my pc have very little to worry about regarding getting access to the internet as my router keeps the connection. 

Do you have a static or dynamic IP from your ISP?? if you have a dynamic but you are forcing your sys/router to stay with a static ip you are possibly using an ip address that is in your ISPs dhcp scope. It works fine as long as the ISP has your machine down as the registered user but every time the DHCP server/clients request a renewal then there is a possibility that the ISP server gives that ip to another user but as your pc is being forced to stay on that IP you and, possibly, the other user can not connect.(*,)

---

### Post by habtish on 2006-12-24
gonesolo, thank you for your reply... I have a dynamic IP which rarely gets renewed (got renewed once in 6 months) But the way it had worked was the router will renew its DCHP table but not pass it on to my machine as I had assigned an internal static IP outside the range of DHCP. 
Even trying to set a connection through DCHP with my router is not working now, I was thinking once I got the router into play , I can worry about the static ip issue later... What do I need to do to get the router to act as a router and not a  bridge?
[I plan on shutting down, disconnecting all connect6ions, power recycling both my router and Modem and connect the router to the modem and my pc to the router and hope Ubuntu will update its network settings] please let me know if you have any remedies in mind... I really need to get my router into play (for port forwarding and all that good stuff)

---

