---
title: "Internet not working"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by Valerys on 2008-05-22
Today I installed Ubuntu 8.04. Internet is not working. The Network is being seen by the os but it doesn't get the things such as IP, DNS etc. If this helps, my network adapter is realtek, integrated on ECS Nforce3-A939 and I guess my internet is DHCP (it comes from the same cable as the tv one).
Also, I want to know if there would be any problem installing the latest driver from Ati website or there are better onea (i have x1650 pro).
Sorry if this was discussed before but i couldn't find anything with the keywords i have tried. :confused:

---

### Post by Peter09 on 2008-05-22
type the following and paste the output into the thread.

```
ifconfig
```

PC

---

### Post by Valerys on 2008-05-22
This is it:

eth0      Link encap:Ethernet  HWaddr 00:14:2a:5e:73:94  
          inet6 addr: fe80::214:2aff:fe5e:7394/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2114 (2.0 KB)  TX bytes:5084 (4.9 KB)
          Interrupt:23 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:14:2a:5e:73:94  
          inet addr:169.254.6.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39692 (38.7 KB)  TX bytes:39692 (38.7 KB)









I tried the *.run file from ati website with the video drivers but after decompressing it tells my that I have to be a superuser. What should I do?

---

### Post by Peter09 on 2008-05-22
To issue a command as super user you put sudo infront of it. Should be ok for code from a known and reputable source.

I suspect you have no gateways and dns set up. Double click on the network icon in your top panel (two screens) and the configure. You will need to know the ip addresses of your gateway (router). If its a reasonable system it may do the DNS for you.

PC

---

### Post by Valerys on 2008-05-22
In Windows XP my network is working normally. Should I use the IP and DNS from there?
I'm new to Linux and I don't know how to put sudo in front of the command since it runs automatically. :confused:

---

### Post by Peter09 on 2008-05-22
Yes, they will be the same machines.

You need to open a terminal Applications->Accesories->terminal

if you wanted to list a directory you would type

ls

to list it as super user you would type
sudo ls

PC

---

### Post by Valerys on 2008-05-22
I did it finally with sudo and then drag and drop of the file.
My problem stay still: my internet doesn't want to work anyway I try, I have used both DHCP and manual configuration of the IP, Subnet and gateway. I have modified them under connections --> properties. Should I make changes somewhere else too?

---

### Post by Peter09 on 2008-05-22
in a terminal do
```
sudo /etc/inet.d/network restart
```
see if that gets it going.

PC

---

### Post by Valerys on 2008-05-22
No, it doesn't. It says that it's an invalid command :(

---

### Post by Peter09 on 2008-05-22
whoops - should be 

```
sudo /etc/init.d/networking restart
```

PC

---

### Post by Valerys on 2008-05-22
Still didn't resolved my problem.
I remember that it worked fine under VMWare through bridged windows network. Maybe I should install it again in VMWare and see what was the configuration :lolflag:

---

### Post by Peter09 on 2008-05-22
The ifconfig output suggest an IP of
169.254.6.51

is this what you would expect?

PC

---

### Post by Valerys on 2008-05-22
Actually, my real IP is 89.37.213.66 and the Gateway 89.37.215.254.
PS: It's not dynamic.

---

