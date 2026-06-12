---
title: "[SOLVED] Fix for flaky Intel N-6205 Wifi (wlp3s0) in 20.04 Focal"
date: 2020-04-21
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2020-04-21
IF YOU HAVE A SIMILAR ISSUE, SEE MY POST (#3) Where if figured out that my router settings and Ubuntu 20.04 at least with my hardware, were not being nice at the party together.  

I had been using Ubuntu 18.04 for a long time on a first gen carbon X1 and the wifi was rock stable with it and Windows 10, and also with my initial install of 20.04, but during the last few updates, it would cut in and out and be really slow at times, then it would just not reconnect after a sleep.  Currently using 5.4.0-26-generic

**EDIT: this only marginally helped:**
This added to a file created in /etc/modprobe.d/iwlwifi-opt.conf:

```
options iwlwifi remove_when_gone=1 swcrypto=1 bt_coex_active=0 power_save=0 11n_disable=1
```

The posts I found these options in varied and suggested I just needed to modprobe -r and modprobe the module but I had mixed results, but only a reboot "fixed" it.

This technically disables n in the card's ability to communicate.  And yes, my speed using 20.04 is slower than it is in 18.04.  Perhaps this will get fixed but of one does some research, apparently the Intel cards in particular seem to have their ups and downs with stability depending on the kernel version  I found stuff going all the way back to 2014.  I tried "replacing" the firmware file for my particular card in /lib/firmware from Intel's site and it didn't really make any kind of noticeable difference.

---

### Post by jeremy31 on 2020-04-22
Interesting, please post results for ```
grep [[:alnum:]] /sys/module/iwlwifi/parameters/*; cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by maestrobwh1 on 2020-04-24
IF YOU HAVE THIS ISSUE: the only thing that may help is manually setting your router channel (if it has dynamic channel selection).  And if it is a 2.4/5 GHz, connect to the higher frequency band 5GHz

After being terribly  frustrated with this, because it is rock solid in Ubuntu LTS 18.04.3 (or 4?) but it is running the hardware stack so the kernel is 5.4, I did some more digging.  For some reason, this particular 20.04 does not play well with my Apple Airport Extreme.  I connected to "simpler" devices, like a Win 10 desktop machine enabled as a hot spot, and my phone enabled as a hot spot and it was super stable.  I kept seeing this particular card kept having issues with "n" enabled, so disabling it helped and that is only the partial picture I think.  I was still having a lot of problems with 20.04, but only that.  Other distributions and Windows 10 were fine on this machine.  One post somewhere caught my eye, and it had to do with someone who traveled a lot and only certain places had the same issue with his Intel Wifi card. 

I tired a few USB wifi adapters and rmmod'ed the intel drivers and I still experienced some instability but only with my Airport Extreme (a,b,g,n) wifi router.  Not connected to hotspots... BUT THIS ONLY HAPPENS WITH Ubuntu 20.04, not with other devices or OS's.

I logged into my Airport Extreme, gave the 5 GHz band it's own name and manually set the channel to like 48.  I also set the 2.4 GHz channel to 1 (my reading of routers and bands pointed me into the channels that would have the least interference).  

BAM.  Super stable after connecting to the 5 GHz only band WITHOUT the file (and thus the options) in my first post.  

My hypothesis is that there is something different about how 20.04 uses the intel wifi driver, (or perhaps it is network-manager thing) when it is connecting to a router that has its channel set to "dynamic."

Again, nothing else acted this way, even the same machine, with other operating systems (other 'nixes including 18.04 with the "same" kernel 5.4, and Windows 10)

To further this testing, I have an identical X1 Carbon with the same card, so I installed 20.04, it was good after the first boot, then I did an apt upgrade, rebooted and the wifi was up and down and off and on. and same deal, EVEN WHEN 3 FEET FROM THE WIFI ROUTER, or 15 feet.  

I have a working machine for 20.04 so I am good, but as you requested:

```
$ grep [[:alnum:]] /sys/module/iwlwifi/parameters/*; cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/amsdu_size:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/disable_11ac:N
/sys/module/iwlwifi/parameters/disable_11ax:N
/sys/module/iwlwifi/parameters/enable_ini:N
/sys/module/iwlwifi/parameters/fw_monitor:N
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/lar_disable:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/power_level:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/remove_when_gone:N
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/uapsd_disable:3
[connection]
wifi.powersave = 3
```

---

### Post by jeremy31 on 2020-04-24
If you want to try something do
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi-opt.conf
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

