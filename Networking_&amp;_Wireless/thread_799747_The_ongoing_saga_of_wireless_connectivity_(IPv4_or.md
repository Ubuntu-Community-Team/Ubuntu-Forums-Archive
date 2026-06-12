---
title: "The ongoing saga of wireless connectivity (IPv4 or IPv6)"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by usernamed on 2008-05-19
Hi All,

I'm getting closer to wireless on Ubuntu (I hope) but I'm not quite there.

What's happening at the moment is that I have an rt73 driver from the lovely people at [SerialMonkey]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page") and I have a device wlan1 that is clearly present because ifconfig picks it up without any prompting and the little green light on the USB key flashes in a friendly welcoming manner, as if wireless connectivity is just around the corner (the little tease)

However, I'm not quite there.  Ifconfig gives me:

```
wlan1     Link encap:Ethernet  HWaddr 00:1e:e5:2a:a5:e2  
          inet6 addr: fe80::21e:e5ff:fe2a:a5e2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:298818 (291.8 KB)  TX bytes:493020 (481.4 KB)

wlan1:avahi Link encap:Ethernet  HWaddr 00:1e:e5:2a:a5:e2  
          inet addr:169.254.9.101  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```

The first thing I notice is that it appears to have an IPv6 IP address when my setup is IPv4 everywhere else.  Is this an issue?  I'd have thought it was, but I'm not knowledgeable enough to tell for sure.

My attempts at manually setting it to IPv4 have failed miserably and even in /etc/network/interfaces (key removed)...

```
iface wlan1 **inet** dhcp
wpa-psk <mykey>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid rtr1
auto wlan1

```

...you can see that the interface is set to inet not inet6.

Given that this is hardware I bought specifically because it had a ralink chipset, rather than the hopelessly unsupported Realtek card I had previously, I'm keen to get this working, and preferably without using ndiswrapper (because there are linux drivers available and because I'm running 64-bit Ubuntu which seems to be less keen on working with ndiswrapper and Windows drivers generally)

If anyone can point me in the right direction, I'd greatly appreciate it.

---

### Post by chili555 on 2008-05-19
> IPv6 IP address when my setup is IPv4 everywhere else. Is this an issue?Nope.> inet addr:169.254.9.101This is what I cal 169.254.boo.hoo. Avahi sets a placeholder address when a valid IP address cannot be obtained from the router/access point/switch/modem/etc.

The little tease is concerned, I think, about your WPA settings versus those in the router. Please double check and here is a great tutorial: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I notice there is a nice big red warning regarding RTxx chipsets and a reference to this: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5)

---

### Post by usernamed on 2008-05-19
You beautiful ape!  (Ah, that will sound insulting once you change your profile picture)

I've disconnected my wired ethernet connection and am connected via the gift of wireless.

Thank you very much!

---

### Post by Gotit on 2008-11-15
I too am having problems with avahi.  When I run wireless in roaming mode all is well and I can connect and I only show wlan1.  
But, when I try to configure my wireless to connect directly to the network I want, I lose connection and ifconfig shows
```
wlan1:avahi Link encap:Ethernet  HWaddr 00:21:29:e5:db:b0
           inet addr:169.254.9.255  Bcast:169.254.255.255  Mask:255.255.0.0
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
```
Chili555, I'm not sure what to do from this point from your comment:
> This is what I cal 169.254.boo.hoo. Avahi sets a placeholder address when a valid IP address cannot be obtained from the router/access point/switch/modem/etc.
can you give a little more assist?  Thanks!

---

