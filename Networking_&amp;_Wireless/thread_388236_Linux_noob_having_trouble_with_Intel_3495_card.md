---
title: "Linux noob having trouble with Intel 3495 card"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by mpompey on 2007-03-19
I've been doing some searching regarding my wifi difficulty, and although others have had trouble with the Intel 3945abg card, I think my issue is a little different. So here goes...

I have a Dell Inspiron 9400 that has the nefarious Intel 3945abg wireless card built in. I just upgraded to Edgy from Dapper. My wireless card worked in Dapper, but I'm having the hardest time getting it to work in Edgy. I dual boot between XP and Edgy and the wireless card works in XP, so I know the wireless card is not defective.  I've reinstalled the Edgy OS twice so far, reformatting the partition each time. Just to make sure there are any hidden settings, tripping me up.

While in Edgy and I go to System-->Networking, I can see the wireless card there. I've enabled the card and entered all the settings for my WLAN. However, I can't connect. I installed wifi radar, as that was the app that I used in Dapper to connect to my WLAN.

My wired connection on DHCP works fine, but my wireless connection on DHCP or static IP doesn't connect. When I unplug my wireless connection, and start wifi radar, the wifi radar applet shows that I am connected to (None) but shows the IP address of the Loopback. The connect button isn't displayed. My guess is because wifi radar thinks I'm already connected (via the loopback address) However, I can't disconnect from the loopback address through wifi radar.

I'm not sure where my next steps should be. I've heard of people using gnome-network-manager to get wifi working in Edgy. Is that what I should do? Have I messed something up internally by installing wifi radar? How do I disconnect from the loopback connection so I can try to connect with the wifi connection?

Is there a depository with the Intel 3945abg driver and everything already setup? I know that the wireless card is supposed to work with Edgy out of the box. But from all of the research I've been doing, it doesn't look like it does.

I've heard others say that I should just stick with XP and forget about wasting time with Linux. But in the month that I've been using Dapper, I've never had a BSOD, stop error, system hang, etc. So I'm really interested in getting Edgy to work on this platform.

---

### Post by chili555 on 2007-03-19
Let's start with the basics. May we please see: ```
sudo iwconfig
iwlist <your_wireless_interface> scan
cat /etc/network/interfaces
```
Obscure any encryption keys as necessary.

> others say that I should just stick with XP They probably enjoy BSOD, viruses, spyware, malware. lockups, etc. Me? I enjoy getting my work done.

---

### Post by mpompey on 2007-03-19
Thanks for replying chili, here are my results:

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3264   Missed beacon:0

sit0      no wireless extensions.
************************************************
Here are the results of iwlist eth1 scan:

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:18:DC:C9
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-32 dBm  Noise level=-32 dBm
                    Extra: Last beacon: 48ms ago
          Cell 02 - Address: 00:0F:B3:BC:BC:F4
                    ESSID:"534D7"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-88 dBm  Noise level=-88 dBm
                    Extra: Last beacon: 32ms ago
*********************************************************************************
Here are the results of cat etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp





iface eth1 inet dhcp
wireless-essid {removed}
wireless-key {removed}



auto eth1

auto eth0

---

### Post by ppatalano on 2007-03-20
I was just about the same troubles as you and I installed Network Selector from add/remove applications and it works now for connecting my ipw3495. I don't know why this is but it does. Hope this helps. :)

---

### Post by ppatalano on 2007-03-20
Prior to installing I installed KWifiManager which was able to turn on the radio then I use NetworkSelector to connect. Seems like a bit of a hassle but it seems to be the easiest fix for me.

---

### Post by chili555 on 2007-03-20
mpompey-
You don't say if your encryption is WEP or WPA. If it is WPA, I'd suggest you check these forums for references to wpa_supplicant. If it is WEP, here is a post that may help: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

What sometimes also helps is to add the word open after the WEP key, like this:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91 open
```

Like space aliens, I heard passphrase works, but neither I, nor anyone I know, has actually seen it. 

Good luck and post back if we can help.

---

### Post by mpompey on 2007-03-20
Chili, I did everything you said and no luck. I double checked the WEP key and SSID to no avail. I uninstalled Gnome-Network Manger, rebooted, double checked the settings and wireless still wouldn't work.

I tried ppatalano suggestion using kwifi-manager, and BRAVO, wireless works. It does seem to be extra work to launch kwifi-manager, then activate the configuration for my WLAN but it seems to work for now. Thanks ppatalano for the tip!

I would still like to know why it would work with just Ubuntu's System-Admin-Networking, that should have been enough to turn on the Wireless radio and connect, correct?

---

