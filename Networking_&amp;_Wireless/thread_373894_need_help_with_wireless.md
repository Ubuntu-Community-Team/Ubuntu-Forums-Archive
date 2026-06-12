---
title: "need help with wireless"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by ch3wyb4r on 2007-03-01
hi, this is also my first time using linux and i like it alot but i'm having a real hard time with my wireless setup.  my wired setup has gone smoothly but this darn wireless has gotten me stumped.  i have a HP laptop with a intel pro 3945abg internal card. i know i have installed the drivers with "windows wireless drivers" but my laptop won't even register it.  Also, my wireless can be enabled or disabled by moving a button side to side and the led indicator says its off when its on the "on" position. I have also looked and ran through other tutorials and they have not worked. i have installed ndiswrapper and here are the outputs

ndiswrapper
Installed ndis drivers:
netw3           driver present, hardware present

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:16:36:DA:F4:6F
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feda:f46f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:633874 (619.0 KiB)  TX bytes:72078 (70.3 KiB)
          Base address:0x5000 Memory:da000000-da020000

eth1      Link encap:Ethernet  HWaddr 00:19:D2:22:5B:BB
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:127 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3286 (3.2 KiB)
          Interrupt:169 Base address:0xa000 Memory:d8000000-d8000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
**iwiconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Xiongplace"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:133   Missed beacon:0

sit0      no wireless extensions.
**lscpi**
0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)

I dont know what else to do. please help

thanks,
chewy

---

### Post by nyinge on 2007-03-02
Try disabling bcm43xx first.
```
  echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist 
```
- Reboot computer.

- Type in the following:
```
 sudo modprobe ndiswrapper 
```
- Check for any error messages.
- If none, continue...
```
 sudo iwconfig wlan0 essid YOUR_SSID 
```
Note that I am using "wlan0" instead of "eth1".  Ndiswrapper uses "wlan0" as the wireless interface.

Type in:
```
 iwconfig wlan0 
```
to see if the number after "Link Quality:" is other than zero.  If not, repeat the process of entering your SSID.

Once your wireless card has been associated with the AP, issue the following command to get an IP address (DHCP):
```
 sudo dhclient wlan0 
```

So...  How's everything?

---

