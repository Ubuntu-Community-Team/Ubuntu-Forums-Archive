---
title: "Intel 3945 not working"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by paulisdead on 2008-02-04
I've read the other threads on this card, and still can't find anything that actually works for me.

I just recently decided to replace the broadcom wireless with an intel 3945abg mini pci wireless card, since the broadcom that the notebook came with has never worked with Ubuntu for me.

I've got the hardware wireless switch on, and ipw3945 module is loaded.  The device is detected as eth2.  In network manager I can see all the wireless networks but am unable to connect, and the hardware WIFI light is flickering like crazy.  In ifconfig I'm seeing lots of errors and almost all RX packets getting dropped.
```
eth2      Link encap:Ethernet  HWaddr 00:1C:BF:45:92:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:817 dropped:2470 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149711 (146.2 KB)  TX bytes:92169 (90.0 KB)
          Interrupt:17 Base address:0xe000 Memory:efdff000-efdfffff
```

Here's the output of iwconfig
```
eth2      IEEE 802.11g  ESSID:"GB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:09:5B:ED:9A:A0   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-57 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1684   Missed beacon:0
```
Here's what I see for the wifi interface in lshw
```
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth2
                version: 02
                serial: 00:1c:bf:45:92:23
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated
```

The only thing I'm seeing in dmesg that might be relevant is
```
[ 1134.272000] ipw3945: association process canceled
```

I rebooted into windows, and installed the drivers for the 3945 wifi card, and it works great.  The light does not flicker, and I'm not getting packet loss.  However, when I tried booting the 7.10 livecd I get the same problem with dropped packets and the hardware light flickering.  There's no fn+f2, just a switch on the side of the laptop, which is definitely flipped on.  I am using WPA on the router, but I'm fairly sure it's not even getting that far, and shouldn't be an issue.  I can't open up the access point, since this is in an office environment, and I can't reset it since we have restricted connections based on MAC address, and I can't lose those.  Plus other users might not be happy having the wireless down.

I did give ndiswrapper a go, but only tried it with the same drivers I installed in windows, which were the latest from Dell's site, but I didn't get an ethX device from them.

Please help, this has been driving me crazy not having wifi working on my notebook.

---

### Post by paulisdead on 2008-02-05
OK, I finally got it working.  I commented out everything to do with either wireless interface in /etc/network/interfaces and rebooted.  At first the wifi light was blinking like crazy, but once I got logged in, and clicked on network manager, and hit my wlan, it connected up fine.

I'm still losing a few packets and getting some errors on the interface, but it seems to be working quite well.  Also when I first startup, until I get logged in fully, the wifi light will flicker, and I'll get tons of dropped packets and a few errors on the interface, but once I'm up and connnected it works.

---

### Post by starsheeep on 2008-02-06
my broadcom device worked after following this guide :) maybe you should try it and get rid of the ipw3945

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by paulisdead on 2008-02-06
I'm pretty happy with the way it's working now.  I do accumulate a lot of dropped packets and a few errors on the interface, but it all seems to work really nicely.  It also connects up at 54mbps.  The behavior from it's a bit weird, but whatever, so long as it works.

---

### Post by starsheeep on 2008-02-12
i have the same card in another notebook
i had lots and lots of problems trying to make it work with wpa, i tried every guide i could find and had finally given up when I replied to your post, but after a suggestion i tried the wicd network manager and wireless worked (with wpa, :guitar:) in a edgy clean install, will try in gutsy 2

---

