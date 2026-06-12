---
title: "Download speed : 5 Mb/s VS 11 Mb/s in W10"
date: 2019-05-12
forum: Networking &amp; Wireless
---

### Post by Draky on 2019-05-12
Hello.

I have a dual boot on Windows 10 and Ubutnu 19.04

Download speed in every software :

- Ubuntu = about 5 Mb/s

- Windows 10 = about 11 Mb/s

300 Mb/s fiber at home, download with Wi-Fi only on notebook.

Any explanation or solution ?

lspci gives :

```
0c:00.0 Network controller: Intel Corporation WiFi Link 5100
```

Thanks.

---

### Post by TheFu on 2019-05-12
Drivers and driver configuration matters. So does the router and wifi capabilities of the router.
**sudo lshw -C network** will show the detailed information needed to check some things.

The Intel 5100 is from 2009 or earlier, so it doesn't have the newer wifi protocol support and is very much impacted by the number of devices nearby, connected or not.

If the router is setup to work with B, G, and N, then the speeds will be much slower and the slowest connection will limit all the others.
If the frequency that the router is using is being used by someone else or even overlapping, that will slow down connections.  Every year, it is worth checking all the frequencies in use nearby and picking the empty one that doesn't overlap with any others.  For 2.4 Ghz, that means using channels 1, 6, 11 for most of the world. Japan has another legal channel. If the local area has lots of wifi networks, there might not be any choice other than using a channel that overlaps with the least bad choice.  Many routers have a way to see nearby networks. Don't assume the automatic choice is actually the best choice.

Anyways, we aren't there and can't know what is happening.  All we can do it look at the driver for the wifi chip used.

A prior thread about this [https://ubuntuforums.org/showthread.php?t=1349271](https://ubuntuforums.org/showthread.php?t=1349271)

[https://askubuntu.com/questions/66810/very-slow-connection-on-an-intelr-wifi-link-5100-agn](https://askubuntu.com/questions/66810/very-slow-connection-on-an-intelr-wifi-link-5100-agn) has a solution that worked long ago.      Create a file **/etc/modprobe.d/intel_11n_disable.conf** containing:

```
    options iwlwifi 11n_disable=1
```
In theory, removing and reloading the iwlwifi driver should be all that is needed. One person reported that a reboot was required.  That would be **sudo rmmod iwlwifi** then **sudo modprobe iwlwifi**
If that isn't sufficient, do these too:
```
    sudo update-initramfs -u
```
```
    reboot
```

---

### Post by Draky on 2019-05-30
1st, thanks and sorry for the delay.

I have testeed nearly all, disabling "N" support, blacklisting and so...

No change in fact : still "slow".

Thanks again for pointing those webpages.

---

