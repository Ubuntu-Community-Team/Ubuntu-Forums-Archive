---
title: "[SOLVED] Wireless not detecting network anymore."
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by markers on 2008-09-23
Hey guys. I'm new to Ubuntu (now running Hardy & trying to learn how to use it) and first off I LOVE it so far. Everything has been working out great for me until now. Out of no where, my wireless stopped detecting my wireless router. I haven't had any problems with my wireless before. Up until now my laptop has been running wirelessly. Here's what comes up when I check out the **lshw -C network**.
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:42:e6:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:55:b0:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

```
Anyone have any ideas as to what my problem is? (Sorry if I didn't provide enough info.)

---

### Post by willca on 2008-09-23
Can you try this and see if it does see any wireless network.

sudo iwlist wmaster0 scan
sudo iwconfig wmaster0

If I read your previous log correctly, the wifi is named wmaster0. Otherwise replace it with whatever is appropriate.

---

### Post by markers on 2008-09-24
Thats another weird thing I noticed. I have never changed the name of my wireless from **wlan0** to **wmaster0**. But thats beside the point. Entered both of the things you recommended and got this in return.
```
markers@markers-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: **:**:**:**:**:**
                    ESSID:"Da House"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=65/100  Signal level=-71 dBm  Noise level=-97 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000001c09e2f603
          Cell 02 - Address: 00:1F:B3:AC:0C:21
                    ESSID:"2WIRE184"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=77/100  Signal level=-57 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000004c5f5494df8
          Cell 03 - Address: 00:11:95:4E:2E:D1
                    ESSID:"default"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/100  Signal level=-72 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000039246cf9f34

markers@markers-laptop:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"Da House"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=12 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:****-****-****-****-****-****-**
          Power Management:off
          Link Quality=55/100  Signal level=-75 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
I tried doing a manual configuration and I was able to connect to my wireless router. What bugs me is that the icon does not show how strong my signal is anymore and it still won't detect (or at least show that it has detected) any wireless networks.

---

### Post by willca on 2008-09-24
Ya does the same thing to my network manager and stuff. Thats why I dont depend on them. Its not reliable. What I do instead to keep track of how my connection to my AP is doing is via conky.

Ran a command sudo iwconfig wlan0 and just grep for the signal strength and bit rate.

---

### Post by markers on 2008-09-24
I wish that I wouldn't have to go through the trouble of looking up the **iwconfig wlan0** every time I want to see what my signal strength is.

I just tried starting up in recovery mode and I caught a glimpse of ***"wlan0: error fetching interface information: device not found"*** for the wireless. This line showed up several times. Do you think that this may explain what is causing the problem?

P.S. Thank you very much for taking time to help me out or at least trying.

---

### Post by styfle on 2008-09-24
Wow I have the exact same problem and no one seems to know whats going on. Manual connection works great but it flips out if I put it in roaming mode.
[http://ubuntuforums.org/showthread.php?t=924554#](http://ubuntuforums.org/showthread.php?t=924554#)

---

### Post by markers on 2008-09-24
No idea what just happened but after a restart of my laptop all the wireless networks that are in range are showing up again and I am able to connect to my network again. Thanks a bunch **willca** for not giving up so quickly on a newbie. And good luck on your problem **styfle**. If I can find out anything that could've changed and solved my problem I will be sure to pass it on to you.

---

### Post by willca on 2008-09-24
cool bro. sounds like a driver issue. believe me since most hardware are windows centric...freaking firmware just aint that fair treatment with *nix boxes. 

if you get tired of that having to reboot to get wireless nic to work...try switching to ndiswrapper

---

### Post by markers on 2008-09-24
Weird though since I haven't had any problems with the driver and the wireless has been working since I installed 8.04.

If it does come to that, is there anywhere I can find a step by step on how to use ndiswrapper?

---

### Post by AJB2K3 on 2008-09-24
Have you tryed reseting your router?
Mine did this and took two weeks of trying before I tryed resetting the router.
If that doesn't work try manual connection via **connect to other wireless network**.

---

### Post by markers on 2008-09-24
(incomplete post)

---

### Post by markers on 2008-09-24
I don't think it has anything to do with my router because all of the other computers on my network are all working fine and are all able to detect and connect to my wireless router.

Will still try this out though just in case you're right. Thanks all for continuing to help me with my problem.

---

