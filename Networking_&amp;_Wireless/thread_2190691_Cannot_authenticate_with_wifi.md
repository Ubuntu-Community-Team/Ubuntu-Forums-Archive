---
title: "Cannot authenticate with wifi"
date: 2013-11-28
forum: Networking &amp; Wireless
---

### Post by waitingroomsnap on 2013-11-28
Hello,

I'm currently traveling and am at a friend's apartment.  I'm running ubuntu 13.10 on my laptop and it will not authenticate with the wifi network.  My phone works fine, and other folk's devices and laptops connect without any issues.  I enter the wifi password, but the enter password dialog box just pops up again after 5-10 seconds.  I've looked around other threads that have reported similar problems, but I don't really follow all the commands and such, and am not sure that my problem is the same.  Because of this I am posting a new thread for hopes of assistance.

From reading the other threads I'm thinking that the following commands may be helpful, so am posting the corresponding outputs

```
sudo lshw -C network
```

[ATTACH]248167[/ATTACH]

```
iwlist scan
```

[ATTACH]248168[/ATTACH]

The place is in an apartment building and there are a lot of wifi networks.  I actually had to delete a large amount of them from the iwlist scan, as the file was too big for the txt file size limit.  I was wondering if that could be the issue, with so many networks around, but again, no else has any problems connecting to the wifi.  In the iwlist scan, the network I am trying to connect to is Cell 08: Home-6B82.  It is also one of those wireless router boxes directly from comcast, and I don't think I am able to change the settings, or shouldn't since its not my place.

If there is any other commands that are needed to troubleshoot this, please let me know.  Thanks!

---

### Post by Bucky Ball on 2013-11-28
What about:

```
iwconfig
```

You might also want to try adding the wireless connection details manually by setting up wireless in Network Manager.

---

### Post by waitingroomsnap on 2013-11-28
here is iwconfig
```
usb0      no wireless extensions.

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off



```

Is network manager different than this Network Connections thing that opens when I click on "edit connections" from the menu bar?

---

