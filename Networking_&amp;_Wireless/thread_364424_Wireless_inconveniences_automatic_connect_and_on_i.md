---
title: "Wireless inconveniences: automatic connect and on indicator"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by yurukov on 2007-02-18
Hi I have some problems with my wireless. They are more of inconveniences. 

First, every time I want to connect to a wireless network, I have to sudo the wlassistent and choose from the list of wifi points. I connect mostly  to the rooter at my place. Is the a way to do that automaticaly - connect to a specific network without me having to sodo it everytime.

Secondly, there is a small button in front of my computer that has its light on when the wireless is on. At least in windows. In ubuntu it is not on and I cannot know if my wireless is on. It is not important, but I often I don't need it and it only drains my battery. I guess it is something with my drivers. Here is my lspci: 

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by eppoh on 2007-02-18
download wifi radar via synaptic. Makes choosing the access point very easy

---

### Post by yurukov on 2007-02-18
Hows that any different from the wlassistent. The interface is better but still I have to sudo it and select a network manualy. I need something that would automaticly connect to a wireless network when it is in range.

---

### Post by chili555 on 2007-02-18
I suggest amending your /etc/network/interfaces file to specifically get the network you want:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid GBR1
wireless-key 096cxxxxxxxxxxxxxxxxxxafe 

```

GBR1 being, in my case, the ESSID of the router in my home. Then you would only have to mess with wlassistant if your are *not* at home.

---

### Post by yurukov on 2007-02-18
Nope, it did not work. I guess that the wireless-essid is the name if the network. I am using a WEP security, so I set the wireless-key to the password. Is that correct? I restarted, but there was no connection.

---

### Post by AusIV4 on 2007-02-18
I'm having the same problem on one of my computers. Wifi-radar won't work because the network is hidden, and for whatever reason configuring /etc/network/interfaces hasn't resulted on connection on boot up. My other laptop does fine - it connects to the wireless network on boot or coming out of sleep mode, basically as soon as ifup is called.

I'd really like to get this straightened out. While it's still functional, it's annoying to have to click three times before I'm online.

---

### Post by chili555 on 2007-02-18
If you do sudo iwlist wlan0 scan (or whatever your relevant interface is) do you see your router? If you want to connect automatically to it, put its name, case-sensitive, in the wireless-essid position.

As for WEP, you may have used a passphrase when you set up your router, for example, ilovecoldbeer. The passphrase then generates a key. The passphrase ilovecoldbeer, for example, returns the 128-bit key 696c6f7665636f6c6462656572. It is the series of numbers and letters you want to enter in the wireless-key position.

Then do sudo ifdown wlan0 followed by sudo ifup wlan0 and let us know, preferably before the Daytona 500 starts.

---

### Post by yurukov on 2007-02-18
I haven't got a 128 bit key. When I config-ed the router I just set the passphrase as it is. When I connect through the wlassistent I entered only that. How can I generate the key?

---

### Post by chili555 on 2007-02-18
The easiest way is to set up your connection under wlassistant, then, when you are connected, open a terminal and do sudo iwconfig wlan0 (or your relevant interface) and you will see your key. Here is mine, obscured, of course:
```
 sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:62:8D:F7   
          Bit Rate:24 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:096C-XXXX-XXXX-XXXX-XXXX-XXXX-FE   Security mode:restricted
          etc. etc.

```
That key, without the hyphens, is what you wat to add to your /etc/network/interfaces file.

---

### Post by teaker1s on 2007-02-18
install
[COLOR="Red"]network-manager-gnome[/COLOR]

---

### Post by AusIV4 on 2007-02-18
> **teaker1s said:**
> install
[COLOR="Red"]network-manager-gnome[/COLOR]

That's what i finally settled on (except I use network-manager-kde), but it doesn't connect until after login, and for me an optimal solution would start-up on boot.

---

### Post by yurukov on 2007-02-19
Actually its **knetworkmanager**. Took me a while to find it. I can't seem to config it right - how can I add new networks. There is nothing in the list. The only state change I see is when I connect via a cable. I assumed that it would detect a new network once I connect to it, but it doesn't.

Also, I tried out the wifi-radar. It's better than the lwassistant in terms that it shows multiply access point of the same network as one -> easier to connect. I have that at the university. However, I have problems connecting with it to my home router. I have set the passphrase and the network name and all else to auto, but it doesn't get an IP. Oh, DHCP is auto too.

And one thing I still haven't figured out - how can I activate the light of the button that activates the wireless. It would make it easier. It works in windows :???: I tried to install the windows drivers with ndiswrapper.

---

