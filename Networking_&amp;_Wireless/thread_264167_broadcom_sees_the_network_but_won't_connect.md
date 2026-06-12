---
title: "broadcom sees the network but won't connect"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by dennis1200 on 2006-09-24
I was so proud to have succesfully setup my broadcom 4318 (the one and only) wireless card on my acer laptop. ndiswrapper plus a few lines in rc.local. it worked like a charm. i just moved and the wireless network here shouldn't be any different, right? apparently not. before i had a d-link 128-bit wep encryption thing going, here it's a 10-digit wep code on a 2WIRE router. The connections manager correctly sees the networks available, including mine, but lists both as unsecured, even thought the 2wire one definitely is (works in windows). i'm not sure if this has anything to do with the fact that it won't connect or not (dhcp). the wep code is entered, by the way. additionally frustrating is a seeming failure of iwconfig to register commands. it doesn't give the essid of my network, instead just "off/any" despite explicit commands to do so (i.e. sudo iwconfig eth1 essid XXXX). i am two floors above the router and the signal isn't phenomenal (24-36MBps, instead of the more ideal 54), but dropped connection doesn't even happen in windows. any help?

---

### Post by happy-and-lost on 2006-09-24
Print output of iwconfig in your next post.

But I suspect the solution is ```
sudo apt-get install wifi-radar
```

---

### Post by dennis1200 on 2006-09-24
IWCONFIG OUTPUT
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

in terms of wifi-radar - i'll try that in the next day or two. have to get my computer downstairs and hardwired to the network. hopefully that won't pose any problems.

---

### Post by dennis1200 on 2006-09-25
i tried wifi-radar, which successfully saw the networks but failed to receive an ip address through dhcp (which is the configuration of the network). perhaps on a related note, it failed for the same reason on a couple local unsecured networks (very weak signals, however). i just upgraded the kernel to the latest (2.6.15.27-386 i believe). no change.

---

### Post by bmasephol on 2006-09-25
I've got a dell mini-pci card (broadcom) and experience the same issues as you... have since I started using the release canadiates of Dapper.

I can see networks but DHCP fails to get ip.

After spending way more time on it that it was worth I fainlly just broke down and bought a PCMCIA card to use when the laptop was booted into linux, use my mini-pci when I'm in XP or OS X but slap in the PCMCIA card when I'm in Ubuntu.

I bought a Zonet card, works without doing anything more... still wireless is kinda funky... using WirelessAssistant in KUbuntu it will connect but fails the test... but it still makes my internet connection.

Oh and I forgot to write about that I could get my Broadcom adapter working when the AP had WEP on it.  But when it was unsecured I couldn't get an IP.

---

