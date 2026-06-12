---
title: "Having problems with my XP and Linux network"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by porkey10 on 2008-08-22
Ok first of all I am very novice when it comes to networking so bear with me.  And i know networking can be extremely complicated ....So here is the deal.  

We have 5 PCs in the house with Windows XP loaded on it.  This is the only PC we have Linux on.

The main router that connects everything to our phone line has 4 ports on it.  1st port is our main XP PC, 2nd is another XP PC, 3rd is this Linux PC and 4th port goes to another router at the other end of the house wich has another 2 XP PCs on it.

We've never had any problems before, but now, every time this Linux PC is connected to the main router, the 2 PCs at the other end of the house get an error "cannot assign network address" - "Limited or no connectivity".  But the other XP PCs still work fine (the ones connected directly to the main routher- not the 2nd one at the other end of the house).  When I unplug this Linux from the main router, everything works fine again.

Please any ideas as to what the heck is going on??

I know you'll need more specs but Linux really isn't my thing (this is my dads PC and he is only testing the Linux system for "something to do"), so you'll have to tell me exactly where to get any extra specs u need from.

Again please bear with us newbies and be patient.

- Dave and Steve

---

### Post by sdide on 2008-08-22
Hey,
Sounds like somehow the linux-box is getting the same address as the 2nd router.

On a sidenote, you might want to change the 2nd router with a "dumb" switch, unless you really need the 2 other pc's to be on a different network.

---

### Post by Neobuntu on 2008-08-22
Is it possible that one computer is set to a static IP that is already assigned by DHCP to another? Thus two ports (including the one to the Two remote PC's) are fighting for the one improper IP address?

---

### Post by porkey10 on 2008-08-22
Yes I think that is the problem, the two ports (Linux PC and the one the 2nd router is connected to) are getting the same address assigned??  But you'll have to guide me through the process of fixing that because I really am quite clueless, especially with Linux.  I'm guessing its fixed by changing the address of the Linux but buggered if I know how to do that. :(

Oh and I just realised, if I plug our 5th XP PC (previously not connected to the network at all) into the port that the linux was in, everything works fine.  So I guess its not exactly the port if another PC works, its just the Linux PC needs its address changed, correct?? :confused: So how do i do that?

---

### Post by Iowan on 2008-08-22
If you can't beat 'em, join 'em...  Under system administration settings, change from Static Address to Automatic Configuration (DHCP).  (personally, I'd change it in **/etc/network/interfaces** file).  Restart networking from a terminal with **_sudo_ /etc/init.d/networking restart**.

---

### Post by matt79 on 2008-08-22
Try shutting all the computers down that you believe are connected to the problem. Then start the linux machine wait like five minutes and start the other computers up (the xp ones). See if that works.

---

### Post by porkey10 on 2008-08-23
Ok so I have tried several of the replys, but no luck.  I changed it to Automatic Configuration (DHCP) and no luck, when i did that the interfaces file changed itself which I assume is what it was supposed to do, then i restart the network, but still no luck.

I also tried changing some of the settings on my Thompson Speedtouch 510, like changing it to auto dhcp, but that didn't do anything either. I tried turning off the power on my Thompson and restarting but that didnt work either.

Please any other ideas? I am pulling my hair out here.

Also, if possible, can you be a bit more in depth with what u want me to do.  It took me close to 2 hours of playing around to even find the network settings haha, and just as long to figure out I had to type "sudo" into the command lines for stuff.  So as you can see I really am very novice.

I feel like a douch but please help, i'm slowly getting there.

---

### Post by mellowd on 2008-08-23
Right, what IP is your linux box getting?

Open a terminal and type this:

```
ifconfig
```

Paste the results here

---

### Post by Iowan on 2008-08-23
> **porkey10 said:**
> 
Also, if possible, can you be a bit more in depth with what u want me to do.  It took me close to 2 hours of playing around to even find the network settings haha, and just as long to figure out I had to type "sudo" into the command lines for stuff. :oops: Oops, my bad... I'm still running Gutsy, so I'm not sure where/what pulldown options are in Hardy.   
I'll fix the info to restart networking (and pretend it was right to begin with...)   [SIZE="1"]...Sorry...[/SIZE]

Another thought - the two routers aren't both acting as DHCP servers?  It'll work as long as their address ranges don't overlap.

---

### Post by porkey10 on 2008-08-27
> **mellowd said:**
> Right, what IP is your linux box getting?

Open a terminal and type this:

```
ifconfig
```

Paste the results here

```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:e3:28:f9  
          inet addr:10.0.0.56  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21b:38ff:fee3:28f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:747452 (729.9 KB)  TX bytes:183159 (178.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49224 (48.0 KB)  TX bytes:49224 (48.0 KB)

```

that good??

---

