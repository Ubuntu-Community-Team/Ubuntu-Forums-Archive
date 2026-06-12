---
title: "wlan0 1350 (dhcp not working)"
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by h3avyarms on 2005-11-19
I have a Inspiron 1200 notebook running Ubuntu 5.10. I've tried installing my wireless card using ndiswrapper and linuxant and both seem to work but I can't get my router to send it an IP. DHCP works fine under windows. Any help would be nice. TIA.

---

### Post by Lambert on 2005-11-19
I want to verify you are connected to the router. If you run iwconfig where it says access point you have more then just zeros? 00:00:00:00:00?

If so try this command



sudo dhclient wlan0

---

### Post by h3avyarms on 2005-11-20
brandon@h3avynote:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"h3avynet"  Nickname:"unknown"
          Mode:Managed  Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brandon@h3avynote:~$ sudo dhclient wlan0
Password:
There is already a pid file /var/run/dhclient.pid with pid 11244
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:14:a5:0c:c5:d5
Sending on   LPF/wlan0/00:14:a5:0c:c5:d5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brandon@h3avynote:~$


It a configuration error of some kind or at least I think so. Please help me figure this out.

---

### Post by Lambert on 2005-11-20
Currently I don't believe you're connected to the router so I don't believe it's a dhcp problem.

First I want to check the driver being used. Post output of these.

sudo lshw -C network

If it's a usb device
lsusb

If it's a pci device
lspci

Also Try to scan for the router.
sudo iwlist wlan0 scan

You can try this command

sudo iwconfig essid <> ap <xx:xx:xx:xx:xx> key <> channel<> commit

If you're not using encryption you can leave out the key part.

Also what make/model of device are we dealing with?

---

### Post by h3avyarms on 2005-11-20
[QUOTE=Lambert]Currently I don't believe you're connected to the router so I don't believe it's a dhcp problem.

First I want to check the driver being used. Post output of these.

sudo lshw -C network

If it's a usb device
lsusb

If it's a pci device
lspci

Also Try to scan for the router.
sudo iwlist wlan0 scan

You can try this command

sudo iwconfig essid <> ap <xx:xx:xx:xx:xx> key <> channel<> commit

If you're not using encryption you can leave out the key part.

Also what make/model of device are we dealing with?[/QUOTE]


brandon@h3avynote:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:E5:4E:F9:67
                    ESSID:"Radiantwinds"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/94  Signal level:-87 dBm  Noise level:-154 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:48 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
          Cell 02 - Address: 00:11:50:6D:D5:A6
                    ESSID:"h3avynet"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:94/94  Signal level:-35 dBm  Noise level:-154 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100

brandon@h3avynote:~$


brandon@h3avynote:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:02:08.0 Ethernet controller: Intel Corp.: Unknown device 1068 (rev 03)
0000:03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
brandon@h3avynote:~$


Also it ia a belkin router from walmart. And I've tried that last commandand it doesnt seem to work. "sudo iwconfig wlan0 essid h3avynet mode managed" is the exact command I used. Anything else?

---

### Post by Lambert on 2005-11-20
With the iwlist scan showing output, the device and the driver are working properly. But the scan showed two routers within range. Even though the signal on the one you're trying to connect is stronger I believe it's trying to connect to radiantwinds. So here is what I recommend.

1. Use this command exactly as I type it.

sudo iwconfig wlan0 essid h3avynet ap 00:11:50:6D:O5:A6 channel 11 commit

2. If this doesn't work then

sudo iwconfig wlan0 sens -35

then try again the command from step 1.

---

### Post by h3avyarms on 2005-11-20
brandon@h3avynote:~$ sudo iwconfig wlan0 essid h3avynet ap 00:11:50:6D:D5:A6 channel 11 commit
Error : unrecognised wireless request "11"
brandon@h3avynote:~$ sudo iwconfig wlan0 sens -35 Error for wireless request "Set Sensitivity" (8B08) :
    SET failed on device wlan0 ; Operation not supported.
brandon@h3avynote:~$ sudo iwconfig wlan0 essid h3avynet ap 00:11:50:6D:D5:A6 channel 11 commit
Error : unrecognised wireless request "11"
brandon@h3avynote:~$

---

### Post by Lambert on 2005-11-20
```

sudo iwconfig wlan0 essid h3avynet ap 00:11:50:6D:O5:A6 freq 2.462G commit
```

Try it using the freq identifier instead.

Your driver doesn't support changing the sensitivity I guess.

Somebody else may see something I'm missing so hopefully the right person will read this next.

---

### Post by h3avyarms on 2005-11-21
anybody else have any ideas?

---

### Post by h3avyarms on 2005-11-22
Does anybody even know how I can get it working with static IP?

---

### Post by h3avyarms on 2005-11-22
wierdest thing just happened. I gave up trying to get the wireless working under linux so I turned WEP back on to keep people off my network and when I rebooted it started working once wep was turned on and a paassword set. any idea why?

---

### Post by Lambert on 2005-11-22
It may have been a daemon/service that wasn't running. When you rebooted if it's in the startup script it would have started service.

---

