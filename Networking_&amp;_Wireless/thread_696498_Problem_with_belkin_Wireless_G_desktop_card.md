---
title: "Problem with belkin Wireless G desktop card"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by beerjen on 2008-02-14
I'v e been searching the forum for solutions but no luck...  It's a computer at work and I'm getting realy frustrated.  (I've also posted in[ this thread]("http://ubuntuforums.org/showthread.php?t=574501"), but got no reply yet so I'm trying here)

I installed the driver through ndiswrapper and I can see the device in the network manager but it doesn't connect to my wireless network. 

I'm using kubuntu  7.10. 

These are the outputs for some network commands

```

internet@internet-desktop:~$ ndiswrapper -l
net8185 : driver installed
        device (1799:700F) present

```


```
lspci
03:09.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

```

```
lspci -n
03:09.0 0200: 1799:700f (rev 20)
```
```

internet@internet-desktop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0g
```

```

lshw -C network

  *-network
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 9
       bus info: pci@0000:03:09.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:31:5a:79
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,02/01/2007,5.1097.0 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
internet@internet-de
```

```

iwlist
internet@internet-desktop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] keys
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
              [interface] auth
              [interface] wpakeys
              [interface] genie
              [interface] modulation
```

---

### Post by DoctorMO on 2008-02-14
what happens when you run a 'sudo iwlist wlan0 scan' ? This should produce a list of wireless networks in your area.

You then need to consider that if you can see the networks you expect in the list weather the driver is supporting the encryption method that's on the network. Not all ndiswrapper drivers support wpa2 for instance (much to my personal chagrin)

---

### Post by Hightide on 2008-02-14
HI Beerjen

It seems there is s problem your AP not being associated 

[B]Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
[/B]

If you are not automatically  associating with an AP, there are a number of possible reasons. The first thing I would try is to manually associate with it by setting the ESSID via:


sudo iwconfig wlan0  essid <the essid of the AP you want to connect to>

Hope this helps

regards

:)

---

### Post by beerjen on 2008-02-14
"no scan results"

that's all I get

---

