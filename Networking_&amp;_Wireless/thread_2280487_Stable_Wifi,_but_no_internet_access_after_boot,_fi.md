---
title: "Stable Wifi, but no internet access after boot, fixable by manual reconnect"
date: 2015-05-31
forum: Networking &amp; Wireless
---

### Post by ben-8409 on 2015-05-31
Hello!

I have strange problem with the internet connection that actually appeared around the switch to systemd on Ubuntu 15.04 beta. Didn't have the time to look into this until now and it appears i the similar issue on another device running ubuntu 15.04 now.

here  is what happens: when i start ubuntu 15.04, and log it, my wifi gets connected instantly  and i actually have an internet connection (for some seconds sometimes,  at other times, it's there for some milliseconds so dropbox starts  syncing, but never syncs a single file). 

after that, network manager  stills shows i am connected to the wifi, but i cannot access the  internet any more.


  i then disconnect the wifi manually, wait some seconds and reconnect. that fixes the problem until the next reboot.


  here are some additional observations: 

[LIST]
[*] the problem appeared on my desktop during 15.04 beta, possibly after the switch to systemd.
[*]it also appeared on a thinkpad after upgrading to 15.04 when it was released
[*]both use a intel wifi chip - no issues with wifi on either windows nor mac or any other devices
[*]there is a bug in ubuntu launchpad, but not much activity and possibly related to wrong software component
[*]the problem does not appear after suspend
[/LIST]

---

### Post by praseodym on 2015-05-31
Please run the wireless-script from the stick-thread and show the output

---

### Post by ben-8409 on 2015-06-01
Thank you, here is the result of wireless-info: [ATTACH]262351[/ATTACH]

---

### Post by praseodym on 2015-06-01
First: Deactivate the power management of the driver:
```

sudo iwconfig wlan1 power off
```
If it is not enough, also deactivate the N-mode and the queue:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Deactivate IPv6 in the NM profile and set the channel "fixed" in the 5 GHz band

---

### Post by ben-8409 on 2015-06-02
Hello praseodym,

thanks fpr your suggestions. But as mentioned, the wifi is stable but does not connect after a reboot. As far as i know, setting the powermanagement off with iwconfig is not persistent.
Could you explain why you think that could be helping?

---

### Post by praseodym on 2015-06-02
With the PM "off" the card will get full current to connect. Can you show the results of the wireless-script after it is not working?

---

### Post by ben-8409 on 2015-06-03
thanks very much for you help. i "fixed" it by a clean install of ubuntu 15.04. strange anyways. there are several people in this bug report [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986) reporting similar issues after updating.
we have another pc affected by a similar problem. i will try to run the wireless-script there as well, as soon i have the time to do so.

thanks again!

---

