---
title: "wireless disabled on boot, but enables after wake from suspend"
date: 2017-04-11
forum: Networking &amp; Wireless
---

### Post by jordan-mccrone on 2017-04-11
I am using the wl driver for a BCM4313 wireless card. A strange thing started happening, and out of nowhere. The wifi is disabled when I boot into ubuntu 16.04, 14.04, or windows 10. The only way I've been able to get it back on is by suspending the computer from ubuntu, and then waking it. After doing this, the wifi works magically.

Here is the outputs of "rfkill list" before and after suspend.

Before:

```
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
1: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: yes
2: hci0: Bluetooth
Soft blocked: yes
Hard blocked: no

```

After resuming from suspend, the line above that previously read "Hard blocked: yes" changes to "Hard blocked: no" 
When I use the keyboard to disable/enable Wifi (Fn-F12 shortcut), all "Soft blocked" values in rfkill toggle to yes or all to no.
Note that I have had this laptop for over 4 years and disassembled it many times. I am 100% certain there is no hard switch, and I triple checked again, despite my intimate relationship with my laptop, before posting to ensure that's the case.

I also tried this:
```

rmmod wl
modprobe wl
```

but doesn't seem to do anything.

Also, the bluetooth works.

I should note that under no circumstances am I able to get the wifi card working in windows 10. In windows 10 I tried various iterations of uninstalling driver, disabling wifi, and rebooting to no avail.

Lastly, the wifi does not work from an ubuntu LiveCD. I'm unable to resume from suspend under a live environment, so who knows if my usual fix would work in that situation.

Thanks in advance!

---

### Post by jordan-mccrone on 2017-04-24
Bump.

---

### Post by chili555 on 2017-04-24
May we please see:```
lspci -nnk | grep -i 14e4 -A3
```We wonder if bcmwl-kernel-source is correct for your device.

---

### Post by jordan-mccrone on 2017-04-25
Here is the output:
```

07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    DeviceName: Valentine 802.11bgn/BT 4.0 Combo
    Subsystem: Hewlett-Packard Company BCM4313 802.11bgn Wireless Network Adapter [103c:1795]
    Kernel driver in use: wl
```

---

### Post by Hadaka on 2017-04-25
Hi,It appears Dr. Chili555 was correct in thinking wl may not be the best driver for your wifi card.
Please open a terminal ctrl/alt/t then Copy and paste one
line at a time...
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -v brcmsmac
```
After the commands are complete, please
boot and test wireless.

---

### Post by jordan-mccrone on 2017-04-27
I performed the above steps, and after rebooting this was my output of the lspci command:

```
lspci -nnk | grep -i 14e4 -A3
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    DeviceName: Valentine 802.11bgn/BT 4.0 Combo
    Subsystem: Hewlett-Packard Company BCM4313 802.11bgn Wireless Network Adapter [103c:1795]
    Kernel driver in use: bcma-pci-bridge
```

Unfortunately, this did not fix the problem. Wireless was still disabled on boot, and then after resuming from suspend it was on again.

I should note that I have intentionally been using the wl driver since 12.04 on this laptop, because the bcma-pci-bridge driver has always had significant problems. I was hoping that maybe something had changed since the last time I tried that driver, but it still gives frequent signal drops, has poor range, and even when I'm right next to the router I get sporadic throughput performance. So I have now switched back to using the wl driver.

Also, the wl driver was serving me perfectly well on my current 16.04 install until just a few weeks ago when this issue began.

If you have any other suggestions please let me know. In the meantime, I'll try to find changelogs to see if there was an update to the driver, and if so compile and install an earlier version.

---

### Post by jordan-mccrone on 2017-05-31
I never got around to performing the above items that I planned to in post #6, but the issue has fixed itself out of nowhere. I have barely used the laptop since posting this, and just the other day all of the issues I had been having disappeared!

---

### Post by Hadaka on 2017-05-31
Hi, Glad you now have wireless !
Please take the time to mark your thread
solved by clicking Thread Tools and then Solved
Thanks.

---

