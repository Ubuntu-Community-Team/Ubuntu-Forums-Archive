---
title: "wireless connection issue"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by carvish on 2011-03-15
My nephew has an older dell latitude Model# PP01l netbook with Xp on it but it is getting very slow to boot up and even slower to shut down. He was ready to throw in the towel on it, But me being a big Ubuntu fan , asked him if I could try ubuntu on it. After a bit of research I found out that Lubuntu 10.10 would be the way to go because of his limited ram 512 mb. So I installed lubuntu on it and it is working great except for one issue. The wireless internet  doesn't seem to want to connect. Hardwire it works fine. but when we try to connect through the wireless it sees the home network and tries to connect to it, but it is unable to do so. I even turned the security off his  rogers wireless modem to see if that was the issue to no avail. Any ideas about why it won't connect?:confused:
thanks

---

### Post by LowSky on 2011-03-16
What model is the wifi card?

can you type this into terminal and paste the output

```
lspci
```

---

### Post by carvish on 2011-03-16
I will be getting the  laptop back this afternoon 2 or 3 pm est will post results then
Thanks

---

### Post by carvish on 2011-03-16
matt@matt-Latitude-C610:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
matt@matt-Latitude-C610:~$ 

sorry about the delay, turned out to be a busy day

---

### Post by wep940 on 2011-03-16
Could you also post back the output of:
 
lsusb
 
 
I don't see a wireless device in the output from lspci.

---

### Post by carvish on 2011-03-16
matt@matt-Latitude-C610:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
matt@matt-Latitude-C610:~$ 
matt@matt-Latitude-C610:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
matt@matt-Latitude-C610:~$ 

thats all I got, even did it twice to make sure

---

### Post by wep940 on 2011-03-16
Hummmm - I still don't see a wireless adapter listed.  Is it internal?  Perhaps it has one of those wireless on/off switches somewhere on the case - my older Compaq has one.

---

### Post by Scooter85 on 2011-03-17
If you can see the network, have you tried entering the WEP key for entry. It is possible that your wireless router is blocking and not your linux installation.
If you can connect hard wired go to your router address... probably 192.168.1.1 and check under something like wireless security.
It should list the pertinent information for you to connect your laptop.

---

### Post by carvish on 2011-03-17
I was already in there, and to be sure, I shut off the security,it sees it but just won't connect to it, it tries.

I'm thinking maybe it's a driver or firmware that I need on it

[http://support.euro.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=5&dateid=-1&impid=-1&osl=TR&typeid=-1&formatid=-1&servicetag=&SystemID=LAT_PNT_P3C_C610&hidos=WW1&hidlang=tr&TabIndex=&scanSupported=False&scanConsent=False](http://support.euro.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=5&dateid=-1&impid=-1&osl=TR&typeid=-1&formatid=-1&servicetag=&SystemID=LAT_PNT_P3C_C610&hidos=WW1&hidlang=tr&TabIndex=&scanSupported=False&scanConsent=False)

this place gives me a list of available drivers for it, but I'm not sure which one I need,or how to install, should I be thinking "wine" I never used the program so go easy.

Also is there a way to take a screen shot in lubuntu 10.10? its easy in ubuntu 10.10, but I don't see it here in Lubuntu 10.10?

---

### Post by carvish on 2011-03-17
> **carvish said:**
> I was already in there, and to be sure, I shut off the security,it sees it but just won't connect to it, it tries.

I'm thinking maybe it's a driver or firmware that I need on it

[http://support.euro.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=5&dateid=-1&impid=-1&osl=TR&typeid=-1&formatid=-1&servicetag=&SystemID=LAT_PNT_P3C_C610&hidos=WW1&hidlang=tr&TabIndex=&scanSupported=False&scanConsent=False](http://support.euro.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=5&dateid=-1&impid=-1&osl=TR&typeid=-1&formatid=-1&servicetag=&SystemID=LAT_PNT_P3C_C610&hidos=WW1&hidlang=tr&TabIndex=&scanSupported=False&scanConsent=False)

this place gives me a list of available drivers for it, but I'm not sure which one I need,or how to install, should I be thinking "wine" I never used the program so go easy.

Also is there a way to take a screen shot in lubuntu 10.10? its easy in ubuntu 10.10, but I don't see it here in Lubuntu 10.10? I notice this link includes the word euro in it, should I be checking closer to home, like Canada??

---

### Post by grahammechanical on 2011-03-17
Does the keyboard have a print screen key? Then press it an see what happens. And forget about wine. It is a good program. Wine does what it is supposed to do as well as it is able to do, but it cannot install a Windows driver in a Linux operating system. It is not designed to do that.

Here is a link that might help

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

P.S. This is the key line:

> 00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)

Be careful, the Intel 82801CA/CAM chip seems to be a multi-purpose device. It also does audio and USB. Advice to fix an audio problem with this device might not fix a wireless problem with this device. But then again, it just might.

---

### Post by carvish on 2011-03-17
IEEE 802.11b Wireless mini-PCI Card

I found that in the specs from dell

I also found this in the terminal

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            3c59x
  State:             connected
  Default:           yes
  HW Address:        00:06:5B:E6:DC:09

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.21
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:6C:0A:61

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    Home:            Infra, 34:EF:44:AA:FA:A1, Freq 2457 MHz, Rate 11 Mb/s, Strength 100 WEP
    JLB-Net:         Infra, 00:21:91:15:F8:99, Freq 2452 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    ARHome:          Infra, 00:26:5A:C4:54:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2

my network is "home"

---

### Post by carvish on 2011-03-17
I think there is something wrong with the update of the wi fi, I installed ubuntu on two more laptops, they worked fine until the update. wifi wouldn't connect again, so I booted live, and was able to get online off a live cd.

---

### Post by Scooter85 on 2011-03-18
This is for Absolute beginners and I am one.
After my last post I lost my wifi connection. I used every bit of information I could find to correct. I knew that my connection had been good.
Started to think that I was going to have to replace the card.
After reinstalling Ubuntu 10.10 (I did my backups) and still had no luck, used the command as root:
rfkill unblock all
No help.
Did a boot into windows and found the same thing...
Then like a dummy found that when my cat walked across the keyboard, had stepped on the wifi connection and dissabled it. Pushed the button, and am back in business.
Well, lots of learning for a 2 mili-second fix.:confused:

---

### Post by carvish on 2011-03-18
I wish it was that simple, the only documentation about turning the wireless off/on is with the fn/f2 keys. If I go into the bios it shows the pci card as enabled.

I tried the live cd again with this one, doesn't work, it's seeing the home connection, and reading it because it keeps asking for my password to connect, it's like it's not sending. Could it be a faulty mini pci card?

---

