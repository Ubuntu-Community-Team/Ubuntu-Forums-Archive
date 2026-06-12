---
title: "[SOLVED] Problem with setting up static ip on new computer"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Go_Bucks on 2008-06-18
I am using Hardy on a new HP Slimline computer that I just got. I have successfully and easily set up static ip on my internal network on several other Hardy computers without a problem so total ignorance is not the issue. The details:

This computer has both wired and built-in wireless capabilities. I am using wired and have a number of different server packages installed, which is why I want a static ip. I am using an older Linksys WRT54G, so static ip setup from the router is not an option. Using either network manager or manually typing into /etc/network/interfaces to set up static ip on eth0 shuts off the wired connection immediately and sends it to wireless. Following up and doing the same with wlan0 (the wireless) shuts off my wireless and gives me no internet. There is another interface, wmaster0, that I think has to do with having both wired and wireless. This does not show up in network manager. Setting it up in /interfaces has no effect.

The ip I want is 192.168.1.15... I have tried that and several other ips to no avail. My ifconfig output is below. "ham0", by the way, is hamachi.

```
marcus@marcus-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:04:76:ea  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe04:76ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:218545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:236175236 (225.2 MB)  TX bytes:11901629 (11.3 MB)
          Interrupt:222 Base address:0x8000 

ham0      Link encap:Ethernet  HWaddr 00:ff:32:35:fd:bd  
          inet addr:5.6.153.218  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:103689 (101.2 KB)  TX bytes:106347 (103.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12321587 (11.7 MB)  TX bytes:12321587 (11.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:a0:b0:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81531 (79.6 KB)  TX bytes:42565 (41.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-A0-B0-0A-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by superprash2003 on 2008-06-19
didnt you try setting up static ip through system->administration->network

---

### Post by argail1980 on 2008-06-19
which one do you want to have the 1.15 IP? because wmaster0 already has it. 

idea number one: can there be a conflict when using two cards in the same network? I don't know much about that stuff, but how does your system know, via which card to send packages out?

idea number two:
have you, by mistake configured wmaster0 to have that IP and is that preventing ham0 from having it?

---

### Post by Go_Bucks on 2008-06-19
> **superprash2003 said:**
> didnt you try setting up static ip through system->administration->network

That was what I meant when I said I used "network manager".

---

### Post by Go_Bucks on 2008-06-19
> **argail1980 said:**
> which one do you want to have the 1.15 IP? because wmaster0 already has it.

That is because that was the last one I tried. I tried eth0, wlan0, and wmaster0 summarily. Wmaster0 seems to do nothing. 

> **argail1980 said:**
> idea number one: can there be a conflict when using two cards in the same network? I don't know much about that stuff, but how does your system know, via which card to send packages out?

That is what I am hoping someone can answer for me.

> **argail1980 said:**
> idea number two:
have you, by mistake configured wmaster0 to have that IP and is that preventing ham0 from having it?

No... see first answer. I have tried all individually, one at a time, etc. It doesn't matter. It doesn't work.

---

### Post by argail1980 on 2008-06-20
ok... now again for the slower of us:

you want to have eth0 on 192.168.1.15 instead of .103?
and wlan0?
what again is the hamachi-device?

---

### Post by Go_Bucks on 2008-06-20
> **argail1980 said:**
> ok... now again for the slower of us:

you want to have eth0 on 192.168.1.15 instead of .103?
and wlan0?
what again is the hamachi-device?

Yes... I want eth0, which is my wired connection, to be 192.168.1.15. wlan0 I don't need to use. This set up is no different from my HP Laptop. Like most laptops, it has both wired and wireless capabilities, and it also has a wmaster0 interface. Unlike my desktop, however, setting the wireless on my laptop to use a static ip works.

Hamachi is virtual private networking program. There are plenty of posts about it here in the forum.

---

### Post by nexist on 2008-06-21
I had a similar problem. I am using Server Edition, so I have no GUI. I added the lines to the /etc/network/interfaces file as in the [documentation]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html#ethernet"). Unfortunately, I did not realize that I needed to keep the 'auto eth0' line. Check if your interfaces file looks like below (with your ip et al). Mine works fine now.

# The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 10.11.93.2
netmask 255.255.255.0
gateway 10.11.93.1

---

### Post by cariboo on 2008-06-21
> # The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 10.11.93.2
netmask 255.255.255.0
gateway 10.11.93.1 

I'd add a broadcast address to the above. In your case it would look like ths:

```
braodcast 192.168.1.0
```

you would place the above in /etc/network/interfaces

Jim

---

### Post by Go_Bucks on 2008-06-21
> **nexist said:**
> I had a similar problem. I am using Server Edition, so I have no GUI. I added the lines to the /etc/network/interfaces file as in the [documentation]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html#ethernet"). Unfortunately, I did not realize that I needed to keep the 'auto eth0' line. Check if your interfaces file looks like below (with your ip et al). Mine works fine now.

# The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 10.11.93.2
netmask 255.255.255.0
gateway 10.11.93.1


The above worked, with one caveat (and its funny because I swear I already did this multiple times). When I reset eth0 to the above it again went to wireless. So I then added the same lines for wlan0 (without the auto part) and it then went to wired using the static ip.

Thanks a lot to everyone for their help.

---

