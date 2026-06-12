---
title: "[SOLVED] Wireless problems with WICD"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by dean20007 on 2007-11-12
Hi Folks

After installing Gutsy and getting the all important whizz bang desktop effects working, I noticed my wireless connection kept dropping. I searched about and people recommended using wicd. So I uninstalled network-manager and installed wicd. 

On running wicd, it finds my network (albeit it says the signal is only 1 bar!) but when it teys to connect is bombs out while trying to obtain an IP. 

The only way I can get my wireless working is to run this script I chucked together based on someones howto. 

```
#!/bin/sh
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "essid"
sudo iwconfig wlan0 key my_key
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0
```


Incidentally, the output of iwconfig gives a strange wmaster0 which I have no idea what it is 

```
dean@dean-desktop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"zoom"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:38:47:29:DB   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

output from ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:11:5B:33:B0:3B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xe200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:176 (176.0 b)  TX bytes:176 (176.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:BF:CF:E9  
          inet addr:10.0.0.9  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:febf:cfe9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2267532 (2.1 MB)  TX bytes:373275 (364.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-BF-CF-E9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by dean20007 on 2007-11-13
Bump

---

### Post by wieman01 on 2007-11-13
What hardware have you got and what driver are you using?

---

### Post by dean20007 on 2007-11-13
Hi

I am using a USB belkin fd57050. It worked straight out of the box after a fresh install of Gutsy but I beleive the driver to be rt73.ko. What output can I give to confirm this? 

Thanks

---

### Post by wieman01 on 2007-11-13
Please post this:
> sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
> sudo lspci -nn | grep Network
> sudo lsusb -nn | grep Network

---

### Post by dean20007 on 2007-11-13
Output from the following
> 
sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=

> driver=sis900 


> sudo lspci -nn | grep Network

Nothing returns for this

> sudo lsusb -nn | grep Network

This returned unknown command so I used
>  sudo lsusb -v | grep Network

which returned this

>  iProduct                2 Belkin 54g USB Network Adapter

Hope this helps

---

### Post by wieman01 on 2007-11-14
Apparently it uses a FSD7050 chipset. 

If the connection keeps dropping, installing "ndiswrapper" might solve things for you. I cannot promise but it is worth the try. 

There is a Ralink tutorial in my signature. Take a look at it as installation should be quite the same for your device.

---

### Post by dean20007 on 2007-11-15
Marking this as solve because it appears to be usb problem

I get usb 4-1: device descriptor read/64, error -110 errrors. This has now affected my wireless usb keyboard.. grrrrr. 

This is for another forum so I just wanted to thank you for help

---

