---
title: "setting up internet in a lan network"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by kuzba on 2007-11-23
im in a co-housing where 12 houses are hooked up to one server via ethernet.

anyway i need to know how  to get the net working on ubuntu 7.10.

i was told that it would automatically detect it. but it didnt. i also went into the network settings and put in the ip subnet and gateway. 

but it sill didnt work.

what do i need to do?

thanks

---

### Post by Mithrilhall on 2007-11-24
What is the output of a...

```

ifconfig

```

---

### Post by kuzba on 2007-11-24
you mean ipconfig?

i cant copy and paste it. but it gives me the 3 things. ip address
subnet mask
gateway ip

---

### Post by Mithrilhall on 2007-11-24
No ipconfig in Linux..it's ifconfig.

Open a terminal and type 'ifconfig' and past the output.

---

### Post by kuzba on 2007-11-24
ill restart and have a look.

---

### Post by kuzba on 2007-11-24
i did it and it came up with lots of stuff. but how do i get the information to you?

im dual booting it. and i tried saving it to the hard drive but that didnt work

---

### Post by Mithrilhall on 2007-11-24
Ok..this is what I would try.

1. From the command line, ping 127.0.0.1 - this should tell you if your NIC is working.
2. Ping your ip address (192.x.x.x or whatever it is).
3. Ping your gateway; something like 192.168.1.1

Post back how each step goes.

---

### Post by kuzba on 2007-11-24
eth0      Link encap:Ethernet  HWaddr 00:16:E6:6A:D5:1C  
          inet6 addr: fe80::216:e6ff:fe6a:d51c/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:141 (141.0 b)  TX bytes:3784 (3.6 KB) 
          Interrupt:20 

eth0:avah Link encap:Ethernet  HWaddr 00:16:E6:6A:D5:1C  
          inet addr:169.254.7.1  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

---

### Post by kuzba on 2007-11-24
thats from the ifconfig. ill check the rest now.

its so annoying. i have to keep restarting and logging into ubuntu lol

---

### Post by Mithrilhall on 2007-11-24
From the terminal try

```

dhclient eth0

```

---

### Post by kuzba on 2007-11-24
the gateway ip said host unreachable or something when i tried to ping it

---

### Post by kuzba on 2007-11-24
i havent installed my network drivers yet. that might be a good idea hahah. 

but how do i install. i have an archive like a .zip but different. i dont know what tio do with it

---

### Post by Mithrilhall on 2007-11-24
What kind of network card is it?

For the archive just right click it and you should see something like extract or something?

---

### Post by kuzba on 2007-11-24
Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller

but what do i do after i have extracted it. i open the folder and there are like 4 different folders with.... i dont know what... in them.

---

### Post by Mithrilhall on 2007-11-25
Is there a ReadMe file in there or something?

Usually you do something like this from a terminal but the readme should have the information you need.

```

./configure
make
make install

```

---

