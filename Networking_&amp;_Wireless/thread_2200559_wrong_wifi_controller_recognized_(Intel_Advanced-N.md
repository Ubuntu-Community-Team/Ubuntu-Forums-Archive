---
title: "wrong wifi controller recognized (Intel Advanced-N 6230)"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by Jan_Guth on 2014-01-20
I installed ubuntu 13.10 on my Dell XPS 13 (L321).
Since then my wifi is really unstable meaning that I can't connect to wifi connections.
After a while looking into the problem I recognized that also the Bluetooth is missing.
Apparently the wifi controller in not recognized correctly. (It should be: Intel Advanced-N 6230)

How can I fix this?
Thanks!

Here some more information:

```

sudo lshw -class network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:7c:11:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-15-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:50 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: bnep0
       serial: 00:02:72:c6:12:a3
       capabilities: ethernet physical
       configuration: broadcast=yes ip=172.20.10.12 multicast=yes

```

... and ...

```

dmesg | grep wifi
[    7.833676] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    7.833862] iwlwifi 0000:02:00.0: irq 50 for MSI/MSI-X
[    7.942008] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    7.972520] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    7.972524] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    7.972526] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    7.972528] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[    7.972531] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    7.972630] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    8.545622] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    8.548686] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[    8.653170] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    8.656788] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0

```

---

### Post by carl4926 on 2014-01-20
Could you actually post the result of

```
lspci -nnk | grep -iA2 net
```

---

### Post by Jan_Guth on 2014-01-20
sure.

```

lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
	Kernel driver in use: iwlwifi



```

---

### Post by carl4926 on 2014-01-20
It kinda look s like it's OK
And I'm pretty sure the same driver would be in use regardless.

Were you using another version of Ubuntu or Linux, before?

---

### Post by Jan_Guth on 2014-01-20
Nope. Before it was installed win8.
Hm I bought this notebook over eBay. Now I'm wondering if the adapter was replaced. : )

But despite of this it does not work properly. I can see most of the time all the surrounding wifis but I can't really connect to them. I guess 1 of 30 times trying it works for about 2 mins. (And after this sometimes it can't find the wifi anymore; also the signals appears to be really weak)


```

cat /var/log/syslog.1 | grep wlan0
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) starting connection 'Android black'
Jan 19 15:18:18 jguth NetworkManager[844]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0/wireless): access point 'Android black' has security, but secrets are required.
Jan 19 15:18:18 jguth NetworkManager[844]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 15:18:18 jguth NetworkManager[844]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0/wireless): connection 'Android black' has security, and secrets exist.  No new secrets needed.
Jan 19 15:18:18 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 15:18:18 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 19 15:18:29 jguth wpa_supplicant[1031]: wlan0: SME: Trying to authenticate with cc:fe:3c:7a:ab:78 (SSID='Android black' freq=2437 MHz)
Jan 19 15:18:29 jguth kernel: [ 9253.974608] wlan0: authenticate with cc:fe:3c:7a:ab:78
Jan 19 15:18:29 jguth kernel: [ 9253.975841] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 1/3)
Jan 19 15:18:29 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 19 15:18:29 jguth kernel: [ 9254.179269] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 2/3)
Jan 19 15:18:29 jguth kernel: [ 9254.383345] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 3/3)
Jan 19 15:18:29 jguth kernel: [ 9254.587474] wlan0: authentication with cc:fe:3c:7a:ab:78 timed out
Jan 19 15:18:29 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 19 15:18:30 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 19 15:18:43 jguth NetworkManager[844]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan 19 15:18:43 jguth NetworkManager[844]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jan 19 15:18:43 jguth NetworkManager[844]: <warn> Activation (wlan0) failed for connection 'Android black'
Jan 19 15:18:43 jguth NetworkManager[844]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 19 15:18:43 jguth NetworkManager[844]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 19 15:18:43 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) starting connection 'Android black'
Jan 19 15:18:53 jguth NetworkManager[844]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0/wireless): access point 'Android black' has security, but secrets are required.
Jan 19 15:18:53 jguth NetworkManager[844]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 15:18:53 jguth NetworkManager[844]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0/wireless): connection 'Android black' has security, and secrets exist.  No new secrets needed.
Jan 19 15:18:53 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 15:18:53 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 19 15:18:56 jguth wpa_supplicant[1031]: wlan0: SME: Trying to authenticate with cc:fe:3c:7a:ab:78 (SSID='Android black' freq=2437 MHz)
Jan 19 15:18:56 jguth kernel: [ 9281.225437] wlan0: authenticate with cc:fe:3c:7a:ab:78
Jan 19 15:18:56 jguth kernel: [ 9281.226731] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 1/3)
Jan 19 15:18:56 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 19 15:18:56 jguth kernel: [ 9281.427780] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 2/3)
Jan 19 15:18:57 jguth kernel: [ 9281.631918] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 3/3)
Jan 19 15:18:57 jguth kernel: [ 9281.835991] wlan0: authentication with cc:fe:3c:7a:ab:78 timed out
Jan 19 15:18:57 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 19 15:18:57 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 19 15:19:18 jguth NetworkManager[844]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan 19 15:19:18 jguth NetworkManager[844]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jan 19 15:19:18 jguth NetworkManager[844]: <warn> Activation (wlan0) failed for connection 'Android black'
Jan 19 15:19:18 jguth NetworkManager[844]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 19 15:19:18 jguth NetworkManager[844]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 19 15:19:18 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0) starting connection 'Android black'
Jan 19 15:20:59 jguth NetworkManager[844]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 15:20:59 jguth NetworkManager[844]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0/wireless): connection 'Android black' has security, and secrets exist.  No new secrets needed.
Jan 19 15:20:59 jguth NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 15:20:59 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 19 15:21:11 jguth wpa_supplicant[1031]: wlan0: SME: Trying to authenticate with cc:fe:3c:7a:ab:78 (SSID='Android black' freq=2437 MHz)
Jan 19 15:21:11 jguth kernel: [ 9415.833379] wlan0: authenticate with cc:fe:3c:7a:ab:78
Jan 19 15:21:11 jguth kernel: [ 9415.834940] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 1/3)
Jan 19 15:21:11 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 19 15:21:11 jguth kernel: [ 9416.037820] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 2/3)
Jan 19 15:21:11 jguth kernel: [ 9416.241891] wlan0: direct probe to cc:fe:3c:7a:ab:78 (try 3/3)
Jan 19 15:21:11 jguth kernel: [ 9416.446001] wlan0: authentication with cc:fe:3c:7a:ab:78 timed out
Jan 19 15:21:11 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 19 15:21:11 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 19 15:21:24 jguth NetworkManager[844]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan 19 15:21:24 jguth NetworkManager[844]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jan 19 15:21:24 jguth NetworkManager[844]: <warn> Activation (wlan0) failed for connection 'Android black'
Jan 19 15:21:24 jguth NetworkManager[844]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 19 15:21:24 jguth NetworkManager[844]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 19 15:21:24 jguth NetworkManager[844]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 19 16:41:34 jguth NetworkManager[821]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Jan 19 16:41:34 jguth NetworkManager[821]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 19 16:41:34 jguth NetworkManager[821]: <info> (wlan0): using nl80211 for WiFi device control
Jan 19 16:41:34 jguth NetworkManager[821]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 2)
Jan 19 16:41:34 jguth NetworkManager[821]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 16:41:34 jguth NetworkManager[821]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 19 16:41:34 jguth NetworkManager[821]: <info> (wlan0): bringing up device.
Jan 19 16:41:34 jguth NetworkManager[821]: <info> (wlan0): preparing device.
Jan 19 16:41:34 jguth NetworkManager[821]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 19 16:41:34 jguth kernel: [    9.049868] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by Jan_Guth on 2014-01-21
Please help. I can't find a solution for this problem.
It's a pain to be not able to use the wifi.
And if this is a hardware problem it would be good to know.

---

### Post by carl4926 on 2014-01-21
> [COLOR=#000000][FONT=Ubuntu Mono]failed (reason 'SSID not found')
[/FONT][/COLOR]


Is [COLOR=#000000][FONT=Ubuntu Mono]Android black
Your AP[/FONT][/COLOR]

---

### Post by chili555 on 2014-01-21
Does this help? ```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll make it permanent.> Now I'm wondering if the adapter was replaced. : )No doubt.

---

### Post by Jan_Guth on 2014-01-22
> **carl4926 said:**
> Is [COLOR=#000000][FONT=Ubuntu Mono]Android black
Your AP[/FONT][/COLOR]

Yes, one of them. I tried about 6 different wifis.

@chili555
No doubt that it was replaced? Hrm could it not be similar to this [http://ubuntuforums.org/showthread.php?t=2003669](http://ubuntuforums.org/showthread.php?t=2003669) ?

This is the Result:
```

jguth@jguth:~$ sudo modprobe -r iwldvm
[sudo] password for jguth: 
jguth@jguth:~$ sudo modprobe -r iwlwifi
Error: missing module name.
FATAL: Error running remove command for iwlwifi
jguth@jguth:~$ sudo modprobe iwlwifi 11n_disable=1
jguth@jguth:~$ 

```

There is not really an improvment.

Thanks for the help!

---

### Post by chili555 on 2014-01-22
> Hrm could it not be similar to thisI fail to see the similarity to your case. The thread you linked is a case of a very new device that didn't work on a very old version of Ubuntu. Your case is instability on a very current Ubuntu version. I suspect the Ebay seller -- best case -- copied and pasted the wrong listing or -- worst case -- substituted a slightly lesser wireless card hoping you'd never notice or care. You could point out his mistake and ask for a refund or replacement or just try to get the 5100 working properly. Googling up 'Ubuntu Intel 6230' isn't going to help you in any way; you don't have one.

I am troubled by this:> jguth@jguth:~$ sudo modprobe -r iwlwifi
Error: missing module name.
FATAL: Error running remove command for iwlwifiPlease see what's loaded now:```
lsmod | grep iwl
```Let's try to make the 11n parameter permanent for a moment and see if it helps:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is any improvement.

---

