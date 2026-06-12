---
title: "Wifi stopped working - (L)ubuntu 3.10 - Intel 5300 wifi"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by solveig.hansen on 2014-01-18
Hi guys, I am having some problems with my wifi suddenly stopped working. I've spent a couple of days trying out every solution I've come over, but I'm starting to feel like that Einstein quote about insanity is doing the same thing over and over and expecting different results. I just reinstalled Lubuntu 3.10 hoping that it would magically start working again, but alas!

I've had this card working for about a three weeks (it worked right away with the default iwlwifi driver) , but then I suddenly started having frequent disconnects, and after a reboot it stopped connecting altogether.

lspci :  
```
Network controller: Intel Corporation Ultimate N WiFi Link 5300
```

iwconfig:  (when trying to connect it does at some point have an ESSID and seems to be connected, but then something goes awry.)
```
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:21:6a:c3:43:6a  
          inet6 addr: fe80::221:6aff:fec3:436a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5514 (5.5 KB)  TX bytes:12776 (12.7 KB)

```
Right after I try connecting and it fails I get this dmesg output:
```
[ 1100.532432] r8169 0000:05:00.0 eth0: link down
[ 1105.454623] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1113.786458] wlan0: authenticate with 00:1d:68:75:5c:ff
[ 1113.789729] wlan0: send auth to 00:1d:68:75:5c:ff (try 1/3)
[ 1113.792789] wlan0: authenticated
[ 1113.793385] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1113.796194] wlan0: associate with 00:1d:68:75:5c:ff (try 1/3)
[ 1113.798947] wlan0: RX AssocResp from 00:1d:68:75:5c:ff (capab=0x411 status=0 aid=3)
[ 1113.801380] wlan0: associated
[ 1113.801462] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1159.471115] wlan0: deauthenticating from 00:1d:68:75:5c:ff by local choice (reason=3)
[ 1159.484105] cfg80211: Calling CRDA to update world regulatory domain
[ 1159.490679] cfg80211: World regulatory domain updated:
[ 1159.490692] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1159.490697] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1159.490700] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1159.490704] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1159.490707] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1159.490710] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1169.174105] r8169 0000:05:00.0 eth0: link up
[ 1169.174134] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1672.992044] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 1673.015519] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.
[ 1750.985206] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 1751.004243] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.
[ 2475.832422] r8169 0000:05:00.0 eth0: link down
[ 2490.325714] wlan0: authenticate with 00:1d:68:75:5c:ff
[ 2490.326734] wlan0: send auth to 00:1d:68:75:5c:ff (try 1/3)
[ 2490.329541] wlan0: authenticated
[ 2490.329892] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2490.329901] wlan0: waiting for beacon from 00:1d:68:75:5c:ff
[ 2490.385557] wlan0: associate with 00:1d:68:75:5c:ff (try 1/3)
[ 2490.392468] wlan0: RX AssocResp from 00:1d:68:75:5c:ff (capab=0x411 status=0 aid=3)
[ 2490.394609] wlan0: associated
[ 2535.618712] wlan0: deauthenticating from 00:1d:68:75:5c:ff by local choice (reason=3)
[ 2535.633761] cfg80211: Calling CRDA to update world regulatory domain
[ 2535.643871] cfg80211: World regulatory domain updated:
[ 2535.643883] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2535.643887] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2535.643891] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2535.643895] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2535.643898] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2535.643901] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)



```

Sorry if this has been discussed before, I couldn't find anything that worked for me at least.
If you need more info, let me know! Crossing my fingers somebody has some creative ideas =)

---

### Post by praseodym on 2014-01-18
> ```
[ 2535.618712] wlan0: deauthenticating from 00:1d:68:75:5c:ff by local choice ([COLOR="#FF0000"]reason=3[/COLOR])
```
This is normally from the network-manager. Checked Wicd?

```
sudo apt-get install wicd
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver in Wicd.

---

### Post by solveig.hansen on 2014-01-18
> **praseodym said:**
> This is normally from the network-manager. Checked Wicd?

```
sudo apt-get install wicd
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver in Wicd.

Hi, thanks for your reply! 

Hum. I tried your suggestion, and never got to the part where I choose interface name or driver, because the "sudo service wicd restart" step gave me a [fail] message. But then I restarted, and suddenly I have wifi! But what is actually managing my wifi now? How do I check that? I am a bit sceptical to this being a stable solution tbh!

---

### Post by solveig.hansen on 2014-01-18
Ok I did "ps aux" in the console, and it says that NetworkManager is running. But now I am back to having wifi that sort of lags, like one third of the times I update a page it takes forever and I have to refresh again to make it behave.

I might try to get the wicd working, and I'll post an update if anything changes.

---

### Post by praseodym on 2014-01-18
Try it again:
```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

### Post by solveig.hansen on 2014-01-18
Hey, I get the same result. 

```
* Restarting Network connection manager wicd                                          [fail] 
```

I tried doing wicd start as root, and I got this, which says me nothing
```

Traceback (most recent call last):
  File "/usr/share/wicd/daemon/wicd-daemon.py", line 1859, in <module>
    main(sys.argv)
  File "/usr/share/wicd/daemon/wicd-daemon.py", line 1708, in main
    os.symlink(dest, backup_location)
OSError: [Errno 17] File exists

```

---

### Post by solveig.hansen on 2014-01-18
Dang, I was googling around and read somewhere that you have to uninstall network manager completely for wicd work. And I did without thinking, and now I get no wifi and no ethernet! Typing this on phone now -.-

How can I get my ethernet working again?

---

### Post by praseodym on 2014-01-18
32 or 64 bit?

---

### Post by solveig.hansen on 2014-01-18
64

---

### Post by praseodym on 2014-01-18
[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.8.0-0ubuntu22_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.8.0-0ubuntu22_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.8.0-1ubuntu5_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.8.0-1ubuntu5_amd64.deb)

Save them in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by solveig.hansen on 2014-01-18
> **praseodym said:**
> [http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.8.0-0ubuntu22_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.8.0-0ubuntu22_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.8.0-1ubuntu5_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.8.0-1ubuntu5_amd64.deb)

Save them in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```


Ok, I got net again via cable, thanks! =)

Still no wifi, and wicd just gives me [fail]. Will be away from computer for a couple of hours. If you or anybody else has any suggestions in the mean time, feel free to spam me! Thanks for the help so far, praseodym :)

---

### Post by praseodym on 2014-01-18
There's a bug with the N-mode of the driver:
```

sudo apt-get remove --purge wicd
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Check:
```

iwconfig
iwlist chan
sudo iwlist scan
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by solveig.hansen on 2014-01-19
> **praseodym said:**
> There's a bug with the N-mode of the driver:
```

sudo apt-get remove --purge wicd
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Check:
```

iwconfig
iwlist chan
sudo iwlist scan
cat /etc/network/interfaces
cat /etc/resolv.conf
```

Hey again! 
I have had a fun day pulling my hair out over this, and I got it solved now. First of all, I got the wicd to work by following this tip [http://askubuntu.com/questions/349952/ubuntu-minimal-wicd-help](http://askubuntu.com/questions/349952/ubuntu-minimal-wicd-help)
But that didn't help my connectivity issue. I tried your suggestion witht the N-mode, but it changed nothing. What solved it for me was to set the router to use WPA (1 or 2 both works) in stead of WEP which it was set to. I didn't think to try this, since it had been working up til this point, and no changes had been made to the router. But I kept reading different places that linux wifi drivers didn't like WEP that much (can't find the sources now, unfortunately), so I tried changing and eureka...

So thanks for your input and time, I learned a lot at least =)

---

