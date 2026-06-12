---
title: "Another wireless problem ..."
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Yoeri on 2007-04-24
Can't get wireless to work. Feisty detects my card and everything seems ok when looking at dmesg. I can see all access points in the network mabnager applet but I am unable to connect ...

I also tried connecting via manual configuration without any success...

Adapter is a Zydas1211, in edgy I followed the guide (with success): [http://ubuntuforums.org/showthread.php?t=92327&highlight=zydas+1211](http://ubuntuforums.org/showthread.php?t=92327&highlight=zydas+1211)

---

### Post by wieman01 on 2007-04-24
What does...
> sudo iwlist scan
...yield? Please post the results.

---

### Post by Yoeri on 2007-04-24
Im currently at work, will post output of dmesg and iwlist tonight ... thanks for wanting to look into this

---

### Post by Yoeri on 2007-04-24
**_Results of dmesg (the zydas part)_**
```

[   39.933238] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   39.999700] usb 3-5: firmware version 0x4330 and device bootcode version 0x4802 differ
[   40.039907] cs: IO port probe 0x100-0x3af: clean.
[   40.041724] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   40.042707] cs: IO port probe 0x820-0x8ff: clean.
[   40.043354] cs: IO port probe 0xc00-0xcf7: clean.
[   40.044118] cs: IO port probe 0xa00-0xaff: clean.
[   40.143468] zd1211rw 3-5:1.0: firmware version 4605
[   40.185442] zd1211rw 3-5:1.0: zd1211 chip 0b05:170c v4802 high 00-13-d4 AL2230_RF pa0 g---
[   40.187834] zd1211rw 3-5:1.0: eth1
[   40.187846] usbcore: registered new interface driver zd1211rw
[   40.505742] intel8x0_measure_ac97_clock: measured 55414 usecs
[   40.505746] intel8x0: clocking to 47498
[   40.693784] fuse init (API version 7.8)
[   40.719476] lp0: using parport0 (interrupt-driven).

```

**_Results of the iwlist scan (my wireless network)_**
```

          Cell 03 - Address: 62:6A:18:B9:19:DD
                    ESSID:"Fixed"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 340ms ago

```

Thanks for the help ...

---

### Post by ian.leckey on 2007-04-24
I'm also having this problem.

I tried removing network-manager and knetworkmanager, and installed wcid. Sadly it didnt connect either.

I reinstalled network-manager and knetworkmanager, and now it's not even detecting my wireless LAN from the tray icon. BUT it does see it when i go to manually configure.

```
wlan0     Scan completed :
          Cell 01 - Address: 00:30:BD:F1:BA:B3
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.462 GHz
                    Signal level=-141 dBm  Noise level=-160 dBm
                    Encryption key:off
                    Extra:tsf=000000033d204186

```

---

### Post by Yoeri on 2007-04-25
Tried changing the channel via
```
sudo iwconfig eth channel 1
```

But I get an error... I am starting to think about going back to edgy or windows :(

---

### Post by wieman01 on 2007-04-25
Your card is apparently working. All I can suggest is that you turn off encryption for a minute (i.e. MAC filtering, WEP/WPA), enable DHCP and ESSID broadcast, and try to reconnect. I am sure it will work, Feisty did the job for me as well when I tested it last week.

---

### Post by Yoeri on 2007-04-25
I turned off security, set a fixed IP, tried manual configuration etc. ... no success...

I'll do some more research tonight... I'll go and buy a (very) long network cable to be able to post from within Feisty... now I constantly have to reboot.

---

### Post by Yoeri on 2007-04-25
I do have to say that it is an ad-hoc network an that the channel is apparently 1 instead of the networkmanagers default 6... maybe i have to search why i can't change the channel?:confused:

---

### Post by wieman01 on 2007-04-25
> **Yoeri said:**
> I turned off security, set a fixed IP, tried manual configuration etc. ... no success...

I'll do some more research tonight... I'll go and buy a (very) long network cable to be able to post from within Feisty... now I constantly have to reboot.
Can't you try DHCP instead? I had troubles connecting via fixed IP, but DHCP did it eventually. There is a workaround for static IP as well, but try DHCP first.

---

### Post by Yoeri on 2007-04-25
hi, DHCP doesn't work either... turned off everything on my gateway, still no connection.

I tried installing wifi radar, it scans for networks, says it is connected but I cannot see any connection on the gateway, nor I can ping something. I do notice that the link quality is very bad although I am sitting next to the other computer :confused: 

thinking harder to reinstall an reconfigure Edgy ... I cannot do anything without my wireless connection.

Do you have other suggestions?

---

