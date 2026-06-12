---
title: "Edgy:  Switched to orinoco a/b/g and not working."
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by ethos101 on 2006-11-28
I was using ndiswrapper before on a previous card (Trendnet) to run wifi in Edgy.  I just picked up the Proxim Orinoco a/b/g card with atheros chipset (8480-FC).  I can't get it to work in ubuntu (works great in windows so I know it's good).

I uninstalled the ndiswrapper driver properly.
Supposedly my card should work out of the box?
Am I missing something?

Here is what confuses me:  I see data RX/TX on wifi0 (via ifconfig) but then I see my neighbors (baboo) wireless connection on ath0 (via iwconfig).  Is there some tangled up operation here?
```
ethos@user-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:20:A6:54:82:4E  
          inet6 addr: fe80::220:a6ff:fe54:824e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

**wifi0**     Link encap:UNSPEC  HWaddr 00-20-A6-54-82-4E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1020 errors:0 dropped:0 overruns:0 frame:275
          TX packets:7173 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          **RX bytes:83957 (81.9 KiB)  TX bytes:319733 (312.2 KiB)**
          Interrupt:11 Memory:e0b40000-e0b50000
``````
ethos@user-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

**ath0      IEEE 802.11g  ESSID:"baboo"  **
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate:36 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Any help would be appreciated. :D

---

### Post by FrodoB on 2006-11-28
Look at lsmod and make sure that ndiswrapper is not loaded.

You new card is ath0 so try:

sudo iwlist ath0 scanning to see nearby networks.

Check /etc/iftab to see if it is keeping your old device around.  If you see wifi0 or whatever it is called in there just remove that line.

And yes it appears that your new card is working.

Publish the outout of lspci and it should show Atheros.

---

### Post by ethos101 on 2006-11-29
Cool so:
1)ndiswrapper is not loaded,
2)networks are visible,
3)lspci shows Atheros, but
4)my iftab only has eth0 and that's it.

Do I add the line Ath0 as well with mac address and anything else?

Thanks for the speedy response.

---

### Post by FrodoB on 2006-11-29
You should just be able to go to the menu:

System -> Administration -> Networking


Fill out the data for ath0, WEP, key, SSID, etc. and then start the network. After it is started you should see that the access point field in iwconfig is filled out with the access point's MAC identifier.  netstat -rn should reveal that ath0 is hooked up to the router etc.

---

### Post by ethos101 on 2006-11-29
You know what's wierd.  I just turned it on tonight and it's working.  Suddenly ath0 is in the list.  It just wasn't there before (in admin/networking I mean).  No matter how many times I re-booted it wouldn't show up but tonight it's there.
Problem solved, thank you FrodoB!
Peace.
Maybe it was those commands you told me to run gave the machine a hint and it sorted itself out.  :D

---

