---
title: "WiFi sometimes fails to start (Dell M3800, Intel 7260 AC)"
date: 2015-10-31
forum: Networking &amp; Wireless
---

### Post by Scott Deagan on 2015-10-31
Hi,

On my Dell M3800 running Ubuntu 15.10, my WiFi sometimes fails to start. I also lose my wifi when my laptop wakes from hibernation (e.g. when I close the lid, then re-open the lid). I didn't have this problem when running Ubuntu 15.04.

Here is my dmesg output:

[FONT=courier new]scott@m3800:~# dmesg | grep -i iwl
[    8.241025] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    8.244502] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[    8.244522] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2
[    8.248041] iwlwifi 0000:06:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    8.270367] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.270448] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    8.270728] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   12.513593] iwlwifi 0000:06:00.0: Failed to run INIT ucode: -110
[   12.513627] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled


If I unload and reload the wireless module using:

sudo rmmod iwlmvm && sudo modprobe iwlmvm

then the wifi will successfully connect to my router. I can also put the above in to my /etc/rc.local, and while this will guarantee my wifi will always start when I boot the laptop, it doesn't solve the problem of the wifi disappearing after waking from hibernation. 

Because I can start my wifi using the terminal, this problem is more of a nuisance than show stopper, but I'd still like to know how to fix it so the wifi works as it should (i.e. starts when I boot, and re-starts after waking from hibernation).

Thanks.

[/FONT]

---

### Post by chili555 on 2015-11-01
The first thing I'd suggest is the latest version of the firmware. First, download this file to your desktop: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz) Right-click each and select 'Extract Here.' Now, in a terminal:

```
cd ~/Desktop/iwlwifi-7260-ucode-15.227938.0
sudo cp iwlwifi*  /lib/firmware
```Reboot and tell us if the symptoms are the same. Also post:```
dmesg | grep iwl
```

---

### Post by Scott Deagan on 2015-11-01
Thanks chili555. Your suggestion definitely solved the issue with the wifi not starting when I boot my laptop (it's also good to know where to obtain the Linux module for the Intel 7260). It has also half solved the issue I've had with wifi not springing back to life when I open the lid (after hibernation/sleep mode) - the wifi now starts up every second time I open the lid.

Output from [FONT=courier new]dmesg | grep -i iwl[/FONT] after starting up then waking from sleep:

```

[    8.085252] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    8.098626] iwlwifi 0000:06:00.0: loaded firmware version 15.227938.0 op_mode iwlmvm
[    8.124955] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.125029] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    8.125290] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   12.547063] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   12.548262] iwlwifi 0000:06:00.0 wlp6s0: renamed from wlan0
[   13.268739] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   13.268985] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   13.464119] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   13.464384] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled

```

---

### Post by chili555 on 2015-11-01
Awesome! Glad it's mostly working.

Please see this suggestion for the suspend issue: [http://ubuntuforums.org/showthread.php?t=2220294&p=13043389#post13043389](http://ubuntuforums.org/showthread.php?t=2220294&p=13043389#post13043389)

---

