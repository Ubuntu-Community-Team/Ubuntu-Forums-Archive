---
title: "Unable to connect to WPA/WPA2 SSID"
date: 2015-08-30
forum: Networking &amp; Wireless
---

### Post by andrew256 on 2015-08-30
Bit odd this one. I´m new to Linux but fairly computer savvy. I recently loaded Lubuntu onto my old Toshiba Satellite and everything seems to work fine except I cannot connect to my Home SSID which features WAP security. I can connect to any unsecured network, so I don´t believe it´s my PCMCIA WiFi card.

When I try to connect to my Home SSID I get ¨Requesting a wireless network address from (my home SSID)¨ until it times out and defaults to an unsecured network.

Anyone care to point me in the right direction or tell me what screen dumps to print that might help?

---

### Post by Bucky Ball on 2015-08-30
Welcome. Click the network icon and 'Edit'. Edit the wireless connection there. Are all the details correct? Set the IPv6 tab to 'Ignore' for IPv6. Check other details. 

Do you generally use a static IP? Is the router/AP serving an IP via its DHCP server, or should be and is not? Have you set a static IP in the computer locally that is having problem with the IP the router is trying to serve you? Is it set to WAP? It should pick it up and ask. 

I'm presuming when you boot up you are getting no offer of available networks. Please give us the output from a terminal of this:

```
sudo lshw -C network
```

Thanks. Use code tags for the output (see last link in my signature).

---

### Post by andrew256 on 2015-08-30
The code your requested is below. I can post wireless-info.txt as well if that helps.

FYI. I can connect to any unsecured network (I&#7743; on one now). It&#347; just WPA secured networks that pose a problem. I can see them. but  I just timeout with ¨requesting a network address¨

```


*-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:3f:7c:21:e2
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e100  driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no  maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:e8104000-e8104fff ioport:4000(size=64)
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:2f:68:85:68
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=ath5k  driverversion=3.2.0-90-generic firmware=N/A ip=10.212.79.82 latency=168  link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:5 memory:54000000-5400ffff



```

---

### Post by chili555 on 2015-08-30
>  so I don´t believe it´s my PCMCIA WiFi card.PCMCIA?? Like this or similar? [http://g03.a.alicdn.com/kf/HTB1knziHVXXXXaiaXXXq6xXFXXXe.jpg](http://g03.a.alicdn.com/kf/HTB1knziHVXXXXaiaXXXq6xXFXXXe.jpg)

The Atheros listed above is PCI, not PCMCIA and seems to be connected as it has an IP address. Please tell us more: ```
sudo pccardctl ls
```With it trying to connect, let's also see:```
iw list | grep -i cipher -A10
```A fair number of older cards, and aren't all PCMCIA cards older, don't do WPA nor WPA2. I have a few on my shelf right now!

---

### Post by andrew256 on 2015-08-30
My WiFi card is a Netgear WPN511. PCI or PCMCIA is surely irrelevant as the security protocol is between the PSK configured in my router agreeing with my Laptop?

PS. It worked under WinXP

---

### Post by chili555 on 2015-08-30
> PS. It worked under WinXPA great many things work in XP but not in Linux and vice versa. Unless you can coax the XP drivers to work in Ubuntu with ndiswrapper, a mighty big IF on any device, the XP experience is not relevant.>  PCI or PCMCIA is surely irrelevantIt surely is relevant. Many PCMCIA cards were manufactured before WPA was developed. Moreover, driver development concentrates on devices made more recently. Your driver may not have been touched in many years.

Your router and laptop don't interoperate independently. They speak through the card.

Did you run the commands I suggested? They will tell us if the hardware (that is, the chip) and software (that is, the Linux driver) are capable of WPA and WPA2.

By the way, there are a few versions of the WG511. Yours may differ from the one I have.

---

### Post by andrew256 on 2015-08-31
My card is a WPN511 not WG511. Here is the code requested.

sudo pccardctl ls[code]
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:00.0)
  CardBus card -- see "lspci" for more information
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:00.1)
Socket 1 Device 0:    [pata_pcmcia]        (bus ID: 1.0)
[\code]

iw list | grep -i cipher -A10[code]
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:00.0)
  CardBus card -- see "lspci" for more information
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:00.1)
Socket 1 Device 0:    [pata_pcmcia]        (bus ID: 1.0)
andrew@andrew-laptop:~$ iw list | grep -i cipher -A10
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
    Available Antennas: TX 0x3 RX 0x3
    Configured Antennas: TX 0x3 RX 0x3
    Supported interface modes:
         * IBSS
         * managed
         * AP
[\code]

 
 
And if I&#7743; correct TKIP means my card supports WPA and CCMP means it supports WPA2. So that still leaves the question, why can´t I log on to my WPA2 secure SSID? I enter an alphanumeric string which I suppose is translated into what? A 128 bit hex string?
Or is my card having trouble determining whether I´m using WPA or WPA2 ???

---

### Post by andrew256 on 2015-09-15
PROBLEM SOLVED.

After a lot of searching on this, and other forums; failed trials; and a few downright scary moments where I thought I bricked my Tosh, I solved my problem by editing the following file:-

/etc/modprobe.d/ath5k.conf

by adding the following line:-

options ath5k nohwcrypt=1

Note: The file was empty before I started.

Saved the file and rebooted. My Tosh now automatically logs on to my home network SSID using WAP2 security.

I hope someone else may find this useful.

---

