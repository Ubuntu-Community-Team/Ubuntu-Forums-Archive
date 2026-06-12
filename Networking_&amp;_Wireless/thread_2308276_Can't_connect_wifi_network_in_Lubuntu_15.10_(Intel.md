---
title: "Can't connect wifi network in Lubuntu 15.10 (Intel PRO/Wireless 3945ABG/BG driver)"
date: 2016-01-01
forum: Networking &amp; Wireless
---

### Post by jason-cordero on 2016-01-01
I have the Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver  for Linux and my laptop finds my home network but can't connect it.

  The output of iwconfig is:
      > enp10s0  no wireless extensions.

    lo                    no wireless extensions.

    wlp2s0        IEEE 802.11abg  ESSID:off/any  
                              Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
                Retry short limit:7   RTS thr:off   Fragment thr:off
                Power Management:off

---

### Post by grahammechanical on 2016-01-01
Your WiFi adapter is switched on. It has transmitting power (Tx-Power) = 15dBm but it is not connected to any wireless access point. Why not? I do not know how to do this on Lubuntu but have you tried opening the Network Manager menu, selecting your home WiFi access point/router? You will be asked to authenticate. You then put in the passphrase - wireless key - WPA-PSK key as the password. Network Manager will remember the passphase for that wireless access point.

Have you tried this? Making a connection to a password protected wireless access point is one of the few times when our own user password is not the password we use to authenticate.

Regards.

---

### Post by sandyd on 2016-01-01
Moved *Networking & Wireless*

---

### Post by jason-cordero on 2016-01-01
Sure, I entered the right pass, but it doesn't connect...

---

### Post by chili555 on 2016-01-01
May we see:```
sudo iwlist wlp2s0 scan
```You may omit everything but your own network. 

Also:```
sudo iw reg get
dmesg | grep iwl
```

---

### Post by jason-cordero on 2016-01-02
```
sudo iwlist wlp2s0 scan
```
```
wlp2s0    Interface doesn't support scanning : Device or resource busy
```

```
sudo iw reg get
```
```
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
```

```
dmesg | grep iwl
```
```
[   13.530517] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.530523] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   13.530593] iwl3945 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   13.530611] iwl3945 0000:02:00.0: enabling device (0000 -> 0002)
[   13.586970] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   13.586975] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.718800] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   13.724876] iwl3945 0000:02:00.0 wlp2s0: renamed from wlan0
[   29.187309] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
```

---

### Post by chili555 on 2016-01-02
> wlp2s0    Interface doesn't support scanning : Device or resource busyBusy? How? Why??

Did you set up any connections in Network Manager? By any chance, the tricky and misleading "Create New WiFi Network"? That actually means to connect computer to computer (ad-hoc) and is not what you want which is a computer to router connection (infrastructure). Please double-check all the settings in Network Manager and remove them all! In most cases, NM should see and connect to your network without any help from us, the lowly users.

Let's see if there are any clues in the log:```
dmesg | grep wlp2s0
```In many cases, seeing but refusing to connect is a symptom of a driver that is sensitive to the access point settings. 

I own and use successfully two Intel wireless devices including a 3945! I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot. Any improvement?

---

### Post by jason-cordero on 2016-01-02
No, I just tried to connect to an existent (my home) network. I introduced the pass but it didn't connect.

```
dmesg | grep wlp2s0
[   13.479507] iwl3945 0000:02:00.0 wlp2s0: renamed from wlan0
[   29.892494] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   30.038592] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   30.383643] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  850.857276] wlp2s0: authenticate with 62:02:71:3a:9b:36
[  850.863628] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 1/3)
[  851.064161] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 2/3)
[  851.268131] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 3/3)
[  851.472155] wlp2s0: authentication with 62:02:71:3a:9b:36 timed out
[  862.796920] wlp2s0: authenticate with 62:02:71:3a:9b:36
[  862.801828] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 1/3)
[  863.004040] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 2/3)
[  863.208056] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 3/3)
[  863.412050] wlp2s0: authentication with 62:02:71:3a:9b:36 timed out
[  867.025182] wlp2s0: authenticate with 62:02:71:3a:9b:36
[  867.029974] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 1/3)
[  867.232065] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 2/3)
[  867.436052] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 3/3)
[  867.640042] wlp2s0: authentication with 62:02:71:3a:9b:36 timed out
[  871.755897] wlp2s0: authenticate with 62:02:71:3a:9b:36
[  871.756228] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 1/3)
[  871.960112] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 2/3)
[  872.164066] wlp2s0: direct probe to 62:02:71:3a:9b:36 (try 3/3)
[  872.368155] wlp2s0: authentication with 62:02:71:3a:9b:36 timed out
[  873.008771] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
```

```
sudo iw reg get
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

```

I set it to Spain and reboot as you said, but it still doesn't work...

I can't access so far the router settings (the default user and pass don't work, and I don't know if someone changed it)

---

### Post by chili555 on 2016-01-04
> I can't access so far the router settings (the default user and pass don't work, and I don't know if someone changed it)We really need that. Unfortunately, many Linux drivers including the iwl* suite, are sensitive to the access point. My Intel 3945 connects perfectly and stays connected to my WPA2-AES network locked to channel 11.

---

### Post by jason-cordero on 2016-01-05
Network authentication is Mixed-WPA/WPA-PSK, and the WPA/WAPI encryption is AES+TKIP. What should I change?

---

### Post by chili555 on 2016-01-05
> **jason-cordero said:**
> Network authentication is Mixed-WPA/WPA-PSK, and the WPA/WAPI encryption is AES+TKIP. What should I change?See if you can select WPA2 only, no mixed mode; and AES only, no mixed mode.

I suspect, but have no way to prove, that the driver struggles to lock on when confronted with a beacon that is searching around for the encryption method and even channel.

---

