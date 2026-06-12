---
title: "Troubleshooting wlan: is mine borked?"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by PenguinLust on 2014-08-02
My wlan is having trouble connecting to the router, and I think it might be broken (it's a bit old and it didn't work so well under my last openSUSE installation). How can I make sure before I go and spring for a new one?
The driver is rt61pci (it used to work w/that module). I've looked in dmesg and get something like:
```
wlan0: Trigger new scan to find an IBSS to join
[I]repeat 2x
[/I]wlan0: Create new IBSS network, BSSID *blah*
IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready (*I don't know why it's doing this. I explicitly disabled IPv6*)
wlan0: No activre IBSS STAs - trying to scan for other IBSS neworks with same SSID (merge)
IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```
And it acts the same way if I set the mode to "Infrastructure" or "Ad-hoc"
The thing is, it's able to detect the router, but when I try to connect, it times out. The above results were when the router has no security, however, when I do encrypt the wireless traffic, the problem isn't any better (it acts like I gave the wrong password.)

My Ubuntu is 14.04 and I'm running on an AMD64.

---

### Post by varunendra on 2014-08-04
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

