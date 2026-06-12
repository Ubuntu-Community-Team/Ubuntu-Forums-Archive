---
title: "[SOLVED] WPA -&amp;gt; Kernel Panic"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by Ber P on 2008-01-18
I've been reading lots of threads about WPA troubles, but not been able to find a solution to my problem.

I've a Netgear PCI wireless network card. It is working without any problems when not using WPA or WEP.
I would really like to add some encryption, but my problem is that I can't get WEP to work, and enabling WPA results in kernel panic!

Is there any solution to this problem without turning to ndiswrapper (I would prefer not to)? 

I can't remeber the name of the netgear card, but 
```
lspci -nn | grep Network
``` 
returns
```
00:0a.0 Network controller [0280]: Texas Instruments ACX 111 
54Mbps Wireless Interface [104c:9066]

```

I'm guessing that ACX 111 is the chip set??!

---

### Post by kevdog on 2008-01-18
can you post lshw -C network so we can discover the driver?  I think the user named RustyBronco -- can send him a personal message -- has the same chipset as you.  He was successful at getting his card up and running.

---

### Post by Ber P on 2008-01-19
```
:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wlan0
       version: 00
       serial: 00:0f:b5:43:69:34
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=acx_pci** ip=192.168.1.3 latency=32 module=acx multicast=yes wireless=IEEE 802.11b+/g+

```

Thanks for the hint about RustyBronco. I'll try and contact him if I this thread doesn't help me

---

### Post by kevdog on 2008-01-19
can you also post

iwlist scan

Do you have the wpa_supplicant package installed?

---

### Post by Ber P on 2008-01-19
```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:64
                    ESSID:"Saturn"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/100  Signal level=22/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

I have wpa_supplicant installed, but I'm not sure what i does? Can I verify that it is working? (I've been reading some threads where they talk about directories and files I can't locate)

---

### Post by rustybronco on 2008-01-21
It worked out of the box using wep. [http://ubuntuhcl.org/pub/reviews.php?product_id=408](http://ubuntuhcl.org/pub/reviews.php?product_id=408)
I can try it again in 7.10 if you would like me to see what driver it uses, iirc in 7.04 it used acx_111? for the driver but I can't remember about 7.10 .

---

### Post by Ber P on 2008-01-21
I got WEP to work. Turned out to be a setting in the router that was wrong. That must do for now.

Thankyou for your help!

---

