---
title: "Kubuntu 18.10: Alfa AWUS036ACH Finding No Networks and Not Connecting"
date: 2018-12-21
forum: Networking &amp; Wireless
---

### Post by rdaze on 2018-12-21
**Solution: **install the [aircrack]("https://github.com/aircrack-ng/rtl8812au/tree/v5.2.20") drivers. This may require a kernel update from 4.18 to 4.19. The connection will hang or disconnect if actually inspected for some reason.

[HR][/HR]

After installing the basic drivers, I got connected to the WiFi. About an hour later, it disconnected and showed no networks in range at all--I tried rebooting, disconnecting the USB, scanning again, etc. Eventually it seemed to start working again.

But then it disconnected and once again shows no networks found. 

I've tried looking in Network Manager--every time it connects to a network it seems to make that a new connection restricted to a particular address, and then won't even show the network whilst it's there. On top of disconnecting, now it seems to refuse to connect--it asks for the password once, then, when it would previously go through configuring interface... it does nothing.

lsusb output:

    ```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 003 Device 003: ID 046d:c07e Logitech, Inc. 
    Bus 003 Device 002: ID 1b1c:1b15 Corsair 
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
    Bus 001 Device 010: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter
    Bus 001 Device 007: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

iwconfig:

```
          wlx00c0caa60a16  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

ip link:

    ```
8: wlx00c0caa60a16: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 00:c0:ca:a6:0a:16 brd ff:ff:ff:ff:ff:ff
```

---

### Post by praseodym on 2018-12-21
Please run the wireless script from the sticky thread and show the complete output

---

### Post by rdaze on 2018-12-21
Sorry about that, [here it is.]("https://pastebin.com/DvvJTcCa")

---

### Post by praseodym on 2018-12-21
Which of the SSIDs do you want to connect to? Change the encryption mode in your router to WPA2-AES (CCMP) only, not mixed mode WPA/WPA2

---

### Post by rdaze on 2018-12-21
Well... for one, an SSID that's not on that list because the interface keeps missing them (despite having connected earlier). [Rerunning the script,]("https://pastebin.com/4LhBh1VB") it would be either the 5ghz-ee-mm7gka option, though the 2.6ghz band ee-mm7gka would also be an option.

So you're saying to change the router settings? I'm not sure that would help with the adapter disconnecting and scan returning a "nothing found" response.

---

### Post by praseodym on 2018-12-21
Do also set the channel to a fixed one: 1, 6 or 13 in the 2,4 GHz band, not automatic

---

### Post by rdaze on 2018-12-21
That hasn't helped. It's still showing nothing in the network manager, and iwlist scan returns:
```
[FONT=monospace][COLOR=#000000]wlx00c0caa60a16  No scan results[/COLOR][/FONT]
```

---

### Post by praseodym on 2018-12-21
How did you install the driver?

---

### Post by rdaze on 2018-12-21
[FONT=monospace][COLOR=#000000]With:

```
sudo apt-get install rtl8812au-dkms
```

Trying to run the makefile from the manufacturer just spewed out warnings-configured-as-errors, and even with warnings ignored didn't finish with something that could be run with make install.
[/COLOR]
[/FONT]

---

### Post by praseodym on 2018-12-21
Lets try
```

sudo dpkg-reconfigure rtl8812au-dkms
```

---

### Post by rdaze on 2018-12-21
Ran it, rebooted, same thing--"no scan results".

I rebooted to windows to check if it was a hardware issue, which gave me a bit of a strange result (first it said it couldn't connect, then hid half the wireless options, then connected--it seems to be working fine). Do you think I should try to use the driver CD that came with it? It wasn't my first thought with Linux (nor was I expecting to have Linux drivers on the disc, but apparently they're there--though it seems like the same thing available from their site and I couldn't get that make file to work)

For the moment it's working again without having changed anything more, but whether that will stick...?

Answer: no.

It stopped working when I plugged in another connection (once again reverting to not being able to see anything) because when it *was* working it had some incredibly frustrating ping spikes that don't exist when running in Windows (which has its own problems because that won't work if the adapter starts off plugged in)

---

### Post by praseodym on 2018-12-22
Did you deactivate SecureBoot?

---

### Post by jeremy31 on 2018-12-22
It showed disabled in the script results
```
SecureBoot disabled
Platform is in Setup Mode
```

Platform in Setup Mode indicates that the Secure Boot keys were deleted, dkms might not function

---

### Post by rdaze on 2018-12-22
Well, after considerably more poking at different driver versions, I finally have the adapter working with some stability after upgrading the kernel to 4.19 over 4.18 and installing the [aircrack]("https://github.com/aircrack-ng/rtl8812au/tree/v5.2.20") drivers (before that the DKMS script was insisting there was already a driver in the kernel and I couldn't remove it). It's mostly stable now.

However, I (and someone else I was talking to) have noted something absolutely bizarre about this chipset: if you look at the connection details in network manager, the entire connection will hang. I've had it disconnect and then reconnect.

---

