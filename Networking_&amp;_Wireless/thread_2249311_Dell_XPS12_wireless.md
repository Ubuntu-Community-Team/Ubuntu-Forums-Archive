---
title: "Dell XPS12 wireless"
date: 2014-10-21
forum: Networking &amp; Wireless
---

### Post by pmb2 on 2014-10-21
Hi, I can't get the wireless to work on XPS12. In the menu it appears as "Wi-Fi is disabled by hardware switch"

```
rfkill list
``` shows phy0 as Hard blocked: yes

I think wireless LAN was disabled on Windows when I installed Ubuntu, but airplane mode (a separate setting) was not on. 

I have tried many things, none of which work.
- Hit Fn-F2 (airplane mode switch)
- Alt-Fn-F2, Fn-F8, other combos
- rmmod dell_laptop then Fn-F2, etc
- rmmod dell_wmi too, then Fn-F2, etc
- Drain the battery. There's no way to remove the battery
- Reset BIOS to default settings

If I use an external USB WiFi card and remove the module for the internal one, then it works, but it fails after about 5 minutes; probably an unrelated problem.

Any more things I can try? I can't easily get windows back, because I removed the system restore partition. (how f'ing stupid is it to not include install media any more. I have a DVD for windows 7 though, as a last resort)

---

### Post by jeremy31 on 2014-10-21
Try the rmmod commands again, but after do ```
sudo rfkill unblock all
```

What is the wifi card ```
lspci -nnk | grep -iA2 net
```

---

### Post by pmb2 on 2014-10-21
Thanks, but no luck on this one:
```

fa2k@electron:~$ sudo rfkill list 
[sudo] password for fa2k: 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
fa2k@electron:~$ sudo modprobe -r dell_laptop
fa2k@electron:~$ sudo rfkill list 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
fa2k@electron:~$ sudo modprobe -r dell_wmi
fa2k@electron:~$ sudo rfkill unblock all
fa2k@electron:~$ sudo rfkill list 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: nfc0: NFC
    Soft blocked: no
    Hard blocked: no

```

---

### Post by jeremy31 on 2014-10-21
Do you have lspci results too? ```
lspci -nnk | grep -iA2 net
```

---

### Post by pmb2 on 2014-10-21
Sorry, forgot
```

06:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
    Kernel driver in use: iwlwifi

```

---

### Post by jeremy31 on 2014-10-21
Follow the instructions to download and run the wireless script and attach resulting file
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by pmb2 on 2014-10-21
[ATTACH]257419[/ATTACH]

Here you go :)

Btw, the reason I'm running the beta is that it didn't work on 14.04

---

### Post by jeremy31 on 2014-10-21
Strange that nothing shows up in dmesg about firmware being loaded.  Is this the original wifi card?
We could unload the driver then load it and check for errors ```
sudo modprobe -r iwlwifi
``````
sudo rfkill unblock all
``````
sudo modprobe iwlwifi
``````
cat /var/log/syslog | tail -30
```

---

### Post by pmb2 on 2014-10-21
Here's the output:

```

fa2k@electron:~$ sudo modprobe -r iwlwifi
[sudo] password for fa2k: 
fa2k@electron:~$ sudo rfkill unblock all
fa2k@electron:~$ sudo modprobe iwlwifi
fa2k@electron:~$ cat /var/log/syslog | tail -30
Oct 21 16:47:44 electron NetworkManager[925]: <info> WiFi now enabled by radio killswitch
Oct 21 16:47:59 electron kernel: [   65.349282] cfg80211: Calling CRDA to update world regulatory domain
Oct 21 16:47:59 electron kernel: [   65.354345] Intel(R) Wireless WiFi driver for Linux, in-tree:
Oct 21 16:47:59 electron kernel: [   65.354348] Copyright(c) 2003- 2014 Intel Corporation
Oct 21 16:47:59 electron kernel: [   65.354985] iwlwifi 0000:06:00.0: irq 62 for MSI/MSI-X
Oct 21 16:47:59 electron kernel: [   65.355837] iwlwifi 0000:06:00.0: loaded firmware version 23.214.9.0 op_mode iwlmvm
Oct 21 16:47:59 electron kernel: [   65.365500] cfg80211: World regulatory domain updated:
Oct 21 16:47:59 electron kernel: [   65.365503] cfg80211:  DFS Master region: unset
Oct 21 16:47:59 electron kernel: [   65.365504] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Oct 21 16:47:59 electron kernel: [   65.365506] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 21 16:47:59 electron kernel: [   65.365508] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 21 16:47:59 electron kernel: [   65.365509] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 21 16:47:59 electron kernel: [   65.365510] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 21 16:47:59 electron kernel: [   65.365511] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 21 16:47:59 electron kernel: [   65.368798] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
Oct 21 16:47:59 electron kernel: [   65.369130] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
Oct 21 16:47:59 electron kernel: [   65.370615] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
Oct 21 16:47:59 electron kernel: [   65.388355] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Oct 21 16:47:59 electron NetworkManager[925]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/ieee80211/phy0/rfkill2) (driver iwlwifi)
Oct 21 16:47:59 electron NetworkManager[925]: <info> WiFi now disabled by radio killswitch
Oct 21 16:47:59 electron NetworkManager[925]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 21 16:47:59 electron NetworkManager[925]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 21 16:47:59 electron NetworkManager[925]: <info> (wlan0): using nl80211 for WiFi device control
Oct 21 16:47:59 electron NetworkManager[925]: <info> (wlan0): driver supports Access Point (AP) mode
Oct 21 16:47:59 electron NetworkManager[925]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Oct 21 16:47:59 electron NetworkManager[925]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 21 16:47:59 electron NetworkManager[925]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 21 16:47:59 electron NetworkManager[925]: <info> (wlan0): bringing up device.
Oct 21 16:47:59 electron NetworkManager[925]: <info> (wlan0): deactivating device (reason 'managed') [2]
Oct 21 16:47:59 electron NetworkManager[925]: <info> NetworkManager state is now DISCONNECTED

```

---

### Post by jeremy31 on 2014-10-21
Hope this works```
sudo ifconfig wlan0 up
```

---

### Post by pmb2 on 2014-10-22
```

fa2k@electron:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

```
I also tried booting with the dell_laptop , dell_wmi or wmi modules blacklisted.

(this is kind of off topic..) I bought a Netgear 300 WLAN dongle, but it had the same problem as the other USB dongle -- worked at first, but slow, then completely stopped working after  ~5min. I then started a windows vm and assigned the dongle to it. Still same problem. I finally found I could use the USB tethering option on my phone, and I'm now on the internet! (there's no ethernet where I am so i need the wifi)

Thanks for all the tips and help jeremy31. It's a weird problem, don't think I'll be able to fix it, but maybe if I find way to boot into windows.

(suppose I could try PCI forwarding (or what it's called) on Qemu too, and try to assign the built in card to windows...)

---

### Post by pmb2 on 2014-10-22
I found that the internal WiFi card works(!!) when I go into suspend mode and then resume. This is a big surprise, and seems like an acceptable solution, and a fantastic improvement. Maybe i should file a bug somewhere though.

---

### Post by jeremy31 on 2014-10-22
> **pmb2 said:**
> I found that the internal WiFi card works(!!) when I go into suspend mode and then resume. This is a big surprise, and seems like an acceptable solution, and a fantastic improvement. Maybe i should file a bug somewhere though.

It would be a good idea

---

### Post by PaulPrice on 2015-01-07
I'm hitting the same problem (with the same workaround: hard blocked on fresh boot, works after suspend) on a Dell Inspiron 3531.  Did you have any luck with the bug report?  Could you please post a link?  And if you have any further information you could share, I would be grateful.

Thanks,

Paul.

---

### Post by PaulPrice on 2015-01-14
Turns out this was a BIOS configuration problem.

We noticed a similar behaviour in Windoze (8.1) --- WiFi would work on a fresh boot, but wouldn't work after suspend.  I discovered that the blue "Fn" key didn't have the expected behaviour in Windoze, e.g., Fn+F2 wouldn't turn the WiFi on/off, Fn+F11 or Fn+F12 wouldn't control the volume, BUT those functions would work without the "Fn" key depressed, e.g., F2 itself turned WiFi on/off, F11 and F12 controlled the volume.  With a bit of help from Google, I found a BIOS setting (Advanced --> Function Key Behavior --> Function Key) that implemented the Correct Behaviour (In the process of debugging this, I updated the BIOS version; I'm not certain I had that choice in the old version, but I probably did).  WiFi now appears to work reliably in both Windoze and Ubuntu, and I can turn it on/off in both with Fn+F2.

---

