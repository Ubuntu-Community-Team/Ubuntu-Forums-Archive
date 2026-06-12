---
title: "hp nx9030 cannot connect to internet with static ip!!!!"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by eternalsunshine on 2006-11-13
Hi,
I have a laptop hp nx9030.
My school gives us ip's and the other things like subnet mask etc.
Everytime i try to connect to internet with these i cannot succeed with ubuntu 6.06 or 6.10 . But at the same time when i log on with windows xp i can connect easily to internet with the same ip's etc.
Can you please help me with this problem, it is becoming to be so annoying , i installed ubuntu so many times because of this.

Thank you....
I hope someone will answer immediately!!!...

---

### Post by mips on 2006-11-13
Maybe you should provide us with a bit more information ?

The following stuff might help:
lspci -v (Just the ethernet controller parts)
ifconfig -a
route -n
cat /etc/network/interface
cat /etc/resolv.conf

From Windows DOS prompt: ipconfig /all

---

### Post by eternalsunshine on 2006-11-13
> **mips said:**
> Maybe you should provide us with a bit more information ?

The following stuff might help:
lspci -v (Just the ethernet controller parts)
ifconfig -a
route -n
cat /etc/network/interface
cat /etc/resolv.conf

From Windows DOS prompt: ipconfig /all


Windows IP Build

        Computer Name  . . . . . . . : metalingus
        Default DNS suffix . . . . . . . :
        Node Type . . . . .. . . : unknown
        IP Forwarding Active . . . . . . : Yes
        WINS Proxy Active . . . . . . . : Hay&#305;r

Ethernet Local Area network:

        Ba&#287;lant&#305;ya özgü DNS Soneki .  . . :
        Explanation  . . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Adress. . . . . . . . . . : 00-C0-9F-5D-30-A6
        Dhcp Active. . . . . . . . . . .: Hay&#305;r
        IP Address. . . . . . . . . . . . . : 10.10.12.211
        Subnet Mask. . . . . . . . . . : 255.255.240.0
        Default Gateway. . . . . . . : 10.10.15.255
        DNS Server. . . . . . . . . . . : 193.140.248.5
                                            193.140.248.10


Sorry for my translation....

Thank You....

---

### Post by mips on 2006-11-13
And the rest of the info ?

Search here for "8139" so long.

---

### Post by eternalsunshine on 2006-11-14
> **mips said:**
> And the rest of the info ?

Search here for "8139" so long.

I have searched for 8139 and read all posts nearly but it is no use.I am sending you all the outputs of the commands you have given.Below in a text file...

I will be thankful if you help me...
Thanks...

---

### Post by mips on 2006-11-14
I'm going to paste your info here as it is easier to see than opening a text file all the time for interested parties.

**lpsci -v output**
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 3084
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 3000 [size=256]
        Memory at e0205800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2


02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 12f6
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e0204000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3084
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e0205000 (32-bit, non-prefetchable) [size=2K]
        Memory at e0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
```


**ifconfig -a output**
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:5D:30:A6  
          inet addr:10.10.12.211  Bcast:10.10.15.255  Mask:255.255.240.0
          inet6 addr: fe80::2c0:9fff:fe5d:30a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:412434 (402.7 KiB)  TX bytes:468 (468.0 b)
          Interrupt:10 Base address:0x4800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:7F:6F:6A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 Memory:e0204000-e0204fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```



**route -n output**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.0.0       0.0.0.0         255.255.240.0   U     0      0        0 eth0
```


**cat /etc/resolv.conf output**
```
nameserver 193.140.248.5
nameserver 193.140.248.10
```


> cat /etc/network/interface output

cat: /etc/network/interface: No such file or directory

Oops my bad, that should read **cat /etc/network/interfaces**

If you looked in the folder you would have seen the file.

---

### Post by mips on 2006-11-14
You have no default gateway specified:

Try this command from the termninal:
```
sudo route add default gw 10.10.15.255 dev eth0
```

Check if you can now access the net. if you can reboot and see what happens, i suspect on a reboot it will not longer work. 

If this is the case then edit your /etc/network/interfaces file and add the following line after the gateway statement:
```
up route add default gw 10.10.15.255 dev eth0
```

---

### Post by lazyart on 2006-11-14
gksudo gedit /etc/network/interfaces

change the info for your adapter to read:
```
auto eth0
iface eth0 inet static
address 10.10.12.211
netmask 255.255.240.0
gateway 10.10.15.255
```

That should fix it.

---

### Post by mips on 2006-11-14
> **lazyart said:**
> gksudo gedit /etc/network/interfaces

change the info for your adapter to read:


How is that any different from what he currently has configured ???

---

### Post by eternalsunshine on 2006-11-15
It didn't work....
Network is unreachable it says when i have done everything you said
What can i do more???

---

### Post by eternalsunshine on 2006-11-15
Now i am on the internet bu via dhcp client on the internet cafe. :D

I cant understand why i cant go on the internet with static ip.

Please help i am going crazy, i wanna use open source but i cant :D

---

