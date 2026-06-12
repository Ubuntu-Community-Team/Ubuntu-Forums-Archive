---
title: "Routing query - how to use both eth0 and wlan0?"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by paulhollow on 2006-11-29
Hello... 

I am hoping that someone can show me how to use both my wired ethernet connection and my wireless card under Edgy...  that is, when one is not connected i'd like the other one to take over the connection to the Internet.

At present, the wired internet (eth0) is working perfectly, the wireless (wlan0) is also configured (it picks up DHCP info ok..) but does not connect to the internet.

I can ping my gateway (192.168.0.1) ok from the wired connection, but when i unplug the cable and try to ping again, it says "HOST UNREACHABLE".

However, i can force a ping on wlan0 (with ping -I wlan0 192.168.0.1) and that works fine...

How do i get wlan0 to take over when eth0 is not available?  I'd like eth0 to be the default connection, if available.

My ifconfig output is:

```
paulh@paulh-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:A5:B4:0E:EE  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:feb4:eee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2545278 (2.4 MiB)  TX bytes:488832 (477.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2235 (2.1 KiB)  TX bytes:2235 (2.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:59:7B:95  
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe59:7b95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2060 (2.0 KiB)  TX bytes:2886 (2.8 KiB)
          Interrupt:11 Memory:36000000-36002000 

```

iwconfig output is:

```
paulh@paulh-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Skydive"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:65:92:06   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-85 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

This sounds like some kind of routing problem to me, but i don't know enough to be sure!  Any help would be much appreciated!  Thanks!

---

### Post by trubblemaker on 2006-11-29
check for a wireless manager in synaptic, I've heard that there is software that will manage your connections for you.  if you want to switch manually you need to simply bring down the interface when you unplug a connection, otherwise your computer doesn't know that it's been unplugged and will still try do use it.

```
sudo ifconfig <wired-interface> down
```
will tell the computer your wired interface is no longer in use, and it will switchover to the wired connection.  to bring it back up with the same Ip use
```
sudo ifconfig <wired-interface> up
```

to bring it up with a new ip use
```
 sudo ifup <wired-interface> 
``` and it will switch back to using the wired connection.

---

### Post by paulhollow on 2006-11-29
Thanks for the prompt reply and your help, i'll give it a go!

Cheers!

---

### Post by MasterOfDisaster on 2006-11-29
In response to trubblemaker, I beleive that you mean Network Manager.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

It makes dealing with multiple networks much easier, and defaults to eth0, so there you go.

It can be installed through Synaptic, and I beleive that you need to comment out the devices that you wish to use in your /etc/network/interfaces file, or else Network Manager will not recognize them.

Anyways, good luck.

---

### Post by paulhollow on 2006-11-30
Ah!  Thanks for that... i was wondering why network manager didn't seem to be doing anything...

One question... how do i inform NetworkManager that eth0 is a static IP address?  It keeps trying to get a dynamic address from eth0 and coming up with all sorts of crazy settings.  The wireless, however, is a dynamically assigned interface (wlan0).

I have read the man pages for nm-applet, NetworkManager and NetworkManager daemon and have looked at the web site for it, but none of them give any decent usage/configuration information.

Thanks!

---

