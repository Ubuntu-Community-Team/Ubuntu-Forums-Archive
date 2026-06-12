---
title: "Turn WiFi On/Off"
date: 2018-09-11
forum: Networking &amp; Wireless
---

### Post by electrosteam on 2018-09-11
Lubuntu 18.04 LTS.
Dell Inspiron 5150, build 2003, 2 GB RAM, Linux 4.15.0-33-generic #36.
USB EDUP dongle model EP-AC1607, with Realtek rtl8811au chip.
Connected by ethernet cable to TP-Link Modem/Router.

Got WiFi running nicely with the ethernet cable disconnected.
Then, when the ethernet cable was connected, both the ethernet and WiFi link were showing data moving between router and laptop on the GKrellM monitor.
So, went back to the GUI - Network Connections to de-select the "Automatically connect to this network when available" box.
The parallel operation ceased.

Dis-connected the ethernet cable, no internet connection, and tried the following:

```

john@Bluebox:~$ iwconfig
wlxe84e065bbf16  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

john@Bluebox:~$ ip link set dev wlxe84e065bbf16 up
RTNETLINK answers: Operation not permitted

john@Bluebox:~$ ip link set dev WIFI@REALTEK up
Cannot find device "WIFI@REALTEK"


```

Can anybody advise the correct approach for a simple command line that will start the WiFi (when I am away from the router with the ethernet cable disconnected).

John.

---

### Post by chili555 on 2018-09-11
I think sudo is required to set the interface up. Please try again.

```
sudo ip link set dev wlxe84e065bbf16 up
```

---

### Post by electrosteam on 2018-09-11
Tried sudo with both device names, no success.
A bit more investigation is required.

This is not a real problem because the WiFi Menu icon on the task bar does start the WiFi.
I think I will leave the setup with NOT automatically connecting the WiFi, to minimise possible problems of two channels inter-acting.

The extra step of selecting on the WiFi Menu icon will remind me of the situation.
If I do inadvertently get the two channels in use, GKrellM will indicate it.

Are there any known problems with parallel operation ?

As a side issue, my kernel was updated in the middle of this, requiring a reinstall of the rtl8812au driver.
Writing this post with WiFi.

Thanks for the help,
John

---

### Post by electrosteam on 2018-09-12
Did some experimenting.

```

john@Bluebox:~$ ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device

john@Bluebox:~$ ifconfig wlxe84e065bbf16 down
SIOCSIFFLAGS: Operation not permitted

john@Bluebox:~$ sudo ifconfig wlxe84e065bbf16 down
[sudo] password for john: 
john@Bluebox:~$ 

```
WiFi off after 10 seconds.
```

john@Bluebox:~$ sudo ifconfig wlxe84e065bbf16 up
john@Bluebox:~$ 

```
No WiFi after 90 seconds.
Re-establish WiFi with GUI Menu.
```

john@Bluebox:~$ sudo ip link set dev wlxe84e065bbf16 down
john@Bluebox:~$ 

```
WiFi off after 10 seconds.
```

john@Bluebox:~$ sudo ip link set dev wlxe84e065bbf16 up
john@Bluebox:~$ 

```
No WiFi after 90 seconds.
Re-establish WiFi with GUI Menu.


The general wlan0 is not recognized, need the specific allocated name for the device.
Command 'sudo down' worked for either 'ifconfig' or' ip link' after 10 seconds.
Command 'sudo up' did not work for either 'ifconfig' or 'ip link', waited 90 seconds for each, and no response from the system.

John

---

### Post by chili555 on 2018-09-12
> The general wlan0 is not recognized, need the specific allocated name for the device.It is not recognized in any case if you haven't any interface named wlan0. You haven't. Your wireless interface is wlxe84e065bbf16. If you want to take it up or down then that's what you must specify.

wlan0 is not some kind of abbreviation for 'whatever my wireless interface turns out to be, I don't want to look it up.'

---

