---
title: "Ubuntu (64-bit) on Raspberry Pi 4 Doesn't use 802.11 ac/n"
date: 2020-06-05
forum: Networking &amp; Wireless
---

### Post by toml_12953 on 2020-06-05
I have Ubuntu Server (64-bit) installed on my RP 4B (8GB) with the Ubuntu Desktop also loaded. When I try to connect to WiFi, my 5GHz connection isn't shown in available servers, only my 2GHz connection. How can I connect to the 5GHz Wifi connection? Both my network and the Pi have the hardware for it.

---

### Post by DuckHook on 2020-06-05
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

### Post by chili555 on 2020-06-06
Is the wireless in your Pi USB? Please run and post:

```
lsusb
sudo iwlist chan
```

---

### Post by bobbena on 2021-02-04
if you can help it would be apceated

bobbe@bobbe-desktop:~$ lsusb
Bus 002 Device 002: ID 152d:0562 JMicron Technology Corp. / JMicron USA Technology Corp. JMS567 SATA 6Gb/s bridge
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 005: ID c0f4:05e0  USB2.0 Hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 046d:082c Logitech, Inc. HD Webcam C615
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bobbe@bobbe-desktop:~$ sudo iwlist chan
[sudo] password for bobbe: 
lo        no frequency information.


eth0      no frequency information.


wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
bobbe@bobbe-desktop:~$ 

Thank You 
Bobbe

---

### Post by chili555 on 2021-02-04
How is networking configured in your server? Netplan or Network Manager?

May we see:

```
nmcli device wifi list
```I suspect that your router is set to autoselect the channel it deems best.

---

