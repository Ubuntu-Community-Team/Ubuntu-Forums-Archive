---
title: "Can't find any wireless connection"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by Toost on 2008-10-01
I'm quite new to Ubuntu, i tried to install my atheros 5007eg in hardy with no succes.

Since a couple days i'm using intrepid alpha 6, with succes driver installed.
But still can't find any wireless aps now.

iwconfig shows:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

And if config shows me:

eth0      Link encap:Ethernet  HWaddr 00:1d:60:9a:16:1d  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe9a:161d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3301 errors:0 dropped:0 overruns:0 carrier:11
          collisions:0 txqueuelen:1000 
          RX bytes:3516931 (3.5 MB)  TX bytes:0 (0.0 B)
          Memory:feac0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:161940 (161.9 KB)  TX bytes:161940 (161.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:3e:e9:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-3E-E9-27-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Can someone please help, trying for hours now

---

### Post by Toost on 2008-10-06
Downloaded intrepid beta version.....

I updatet everything and can  now see wireless aps.
but still cant connect to any of them...


can someone help....

trying for weeks now

---

### Post by Bucky Ball on 2008-10-06
System->Admin->Network and unlock, click your wireless and then properties. In there, make sure you have configuration set to 'Automatic DHCP' and 'enable roaming' is unticked for the moment. Fill in the correct ESSID and WEP or WPA details for your router and see how that goes. Your details show you are not being served an address by anything to transmit or receive on. :)

---

### Post by Toost on 2008-10-06
I cant find the function you meant in intrepid, but i found some other function and manually filled it in. but still nothing stays asking me for the security key

---

### Post by Toost on 2008-10-06
Tried connecting without a key on my wireless ap. 
still cant connect

iwconfig gives me:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Pulse"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Iwlist gives me no scan results

---

### Post by Toost on 2008-10-06
lshw shows me my interface is wmaster0 and all the other commands and apps showing me wlan0

---

### Post by Bucky Ball on 2008-10-07
Yes, because wlan0 is what you use to connect so that is right. You will find if you try changing wlan0 it won't let you as the device doesn't exist (an alias I think but you can research this).

```
Access Point: Not-Associated
```Not finding your router as your machine hasn't been assigned address and/or is not broadcasting one.



The command you need to use is:

```
sudo iwlist scanning
```Post the result of that. If you input 'iwlist', you get a list of options you can use with iwlist. If you input 'iwlist --help' you will get the instructions for using them.

If you don't fill in the details of your access point somewhere though, you are not going to be able to connect to your router. Intrepid is not that different so I would look for where you set up your network if it not where I suggested. :)

---

### Post by Toost on 2008-10-07
Don't know what you mean with changing wlan0 

but this is what iwlist shows me:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by Toost on 2008-10-13
installed a usb wireless adapter. works without any problems... still cant get my onboard wireless working wright

---

