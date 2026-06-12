---
title: "Able to connect to router but not internet?"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by majorawesome on 2014-06-17
So here's the dealio. 
Ubuntu-Gnome 13.04 - Able to detect routers, connect, and get internet access
Upgrade to Ubuntu-Gnome 13.10 - Able to detect routers, connect, but no internet access (Unable to ping 8.8.8.8)
Clean install Ubuntu-Gnome 14.04 - Able to detect routers, connect, but no internet access (Unable to ping 8.8.8.8)

I am currently running a live usb of 13.04 (I'll install later today in triple boot with win 8, Ubuntu-Gnome 13.10). 

I did try to install WICD, no help there. 

I do have a DNS in 13.10 (forgot to chech 14.04 before I unsinstalled). 

I am extremely confused by this situation. 
Can someone give me commands for trouble shooting?

PS: I did not try ethernet as my router is in a different room and I don't have a long enough ethernet cable.

---

### Post by majorawesome on 2014-06-17
I got a long enough ethernet cable and that works on 13.10. I used nm-tool and here's the output

```
austin@LinuxBox:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        94:DB:C9:4B:98:0D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    delauney:        Infra, 00:1F:90:E2:A4:FD, Freq 2437 MHz, Rate 54 Mb/s, Strength 29


- Device: wlan1  [Auto delauney] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        08:10:76:26:31:BD

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *delauney:       Infra, 00:1F:90:E2:A4:FD, Freq 2437 MHz, Rate 54 Mb/s, Strength 30

  IPv4 Settings:
    Address:         192.168.1.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.242.0.12


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        C8:60:00:E3:6B:85

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.242.0.12


```

The Ethernet and WiFi have different ip addresses...

---

### Post by majorawesome on 2014-06-17
Ok, so I figured that the requests for internet kept trying to go through mt atheros wireless device instead of my realtek one. I had the RT one connected to the internet and not the ATH one. Does anyone know how to force Ubuntu to use wlan1 instead of wlan0? I think that will fix my problem.

---

### Post by majorawesome on 2014-06-18
All right. I believe the problem is with the Realtek drivers. (I had the 8192ce). I had an Atheros wireless adapter in my computer that came with my motherboard but the antenna broke so that's why I got the realtek one. My Atheros is working but with limited signal.

If anyone is reading this looking for a solution and you have a realtek device, I going to realtek and trying to install their drivers (you have to compile them). If that doesn't work read further down on the README and find how to install via compat. That should work.

---

