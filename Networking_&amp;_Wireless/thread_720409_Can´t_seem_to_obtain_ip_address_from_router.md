---
title: "Can´t seem to obtain ip address from router"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by Bino on 2008-03-10
I´ve been tampering with ubuntu now for quite some time but still I´m not able to get my wireless to work. I´ve tried manually connecting, wifi radar and now even wicd, all with the same result: no wireless.
I´ve had a look at the connecting status of wicd and it looks like I´m having trouble obtaining an ip address from the router. Does anyone have any idea what might be the problem and how to solve this?

---

### Post by ssj3strife on 2008-03-10
You seem convinced the router is working properly. Are you sure of that? Can other machines connect to it? Also, what wireless card are you using?

---

### Post by njparton on 2008-03-10
Is DHCP activated in the router?

Do you have mac address filtering turned on?

---

### Post by Bino on 2008-03-10
I have MAC filtering enabled but this is no issue when using Vista where wireless is working perfectly fine.
I presume this also answers the question about DHCP?

And my wireless card is Intel(R) PRO/Wireless 3945.

---

### Post by ssj3strife on 2008-03-10
What sort of encryption are you using with your router?

---

### Post by Bino on 2008-03-10
I have SSID disabled and encryption is WEP.

Also, I already enabled SSID, disabled WEP and MAC without luck.

---

### Post by ittiam on 2008-03-10
Did you try knetworkmanager?

---

### Post by njparton on 2008-03-10
Double check that DHCP is operating in the configuration settings and temporarily disable mac address filtering.

---

### Post by Bino on 2008-03-11
I had a look at the router settings. 
MAC filtering is disabled and the  DCHP server enabled.
Situation is still the same tho :(

---

### Post by Eiríkr on 2008-03-11
A couple requests:
[list][*]Post the results of [font=courier]ifconfig[/font]
[*]Post the results of [font=courier]iwconfig[/font]
[*]Post the results of [font=courier]cat /etc/network/interfaces[/font]
[*]Post your router brand / model name[/list]
And make sure the router settings are back wherever they need to be for Vista to automagically work.  Since Vista can get at it, it really doesn't sound like a router issue at this point.  

Cheers,

Eiríkr

---

### Post by ssj3strife on 2008-03-12
Can you connect to another router without a problem?

---

### Post by Bino on 2008-03-12
I haven´t tried connecting to another router, especially since I don´t have an extra one.

Here are the required outputs:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:13:A9:85:2D:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:19:D2:49:D2:0E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:11 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x4000 Memory:cc000000-cc000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"GobeynWifi"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:12:BF:35:D4:EA   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#iface eth0 inet dhcp
```

Router: Philips

---

### Post by Eiríkr on 2008-03-13
Okay, [font=courier]ifconfig[/font] and [font=courier]iwconfig[/font] don't show much of note aside from confirming that no network adapter (aside from the loopback) has any internet address assigned, and none show any bits received (RX) or transmitted (TX).  

Your [font=courier]/etc/network/interfaces[/font] file, however, shows us interestingly that only your loopback interface (a means for a computer to contact itself via the network) is set up for automated activation on boot -- all the others (and some your machine doesn't seem to have anyway :confused:) are commented out.  

Presuming you want your eth1 wireless network adapter to be activated on boot, edit your [font=courier]/etc/network/interfaces[/font] file to look something like this:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```
Now take all interfaces marked for automated activation offline, and then bring them up again:
```
sudo ifdown -a
sudo ifup -a
```

If this doesn't work, you might need to add the following two lines to the bottom, in the [font=courier]eth1[/font] section.  Given that [font=courier]ifconfig[/font] showed [font=courier]eth0[/font] and [font=courier]eth1[/font] as both "UP" anyway, despite their lack in the [font=courier]/etc/network/interfaces[/font] file, I suspect the issue might just be that these lines below are missing:
```
wireless-essid WIRELESS_NETWORK_NAME
wireless-key KEY
```
Replace the caps with the appropriate values.  KEY should be whatever password you use to access your wireless router.  

HTH,

Eiríkr

---

