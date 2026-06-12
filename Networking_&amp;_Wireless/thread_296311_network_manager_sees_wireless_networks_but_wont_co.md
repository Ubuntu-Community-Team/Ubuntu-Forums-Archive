---
title: "network manager sees wireless networks but wont connect?"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by paultru on 2006-11-09
Hey,

Have a really strange problem going on. The other day I decided to use Network manager, so I install it, followed all the the instructions, like disable the connections in the networking properties so network manager can work. Rebooted the thing, network manager works, I can click on it in the system tray, see the wireless networks, but when I try to select one nothing happens! I am having to connect my laptop into the router via cable to get on the net now! as soon as i connected the network cable network manager connects and its all fine on wired!.. I can still see the wireless networks in there though.. 

what's going on? am i using the manager wrong? 

Thanks for all you help in advance.. 
Ben

---

### Post by FrodoB on 2006-11-09
I was never able to get Network Manager to work with some devices, so maybe you should remove it and see if your system can at least be configured then?

---

### Post by Najand on 2006-11-09
Hmm, well... let us going through it manually...
Can you run the command "iwconfig" and send us the output?

---

### Post by paultru on 2006-11-09
> **Najand said:**
> Hmm, well... let us going through it manually...
Can you run the command "iwconfig" and send us the output?

here is the iwconfig output.


```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"TrumanNet"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:0F:B5:7F:C4:5A   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-29 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

TrumanNet is my wireless connection. Hope that helps. Cheers.

---

### Post by FrodoB on 2006-11-09
Looks connected, have you manually run dhclient from a terminal window? Post the results.

---

### Post by Najand on 2006-11-09
Looks fine to me.... Let us update local DNS server using the "bind" command. Then try to restart the whole thing by:
```

sudo /etc/init.d/networking

```
and then "ping" to see if it works or not?

---

### Post by featherking on 2006-11-09
FWIW, this is a list of supported cards that work with Network Manager [http://live.gnome.org/NetworkManagerHardware]("http://live.gnome.org/NetworkManagerHardware")

---

### Post by jkshu on 2006-11-11
Let me join in this discussion, since I have the same problem. Here's the output of iwconfig:

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"joeandmatt"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0D:88:9F:97:11   
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/94  Signal level=-54 dBm  Noise level=-95 dBm
          Rx invalid nwid:71650  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


When I tried to connect through wireless, it would try and then the window popup to ask for the key for the WPA. I entered it, but then after about 10 to 15 second the window asking for WPA passkey pops up again. Seems like somehow it didn't connect to the router properly.

I then connect the wired connection and check for the log on my router. I can see that it says wireless authentication success. So seems like the router is fine with my passcode. What do you think is the problem?

Also, what is this "bind" command that you talk about?

---

### Post by jkshu on 2006-11-11
Oh BTW, here's the output for dhclient:
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
```

Is that mean DHCP is not working somehow?

---

### Post by FrodoB on 2006-11-11
You likely need to drop your access point back to WEP or better yet no security while you are debugging. Once you get connected you can go to WEP for sure.  WPA is more trouble and may or may not work with your card and drivers.

---

### Post by FrodoB on 2006-11-11
Try to get connected without Network Manager and then work your way up.

---

### Post by jkshu on 2006-11-11
You're right, I dropped back to no authetication and WEP, and they both work. But I really want to use WPA (or even WPA2). How do I find out how whether my card is supported. I know it works fine in WinXP.

---

### Post by FrodoB on 2006-11-12
Well you are beyond me now, WEP is as far as I go.  

Not really secure, but puts folks on notice that this is not intended to be free bandwidth.

I suppose that you have already been through these. Some folks talk of WPA success in the write ups for drivers.

Good hunting and good luck to you.

---

### Post by jkshu on 2006-11-12
Thanks for the help though. At least I have wireless with WEP now. This is the last thing that hasn't work for me with Ubuntu. If WEP is the best I can do for now, I'm still happy.

---

