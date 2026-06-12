---
title: "Unable to use connect to the internet"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by Visti on 2007-01-14
Hi, I'm a new user. New as in: I just installed Ubuntu (Edgy) and I can't connect to the internet. In XP, it's all set to automatically acquire IP adresses and such, but it just doesn't work in Ubuntu.

I tried fiddling a bit with it according to some stuff I read on the net, so maybe I've screwed it all up, but please try to help me anyhow.

Here's some various output:

ifconfig &#8211; a

eth0      Link encap:Ethernet  HWaddr 00:13:8F:7E:E4:94  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0x6000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lspci|grep controller:
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

cat /etc/network/interfaces
auto lo
iface lo inet loopback


[I]iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.1[/I] (I added this because I tried replacing what was there with on that looked like the other ones except for eth0 and now I don't know what was actually there - but it looked like this - I just don't know the actual IPs and such)

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



ANY help would be most appreciated.. I don't really have much use for Ubuntu if the internet isn't working on it.

---

### Post by vitalis on 2007-01-14
Hello,
I have exaclty the same problems - it does not work for me as well. Have no ideas

---

### Post by Floppyjoe on 2007-01-14
How are you connecting to the internet? Are you connected through a modem or a router or a combo product?Your configuration file shows you are trying to get a static IP address whereas your post says it aquires them automatically which would suggest DHCP.

---

### Post by Visti on 2007-01-14
I am trying to use DHCP through my cable modem, that's why I added that note next to the static information - That's not the real info, that's just something stock from the Ubuntu documentation, because I accidentally deleted what was actually there..

---

### Post by Floppyjoe on 2007-01-14
You should try something like this:
```
sudo gedit /etc/network/interfaces
```

Then use this in the file:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Then make sure the interface is activated in System/Administration/Networking.
Then restart.

This may not work. You might need to run something like pppoeconf from the terminal depending on how your modem connects to the internet.

---

