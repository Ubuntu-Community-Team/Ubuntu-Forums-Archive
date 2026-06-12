---
title: "Wireless Connected?!?"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by Bofur on 2007-07-05
I just finished installing my drivers with ndiswrapper and they worked great, I connected to the internet just fine, But right after I restarted I can't connect and I don't know why. My wireless is showing up and it says I'm sending and recieving packets, I'm also getting a signal strength at 80% while in roaming mode. Does anyone know why it's doing this but won't connect to the internet? 

Heres some additional info:
```
justin@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11b ESSID:"Wireless"
Mode:Managed Frequency:2.462 GHz Access Point: 00:09:5B:35:5B:24
Bit Rate=11 Mb/s Tx-Power:32 dBm
RTS thr=2347 B Fragment thr=2346 B
Power Managementff
Link Quality:71/100 Signal level:-50 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:5B:29:E0  
          inet addr:10.75.0.6  Bcast:10.75.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe5b:29e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:267886 (261.6 KiB)  TX bytes:38642 (37.7 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CF:B3:76:72  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1018 (1018.0 b)  TX bytes:168 (168.0 b)
          Interrupt:17 Memory:ecffc000-ed000000
```

Then this is what it says when I sudo gedit /etc/network/interfaces:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0
```

Thanks!

I'd also like to mention after the restart when I click the icon to show available connections, it only shows loopback and eth0, I have to type in wlan0 for it to connect.

---

### Post by kevinlyfellow on 2007-07-05
> **Bofur said:**
> 
Then this is what it says when I sudo gedit /etc/network/interfaces:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0
```

Network manager doesn't play nicely with /etc/network/interfaces.  Try to comment everything but the loopback out.

```

auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto eth0

```

---

### Post by Bofur on 2007-07-05
That was everything in the interface document if thats what your asking?

---

### Post by kevinlyfellow on 2007-07-05
> **Bofur said:**
> That was everything in the interface document if thats what your asking?

:-?  I'm suggesting that you comment lines out of the file /etc/network/interfaces  It's almost everything in the config file, but not the loopback.  Network manager (what handles connecting to networks in feisty) works independently of the interfaces file, so when there is stuff in it, it can conflict with what network manager wants to do.

---

