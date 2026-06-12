---
title: "ath0 question"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by texas697 on 2006-11-14
I have d-link wireless pci card, it is working fine, but when i look at the "ifconfig" output it gives me ath0 and wifi0 status. is having both of these normal? Also, does 'auto' in the /etc/network/interfaces refer to automatic start up during boot? wifi0 has it, but ath0 does not, should i change this? thanks for any help.

ath0      Link encap:Ethernet  HWaddr 00:13:46:79:F8:17  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe79:f817/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1735620 (1.6 MiB)  TX bytes:286673 (279.9 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20858 (20.3 KiB)  TX bytes:20858 (20.3 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-79-F8-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31492 errors:0 dropped:0 overruns:0 frame:37020
          TX packets:4696 errors:98 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5073083 (4.8 MiB)  TX bytes:466000 (455.0 KiB)
          Interrupt:177 Memory:f8b40000-f8b50000

---

### Post by dannyboy79 on 2006-11-14
i am not sure what this means? notice that the wifi 1 doesn't have an ip so I don't believe that's the interface that is actually allowing you to be online, I would lean towards the ath0 interface. you could do a test, put a "#" in front of every line for the wifi 1 within your interfaces file and the reboot your machine, if everything works ok than I am guessing that ubuntu was just confussed and it doesn't need the wifi0 interface. that's all I can suggest. I use a laptop, and I have ath0, it's a pc card using a netgear wireless card that has the atheros chip. i am not sure what the auto option does, this is my interfaces file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface ath0 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid secret
        wireless-key1 can't tell ya, ha ha
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers secret
        wireless-key can't tell ya, ha ha

can't help ya more than that.

---

### Post by texas697 on 2006-11-14
thanks for the advice, i will give it a try.

---

