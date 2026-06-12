---
title: "best half size mini pci-e wifi card"
date: 2016-10-02
forum: Networking &amp; Wireless
---

### Post by MarcSN on 2016-10-02
Hello,    

I am currently using an Intel Centrino 6235 half size mini pci-e Wireless card in my notebook.  

Using iperf I measured a throughput of about 75Mbit/s in a 5GHz network.  
Using the exact same hardware under Windows 8.1 I reach a throughput of 190Mbit/s. 

 Can anyone recommend a wireless card (preferably with Bluetooth support)  that is able to reach at least the 190Mbit/s i get using Windows, or maybe even more?  

Regards,  
Marc

---

### Post by jeremy31 on 2016-10-02
I would try disabling IPv6 in Network Manager for the connection and ```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlopt.conf
```
Reboot and see if it gets better as the 11n_disable=8 actually enables aggressive TX and it should help performance

---

### Post by MarcSN on 2016-10-02
Hi!

I already have 11n_disable=8 set:

```

 marc@marc-zenbook~ for p in /sys/module/iwlwifi/parameters/*; do echo $p; cat $p; done
/sys/module/iwlwifi/parameters/11n_disable
8
/sys/module/iwlwifi/parameters/amsdu_size_8K
0
/sys/module/iwlwifi/parameters/antenna_coupling
0
/sys/module/iwlwifi/parameters/bt_coex_active
N
/sys/module/iwlwifi/parameters/d0i3_disable
Y
/sys/module/iwlwifi/parameters/fw_monitor
N
/sys/module/iwlwifi/parameters/fw_restart
Y
/sys/module/iwlwifi/parameters/lar_disable
N
/sys/module/iwlwifi/parameters/led_mode
0
/sys/module/iwlwifi/parameters/nvm_file
(null)
/sys/module/iwlwifi/parameters/power_level
0
/sys/module/iwlwifi/parameters/power_save
N
/sys/module/iwlwifi/parameters/swcrypto
1
/sys/module/iwlwifi/parameters/uapsd_disable
Y

```

Disabling IPv6 got me up to around 82Mbit/s but still nowhere near 190Mbit/s.

Regards,

Marc

---

### Post by kurt18947 on 2016-10-02
You might try setting a country code if you haven't done so. I have a Centrino Advanced-N 6200 (rev 35) card and setting the country code bumped the speed shown in iwconfig from around 60-80 mb. to 180. I had already made the changes to iwlwifi.conf in /etc/modprobe.d/iwlwifi.conf.

Instructions for checking and setting the country code can be found here:

[https://ubuntuforums.org/showthread.php?t=2304607](https://ubuntuforums.org/showthread.php?t=2304607)   post #5.  Ignore the rtlwifi related stuff.

Here is the line I added to the end of the iwlwifi.conf file:

```
options iwlwifi bt_coex_active=1 swcrypto=1 11n_disable=8
```

I played around a bit with different settings and the above seemed to yield the best throughput.

---

