---
title: "New issue   :("
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by djmoore85 on 2008-03-28
Hey yall, have a new issue now. I cannot get signal strength over 0/100 when my laptop is where it is normally stationed for use. I am now about 5 feet from the router and am currently getting 

 ```
IEEE 802.11b/g  ESSID:"klinger"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1E:8C:02:FD:10   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          **Link Quality=66/100  Signal level=-46 dBm ** Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:179  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Anything I may be able to do? Thanx in advance for any help, this forum has been great for gathering information and the support.

---

### Post by luisromangz on 2008-03-28
Try using ndiswrapper, if you are using the bcm43xx driver, or viceversa.

---

### Post by tgalati4 on 2008-03-28
Rx invalid crypt seems to imply that received wireless packets have an invalid crypto key.  Have you tried resetting the router?  Sometimes they need rebooting to reset the wireless transmissions.

---

### Post by djmoore85 on 2008-03-29
Now I'm stumped, I have the GUI for ndiswrapper installed, but sourceforge's list for windows drivers only has an .exe file for my chipset. How do I extract the .inf or .sys files needed from this .exe?

**EDIT**  Alright, I blacklisted bcm43xx due to the conflicting it would have with ndiswrapper, and now I have no wireless at all. I have the driver files on my XP partition, and selected all .inf files for the ndiswrapper . Any help I can get to have my wireless back and running with ndiswrapper instead of the bcm43xx stuff? currently connected through ethernet connection

---

### Post by tgalati4 on 2008-03-29
Post the output of:

>ifconfig

>iwconfig

If ndiswrapper loaded correctly then you should be able bring up network manager and add a location with SSID and WEP key.

---

### Post by luisromangz on 2008-03-29
In the ndiswrapper page they have tutorials on how to setup the driver.

---

### Post by djmoore85 on 2008-03-30
Also it is telling me that ndiswrapper is associating the driver with the hardware, I included that readout for the ndiwsrapper -l to show yall 


```
daniel@DJK71307:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@DJK71307:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

```

**EDIT** Modified the /etc/modules file to load ndiswrapper at startup, and now have the laptop back in its normal location. Now have an iwconfig readout of

```
eth1      IEEE 802.11g  ESSID:"klinger"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:8C:02:FD:10   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

