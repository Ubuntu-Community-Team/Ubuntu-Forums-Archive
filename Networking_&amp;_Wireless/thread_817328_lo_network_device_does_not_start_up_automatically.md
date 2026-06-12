---
title: "lo network device does not start up automatically"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by supergenius23 on 2008-06-03
I noticed that my lo network device does not start up when I restart any more. This is my /etc/network file:

```
auto lo
iface lo inet loopback


iface eth0 inet static
	address 192.168.1.4
	netmask 255.255.255.0
	gateway 192.168.1.1

auto eth0

#Wireless
noauto ath0
allow-hotplug ath0

iface ath0 inet manual
wpa-driver madwifi
wpa-roam /etc/network/wpa_supplicant.conf

iface default inet dhcp

```

when i try to restart my interfaces with ```
sudo /etc/init.d/networking restart
``` i get this error:

```
 * Reconfiguring network interfaces...
/etc/network/interfaces:13: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:13: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

PLEASE HELP ME!!!

---

### Post by chili555 on 2008-06-03
Wow! That's a hairy *interfaces!* Let's try this:```
auto lo
iface lo inet loopback


iface eth0 inet static
	address 192.168.1.4
	netmask 255.255.255.0
	gateway 192.168.1.1

auto eth0

#Wireless
#auto ath0
iface ath0 inet dhcp
allow-hotplug ath0

#iface ath0 inet manual
wpa-driver madwifi
wpa-roam /etc/network/wpa_supplicant.conf

#iface default inet dhcp
```Restart networking and let's see if we are closer.

---

### Post by supergenius23 on 2008-06-03
thanks, but that didnt work.. now im gettin an error on line 18 

```
 * Reconfiguring network interfaces...
/etc/network/interfaces:18: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:18: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                     [fail]

```

---

### Post by issih on 2008-06-03
I'm only guessing here, but I'd say you want :

```
auto lo
iface lo inet loopback

iface eth0 inet static
	address 192.168.1.4
	netmask 255.255.255.0
	gateway 192.168.1.1

auto eth0

#Wireless

#auto ath0
allow-hotplug ath0

iface ath0 inet dhcp
        wpa-driver madwifi
        wpa-roam /etc/network/wpa_supplicant.conf


```


I don't think theres any such thing as noauto (just don't put auto in :)), which was the problem with your original, although I also doubt you wanted manual as the interface setup, but you will know better than us.

In the 2nd version, the allow hotplug line was within the interface definition...I don't think that's right.

Give it a whirl, and let us know how it goes

---

### Post by supergenius23 on 2008-06-03
Thanks a lot that worked :guitar: How do I thank post a thank you?

---

### Post by issih on 2008-06-04
Click the little medal in the bottom right of my post....I like getting thanked...makes me feel useful :)

Glad it worked for you.

---

### Post by supergenius23 on 2008-06-07
My wireless adapter does not load up when I reboot.. What can I change back so that I can get the interface to load at start-up?

---

### Post by Unix_Slayer on 2008-06-07
> **supergenius23 said:**
> My wireless adapter does not load up when I reboot.. What can I change back so that I can get the interface to load at start-up?

I use Ndiswrapper. You look like your using madwifi. My network interface is as follows:

```
auto lo
iface lo inet loopback

```


I load up wireless, and wired at the same time without a problem. But don't take my word for it.

Ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:30:b3:dd
          inet addr:192.168.0.202  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe60::32e:e6gg:feda:9386/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:19240 (18.7 KB)  TX bytes:8245 (8.0 KB)
          Base address:0x2000 Memory:e7200000-e7220000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12500 (12.2 KB)  TX bytes:12500 (12.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:da:93:86
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:feda:9386/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16650877 (15.8 MB)  TX bytes:2199158 (2.0 MB)
```

---

### Post by supergenius23 on 2008-06-07
Maybe this can help debug the problem

```
 * Reconfiguring network interfaces...                                           * Stopping NTP server ntpd
   ...done.
ath0: ERROR while getting interface flags: No such device
wpa_supplicant: wpa-roam can only be used with the "manual" inet METHOD
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.

```

---

### Post by issih on 2008-06-07
its possible you need to  add madwifi to /etc/modules so that the module is loaded at boot, but frankly I just don't know as I use ndiswrapper and have my interfaces configured by the network manager rather than statically in the interfaces file.

With that set up, I have to add ndiswrapper to /etc/modules to ensure the module is loaded.

Worth investigating anyway

---

### Post by Unix_Slayer on 2008-06-07
If you were using ndiswrapper, this post would be what your looking for ==>[http://ubuntuforums.org/showthread.php?t=821936]("http://ubuntuforums.org/showthread.php?t=821936")

---

### Post by supergenius23 on 2008-06-07
> its possible you need to add madwifi to /etc/modules so that the module is loaded at boot, but frankly I just don't know as I use ndiswrapper and have my interfaces configured by the network manager rather than statically in the interfaces file.

With that set up, I have to add ndiswrapper to /etc/modules to ensure the module is loaded.

Worth investigating anyway 

I understand where your going with your suggestion..  I was searching for a solution the other day and I came across the same suggestion. I will look into it. THANKS

---

### Post by supergenius23 on 2008-06-07
I finally got my wireless card to work again.. All I had to do was reinstall the drivers. I dont know why, but that worked. Thanks to everyone who posted suggestions.

---

### Post by Unix_Slayer on 2008-06-08
> **supergenius23 said:**
> I finally got my wireless card to work again.. All I had to do was reinstall the drivers. I dont know why, but that worked. Thanks to everyone who posted suggestions.

I knew it. The video, and wifi drivers go out with each new kernel. God knows what else. Congratz there sg23.

---

### Post by supergenius23 on 2008-06-08
> I knew it. The video, and wifi drivers go out with each new kernel. God knows what else. Congratz there sg23

That explains a lot because my vid card is also acting funny again! Thanks for the info!

---

