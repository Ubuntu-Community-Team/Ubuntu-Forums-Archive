---
title: "Connected but no internet"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Frenske on 2009-12-28
Help, according the network manager I'm connected but when opening firefox it is saying I'm not connected.
Problems started when I connected to a new network in Windows 7 (dual boot). In Windows 7 it is working fine.

---

### Post by spiky001 on 2009-12-28
i had the same problem are yu connected by cable or wireless?

---

### Post by proxess on 2009-12-28
The above, plus, is there a proxy? If you're on wireless, have you tried changing the password encryption? How about replacing NetworkManager with WICD?

---

### Post by mbzn on 2009-12-28
Had this problem with a e220 device, my solution was to put firefox in offline mode. Don't know why but it worked. Have you tried your other apps ie. links, evolution, do they connect?

---

### Post by brad_c6 on 2009-12-28
Can you give us more information.
Such as...

What are you connecting to the internet with? (Wireless/Ethernet{wired})
What is your network configured to? (Using a wireless router?)
Whats your ip? (Via Applications>Accessories>Terminal Then type "sudo /sbin/ifconfig")

---

### Post by Frenske on 2009-12-28
It is a wireless network connecting to the network router of my parents using the network card in my MSI GT627. It was working fine in Ubuntu until I went in dual boot to Windows 7 and connected to the wireless network in windows 7. Even my mobile phone connects nicely to the router.

Thunderbird as well the update-manager don't connect either to the wwww.

---

### Post by Frenske on 2009-12-28
sudo /sbin/ifconfig gives me:

```
eth0      Link encap:Ethernet  HWaddr 00:24:21:62:6b:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6531 (6.5 KB)  TX bytes:6531 (6.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:ea:31:84  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:feea:3184/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4336 (4.3 KB)  TX bytes:7183 (7.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-EA-31-84-65-61-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by mike555 on 2009-12-28
Sometimes you need to let the router re-discover the operating system ........... so shutting down for a couple of minutes ,then booting into a different operating system should work .......at least it does on mine ......

---

### Post by Frenske on 2009-12-28
> **mike555 said:**
> Sometimes you need to let the router re-discover the operating system ........... so shutting down for a couple of minutes ,then booting into a different operating system should work .......at least it does on mine ......

I switch the router off and on again and everything is fine now, but at least I was a place (my parents) were I can do it but will not always be in that position. If somebody knows a viable alternative of de-plug and plug-in I would like to hear it.

---

