---
title: "wifi does not work after upgrade"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by dphipps on 2005-10-16
I use a Realtek rtl8180 wifi card on my desktop.  Before upgrade to Breezy it worked fine but now it won't work at all.  I use the ndiswrapper with xp drivers.

I have reinstalled the driver with these comands 'ndiswrapper -e NAME' and 'ndiswrapper -i DRIVER.inf'.  I then used 'modprobe ndiswrapper'.  It seemed to be installed properly but I still did not work.  When I used 'ndiswrapper -l' it gave the correct driver and said the hardware was present.

When that did not work I reinstalled ndiswrapper, but that did not help.

If I use a manual IP I can enable my wlan0 but I have not conection.  If I set it to dhcp than it just always remains disabled.

---

### Post by knappen on 2005-10-16
You should really post this thread in the networking section.

I had problems with my wireless network card since I installed Breezy. Kubuntu.

What I had to do was to manually change the /etc/network/interfaces

I added my essid and wep key and now it loads fine.

---

### Post by mlomker on 2005-10-16
What's the output of:

```

iwconfig wlan0
ifconfig wlan0

```

---

### Post by dphipps on 2005-10-16
Here are the results of iwconfig wlan0 and ifconfig wlan0
```
root@dphipps:/home/phipps # iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Auto  Frequency:2.422 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-69 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@dphipps:/home/phipps # ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0B:9D:01:30:EA
          inet6 addr: fe80::20b:9dff:fe01:30ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:e6000000-e60000ff

root@dphipps:/home/phipps #
```

---

### Post by mlomker on 2005-10-16
Hmm.  What does dmesg tell you after modprobing ndiswrapper?

```

dmesg | tail

```

I haven't seen that kind of output before, where the essid is listed as any/off.

---

### Post by dphipps on 2005-10-16
This is what I get.

```
root@dphipps:/home/phipps/ndiswrapper # dmesg | tail
[4294755.566000] Bluetooth: L2CAP ver 2.7
[4294755.566000] Bluetooth: L2CAP socket layer initialized
[4294755.597000] Bluetooth: RFCOMM ver 1.5
[4294755.597000] Bluetooth: RFCOMM socket layer initialized
[4294755.597000] Bluetooth: RFCOMM TTY layer initialized
[4294764.553000] eth0: no IPv6 routers present
[4294905.063000] wlan0: no IPv6 routers present
[4294960.368000] UDF-fs: No VRS found
[4294960.451000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294960.543000] ISO 9660 Extensions: RRIP_1991A
root@dphipps:/home/phipps/ndiswrapper #
```

---

### Post by mlomker on 2005-10-16
> This is what I get.


Not much help there.  Have you checked to see if there is a newer/different driver available?  

I know in the Hoary days you had to compile the latest ndiswrapper before anything would work, but I haven't heard enough feedback yet about Breezy.

---

### Post by knappen on 2005-10-17
Well I have managed to get my wireless working with the ndiswrapper in Breezy.

---

### Post by breakthestate on 2005-10-17
dphipps,

what is the chipset?

---

