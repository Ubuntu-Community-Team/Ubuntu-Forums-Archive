---
title: "static ip trouble in feisty"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by jamesford on 2007-05-20
im running feisty amd64 and i cant get static ip to work between my pc and wired router, which is a thompson speedtouch 516i.
it worked just fine in edgy but in feisty i get no connection between the router and pc whatsoever and i have to use dhcp

i dont know what more info i could post, but if anyone knows anything lemme know

---

### Post by Kobalt on 2007-05-20
Do you use Network-Manager to connect to the internet ?

---

### Post by kh4nh on 2007-05-20
> **jamesford said:**
> 
i dont know what more info i could post, but if anyone knows anything lemme know

could you post the content of /etc/network/interface and /etc/resolv.conf

have you tried different ip addresses or just one.

Did you /etc/init.d/networking restart

---

### Post by dustigroove on 2007-05-20
[FONT=Arial][SIZE=2][COLOR=Black]Click on the Network Manager icon, choose Manual Configuration, enter your password if prompted. When the Network Settings widow comes up, locate and right-click on the wired connection that you are using and select Properties. Ensure that your desired static IP settings are entered and that there is not a check in the box for Enable Roaming Mode.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by jamesford on 2007-05-20
kobalt:yes

dustigroove:thats how i do it

kh4nh: yes tried various ips, did /etc/init.d/networking restart
/etc/network/interface is empty...
resolv.conf:
search lan
nameserver 10.0.0.1
(when i try to add additional nameservers in the network thingy they just disappear)
my router is 10.0.0.1
--
only works with dhcp :(

---

### Post by kh4nh on 2007-05-20
> **jamesford said:**
> kobalt:yes

dustigroove:thats how i do it

kh4nh: yes tried various ips, did /etc/init.d/networking restart
/etc/network/interface is empty...
resolv.conf:
search lan
nameserver 10.0.0.1

my router is 10.0.0.1
--
only works with dhcp :(

Could you post the output of:

sudo ifconfig -a

Your /etc/network/interfaces should have this:

auto eth0
iface eth0 inet static
        address 10.0.0.8
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        getway 10.0.0.1

---

### Post by jamesford on 2007-05-20
kh4nh
thansk ill try that when i have some time later
is the "address 10.0.0.8" my computers ip that i can change to anything i want?
and by getway i presume u mean gateway?

how come this isnt added by default? ive done 2 fresh reinstalls trying to get this fixed. is the feisty network manager a bit broken?


```
sudo ifconfig -a
Password:
eth0      Link encap:Ethernet  HWaddr 00:01:29:D2:8E:96  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9474055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8831940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4631156568 (4.3 GiB)  TX bytes:8757536624 (8.1 GiB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40500 (39.5 KiB)  TX bytes:40500 (39.5 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.130.1  Bcast:172.16.130.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.205.1  Bcast:192.168.205.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by kh4nh on 2007-05-20
> **jamesford said:**
> kh4nh
thansk ill try that when i have some time later
is the "address 10.0.0.8" my computers ip that i can change to anything i want?
and by getway i presume u mean gateway?

how come this isnt added by default? ive done 2 fresh reinstalls trying to get this fixed. is the feisty network manager a bit broken?

That's right, you can change 8 in 10.0.0.8 to whatever you want except 10.0.0.1 and 10.0.0.255 which are reserved for gateway and broadcast addresses. It's the gateway, sorry for the misspelling.

By default, Feisty uses dhcp and your /etc/network/**interfaces** should have
```

auto eth0
iface eth0 inet **dhcp**

```

I was a little surprised when you said /etc/network/interfaces (there is a **s** at the end) is empty.

After modifying your /etc/network/interfaces, do a /etc/init.d/networking restart or restart your system

---

### Post by dustigroove on 2007-05-20
[FONT=Arial][SIZE=2][COLOR=Black]**EDIT:**   I was just replying with the same suggestion as kh4nh.

By default when using Network Manager there will be no manual entries in your /etc/network/interfaces file unless you manually enter them directly into the file, or if you select Manual Configuration through the Network Manager applet.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by jamesford on 2007-05-20
oops its interfaceS, sorry my fault
its not empty

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet dhcp

auto eth0
```

i will try all your suggestions later, cant now as im ripping a stream and i dont want to disconnect
thanks for help :)

---

### Post by dustigroove on 2007-05-20
[FONT=Arial][SIZE=2][COLOR=Black]Yes, there is your culprit:```
iface eth0 inet dhcp
```Adding kh4nh's changes should give you your desired configuration.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by jamesford on 2007-05-20
thanks :)

---

### Post by kh4nh on 2007-05-20
That all makes sense now. Modify to make

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet dhcp

auto eth0
```

look like this

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet static
         address 10.0.0.#
         netmask 255.255.255.0
         network 10.0.0.0
         broadcast 10.0.0.255
         gateway 10.0.0.1


auto eth0
```

Good luck

---

### Post by jamesford on 2007-05-20
hello guys
im pleased to report everything is up and running and working as it should be :D

thanks a lot, its greatly appreciated

---

