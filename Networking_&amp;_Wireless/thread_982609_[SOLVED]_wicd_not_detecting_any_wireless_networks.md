---
title: "[SOLVED] wicd not detecting any wireless networks"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Ludachrispeed on 2008-11-14
I'm sorry about asking about a very specific problem but...

wicd says "no wireless networks found."  The problem may have been caused by this:

The last time I used my computer before wicd stopped working, I was browsing through System->Prefernces->Sessions "Startup Programs" and noticed "Network Manager" was checked.  I thought, "psh, that was supposed to be uninstalled when wicd was installed," and unchecked it.  Next time the computer was rebooted, wicd didn't work, and I rechecked "Network Manager" in Startup Programs.  Still doesn't work.

I think these may have something to do with it:

$lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:c2:01:ad
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

(that's just the relevant section)


I tried manually adding my home network to wpa_supplicant.conf... but I get this feeling that wicd doesn't look at it.  Any help would be greatly appreciated!

Thanks in advance

---

### Post by Ludachrispeed on 2008-11-16
I guess my question is how to enable my wireless interface, wlan0.  It seems like that should be really easy, but I can't find something that says how.

---

### Post by kevdog on 2008-11-16
under what exactly you posted on the first post -- you see the big word DISABLED.  That means something is wrong.  I would check dmesg to see if there is a clue about something listed with your wireless card.  go through it page by page:

dmesg | more

---

### Post by Ludachrispeed on 2008-11-16
Wow, dmesg produces a huge list of stuff.  What should I look for?

Oddly, the wicd log (/var/log/wicd/wicd.log) says that wlan0 actually does some stuff...

2008/11/16 20:24:04 :: ---------------------------
2008/11/16 20:24:04 :: wicd initializing...
2008/11/16 20:24:04 :: ---------------------------
2008/11/16 20:24:04 :: Automatically detected wireless interface wlan0
2008/11/16 20:24:04 :: found wireless_interface in configuration wlan0
2008/11/16 20:24:04 :: setting wireless interface wlan0
2008/11/16 20:24:04 :: automatically detected wired interface eth0
2008/11/16 20:24:04 :: found wired_interface in configuration eth0
2008/11/16 20:24:04 :: setting wired interface eth0
2008/11/16 20:24:04 :: found wpa_driver in configuration wext
2008/11/16 20:24:04 :: setting wpa driver wext

... that's just the first few lines


I thought there must be some simple command to fire up a network interface... I tried

```
sudo ifconfig wlan0 up

```
but it returned
SIOCSIFFLAGS: No such device

I've checked around this forum a for a while but I am still not able to find a solution.  Here are a few more possibly useful tidbits:

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by kevdog on 2008-11-16
look in dmesg for things regarding your wireless device.  There seems to be a driver problem.

Sorry

dmesg | more 

Will give you page by page output.

---

### Post by Ludachrispeed on 2008-11-16
Thanks a lot for the post!

I'm not experienced at all with looking through these kinds of files, but I found some interesting lines:

dmesg | grep iwl3945

```
[   14.423624] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.423628] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   14.423752] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.423767] iwl3945 0000:0c:00.0: setting latency timer to 64
[   14.423790] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   14.487317] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.853336] iwl3945 0000:0c:00.0: PCI INT A disabled
[   23.517126] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.517296] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   23.636425] iwl3945: Radio disabled by HW RF Kill switch
[   23.636533] iwl3945 0000:0c:00.0: PCI INT A disabled
[  115.618212] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  115.618397] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[  115.618720] iwl3945: Radio disabled by HW RF Kill switch
[  115.618800] iwl3945 0000:0c:00.0: PCI INT A disabled
[  115.790476] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  115.790659] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[  115.790988] iwl3945: Radio disabled by HW RF Kill switch
[  115.791071] iwl3945 0000:0c:00.0: PCI INT A disabled
[ 2817.797552] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2817.797722] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 2817.802033] iwl3945: Radio disabled by HW RF Kill switch
[ 2817.803444] iwl3945 0000:0c:00.0: PCI INT A disabled
[ 5468.150958] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5468.151132] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 5468.155574] iwl3945: Radio disabled by HW RF Kill switch
[ 5468.157102] iwl3945 0000:0c:00.0: PCI INT A disabled
[ 5621.251081] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5621.251264] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 5621.251578] iwl3945: Radio disabled by HW RF Kill switch
[ 5621.251655] iwl3945 0000:0c:00.0: PCI INT A disabled
```

---

### Post by imdano on 2008-11-16
It looks like your killswitch is on (or Linux thinks so, at least).  Is there a switch or button on your laptop which turns off your wireless card?

---

### Post by Ludachrispeed on 2008-11-17
AAAAHHHH YOU ARE A GENIUS!

So thats what that little guy does.

Ah, well at least I learned a lot.  What would I do if I didn't have secret switches getting toggled on my laptop to keep me entertained?

Thank you both very much for your replies!  The problem is solved.

---

