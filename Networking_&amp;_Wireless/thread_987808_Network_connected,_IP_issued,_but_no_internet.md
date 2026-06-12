---
title: "Network connected, IP issued, but no internet"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by jacal on 2008-11-19
Hi there. I'm brand new to Linux, literally only a few days. I've installed Ubuntu 8.10 on two separate machines now. The first worked flawlessly, the network and internet were working without any additional setup. The second one however doesn't seem to be so straightforward.

It tells me the Wired Network is Connected. If i right click on the network and view the details, it appears that it has issued an IP address, although it seems to be in the wrong range. I dual boot with Vista, and the internet is working fine in vista. However, my gateway is 192.168.1.1, but in Ubuntu i'm being issued with something different. So whilst it would appear i have connectivity, i cannot ping out, and cannot even ping my router.

Here is the output from *sudo lshw -C network* :
```
  
*-network                
       description: Ethernet interface        
       product: L1 Gigabit Ethernet Adapter        
       vendor: Attansic Technology Corp.        
       physical id: 0        
       bus info: pci@0000:04:00.0        
       logical name: eth0        
       version: b0        
       serial: 00:1e:8c:68:0d:fe        
       size: 100MB/s        
       capacity: 1GB/s        
       width: 64 bits        
       clock: 33MHz        
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation        
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.0.2 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
 
*-network DISABLED 
       description: Ethernet interface        
       physical id: 1        
       logical name: pan0        
       serial: 02:12:15:25:90:8e        
       capabilities: ethernet physical        
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

```


and here is the output from *ifconfig*

```

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:68:0d:fe 
          inet addr:192.168.0.2  Bcast:192.168.0.255 Mask:255.255.255.0 
         inet6 addr: fe80::21e:8cff:fe68:dfe/64 Scope:Link           
         UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1           
        RX packets:8 errors:0 dropped:0 overruns:0 frame:0           
        TX packets:36 errors:0 dropped:0 overruns:0 carrier:1           
        collisions:0 txqueuelen:1000            
        RX bytes:2783 (2.7 KB)  TX bytes:5372 (5.3 KB) 

lo        Link encap:Local Loopback             
          inet addr:127.0.0.1  Mask:255.0.0.0           
          inet6 addr: ::1/128 Scope:Host           
          UP LOOPBACK RUNNING  MTU:16436  Metric:1           
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0           
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0           
          collisions:0 txqueuelen:0            
          RX bytes:8092 (8.0 KB)  TX bytes:8092 (8.0 KB) 

```


Also, just for comparison, on the same computer but booted in Vista (where the internet & network works fine), here is the output from *ipconfig*

```

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::9513:7f37:cdb:3912%8
   IPv4 Address. . . . . . . . . . . : 192.168.1.9
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

```

Any help or suggestions would be greatly appreciated :)

---

### Post by jonobr on 2008-11-19
Hello


I would recommend disabling IPV6,
I wont post any links to how to do, If you research it, it should give lots of info.

I notice your gateway is 192.168.1.1 and your getting an IP address of 192.168.0.2?

As a test (if this is your network) you could probably change the IP address to a static address, use something like 192.168.1.20 , just make sure its not used.
Im sure then you can ping your router.

And also, just to state again your config,
You have a dual boot requesting an ip off the router/dhcp?

THanks

---

### Post by jacal on 2008-11-19
that's correct, dual boot requesting an IP from the router, which is working fine for other computers on the network, hence I really only want to use a static IP as a last resort, because there should be no reason why I can't have the same setup on Ubuntu.

Will try disabling IPv6 and see if I have any luck. Thank you for the suggestion.

---

### Post by jacal on 2008-11-19
Sadly, nothing changed after disabling IPv6.

On another note though, before disabling it I checked the IP address again. This time by chance it had found the right gateway (192.168.1.1) and issued an IP in the correct range (192.168.1.9). However, from the terminal, typing *ping 192.168.1.1* resulted in the response: *connect: Network is unreachable*

---

### Post by jonobr on 2008-11-19
Could you check what your default gatwayu is set to?

And report the new Ifconfig.
If you ping your local 192 address Im sure you get a response, Correct?

---

### Post by jonobr on 2008-11-20
Actually rereading your post you did give that info.

Post back if the ping to local host works and local IP work.
Are there any other devices you can ping to on the local network?

---

### Post by jacal on 2008-11-20
I noticed that it was very strange, sometimes it would issue a correct IP, other times the range would be incorrect. However, in the network manager I just ended up forcing a specific static IP and routing it through the correct gateway like you first recommended. After a restart the internet is working fine. I've still got IPv6 disabled though, should I re-enable it? How will it affect me if i leave it disabled?

Thank you very much for your help.

---

### Post by jonobr on 2008-11-20
Hey 


I doubt your using IPV6 on your equipment.

IPV4 addresses were running out up to the tech boom.

IPV6 was introduced to be the successor to IPV4.
It provides for a lot more address spaces.
After the 2000 tech boom crash, there was a lot of free space, and the urgency went out of it again, however, its coming back due to internet growth.

Your network issuing you a 192.168.x.x is a standard IPV4 address and you wont need to worry about it. Leave it disabled.


Ciao

---

