---
title: "USB Bluetooth Dongle &amp; Sony Ericsson w850i"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by MikeJ112 on 2007-06-04
Hi. I'm having a few issues establishing a connection with my computer and my phone. 

lsusb shows my bluetooth dongle;

```
mike@desktop-ubuntu:~$ lsusb
Bus 001 Device 004: ID 0a5c:2021 Broadcom Corp. 
Bus 001 Device 002: ID 1606:0060 Umax [hex] Astra 3400U
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 043d:0073 Lexmark International, Inc. 
Bus 002 Device 001: ID 0000:0000  
mike@desktop-ubuntu:~$ 
```

hcitool finds my phone;

```
mike@desktop-ubuntu:~$ hcitool scan
Scanning ...
        00:1A:75:9C:93:23       W850i
mike@desktop-ubuntu:~$ 
```

but when i try to connect to my phone it asks for the passcode, which is set to 1234 in hcid.conf
and the phone says bluetooth connection failed

I have been able to send/recieve files from phone using Bluetooth File Sharing (OBEX push) but I want to be able to establish a proper connection

HELP!

---

### Post by durfff on 2007-06-23
Yo, 

I've been trying to get this to work but to no avail. 

whenever I enter sudo hidd --connect [mac address of the phone] , I get asked for the passcode (passkey in ubuntu). 

I've checked my hcid.conf file in /etc/bluetooth, and the passkey in there is 1234. Entering that on my phone doesn't work, connection is refused. I've then gone on to change the passkey in hcid.conf to something different, like 1, or 1111, or 123, and still no result. 

My bluetooth dongle is a cheapo version, recognised as ISSCBTA in windows. It seems to want to connect to my phone but cannot establish a proper connection. 

I've tried this using sudo hidd --connect [mac address of the phone] on hte computer and also tried to launch the remote control directly from the phone (which seems o connect as it's recognising the computer but then asking for a passkey and failing, same way)

Any idea, anyone? :(

---

