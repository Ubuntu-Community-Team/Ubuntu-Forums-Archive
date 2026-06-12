---
title: "Intel Centrino Wireless-N 1030 Issues"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by Elliot_Berg on 2015-03-08
Hi,

I've got an irritating issue with my Intel Centrino Wireless-N 1030 [Rainbow Peak] - I don't think I'm alone in this, but none of the other 'solutions' I've seen quite work for me. I use this card for both the Bluetooth and WiFi - when I have bluetooth disabled, and use the card at N speeds, it's incredibly quick and I don't have any issues. However, if I enable the bluetooth (I use it to play music to a stereo system primarily), the WiFi becomes unusable. It doesn't completely drop, but it does do what everyone else suggests and drop down to 1Mb/s (sometimes fluctuates between that and 6Mb/s) - and some things will just time out, others will load very slowly. At the moment I've done what a few people suggest, and disabled N on the card - this means I can use the WiFi and Bluetooth at the same time, but the WiFi is really slow, so it's not a long term solution.

I need to use both the WiFi, and the Bluetooth, and I don't have enough spare USB ports on my laptop to leave either a USB Bluetooth or WiFi adapter connected constantly - so I'd appreciate any help in making both usable. I should clarify that I use this laptop in quite a few places, and have the same issue everywhere - I've also used a different wireless N access point at home, in order to prove it's the laptop. When my laptop plays up, other devices (e.g. my phone) work fine, so I'm certain it's an issue with the laptop - however it doesn't seem to be an issue when in Windows. This leads me to assume that (as everyone else suggests) it's a driver issue, but I appear to be running the latest one - I was wondering if I could use something like Ndsiwrapper and try the Windows drivers, but couldn't see how to extract the driver from the Windows installation packages (possible I'll be able to steal it from the Windows system?)

Thanks in advance,

Elliot

---

### Post by jeremy31 on 2015-03-08
Lets see what your current parameters are ```
for p in /sys/module/iwlwifi/parameters/*; do echo $p; cat $p; done
```

---

### Post by Elliot_Berg on 2015-03-08
Thanks for the speedy reply - output below;

```
/sys/module/iwlwifi/parameters/11n_disable
1
/sys/module/iwlwifi/parameters/amsdu_size_8K
0
/sys/module/iwlwifi/parameters/antenna_coupling
0
/sys/module/iwlwifi/parameters/bt_coex_active
Y
/sys/module/iwlwifi/parameters/fw_restart
Y
/sys/module/iwlwifi/parameters/led_mode
0
/sys/module/iwlwifi/parameters/nvm_file
(null)
/sys/module/iwlwifi/parameters/power_level
0
/sys/module/iwlwifi/parameters/power_save
N
/sys/module/iwlwifi/parameters/swcrypto
0
/sys/module/iwlwifi/parameters/wd_disable
1

```

---

### Post by jeremy31 on 2015-03-08
You can try editing the file ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
``` and change it from ```
options iwlwifi 11n_disable=1
``` to ```
options iwlwifi 11n_disable=8
``` save and exit program and disabling bt_coex might help so ```
echo "options iwlwifi bt_coex_active=N" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

Reboot and see if it works, there are times that turning off bt_coex causes issues, if it does edit the file and delete the line ```
options iwlwifi bt_coex_active=N
``` reboot again

---

### Post by Elliot_Berg on 2015-03-08
Hi,

I'll give both a try separately - what do they actually do, though? Apologies if this is documented somewhere!

Elliot

---

### Post by jeremy31 on 2015-03-08
> **Elliot_Berg said:**
> Hi,

I'll give both a try separately - what do they actually do, though? Apologies if this is documented somewhere!

Elliot
You can turn 11n back on on the router and see if the 11n_disable=8 makes it work correctly with 11n .  The command enable agg tx for the card and can really speed it up, bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630)

And the bt_coex_active doesn't always work as expected and it might be improved on in newer kernels.  We know it didn't work as expected(allowing bluetooth to work with wifi and not interfering) so we might as well try it being disabled

---

### Post by Elliot_Berg on 2015-03-08
Great - the first on it's own didn't seem to help (still dropped to 1Mb/s and didn't do much), but the second seems to have helped. Is there any reason not to leave the first option enabled (i.e. try the bt_coex config without touching the N stuff), if it seems to be working? I'll have to leave it for a couple of days and make sure it behaves, but this certainly looks good - it was happening almost constantly, and hasn't at all since adjusting that config. I still seem to have a high (and constantly climbing) 'Invalid misc' number on the card - the laptop's only been up 6 minutes and it's already at 319. I forgot to mention that earlier, but it's happened for as long as I can remember- is that anything to worry about, if it seems to be working?

---

### Post by jeremy31 on 2015-03-08
I see the invalid misc too but it happens on all my machines with different wifi cards, already at 122 on an atheros and I haven't looked into what might cause it but I don't think it affects anything

If you leave your router with 11N disabled, there is no need to change the 11n_disabled parameter from 1 and it could be at 0 will no ill effect

---

### Post by Elliot_Berg on 2015-03-08
Weird! I never disabled N on the router, only on the NIC on my laptop - but I think I'll leave it all as-is for now, as it seems to be happy. I'll leave it for a couple of days and then report back - thanks!

---

### Post by jeremy31 on 2015-03-08
> **Elliot_Berg said:**
> Weird! I never disabled N on the router, only on the NIC on my laptop - but I think I'll leave it all as-is for now, as it seems to be happy. I'll leave it for a couple of days and then report back - thanks!

I must have misunderstood about disabling it on the router

---

### Post by Elliot_Berg on 2015-03-09
Been using it all day yesterday, and all evening today - not a single issue. Problem solved...thanks!

---

