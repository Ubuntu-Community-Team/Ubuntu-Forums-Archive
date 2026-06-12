---
title: "Wifi adapter stops working after upgrade to 4.10"
date: 2017-04-08
forum: Networking &amp; Wireless
---

### Post by Forceflow on 2017-04-08
I have a Ubuntu Server installation on a Fujitsu Amilo laptop. The laptop is headless and sits in the basement, connecting to the network by wifi.
In Xenial (Kernel 4.8.x), wifi worked perfectly. After upgrading to Zesty (kernel 4.10), the system says my wifi is hardlocked by a physical switch.

The chip is an Atheros AR2425.
[LIST]
[*]Booting with the 4.8 kernel solves the problem. Wifi light turns on and the device is usable.
[*]There is no hard switch on the laptop device - there used to be a keyboard-based method (FN+F1 to enable/disable wifi, but the keyboard on the laptop has come off (as in: physically detached) and is unavailable.
[*]A simple ```
rfkill unblock all
``` does not unblock the wifi.
[*]I've already tried setting "options ath5k no_hw_rfkill_switch=Y" when booting with the 4.10 kernel, and while that alleviates the problem of the device being hardlocked (rfkill list doesn't list it as blocked anymore), the device is still not usable. iwlist scan delivers no results.
[/LIST]

Here's the wireless info when booted with the 4.8 kernel (and thus working wifi): [https://pastebin.com/1cJa9LL8](https://pastebin.com/1cJa9LL8)
Here's the wireless info when booted with the 4.10 kernel (and thus hard-locked, not working wifi): [https://pastebin.com/qijic47k](https://pastebin.com/qijic47k)

Any ideas? Seems somewhere between kernel versions 4.8 and 4.10, something broke.

---

### Post by Hadaka on 2017-04-08
Hi, as you suggested it is most likely related to the kernel upgrade.
There are a couple things you might try and should be corrected anyway.
There are 2 access points with the same name..If you do not own these ..perhaps the owner can 
give a different SSID to one of them...you are currently connected to the one with the weaker signal
but your dmesg in the wireless report shows that you toggeled between the 2 access points before finally
connecting...
```
SSID                BSSID                              CHAN  FREQ        RATE     SIGNAL  BARS    SECURITY            ACTIVE  *
TelenetWiFree   'TelenetWiFree' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 WPA2 802.1X  no
TelenetWiFree   'TelenetWiFree' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2 802.1X  yes
```
*It is also preferred WPA2 only..not mixed as it is..WPA1 / WPA2
I would suggest removing the command..
```
"options ath5k no_hw_rfkill_switch=Y"
```
and replace with..
```
sudo rm -rf acer_wmi
echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/blacklist-acer_wmi.con
```
*Your country ode is also currently unset and is on defaullt 00, this also can cause issues
please copy and past to correct.. BE    +5050+00420    Europe/Brussels```
sudo iw reg set BE
sudo sed -i 's/=.*/=BE/' /etc/default/crda
```
Boot and test wireles
Thanks.

---

### Post by Forceflow on 2017-04-08
Did all that - thanks for the suggestions.
Still no wifi - it is listed as hard blocked.

Here's an updated wireless-info report: [https://pastebin.com/8X6WibAm](https://pastebin.com/8X6WibAm)

---

### Post by Hadaka on 2017-04-08
You are likely correct with the problem being cause by the kernel, but you
did make some improvements to a couple items. Try your command again
with the updated kernel and the current changes you did and see if that makes
a difference...
```
echo "options ath5k no_hw_rfkill_switch=Y" | sudo tee -a /etc/modprobe.d/ath5k.conf 
```
meantime im going to do some research on that kernel.
thanks..

---

### Post by Forceflow on 2017-04-08
(whoops double post) 

- but thanks for the research man, really appreciate it.

If I blacklist the acer_wmi module though, it also stops working on the older kernel, so I reverted that.

---

### Post by praseodym on 2017-04-09
Reset the BIOS to default settings

---

### Post by Forceflow on 2017-04-10
> **praseodym said:**
> Reset the BIOS to default settings
The BIOS Is a very basic one (only time / boot priority settings), but I've reset it to default - to no avail.

---

### Post by chili555 on 2017-04-10
Hadaka and I want to see:```
cat /etc/modprobe.d/ath5k.conf
lsmod
rfkill list all
```

---

### Post by Forceflow on 2017-04-10
> **chili555 said:**
> Hadaka and I want to see:```
cat /etc/modprobe.d/ath5k.conf
lsmod
rfkill list all
```

This is the output of that:

```
jeroen@hitchens:~$ cat /etc/modprobe.d/ath5k.conf
options ath5k nohwcrypt=1
options ath5k no_hw_rfkill_switch=Y
jeroen@hitchens:~$ lsmod
Module                  Size  Used by
xt_multiport           16384  1
iptable_filter         16384  1
arc4                   16384  2
sparse_keymap          16384  0
ath5k                 147456  0
ath                    28672  1 ath5k
mac80211              782336  1 ath5k
snd_hda_codec_realtek    90112  1
coretemp               16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  0
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
cfg80211              602112  3 mac80211,ath,ath5k
input_leds             16384  0
joydev                 20480  0
serio_raw              16384  0
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
lpc_ich                24576  0
snd_timer              32768  1 snd_pcm
snd                    77824  7 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_generic,snd_hda_codec_realtek,snd_pcm
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
ip_tables              24576  1 iptable_filter
x_tables               36864  3 xt_multiport,ip_tables,iptable_filter
autofs4                40960  2
uas                    24576  0
usb_storage            69632  2 uas
i915                 1449984  1
psmouse               139264  0
ahci                   36864  1
libahci                32768  1 ahci
pata_acpi              16384  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
r8169                  81920  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
mii                    16384  1 r8169
drm                   352256  3 i915,drm_kms_helper
wmi                    16384  0
fjes                   73728  0
video                  40960  1 i915
jeroen@hitchens:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
jeroen@hitchens:~$

```

---

### Post by chili555 on 2017-04-10
>  After upgrading to Zesty (kernel 4.10), the system says my wifi is hardlocked by a physical switch.So that seems to be solved:> jeroen@hitchens:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: noSo you are all set, or is there some other problem?

---

### Post by Forceflow on 2017-04-10
> **chili555 said:**
> So that seems to be solved:So you are all set, or is there some other problem?

Well, that unblocking got solved by adding the ```
options ath5k no_hw_rfkill_switch=Y
``` to the conf file, but the card still doesn't seem to be working. Iwlist scan gives no results, while it does when I boot with the 4.8 kernel.

---

### Post by chili555 on 2017-04-10
Hadaka wants us to review:```
dmesg | grep ath
cat /var/log/syslog | grep -e etwork -e ath | tail -n20
```

---

### Post by Forceflow on 2017-04-11
> **chili555 said:**
> Hadaka wants us to review:```
dmesg | grep ath
cat /var/log/syslog | grep -e etwork -e ath | tail -n20
```

The result voor those is:

```
jeroen@hitchens:~$ dmesg | grep auth
jeroen@hitchens:~$ cat /var/log/syslog | grep -e etwork -e ath | tail -n20
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0142] device (enp2s0): Activation: starting connection 'Wired connection 1' (ce49f05e-8a43-386c-b515-930ce48b6b99)
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0146] device (enp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0150] manager: NetworkManager state is now CONNECTING
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0158] device (enp2s0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0171] device (enp2s0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0279] device (enp2s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0305] device (enp2s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0318] device (enp2s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0328] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 11 20:01:01 hitchens NetworkManager[577]: <info>  [1491933661.0500] device (enp2s0): Activation: successful, device activated.
Apr 11 20:01:05 hitchens NetworkManager[577]: <info>  [1491933665.9823] manager: startup complete
Apr 11 20:01:08 hitchens NetworkManager[577]: <info>  [1491933668.9836] manager: WiFi hardware radio set enabled
Apr 11 20:01:08 hitchens NetworkManager[577]: <info>  [1491933668.9837] manager: WWAN hardware radio set enabled
Apr 11 20:01:10 hitchens kernel: [   42.056115] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap ath5k coretemp ath mac80211 snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel joydev input_leds snd_hda_codec cfg80211 snd_hda_core serio_raw snd_hwdep snd_pcm lpc_ich snd_timer snd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 psmouse ahci libahci pata_acpi i2c_algo_bit drm_kms_helper syscopyarea r8169 sysfillrect sysimgblt mii fb_sys_fops drm wmi fjes video
Apr 11 20:01:10 hitchens kernel: [   42.056207]  warn_slowpath_fmt+0x5f/0x80
Apr 11 20:01:10 hitchens kernel: [   42.056722]  entry_SYSCALL_64_fastpath+0x1e/0xad
Apr 11 20:01:10 hitchens kernel: [   42.193813] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap ath5k coretemp ath mac80211 snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel joydev input_leds snd_hda_codec cfg80211 snd_hda_core serio_raw snd_hwdep snd_pcm lpc_ich snd_timer snd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 psmouse ahci libahci pata_acpi i2c_algo_bit drm_kms_helper syscopyarea r8169 sysfillrect sysimgblt mii fb_sys_fops drm wmi fjes video
Apr 11 20:01:10 hitchens kernel: [   42.193890]  warn_slowpath_fmt+0x5f/0x80
Apr 11 20:01:10 hitchens kernel: [   42.194612]  entry_SYSCALL_64_fastpath+0x1e/0xad
Apr 11 20:01:29 hitchens systemd[1603]: Reached target Paths.

```

---

### Post by chili555 on 2017-04-11
You said:> jeroen@hitchens:~$ dmesg | grep authBut we requested:> dmesg | grep athMay we see ath instead of auth?

In the syslog, we see nothing wrong related to wireless; however we see:> Apr 11 20:01:10 hitchens kernel: [   42.056115] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap ath5k coretemp ath mac80211 snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel joydev input_leds snd_hda_codec cfg80211 snd_hda_core serio_raw snd_hwdep snd_pcm lpc_ich snd_timer snd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 psmouse ahci libahci pata_acpi i2c_algo_bit drm_kms_helper syscopyarea r8169 sysfillrect sysimgblt mii fb_sys_fops drm wmi fjes video
Apr 11 20:01:10 hitchens kernel: [   42.056207]  warn_slowpath_fmt+0x5f/0x80
Apr 11 20:01:10 hitchens kernel: [   42.056722]  entry_SYSCALL_64_fastpath+0x1e/0xad
Apr 11 20:01:10 hitchens kernel: [   42.193813] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap ath5k coretemp ath mac80211 snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel joydev input_leds snd_hda_codec cfg80211 snd_hda_core serio_raw snd_hwdep snd_pcm lpc_ich snd_timer snd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 psmouse ahci libahci pata_acpi i2c_algo_bit drm_kms_helper syscopyarea r8169 sysfillrect sysimgblt mii fb_sys_fops drm wmi fjes video
Apr 11 20:01:10 hitchens kernel: [   42.193890]  warn_slowpath_fmt+0x5f/0x80
Apr 11 20:01:10 hitchens kernel: [   42.194612]  entry_SYSCALL_64_fastpath+0x1e/0xadThese 'modules linked in' messages often follow a kernel oops. [https://en.wikipedia.org/wiki/Linux_kernel_oops](https://en.wikipedia.org/wiki/Linux_kernel_oops) I suggest that you run:```
less /var/log/syslog 
```Using the arrow keys, scroll around near the noted timestamp 20:01:10 and see if you can find, Google and correct whatever went wrong. It probably doesn't have anything to do with wireless, but it's simply better, in my opinion, to correct any faults so that you have a clean, smooth-running system.

---

### Post by Forceflow on 2017-04-11
> **chili555 said:**
> You said:But we requested:May we see ath instead of auth?

In the syslog, we see nothing wrong related to wireless; however we see:These 'modules linked in' messages often follow a kernel oops. [https://en.wikipedia.org/wiki/Linux_kernel_oops](https://en.wikipedia.org/wiki/Linux_kernel_oops) I suggest that you run:```
less /var/log/syslog 
```Using the arrow keys, scroll around near the noted timestamp 20:01:10 and see if you can find, Google and correct whatever went wrong. It probably doesn't have anything to do with wireless, but it's simply better, in my opinion, to correct any faults so that you have a clean, smooth-running system.

My apologies. Here's an updated output.

```
jeroen@hitchens:~$ dmesg | grep ath
[   12.354410]  warn_slowpath_fmt+0x5f/0x80
[   12.541585]  warn_slowpath_fmt+0x5f/0x80
[   19.149930] ath5k 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM cont                                                                                                    rol
[   19.150147] ath5k 0000:08:00.0: registered as 'phy0'
[   19.748341] ath: EEPROM regdomain: 0x30
[   19.748343] ath: EEPROM indicates we should expect a direct regpair map
[   19.748345] ath: Country alpha2 being used: AM
[   19.748346] ath: Regpair used: 0x30
[   19.759987] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   19.764267] ath5k 0000:08:00.0 wlp8s0: renamed from wlan0
[   28.996068] Modules linked in: arc4 sparse_keymap snd_hda_codec_realtek snd_h                                                                                                    da_codec_generic ath5k snd_hda_intel snd_hda_codec coretemp snd_hda_core snd_hwd                                                                                                    ep snd_pcm ath mac80211 joydev input_leds serio_raw cfg80211 snd_timer lpc_ich s                                                                                                    nd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 ahci                                                                                                     psmouse libahci i2c_algo_bit pata_acpi drm_kms_helper syscopyarea r8169 sysfill                                                                                                    rect sysimgblt fb_sys_fops mii drm wmi fjes video
[   28.996122]  warn_slowpath_fmt+0x5f/0x80
[   28.996331]  entry_SYSCALL_64_fastpath+0x1e/0xad
[   29.134323] Modules linked in: arc4 sparse_keymap snd_hda_codec_realtek snd_h                                                                                                    da_codec_generic ath5k snd_hda_intel snd_hda_codec coretemp snd_hda_core snd_hwd                                                                                                    ep snd_pcm ath mac80211 joydev input_leds serio_raw cfg80211 snd_timer lpc_ich s                                                                                                    nd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 ahci                                                                                                     psmouse libahci i2c_algo_bit pata_acpi drm_kms_helper syscopyarea r8169 sysfill                                                                                                    rect sysimgblt fb_sys_fops mii drm wmi fjes video
[   29.134368]  warn_slowpath_fmt+0x5f/0x80
[   29.134651]  entry_SYSCALL_64_fastpath+0x1e/0xad
[   42.304947] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap                                                                                                     snd_hda_codec_realtek snd_hda_codec_generic ath5k snd_hda_intel snd_hda_codec c                                                                                                    oretemp snd_hda_core snd_hwdep snd_pcm ath mac80211 joydev input_leds serio_raw                                                                                                     cfg80211 snd_timer lpc_ich snd soundcore shpchp mac_hid ip_tables x_tables autof                                                                                                    s4 uas usb_storage i915 ahci psmouse libahci i2c_algo_bit pata_acpi drm_kms_help                                                                                                    er syscopyarea r8169 sysfillrect sysimgblt fb_sys_fops mii drm wmi fjes video
[   42.305038]  warn_slowpath_fmt+0x5f/0x80
[   42.305623]  entry_SYSCALL_64_fastpath+0x1e/0xad
[   42.492601] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap                                                                                                     snd_hda_codec_realtek snd_hda_codec_generic ath5k snd_hda_intel snd_hda_codec c                                                                                                    oretemp snd_hda_core snd_hwdep snd_pcm ath mac80211 joydev input_leds serio_raw                                                                                                     cfg80211 snd_timer lpc_ich snd soundcore shpchp mac_hid ip_tables x_tables autof                                                                                                    s4 uas usb_storage i915 ahci psmouse libahci i2c_algo_bit pata_acpi drm_kms_help                                                                                                    er syscopyarea r8169 sysfillrect sysimgblt fb_sys_fops mii drm wmi fjes video
[   42.492683]  warn_slowpath_fmt+0x5f/0x80
[   42.493485]  entry_SYSCALL_64_fastpath+0x1e/0xad
jeroen@hitchens:~$ cat /var/log/syslog | grep -e etwork -e ath | tail -n20
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9312] device (enp2s0): Activation: starting connection 'Wired connection 1' (ce49f05e-8a43-386c-b515-930ce48b6b99)
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9316] device (enp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9319] manager: NetworkManager state is now CONNECTING
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9328] device (enp2s0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9338] device (enp2s0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9436] device (enp2s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9452] device (enp2s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9457] device (enp2s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9460] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 12 02:02:18 hitchens NetworkManager[580]: <info>  [1491955338.9633] device (enp2s0): Activation: successful, device activated.
Apr 12 02:02:23 hitchens NetworkManager[580]: <info>  [1491955343.9831] manager: startup complete
Apr 12 02:02:26 hitchens NetworkManager[580]: <info>  [1491955346.9835] manager: WiFi hardware radio set enabled
Apr 12 02:02:26 hitchens NetworkManager[580]: <info>  [1491955346.9836] manager: WWAN hardware radio set enabled
Apr 12 02:02:28 hitchens kernel: [   42.304947] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap snd_hda_codec_realtek snd_hda_codec_generic ath5k snd_hda_intel snd_hda_codec coretemp snd_hda_core snd_hwdep snd_pcm ath mac80211 joydev input_leds serio_raw cfg80211 snd_timer lpc_ich snd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 ahci psmouse libahci i2c_algo_bit pata_acpi drm_kms_helper syscopyarea r8169 sysfillrect sysimgblt fb_sys_fops mii drm wmi fjes video
Apr 12 02:02:28 hitchens kernel: [   42.305038]  warn_slowpath_fmt+0x5f/0x80
Apr 12 02:02:28 hitchens kernel: [   42.305623]  entry_SYSCALL_64_fastpath+0x1e/0xad
Apr 12 02:02:28 hitchens kernel: [   42.492601] Modules linked in: xt_multiport iptable_filter arc4 sparse_keymap snd_hda_codec_realtek snd_hda_codec_generic ath5k snd_hda_intel snd_hda_codec coretemp snd_hda_core snd_hwdep snd_pcm ath mac80211 joydev input_leds serio_raw cfg80211 snd_timer lpc_ich snd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 ahci psmouse libahci i2c_algo_bit pata_acpi drm_kms_helper syscopyarea r8169 sysfillrect sysimgblt fb_sys_fops mii drm wmi fjes video
Apr 12 02:02:28 hitchens kernel: [   42.492683]  warn_slowpath_fmt+0x5f/0x80
Apr 12 02:02:28 hitchens kernel: [   42.493485]  entry_SYSCALL_64_fastpath+0x1e/0xad
Apr 12 02:02:53 hitchens systemd[1601]: Reached target Paths.
jeroen@hitchens:~$

```

The kernel oops originate from an unrelated GPU driver error, which I can ignore, since this is a headless server .

```
Apr 12 02:02:15 hitchens kernel: [   28.996034] ------------[ cut here ]------------
Apr 12 02:02:15 hitchens kernel: [   28.996066] WARNING: CPU: 0 PID: 311 at /build/linux-Fk60NP/linux-4.10.0/drivers/gpu/drm/drm_irq.c:1237 drm_wait_one_vblank+0x1aa/0x1b0 [drm]
Apr 12 02:02:15 hitchens kernel: [   28.996067] vblank wait timed out on crtc 0
Apr 12 02:02:15 hitchens kernel: [   28.996068] Modules linked in: arc4 sparse_keymap snd_hda_codec_realtek snd_hda_codec_generic ath5k snd_hda_intel snd_hda_codec coretemp snd_hda_core snd_hwdep snd_pcm ath mac80211 joydev input_leds serio_raw cfg80211 snd_timer lpc_ich snd soundcore shpchp mac_hid ip_tables x_tables autofs4 uas usb_storage i915 ahci psmouse libahci i2c_algo_bit pata_acpi drm_kms_helper syscopyarea r8169 sysfillrect sysimgblt fb_sys_fops mii drm wmi fjes video
Apr 12 02:02:15 hitchens kernel: [   28.996107] CPU: 0 PID: 311 Comm: plymouthd Tainted: G        W       4.10.0-19-generic #21-Ubuntu
Apr 12 02:02:15 hitchens kernel: [   28.996108] Hardware name: FUJITSU SIEMENS AMILO Li 2735                  /LV2                            , BIOS V1.07      01/16/2008
Apr 12 02:02:15 hitchens kernel: [   28.996109] Call Trace:
Apr 12 02:02:15 hitchens kernel: [   28.996116]  dump_stack+0x63/0x81
Apr 12 02:02:15 hitchens kernel: [   28.996120]  __warn+0xcb/0xf0
Apr 12 02:02:15 hitchens kernel: [   28.996122]  warn_slowpath_fmt+0x5f/0x80
Apr 12 02:02:15 hitchens kernel: [   28.996125]  ? finish_wait+0x56/0x70
Apr 12 02:02:15 hitchens kernel: [   28.996137]  drm_wait_one_vblank+0x1aa/0x1b0 [drm]
Apr 12 02:02:15 hitchens kernel: [   28.996140]  ? wake_atomic_t_function+0x60/0x60
Apr 12 02:02:15 hitchens kernel: [   28.996155]  ? drm_atomic_state_clear+0x30/0x30 [drm]
Apr 12 02:02:15 hitchens kernel: [   28.996215]  intel_get_load_detect_pipe+0x5ff/0x650 [i915]
Apr 12 02:02:15 hitchens kernel: [   28.996247]  intel_tv_detect+0x158/0x550 [i915]
Apr 12 02:02:15 hitchens kernel: [   28.996258]  drm_helper_probe_single_connector_modes+0x2c4/0x520 [drm_kms_helper]
Apr 12 02:02:15 hitchens kernel: [   28.996271]  ? drm_mode_object_get_properties+0xdd/0x100 [drm]
Apr 12 02:02:15 hitchens kernel: [   28.996274]  ? mutex_lock+0x12/0x40
Apr 12 02:02:15 hitchens kernel: [   28.996288]  drm_mode_getconnector+0x372/0x3c0 [drm]
Apr 12 02:02:15 hitchens kernel: [   28.996301]  drm_ioctl+0x21b/0x4c0 [drm]
Apr 12 02:02:15 hitchens kernel: [   28.996305]  ? mem_cgroup_commit_charge+0x7e/0x510
Apr 12 02:02:15 hitchens kernel: [   28.996319]  ? drm_mode_connector_property_set_ioctl+0x60/0x60 [drm]
Apr 12 02:02:15 hitchens kernel: [   28.996323]  do_vfs_ioctl+0xa3/0x610
Apr 12 02:02:15 hitchens kernel: [   28.996326]  ? __do_page_fault+0x266/0x4e0
Apr 12 02:02:15 hitchens kernel: [   28.996328]  SyS_ioctl+0x79/0x90
Apr 12 02:02:15 hitchens kernel: [   28.996331]  entry_SYSCALL_64_fastpath+0x1e/0xad
Apr 12 02:02:15 hitchens kernel: [   28.996333] RIP: 0033:0x7f5a37bf0987
Apr 12 02:02:15 hitchens kernel: [   28.996334] RSP: 002b:00007fffbed6d7d8 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
Apr 12 02:02:15 hitchens kernel: [   28.996337] RAX: ffffffffffffffda RBX: 0000000000000800 RCX: 00007f5a37bf0987
Apr 12 02:02:15 hitchens kernel: [   28.996338] RDX: 00007fffbed6d810 RSI: 00000000c05064a7 RDI: 0000000000000009
Apr 12 02:02:15 hitchens kernel: [   28.996339] RBP: 00007f5a35966010 R08: 000055d65a6b22d0 R09: 00007f5a37c47c00
Apr 12 02:02:15 hitchens kernel: [   28.996341] R10: 000055d65a6b2370 R11: 0000000000000246 R12: 00000000000000ff
Apr 12 02:02:15 hitchens kernel: [   28.996342] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000000
Apr 12 02:02:15 hitchens kernel: [   28.996344] ---[ end trace f26d06ea2dc00362 ]---
Apr 12 02:02:15 hitchens kernel: [   29.134301] ------------[ cut here ]------------

```

And here's an updated output of the Wireless Info script: [https://pastebin.com/qRS58VUH](https://pastebin.com/qRS58VUH)

---

### Post by chili555 on 2017-04-12
> since this is a headless server .Is Network Manager able to run when it boots headless; that is, without graphics and a desktop environment? Typically, in a headless server, NM is not even installed and all interfaces are configured in /etc/network/interfaces.

I suggest that you edit /etc/modprobe.d/ath5k.conf to change it to:```
options ath5k no_hw_rfkill_switch=Y
```I notice that the ethernet is attached and you have an IP address. Usually, Network Manager, if it is running, will default to the more secure and often faster ethernet. If you detach the ethernet and give NM a minute or two to notice the change in state, does the wireless then scan?```
sudo iwlist scan
```If it doesn't scan, what are the errors, warnings, et al?

---

### Post by Forceflow on 2017-04-12
Yes, NM runs just fine without a GUI. Remember, when I boot with the 4.8 kernel, both my ethernet and wifi connection immediately get an IP.
The no_hw_rfkill_switch=Y is already on in ath5k.conf.

The sudo iwlist scan just returns "no scan results". If I boot with the 4.8 kernel and scan, I get 12 SSID's.

---

### Post by chili555 on 2017-04-13
> The no_hw_rfkill_switch=Y is already on in ath5k.conf.
Yes, but what I was referring to is that there are two declarations in the file. I suggest that you amend the file to include only the latter.

It may or may not surprise you to know that several of the more experienced posters here talk about tough threads behind your backs by private message. A few of us are suspicious that it is Network Manager that has a flaw in 17.04. In fact, we have seen and will soon work on a very similar case elsewhere.

In order to rule in or rule out NM, we propose that you populate /etc/network/interfaces something like:```
auto lo
iface lo inet loopback

auto wlp8s0
iface wlp8s0 inet dhcp
wpa-ssid <your_network>
wpa-psk <your_wpa_password>
```Reboot with the ethernet detached and tell us if you connect:```
ifconfig wlp8s0
ping -c3 www.ubuntu.com
```

---

### Post by Forceflow on 2017-04-13
> **chili555 said:**
> Yes, but what I was referring to is that there are two declarations in the file. I suggest that you amend the file to include only the latter.
Oh, check - will do that and report.
> **chili555 said:**
> It may or may not surprise you to know that several of the more experienced posters here talk about tough threads behind your backs by private message. A few of us are suspicious that it is Network Manager that has a flaw in 17.04. In fact, we have seen and will soon work on a very similar case elsewhere.
Oh, nice. It is a weird case - I'm not too bad with troubleshooting myself and usually can get to the root of the problem myself, but this is a weird one

> **chili555 said:**
> 
In order to rule in or rule out NM, we propose that you populate /etc/network/interfaces something like:```
auto lo
iface lo inet loopback

auto wlp8s0
iface wlp8s0 inet dhcp
wpa-ssid <your_network>
wpa-psk <your_wpa_password>
```Reboot with the ethernet detached and tell us if you connect:```
ifconfig wlp8s0
ping -c3 www.ubuntu.com
```
This would effectively make wlp8s0 unmanaged by NM right? Good idea. I'll try that and report back to you. The network I want to connect to has a more advanced security method (PEAP), but I'll quickly make a simple WPA one to see if I can connect to that.

---

### Post by chili555 on 2017-04-13
I have now seen *three *posts about this in various fora. I am, as we speak, burning the 17.04 DVD to see if I have the same issue and, if so, to see if I can figure out why.> This would effectively make wlp8s0 unmanaged by NM right? That's correct, assuming that /etc/NetworkManager/NetworkManager.conf remains in its default state including managed=false. The clearer explanation is that do we, NM, manage interfaces which are declared in /etc/network/interfaces? If it is set to false and then we, NM, do *not* manage them.

I wonder if this is actually a PEAP issue. Can you please temporarily change to WPA2-AES and, before you amend /etc/network/interfaces, try to connect and report?

---

### Post by chili555 on 2017-04-13
I downloaded 17.04 and my wireless works perfectly. 

One of our best driver dawgs reminds me that this is the subject of at least one and perhaps several official filed bugs. He reports that it seems to most plague Atheros cards and some USB devices. Here is an interesting post from a thread he has been working on: [https://ubuntuforums.org/showthread.php?t=2354066&p=13621393#post13621393](https://ubuntuforums.org/showthread.php?t=2354066&p=13621393#post13621393)

Will you please try adding the text to the file, rebooting and tell us if it helps.> I have found a fix that has been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open
/etc/NetworkManager/NetworkManager.conf

add lines
```
[device]
wifi.scan-rand-mac-address=0
```

This got me connected again. Fingers crossed.

---

### Post by Forceflow on 2017-04-13
> **chili555 said:**
> I downloaded 17.04 and my wireless works perfectly. 

One of our best driver dawgs reminds me that this is the subject of at least one and perhaps several official filed bugs. He reports that it seems to most plague Atheros cards and some USB devices. Here is an interesting post from a thread he has been working on: [https://ubuntuforums.org/showthread.php?t=2354066&p=13621393#post13621393](https://ubuntuforums.org/showthread.php?t=2354066&p=13621393#post13621393)

Will you please try adding the text to the file, rebooting and tell us if it helps.Fingers crossed.
I'll try all of this tomorrow, didn't have much time to fiddle around with it today - thanks for the hints!
The AP that uses PEAP is not under my command (was delivered by ISP), and is the one I'm supposed to connect to. In order to test more easily, I'll whip out a quick old AP I have here that *is* under my command and make a simple WPA AP on it.

---

### Post by chili555 on 2017-04-14
I suggest that you try these steps in this order:

# Change to NetworkManager.conf. Reboot. Now, does the interface scan and see networks? Does it connect with Network Manager? If so, done. 

# Set up an AP with WPA2-AES. Does it connect? If so, then the problem may be PEAP and we'll further address it.

# Bypass NM by making all settings in /etc/network/interfaces.

My hunch is that the first step is going to solve it.

---

### Post by hotellina on 2017-04-15
After I installed my new sparkling **Kubuntu 17.04** on my Desktop PC wifi didn't work.
Strangely enough during the installation from CD I was connected to internet.

The solution for me was to  

Open
/etc/NetworkManager/NetworkManager.conf

and add lines
 	Code:

 	[device]
wifi.scan-rand-mac-address=0

---

### Post by Forceflow on 2017-04-17
> **chili555 said:**
> I suggest that you try these steps in this order:
# Change to NetworkManager.conf. Reboot. Now, does the interface scan and see networks? Does it connect with Network Manager? If so, done. 
# Set up an AP with WPA2-AES. Does it connect? If so, then the problem may be PEAP and we'll further address it.


Unfortunately, adding that line in NetworkManager.conf and rebooting doesn't solve it. I still cannot scan and see networks, and thus cannot connect to even a WPA2-AES network...

---

### Post by chili555 on 2017-04-17
Frankly, I see no reason in the logs that the hardware, driver and Network Manager won't start and run. It reminds me of an old Ford I once owned and cursed.

Does this help?```
sudo service network-manager stop
sudo iwlist scan
```

I suggest that you download the Ubuntu 17.04 server edition that doesn't include Network Manager at all and run a live session. All I'd love to know is if, when running live, the wireless scans.```
sudo iwlist scan
```If it does, then we should consider either installing it or removing NM in your current install.

[https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

If none of these steps help, then I shall regrettably recommend that you return to 16.10 and try again in 60 days or so.

:confused: :confused: :confused:

---

