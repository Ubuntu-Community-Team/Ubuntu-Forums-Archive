---
title: "WG511 v1 Headaches"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by justin credible on 2006-11-14
I've been having some serious issues with my wireless card. It began when I first received the card (WG511 v1). It worked initially, but I realized later that the GUI and command line tools in Kubuntu did not let me connect to the wireless network I wanted to. The only way I could connect was to use 'dhclient' in console and let it connect to an open AP.

I have looked around and found several people commenting that I could just copy the Windows Prism54 driver into the hotplug firmware directory and rename it isl3890. I tried it an rebooted but it didn't really seem to make a difference however dmesg says the firmware loads.

From what I gathered, my last option was to use ndiswrapper and wrap the configuration file to the kernel and recompile. I haven't been able to find the .inf file for the WG511 or my Windows install disk for it so I am really just stuck. Anyone ideas?

---

### Post by j2fraser on 2006-11-24
Preface: I'm using WG511v1, connecting to a Netgear WGR614 using WEP, under Edgy, without ndiswrapper.

I had problems getting my WG511v1 working properly as well, but I found a useful thread at [www.kubuntuforums.com]("http://www.kubuntuforums.com"), which recommended that I look at /usr/share/doc/wireless-tools. When I went through there and then compared it to my wireless card's ethX entry in /etc/network/interfaces, I realized that the Kubuntu wireless-assistant (may have the name wrong there, writing from work) wasn't putting the correct entries in: it was using the wrong syntax for the WEP key and default key number entries! Once I edited that file as root, fixed the syntax and rebooted, everything worked flawlessly and I was able to connect to my Wireless Access Point (WGR614). Hope that helps -- good luck!

---

### Post by sumgi on 2007-02-11
So I too have a WG511 V1 Card and I have very little knowledge of ubuntu. The Network Connection icon only says lo and does a loop back. When I look at System ..> Admin ..> Networking and try to activate wireless it doesn't give any options in the drop down for connection.  

Any ideas?? I am completely clueless and new. Is there something I should be doing from the command line?

Thanks

EDIT:

Oh I did install the wrapper guy and some driver but I think it was for v2, I've been looking around and all I can find is an exe for v1. is there a .inf file for this card?

EDIT:

Ok I got the card installed by running the exe in windows and then grabbing the .inf and .sys files from the WINDOWS directory. Now I get this when I run lshw...

```

     *-network
          description: Wireless interface
          product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
          vendor: Intersil Corporation
          physical id: 0
          bus info: pci@03:00.0
          logical name: eth2
          version: 01
          serial: 00:09:5b:c5:a5:d0
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=prism54 multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:d2000000-d2001fff irq:11

```

But the card still doesn't work, here is my interfaces content..

```

#auto lo
#iface lo inet loopback


iface eth2 inet dhcp
wireless-essid linksys
wireless-key XXXXXXXXX

iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid linksys
wireless-key XXXXXXXXXX


auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp














#iface eth2 inet dhcp
#wireless-essid linksys
#wireless-key XXXXXXXXXX

```

as you can see I was playing with it. Please give suggestions.

Thanks

---

### Post by sumgi on 2007-02-11
Ok that was a bad idea, soo no edit that file. But at least I see eth0 which is my nic in the network connection icon now rather than just lo. Ahh well, thanks for any help you linux gurus can come up with.

---

### Post by Floppyjoe on 2007-02-12
Try not to comment out the lo interface sumgi
Maybe add the lines under eth2 that I have added where wireless-channel is the channel of your router.

```
auto lo
iface lo inet loopback


iface eth2 inet dhcp
wireless-essid linksys
wireless-mode managed
wireless-channel 6
wireless-key XXXXXXXXX

iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid linksys
wireless-key XXXXXXXXXX


auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by sumgi on 2007-02-12
Ok done but I have another problem, when I run ndiswrapper -l I get this..

```

ryanw@ryanw-laptop:~$ ndiswrapper -l
netwg511 : driver installed
        device (1260:3890) present (alternate driver: prism54)

```

I blacklisted prism54 and now wireless isn't an option under Networking in Administration. So it isn't using this driver, should I just uninstall it and go with the prism54 one? Is that what I should have been doing all along?

---

### Post by Floppyjoe on 2007-02-12
> **sumgi said:**
> Ok done but I have another problem, when I run ndiswrapper -l I get this..

```

ryanw@ryanw-laptop:~$ ndiswrapper -l
netwg511 : driver installed
        device (1260:3890) present (alternate driver: prism54)

```

I blacklisted prism54 and now wireless isn't an option under Networking in Administration. So it isn't using this driver, should I just uninstall it and go with the prism54 one? Is that what I should have been doing all along?

It is possible. 
I had one case where I thought one of my ndiswrapper drivers worked with another device but it turns out there was a native driver that allowed the second device to function.

---

### Post by sumgi on 2007-02-12
Ok so it appears everything is working on my card, but wireless security is causing all the trouble.

```

ryanw@ryanw-laptop:~$ iwconfig eth2
eth2      IEEE 802.11b/g  ESSID:"central"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:18:39:BB:9C:21   
          Bit Rate:54 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Link Quality:248/0  Signal level:-43 dBm  Noise level:-36 dBm
          Rx invalid nwid:0  **_Rx invalid crypt:28_**  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've was able to connect when I disabled security, anyone have thoughts? I tried 

sudo iwconfig eth2 essid central ap 00:18:39:BB:9C:21 key XXXXXXXXXX mode Managed commit
Error : unrecognised wireless request "XXXXXXXXXX"

sudo iwconfig eth2 essid central ap 00:18:39:BB:9C:21 key XXXX-XXXX-XX mode Managed commit
Error : unrecognised wireless request "XXXX-XXXX-XX"

sudo iwconfig eth2 essid central ap 00:18:39:BB:9C:21 key restricted 1 XXXX-XXXX-XX mode Managed commit
Error : unrecognised wireless request "restricted"

sudo iwconfig eth2 essid central ap 00:18:39:BB:9C:21 key restricted [1] XXXX-XXXX-XX mode Managed commit
Error : unrecognised wireless request "restricted"

I get this every time..

---

### Post by sumgi on 2007-02-13
Ok I feel really silly. So when I set up WEP encryption my router gave me four keys, I didn't realize that only one would work at any given time. I had been using the second key in the list for some reason, once I started using the first it works fine now!!

Thanks for all your patience

---

