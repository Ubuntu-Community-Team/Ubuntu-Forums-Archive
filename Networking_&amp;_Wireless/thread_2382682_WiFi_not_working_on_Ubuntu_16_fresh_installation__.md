---
title: "WiFi not working on Ubuntu 16 fresh installation | Intel Dual Band Wireless-AC 3165"
date: 2018-01-16
forum: Networking &amp; Wireless
---

### Post by apanek on 2018-01-16
Hi,
I've just installed fresh Ubuntu 16 on my Lenovo Y520-15 alongside Windows 10. WiFi works perfectly fine on Windows, but when I was installing Ubuntu there were no available WiFi connections. I thought it'll install itself with Ubuntu, so I proceeded the installation. However, WiFi still doesn't work. I have Intel Dual Band Wireless-AC 3165 Plus Bluetooth, I've tried copying firmware from Intel site into /lib/firmware but it doesn't work. I also looked at this solution: [https://codeyarns.com/2017/02/04/how-to-make-intel-wireless-ac-3165-work-in-ubuntu/](https://codeyarns.com/2017/02/04/how-to-make-intel-wireless-ac-3165-work-in-ubuntu/) but my kernel is 4.10.0-28-generic so the newest one I think (?)
Well, I have no idea what else can I do to make this work. Do you have any ideas?

---

### Post by chili555 on 2018-01-16
Let’s do some diagnostics to see why it isn’t working as expected. Please open the terminal and run and post:```
dmesg | grep iwl
rfkill list all
```

---

### Post by apanek on 2018-01-16
Hi, so it's the output:

```

~$ dmesg | grep iwl
[   12.909036] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-26.ucode failed with error -2
[   12.909046] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-25.ucode failed with error -2
[   12.966829] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[   12.966838] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[   13.225959] iwlwifi 0000:03:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[   13.236955] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   13.239262] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   13.239703] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   13.307926] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   13.726987] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0

```



```
~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2018-01-16
> 0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]Let me just predict the next three or four posts here:

* Chili: "Hard blocked usually means that the hardware switch, key combination, sometimes called airplane mode switch, is set to disable the wireless. Find it and switch it."

* Apanek: "But Chili, I have pushed the button fifty times and it makes no change. The wireless is *still *hard blocked."

* Chili: "Let's try another technique. Please open a terminal and do:

```
sudo modprobe -r ideapad-laptop
```Does your wireless work now?"

* Apanek: "Wow! It's working! How can we make this permanent?"

* Chili: "Please open a terminal and do:```
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```You should be all set."

* Apanek: "Awesome! It's working perfectly now."

Am I right or am I right??

---

### Post by apanek on 2018-01-16
Haha yes, you're perfectly right. I've visited some similar threads and tried to push the mentioned button but it haven't worked. Thank you so much kind soul, that's the power of open source, love ya :)

---

### Post by chili555 on 2018-01-16
Awesome! Glad it's working. Have fun!

---

