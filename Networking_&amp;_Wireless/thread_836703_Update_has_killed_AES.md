---
title: "Update has killed AES?"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by EnlistedSquire on 2008-06-21
Hi,

I'm using Gutsy on a Fujitsu laptop with an onboard Atheros wifi card. As of yesterday the wireless was working tickety-boo using WPA with AES encryption. Yesterday I got a (kernel?) upgrade (from 2.6.22-14 to 2.6.22-15 I think - I'm a bit new at this Linux game) and now today the wireless will only work with TKIP. With AES the connection just times out after trying for a few minutes.

I tried booting with the old kernel from Grub and it still doesn't work so I'm not convinced it's this update that caused the problem but it's the only thing that's changed since yesterday AFAIK.

Here's my hardware info:

```
darren@ubuntu-laptop:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wifi0
       version: 01
       serial: 00:c0:a8:d2:cf:18
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.1.71 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

```
darren@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"network01"  Nickname:""
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:11:50:24:FB:B4   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-41 dBm  Noise level=-91 dBm
          Rx invalid nwid:8233  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

As can see from the below, my wifi card does support AES (and as I said, it's been working fine until now):

```
darren@ubuntu-laptop:~$ dmesg | grep wifi0
[   26.132000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   26.132000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   26.132000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   26.132000] wifi0: mac 7.8 phy 4.5 radio 5.6
[   26.132000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   26.132000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   26.132000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   26.132000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   26.132000] wifi0: Use hw queue 8 for CAB traffic
[   26.132000] wifi0: Use hw queue 9 for beacons
[   26.208000] wifi0: Atheros 5212: mem=0x30000000, irq=22
```

Googling and searching these forums hasn't really produced any similar results so I hope someone can shine some light on this.

Thanks.

Darren.

---

### Post by josmcc on 2008-06-21
You could try this utility

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by kevdog on 2008-06-22
Can you confirm some of the methods you have tried to connect with WPA2?

---

### Post by EnlistedSquire on 2008-06-22
@josmcc, thanks for the suggestion. I like the look of that utility. Unfortunately, it's the same problem - works fine with TKIP but with AES it's just constantly trying to pick up an IP address. I tried all the different drivers in the preferences with no joy.

@kevdog, my WAP doesn't support WPA2 I'm afraid.

[EDIT]I think I may have misunderstood your post. Not sure what info you want though. I've tried connecting with Gnome Network Manger as I always have done previously, and WIDC as recommended above.[/EDIT]

Thanks.

[NewEDIT]Looks like [this]("http://ubuntuforums.org/showthread.php?t=810723") thread might be connected to the problems I'm having. I will try some of the suggestions in when I get home.[/EDIT]

---

### Post by kevdog on 2008-06-22
I thought AES only worked with WPA2?  Where you using AES with WPA(1) in your case or what application have you noticed is broken with AES in your situation?

---

### Post by EnlistedSquire on 2008-06-22
Hi kevdog,

My WAP (a Belkin pre-N MIMO wi-fi router for reference) only supports WPA v1 but you can change the encryption from the default TKIP to AES. I think the encryption is auto-negotiated so the only devices I've had trouble connecting are WEP only (except Windows Mobile 5 for some reason). My Wii, the laptop running both Ubuntu and Windows XP as well as other peoples' laptops have all connected fine with this configuration.

> what application have you noticed is broken with AES in your situation? 

All of them! The laptop just can't establish a connection (as described above). I don't know what has changed to stop this from working.

Thanks.

---

### Post by EnlistedSquire on 2008-07-06
OK, just to bump this thread up a bit. It seems I'm not the only person to have lost some or all wi-fi connectivity with a recent upgrade.

Just to update, I've given up trying to resolve this problem on Gutsy and started a new install of Hardy where I have exactly the same problem - connects fine with TKIP, nothing with AES.

I've tried the Windows drivers with Ndiswrapper, I've tried WICD, I've tried every possible combination of settings possible with no luck.

This is really annoying. It took weeks to get my laptop to a functional state with Gutsy and I was hoping an upgrade to Hardy would be relatively simple. Unlike others, I still at least can get my connection working somehow, but I've always found AES to be quicker so would prefer to use it over TKIP. :confused:

---

### Post by kevdog on 2008-07-06
So your router is set to use the AES cipher with WPA encryption?  Just to verify.

Have you tried making a manual connection using wpa supplicant with the above parameters?

Just for kicks can you post iwlist scan showing the router you want to connect with.

---

### Post by EnlistedSquire on 2008-07-07
> **kevdog said:**
> So your router is set to use the AES cipher with WPA encryption?  Just to verify.

Correct.

iwlist:
```
          Cell 03 - Address: 00:11:50:24:FB:B4
                    ESSID:"network01"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=60/70  Signal level=-35 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f20201010f0002a4640027a400004243c80062326400
```

WPA_Supplicant output attached (never used it before but I think I've set it up OK).

Thanks.

---

### Post by kevdog on 2008-07-07
What does your wpa_supplicant.conf file look like?

---

### Post by EnlistedSquire on 2008-07-08
> **kevdog said:**
> What does your wpa_supplicant.conf file look like?

```
          network={
               ssid="network01"
               scan_ssid=1
               key_mgmt=WPA-PSK
               psk="XXXXXXXXXXXXXXXXXXX"
          }
```

Ran it with the command:

```
wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -d
```

Cheers.

---

### Post by Midwest-Linux on 2008-07-08
Why doesn't anyone out a "sticky" warning users of the possibility of the loss of wireless or other functions due to these kernel updates?

---

### Post by EnlistedSquire on 2008-07-08
> **Midwest-Linux said:**
> Why doesn't anyone out a "sticky" warning users of the possibility of the loss of wireless or other functions due to these kernel updates?

It shouldn't really happen though should it? Updates are supposed to add and improve functionality, not remove it. :D

The annoying thing is, I always go through the updates to see what's likely to happen to my rig and nothing suggested to me that something was likely to go wrong with that batch of updates.

---

### Post by EnlistedSquire on 2008-07-10
OK, I've made a (small) breakthrough.

I've discovered that by turning off QOS (802.11e) on the WAP I am able to connect with AES. QoS has been enabled the whole time prior to now so now I need to find out why this particular oddity is occurring and if I can enable QoS again in Ubuntu.

So to sum up (Y = Connected, N= Not Connected):

______QoS On_____QoS Off

AES:___N____________Y

TKIP:__Y____________Y (presumably, didn't test this)

---

### Post by kevdog on 2008-07-10
This latest set of updates have been particularly buggy.  Ubuntu seems to have a bad reputation outside of this forum community for bad buggy kernels.  I have no actual proof of this statement of than for the Hardy kernels.  They seem to be terrible.  Prior to Hardy I myself never had any problems with kernel related problems.

---

### Post by EnlistedSquire on 2008-07-15
OK, so I just booted into my old Gutsy installation and there were some updates. Installed them and now AES works again, but only with QoS switched off as per my Hardy install. I'm almost back where I started, but not quite...:confused:

---

