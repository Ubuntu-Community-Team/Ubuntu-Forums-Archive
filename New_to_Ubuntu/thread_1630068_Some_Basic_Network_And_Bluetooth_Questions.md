---
title: "Some Basic Network And Bluetooth Questions"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-24
Hi,

I've been going round in circles now for the last few days, trying to work some basics out. Because my networking knowledge is poor I'm probably looking in the wrong places, asking the wrong questions or have misplaced expectations.

I have two netbooks each with Maverick installed, both with Bluetooth and with wireless. One of them connects to the internet via GPRS dongle. So far I can send files via Bluetooth to each other but they don't appear to be part of a network. I can't see, for example, Machine B from Machine A under my Networks link in the Places drop-down. 

1) Can I create a Bluetooth or wireless network without a router and, if so, how?
2) Can I use Remote Desktop between these two computers via this connection or do I have to be connected to the internet to do this?

The help files are not helping. For example under Internet/Networking index:

[https://help.ubuntu.com/10.10/internet/C/index.html](https://help.ubuntu.com/10.10/internet/C/index.html)

... why is the first link not 'Setting up a network'? 

What am I not understanding here? I am very, very confused. If someone could give me just a few minutes explaining the basics, perhaps helping me to understand what I can and cannot do with my current set-up,  I would be very grateful. Thank you.

---

### Post by Verbeck on 2010-11-24
to create a wireless network, right click the network icon on the top panel and select 'create new wireless network'

to enable remote destop, check the settings in  system>preferences>Remote Desktop. then use the Remote desktop  viewer in applications>internet

edit : didn't notice that you were using the netbook version - might differ how its done

---

### Post by demonboy on 2010-11-24
OK, if I create a wireless network (it's not quite as you suggest because right-hand clicking doesn't give me the option to create a new wireless network, you have to go via Edit Connections), that then makes me lose my Mobile Broadband connection. It seems I can be a member of either/or, not both.

How can I use my Mobile Broadband to connect to the internet whilst also connecting to the Wireless Network I just created?

Also, having just created that wireless network on Machine A, why can Machine B not see that network and join it?

---

### Post by Verbeck on 2010-11-24
i'm not sure whether the gnome network manager can connect to two wireless networks simultaneously..never tried that

if machine B cannot see it, try the option 'connect to a hidden wireless network' when you click on the 'network' icon, or restarting the adapter

---

### Post by spiky001 on 2010-11-24
Is it a usb dongle that you use for internet?

---

### Post by demonboy on 2010-11-24
> **spiky001 said:**
> Is it a usb dongle that you use for internet?

Yes.

I have now managed to create an ad hoc wireless network on Machine A. However I can't connect to the internet and be on that ad hoc network at the same time.

Also, how do I get Machine B to connect to that ad hoc network? Should I just view the available wireless connections and click connect (there is no password as yet)? If this is the case then Machine B failed to connect, so do I have to manually configure Machine B to connect to the ad hoc network that was created in Machine A? Do I not have to add IP ranges etc or should any computer be able to connect within range?

---

### Post by spiky001 on 2010-11-24
Ok lets start again I have a mobile broadband connection, then i have a wireless connection setup as adhoc. Is this how yours is?

---

### Post by demonboy on 2010-11-24
> 
Ok lets start again I have a mobile broadband connection, then i have a  wireless connection setup as adhoc. Is this how yours is? 	


Correct.

(Also I have now successfully got Machine B to connect to the ad hoc network. I had to change the IPv4 settings to 'Shared To Other Computers' on Machine B.)

---

### Post by spiky001 on 2010-11-24
Good you beat me to it so you set to go now?

---

### Post by demonboy on 2010-11-24
No, because I cannot connect to the internet via the Mobile Broadband USB dongle AND be on my wireless network at the same time. Sorry if I misled you there but I can get the two machines to join the network only when I disable my USB dongle, which means coming offline.

Do you have both running concurrently then?

---

### Post by spiky001 on 2010-11-24
Yes am on it now, Ok check the ip on both machines ```
ifconfig
```

---

### Post by demonboy on 2010-11-24
On Machine A (my machine with dongle):

> 
jamie@jamie-NC10:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:77:d3:c6:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1511991 (1.5 MB)  TX bytes:1511991 (1.5 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.97.44.43  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3385567 (3.3 MB)  TX bytes:692320 (692.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:c9:e4:90  
          inet6 addr: fe80::221:63ff:fec9:e490/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16914 (16.9 KB)  TX bytes:124577 (124.5 KB)



On Machine B, my ship's computer:

> 
ship@ship-nc10:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:54:a4:97:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:0b:6b:7c:6a:78  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6bff:fe7c:6a78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:503 errors:0 dropped:0 overruns:0 frame:24169
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38459 (38.4 KB)  TX bytes:22075 (22.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1629355 (1.6 MB)  TX bytes:1629355 (1.6 MB)



---

### Post by spiky001 on 2010-11-24
On machine a there is no ip address on wlan0 which i assume is your wireless, B has address of 10.42.43.1 I presume is wireless?

---

### Post by demonboy on 2010-11-24
Correct for Machine B since this is the only device running. Am unsure of Machine A. How can I check?

---

### Post by Penguin=) on 2010-11-24
Try connecting them both through a USB

---

### Post by spiky001 on 2010-11-24
so the machine with internet you set wireless ipv4 to shared the other machine wireless ipv4 set Automatic dhcp maybe when you set all this reboot systems

---

### Post by demonboy on 2010-11-24
No. Machine A created the ad hoc wireless network so it has to be set up with manual IPv4 settings, where:

> 
Address: 192.255.0.1
Netmask: 255.255.255.0
Gateway 1.1.1.1


Machine B's IPv4 settings were set to 'Shared to Other Computers'.

This set-up works in terms of connecting to the wireless network, but prevents my Mobile Broadband connection. The Mobile Broadband connection isn't disconnected though, it still says it's connected, it just won't let me do anything online. Maybe there is a port conflict?

It is now 4.20 in the morning and I have an early start tomorrow, so I have to head to bed! I'll pick this up again in the morning and if you have any further thoughts please let me know. Thank you very much for your help thus far, spiky.

---

### Post by spiky001 on 2010-11-24
Il,, be back here in about 13 hours if you still have probs pm if you need help

---

