---
title: "Can see access point but not connect. Thinks it is using IPv6 tho I removed it"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by Matt Heath on 2007-05-18
I have a Belkin F5D7050 ver 3000 usb wireless card and installed the drivers as in 
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)).

My computer now knows what wireless networks there are and "network settings" has rausb0 active and pointed at the right access point. 

The network in my flat is set up like the ones in cafés. I am supposed to connect to the wireless access point( which has no encryption)  open a web browser and be redirected to a log in needing a password to be allowed onto the internet. 

Opening Firefox or Konquerer just gives "page unavailable"

If I copy the IP address that an XP laptop connected to the same network has  an try to ping it from the Ubuntu computer I get "Network is unreachable".

If i type "route" in the terminal I get 
```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

I followed the advice on this [http://ubuntuforums.org/showthread.php?t=443209&page=2](http://ubuntuforums.org/showthread.php?t=443209&page=2) thread to remove IPv6 according to these [http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6) instuctions and to change something about window scaling I didn't really understand.

iwconfig gives:
```

lo         no wireless extensions
rausb0 RT73 WLAN  ESSID:""
            Mode:Auto  Frequency=2.412 GHz  Bit Rate=54 Mb/s
            RTS thr:off   Fragment thr:off
            Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
eth0     no wireless extensions
sit0       no wireless extensions
```
but "Network settings, Properties" has the ESSID in the form"DEVELOPMENT BUILDINGNUMBER CORRIDOR FLAT" which is right.

If I open "Network tools" go to the "devices" tab and ask about raub0 it says "IPv6" as the only Protocol listed which seems very wrong.


Any help would be appreciated.

---

### Post by Matt Heath on 2007-05-20
I got some help here [http://www.phdcomics.com/proceedings/viewtopic.php?t=3007&start=15](http://www.phdcomics.com/proceedings/viewtopic.php?t=3007&start=15) and it seems ok atm

---

