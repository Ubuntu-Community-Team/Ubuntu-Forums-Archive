---
title: "Broadcom 4328 and WPA?"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by kutjara on 2008-04-22
[Note: Even though I'm running Hardy, my problem is not specific to this distribution, so I'm posting it here, rather than in the Hardy Development forum.]

Has anyone got the Broadcom 4328 wireless card to work with WPA encryption? I've been trying for a week and, frankly, it's got me stumped.

I installed the card on my HP Pavilion tx1420us under Hardy 64 bit, using the latest NDISWrapper (which I compiled myself) and the bcmwl5.inf and bcmwl564.sys driver files. The installation went well and the card works great with unsecured and WEP-secured networks.

The problem starts when I try to use WPA encryption (yes, I have installed and configured wpa-supplicant). No matter what I do, I can't make the damned card connect to my wireless router using WPA. I've read and implemented the advice in just about every HOWTO, thread, blog, and IRC channel with even a peripheral connection to WPA, but nothing will work. I've used Gnome Network Manager, WICD, Wifi Radar, the command line, chicken entrails, and threats, all to no avail.

What I'm asking for here is not another rehash of possible solutions, but advice from someone who has actually figured the puzzle out. There is something screwy about the way this card uses WPA, so it's going to take very specific knowledge of this particular problem, I think, to work out what's going wrong. I'm not seeing a lot of threads about the problem by people with 32 bit installs, so I suspect it might be a 64 bit issue, but that's just speculation.

If this sounds like a desperate plea, that's because it is. I've never had so much trouble getting a feature working under Linux. What makes it worse is that I'm so tantalizingly close to having a great Ubuntu laptop, if not for this metaphorical stone in my shoe.

---

### Post by kevdog on 2008-04-22
I may not be able to help you since I dont have this card.  I think weve corresponded before, however with the new forum theme change...yea...

Anyway when you post a thread like this, please post some information so we can examine your configuration such as
iwlist scan
/etc/wpa_supplicant.conf

And your invocation of the wpa_supplicant process you type at the command line.  This may all be for not however I need specific output in addition to a cry for help.

---

### Post by kutjara on 2008-04-22
> **kevdog said:**
> I may not be able to help you since I dont have this card.  I think weve corresponded before, however with the new forum theme change...yea...

Anyway when you post a thread like this, please post some information so we can examine your configuration such as
iwlist scan
/etc/wpa_supplicant.conf

And your invocation of the wpa_supplicant process you type at the command line.  This may all be for not however I need specific output in addition to a cry for help.

We have indeed discussed the issue, Kevdog. I reposted my question in this thread, because I thought it might get a bit more traction here than on page 43 of the NDISWrapper HOWTO thread.

I apologize for not including output with my original post, but I really was taking a shot in the dark that someone has experienced this exact problem and knows exactly what needs to be done. After working through 30+ ways of configuring WPA (including about fifteen different command line methods), I felt that the solution was going to be an all or nothing proposition. But enough preamble.

I replied to your questions in the last thread, with the output you requested, but the thread got buried in the reorg. Here's the relevant section of that post:

wpa_supplicant.conf:

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
   ssid="mySSID"
   scan_ssid=0
   proto=WPA
   key_mgmt=WPA-PSK
   psk="myASCIIPassphrase"
   pairwise=TKIP
   group=TKIP
}
```

lshw -C network:
```

  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:1a:73:e7:50:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

iwlist scan

```

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:3D:4E:10:2A:42
                    ESSID:"myNetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-27 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1C:10:AB:8E:19
                    ESSID:"Flyer1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:14:BF:C9:02:B4
                    ESSID:"linksys 2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:1B:11:5C:F2:C5
                    ESSID:"hole in the sky"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:14:6C:3D:C8:1C
                    ESSID:"Tiffany"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:18:4D:83:4A:F6
                    ESSID:"hovanessian"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

The Cell 01 network ("myNetwork") is my home network. The encryption key is off because I'm using it now in unsecured mode to access the forums on the machine that's causing this problem. When WPA is switched on, iwlist scan shows encryption as "on" (so it can at least recognize that much). The other networks belong to the other people in my apartment complex - as you can see, the card has no trouble scanning and finding networks.

I used your command line wpa-supplicant HOWTO last night (thanks very much for that, by the way), and it got me close, but just as I thought everything was going to work, the connection timed out during authentication.

---

### Post by kevdog on 2008-04-22
Found your old post by the way --

Few things with the encryption on -- does your iwlist scan show specifically that it is WPA encrypted (not WPA2), and is the output regarding the encryption similar to your neighbors?

The settings in the router -- what are they? TKIP cipher -- not AES? or some combination?

What mode are you working with -- I see your card does a/b/g/n.  I dont think n is supported because of the ndiswrapper thing.  Your probably not using a.  So I think you probably want g.  Is the router set for only g of mixed b/g?

What specifically timed out?  The wpa_supplicant invocation of the dhclient invocation?

---

### Post by kutjara on 2008-04-22
> **kevdog said:**
> Found your old post by the way --

Few things with the encryption on -- does your iwlist scan show specifically that it is WPA encrypted (not WPA2), and is the output regarding the encryption similar to your neighbors?

The settings in the router -- what are they? TKIP cipher -- not AES? or some combination?

What mode are you working with -- I see your card does a/b/g/n.  I dont think n is supported because of the ndiswrapper thing.  Your probably not using a.  So I think you probably want g.  Is the router set for only g of mixed b/g?

What specifically timed out?  The wpa_supplicant invocation of the dhclient invocation?

OK, I switched my router's WPA encryption back on and reran the iwlist scan. Here's the output for that (with my neighbors' networks removed for clarity):

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:2F:13:6A:32
                    ESSID:"myNetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

I must have read the wrong entry before, because I could have sworn the card recognized the router's encryption. Clearly, on this run, the card thought encryption was still off. For comparison, I just ran iwlist scan on my Acer laptop, running 32 bit Hardy (with an Atheros card using madwifi driver), which works perfectly with the router using WPA. Under the "IE" section, it reports:

```

IE:  WPA Version 1
     Group Cipher: TKIP
     Pairwise Ciphers (1) : TKIP
     Authentication Suites (1): PSK
     Extra:wme_ie:<52 digit hex number>

```

It seems that the Broadcom card doesn't even recognize that WPA is in use, which is strange, because WICD does: it displays the protocol right next to the network name. I would have thought WICD would get its knowledge of what encryption a router is using straight from the wireless card, so how can WICD know when the card doesn't? Most perplexing.

I just noticed something else strange: my card can recognize the encryption setup of every network in my area, except my own. That's too bizarre to be a coincidence.

---

### Post by kevdog on 2008-04-22
Yes strange things afoot here, if you switch on WEP or WPA2, do you get a similar output?  Im not expecting it to say WEP, or WPA, however the encryption of/off line should at least recognize that's its on.  If not, I think you have a driver issue.

---

### Post by kutjara on 2008-04-22
> **kevdog said:**
> Yes strange things afoot here, if you switch on WEP or WPA2, do you get a similar output?  Im not expecting it to say WEP, or WPA, however the encryption of/off line should at least recognize that's its on.  If not, I think you have a driver issue.

Here's the output for iwlist scan under 64 bit WEP:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:3E:7E:12:5F:47
                    ESSID:"myNetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

Note, the encryption key is recognized as being on, and the BCM4328 card works fine under WEP (40/64/128 bit).

When I switch to WPA2, however, it's back to the old story:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:7E:11:61:47
                    ESSID:"myNetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-34 dBm  Noise level:-97 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

So let me recap what I know:

- The BCM4328 works fine with my Linksys WRT600N router under Windows XP 64 bit, using the bcmwl5.inf and bcmwl564.sys driver files, under any encryption scheme (unsecured, WEP, WPA1 and WPA2).
- The card also works fine with my router under Ubuntu Hardy 64 bit, using the bcmwl5.inf and bcmwl564.sys driver files with NDISWrapper 1.52, but only with unsecured or WEP encryption. WPA won't work.
- An iwlist scan of the networks in my area can tell what flavor of WPA they're using, and whether it's TKIP or AES, but can't tell the same thing about the router sitting in the same room as the machine it's running on, barely ten feet away.
- My other laptop, using an Atheros AG5007 card and madwifi, running under Hardy 32 bit, connects to my Linksys router using WPA1/2 with no problems whatsoever.

All I can conclude from this is that there is some glitch in the way NDISWrapper handles WPA messages to/from the bcmwl564.sys driver, but only with respect to one particular model of router: the Linksys WRT600N.

I'm still using the latest version of the stock Linksys firmware, but I think I'll look into replacing it with something like dd-WRT. That might prove more compatible (or at least more hackable). If that fails, I guess I'll have to buy a USB wifi card.

Anyway, thanks for taking the time to help me think through this problem. Even though I haven't solved it, I believe I have a much better idea of what's going on (or, rather, what isn't). Unless someone comes along with a magic bullet, though, I'm going to have to admit that the BCM4328 under 64 bit Hardy isn't a practical proposition for anyone who wants decent wireless security.

---

### Post by kevdog on 2008-04-22
I'd have to agree with your assessment.  Looks like you are going to be in the market for a new wireless device -- I dont know a lot about usb devices to recommend.  I think the madwifi drivers are purely for pci based devices.  You might want to find an ra-based chipset device to change things up.

---

### Post by kutjara on 2008-04-23
> **kevdog said:**
> I'd have to agree with your assessment.  Looks like you are going to be in the market for a new wireless device -- I dont know a lot about usb devices to recommend.  I think the madwifi drivers are purely for pci based devices.  You might want to find an ra-based chipset device to change things up.

I guess great minds really do think alike. While you were posting this, I was at my local Fry's Electronics, buying a Belkin F5D7050 usb dongle. It's got the Ralink rt73 chipset. It didn't quite install out of the box, but I installed it with the Serialmonkey RT2x00 driver in about thirty seconds and am using the RutilT GUI wifi manager to connect in glorious WPA. Total time for installation and setup: five minutes. Hurrah!

A pox on Broadcom and their awful products.

---

### Post by marlier on 2008-04-23
Kutjara --

I certainly won't say that I've fixed anything, but invoking wpa_supplicant from the command line I was able to get a stable connection when I changed

ap_scan=1

to

ap_scan=0

in the wpa_supplicant config file.  Now if I could just figure out how to get NetworkManager to use that stupid parameter...

---

### Post by kutjara on 2008-04-23
> **marlier said:**
> Kutjara --

I certainly won't say that I've fixed anything, but invoking wpa_supplicant from the command line I was able to get a stable connection when I changed

ap_scan=1

to

ap_scan=0

in the wpa_supplicant config file.  Now if I could just figure out how to get NetworkManager to use that stupid parameter...

Thanks for that, Marlier. I'll give that a try if I get up the courage to attack the problem again. For now, I'm just going to use my new Belkin dongle and work on the other stuff I need to get working on this machine.

I'll definitely keep your tip in mind for when I (inevitably) try again.

---

### Post by kevdog on 2008-04-23
I don't know how network manager and wpa_supplicant interact together.  However you have a few options to get around this.  It seems like you want to use Network Manager in roaming mode.  You either need to manually add your changes to the /etc/network/interfaces file (something like this thread: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)) -- if that doesn't work you can also call wpa_supplicant directly from the interfaces file with use of the preup statements (more on this later if you want to go this route).

Also WICD, an alternative to network manager, works much in the same way as the command line, and you can manually alter the parameters it uses to call wpa_supplicant.  You could try this in leiu of network manager.

---

