---
title: "Avahi-daemon missing from WiFi"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by king_arthur on 2007-04-25
Hi everybody,
as for subject: I have successfully installed Feisty Fawn (best release ever!) and  managed also to go on-line WiFi.

Everything works great but I am missing avahi support on my WiFi card.

As a matter of fact, the **ifconfig** command shows the following settings:
```
arthur@ubuntu-hp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:23:9D:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:01:03:05:D6:2E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x4800 

eth0:avah Link encap:Ethernet  HWaddr 00:04:76:23:9D:43  
          inet addr:169.254.5.29  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xa000 

eth1:avah Link encap:Ethernet  HWaddr 00:01:03:05:D6:2E  
          inet addr:169.254.4.85  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7754463 (7.3 MiB)  TX bytes:7754463 (7.3 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:24:3F:7F  
          inet addr:10.0.0.9  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20e:2eff:fe24:3f7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10012 errors:0 dropped:5 overruns:0 frame:0
          TX packets:9911 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6745871 (6.4 MiB)  TX bytes:1806720 (1.7 MiB)
          Interrupt:5 Memory:d087e400-d087e500 

```As you can guess from above output, I have 3 cards installed, only WiFi is connected and in use.
Ironically, wlan0 is the only interface that doesn't appear to be supported by the avahi-daemon.

Any idea as how-to configure /etc/avahi/avahi-daemon.conf in order to achieve what I want? :)


/P

---

### Post by spd106 on 2007-04-26
This isn't irony, it's supposed to work this way. Avahi-autoip will only step in and get an IP address if dhclient doesn't find an DHCP server and you haven't set a static address.

Don't worry though, you will still be able to use the benefits of the avahi-daemon as this is separate from avahi-autoip.

The easiest way to test avahi is to install the service-discovery-applet and/or avahi-utils.

---

### Post by king_arthur on 2007-04-26
> **spd106 said:**
> This isn't irony, it's supposed to work this way. Avahi-autoip will only step in and get an IP address if dhclient doesn't find an DHCP server and you haven't set a static address.

Don't worry though, you will still be able to use the benefits of the avahi-daemon as this is separate from avahi-autoip.

The easiest way to test avahi is to install the service-discovery-applet and/or avahi-utils.

Thanks for your reply spd106.

Not so sure what to think at this stage as from the network control panel, I can choose among DHCP, static or Avahi connection, for my two eth cards.
That does not appear to be the case for the WiFi nic, as I am given the choice only between DHCP or static and, as a matter of fact, no support is shown with **ifconfig**.

Am I missing something here?

/P

---

### Post by spd106 on 2007-04-26
I'm not quite sure that I follow, what do you want from Avahi?

You have previously stated that you have a connection through the wlan0 interface, isn't this what you want?

If you want to learn more about Avahi then have a read through the developer's website at [http://avahi.org/](http://avahi.org/), it might be a little confusing if you are not familiar with networking concepts. 

The best way to understand it is to see it in action and the simplest way would be through DAAP music sharing. Rhythmbox will allow you to share your music with others as long as they see DAAP shares. So this is other Ubuntu users as well as Apple Mac users and Windows users that have Bonjour for Windows and iTunes installed.

---

