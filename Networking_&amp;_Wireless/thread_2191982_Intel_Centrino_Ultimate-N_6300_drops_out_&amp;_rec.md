---
title: "Intel Centrino Ultimate-N 6300 drops out &amp; reconnects almost every minute"
date: 2013-12-05
forum: Networking &amp; Wireless
---

### Post by Jim_Granite on 2013-12-05
Suddenly my wireless connection drops out & reconnects almost every minute.

[I]EDIT: Looks like more than a few of us have had this problem crop up within the past two days!
- [Wifi stops working after a while but works after reboot]("http://ubuntuforums.org/showthread.php?t=2191589")
I suspect something changed in Ubuntu recently, which crapped on the wireless card or driver.
[/I]
It's not the router, because all the other computers are fine. 
Plus, nothing (to my knowledge) has changed.

I've had Ubuntu 13.10 on for about two months, and I haven't installed anything recently - yet - in the past day - the connection drops out constantly.
I can easily reconnect by switching to a different SSID (back and forth) - but then it drops out again.

I can see the disconnect and automatic reconnects constantly, simply by running a forever ping.
The ping stops. Then restarts at a later count. Stops. Then restarts (on and on and on).

Debugging my Lenovo W510 notebook, I see it has an Intel Centrino Ultimate-N 6300:
```
$ lspci| grep -i network
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
```

The driver seems to be the Intel Wireless Link WiFi driver:
```

$ lspci -vv
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
        Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 57
        Region 0: Memory at f2000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlwifi
```

Googling, I see the firmware is the [same as that Intel provides]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm"):
$ diff /tmp/iwlwifi-6000-4.ucode /lib/firmware/iwlwifi-6000-4.ucode
REPORTS: The downloaded firmware is the same as what was there.

While the ping is conclusive, I think this error is telling me something about the dropping & reconnecting (but I'm not sure what it's trying to tell me):
$ dmesg | grep iwlwifi
```

[   11.687180] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   11.687280] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   23.627827] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   23.635149] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   23.859203] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   23.865920] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  133.716350] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  133.723147] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  134.860347] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  134.867103] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  136.755224] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  136.762032] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
```

Basic Question:
**Q: If I assume something in the Ubuntu distribution changed, how do I reinstall the Intel Wireless Link WiFi driver?**

---

### Post by praseodym on 2013-12-05
Deactivate the N-mode of the driver:
```

echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by Jim_Granite on 2013-12-05
> **praseodym said:**
> Deactivate the N-mode of the driver:
```

echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

Thanks for the advice - as I do know that nobody has to help us, and, I appreciate your help.

I should have mentioned that, in the *many* things I tried, that was one of them, which I had found in these two threads:
- [http://forum.linuxmint.com/viewtopic.php?f=53&t=118812](http://forum.linuxmint.com/viewtopic.php?f=53&t=118812)
- [http://ubuntuforums.org/showthread.php?t=1980142](http://ubuntuforums.org/showthread.php?t=1980142)

Those commands are intended to disable the "n" flavor  of the 802.11 protocol, which is apparently buggy on Intel chipsets.  
Check the output of "iwconfig wlan0" before and after issueing those  commands. 
It should start with "IEEE 802.11abgn" before and just  "802.11abg"

However, the wifi dropouts are still happening, even after multiple reboots after performing that task.

Here is my original Intel Wireless Link WiFi (iwlwifi) configuration file:
```

$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

Here is the same file, after running the "tee" command:
```
$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1
```

And, here is what the xterminal said when I ran the modprobe commands:
```

$ sudo modprobe -rfv iwlwifi
FATAL: Module iwlwifi is in use.
$ sudo modprobe -v iwlwifi
$
```

And, here is the result of running "iwconfig wlan0", which would show the "n" option had I known ahead of time to run it before issuing the commands above:
```
$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"JIMGRANITE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address redacted>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:831   Missed beacon:0
```
*Note: I had turned off power management, in addition to the "n" capabilities, in an attempt to solve this problem.*

Googling like crazy, I find this is a pretty common problem with the Intel wifi cards; but, what I don't get is why it's happening now. 
I mean, I've had ubuntu 13.10 for a couple of months, and this problem only cropped up very recently.

---

### Post by Jim_Granite on 2013-12-05
Googling for how to debug this problem (debugging is always the hardest part of any problem), I find these commands.
They don't make much sense to me, but, maybe they'll make sense to someone else?

```
$ sudo lsmod | grep iwl
iwldvm      237440  0
mac80211  596969  1 iwldvm
iwlwifi       165398  1 iwldvm
cfg80211    479757  3 iwlwifi,mac80211,iwldvm
```

```

$ sudo lshw -C network
... Ethernet stuff omitted ...
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: (redacted)
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-14-generic firmware=9.221.4.1 build 25532 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:55 memory:f2000000-f2001fff
```

This supposedly turns off automatic power management of the wifi card:
```

$ sudo iwconfig wlan0 power off
```

This supposedly does something useful:
```

$ sudo apt-get install libnss-myhostname
```

```

$ dmesg
[   16.859134] ppdev: user-space parallel port driver
[   18.209359] e1000e 0000:00:19.0: irq 53 for MSI/MSI-X
[   18.310629] e1000e 0000:00:19.0: irq 53 for MSI/MSI-X
[   18.310776] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.311153] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.313056] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   18.319820] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   18.544204] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   18.550838] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   18.650647] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.840734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.582923] wlan0: authenticate with <redacted MAC address>
[   25.640491] wlan0: send auth to <redacted MAC address> (try 1/3)
[   25.642539] wlan0: authenticated
[   25.642824] wlan0: waiting for beacon from <redacted MAC address>
[   25.694484] wlan0: associate with <redacted MAC address> (try 1/3)
[   25.697703] wlan0: RX AssocResp from <redacted MAC address> (capab=0x411 status=0 aid=5)
[   25.709368] wlan0: associated
[   25.709454] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[22260.050676] perf samples too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
```

```
$ tail /var/log/syslog
Dec  5 15:17:01 localhost CRON[2003]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  5 15:23:33 localhost colord: device removed: xrandr-Lenovo Group Limited
Dec  5 15:23:33 localhost colord: Profile removed: icc-d627b8721f9960309988ebca341c11d2
Dec  5 15:23:33 localhost NetworkManager[890]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Dec  5 15:23:34 localhost dbus[697]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Dec  5 15:23:34 localhost dbus[697]: [system] Successfully activated service 'org.freedesktop.systemd1'
Dec  5 15:23:34 localhost rtkit-daemon[1520]: Successfully made thread 2278 of process 2278 (n/a) owned by '1000' high priority at nice level -11.
Dec  5 15:23:34 localhost rtkit-daemon[1520]: Supervising 5 threads of 2 processes of 2 users.
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Successfully made thread 2319 of process 2278 (n/a) owned by '1000' RT at priority 5.
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Supervising 6 threads of 2 processes of 2 users.
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Successfully made thread 2321 of process 2278 (n/a) owned by '1000' RT at priority 5.
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Supervising 7 threads of 2 processes of 2 users.
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Successfully made thread 2322 of process 2278 (n/a) owned by '1000' RT at priority 5.
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Supervising 8 threads of 2 processes of 2 users.
Dec  5 15:23:35 localhost bluetoothd[740]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPAG
Dec  5 15:23:35 localhost bluetoothd[740]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPHS
Dec  5 15:23:35 localhost bluetoothd[740]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Dec  5 15:23:35 localhost bluetoothd[740]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Successfully made thread 2324 of process 2324 (n/a) owned by '1000' high priority at nice level -11.
Dec  5 15:23:35 localhost rtkit-daemon[1520]: Supervising 9 threads of 3 processes of 2 users.
Dec  5 15:23:35 localhost pulseaudio[2324]: [pulseaudio] pid.c: Daemon already running.
Dec  5 15:23:35 localhost dbus[697]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Dec  5 15:23:35 localhost dbus[697]: [system] Successfully activated service 'org.freedesktop.locale1'
Dec  5 15:23:35 localhost colord: Device added: xrandr-Lenovo Group Limited
Dec  5 15:23:35 localhost colord: Automatic metadata add icc-b9921548b33ffea25f6068e4cd4f9155 to xrandr-Lenovo Group Limited
Dec  5 15:23:35 localhost colord: Profile added: icc-b9921548b33ffea25f6068e4cd4f9155
Dec  5 15:23:37 localhost dbus[697]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Dec  5 15:23:37 localhost udisksd[2441]: udisks daemon version 2.1.0 starting
Dec  5 15:23:37 localhost dbus[697]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Dec  5 15:23:37 localhost udisksd[2441]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Dec  5 15:23:53 localhost bluetoothd[740]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/HFPAG
Dec  5 15:23:53 localhost bluetoothd[740]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/HFPHS
Dec  5 15:23:53 localhost bluetoothd[740]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Dec  5 15:23:53 localhost bluetoothd[740]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Dec  5 15:24:07 localhost whoopsie[1087]: online
Dec  5 15:25:09  whoopsie[1087]: last message repeated 5 times
Dec  5 15:26:26  whoopsie[1087]: last message repeated 2 times
Dec  5 15:26:36 localhost whoopsie[1087]: online
Dec  5 15:31:13 localhost whoopsie[1087]: online
Dec  5 15:31:36 localhost whoopsie[1087]: online
Dec  5 15:32:42 localhost whoopsie[1087]: online
Dec  5 15:33:56  whoopsie[1087]: last message repeated 3 times
Dec  5 15:36:41 localhost whoopsie[1087]: online
Dec  5 15:37:42  whoopsie[1087]: last message repeated 2 times
Dec  5 15:38:20 localhost whoopsie[1087]: online
Dec  5 15:39:49 localhost whoopsie[1087]: online
Dec  5 15:40:57  whoopsie[1087]: last message repeated 3 times
Dec  5 15:41:59 localhost whoopsie[1087]: online
Dec  5 15:43:27  whoopsie[1087]: last message repeated 2 times
Dec  5 15:44:07 localhost whoopsie[1087]: online
Dec  5 15:45:08  whoopsie[1087]: last message repeated 2 times
Dec  5 15:46:24  whoopsie[1087]: last message repeated 2 times
Dec  5 15:47:27  whoopsie[1087]: last message repeated 4 times
Dec  5 15:47:28 localhost whoopsie[1087]: online
Dec  5 15:48:42 localhost whoopsie[1087]: online
Dec  5 15:49:57  whoopsie[1087]: last message repeated 2 times
Dec  5 15:52:34 localhost whoopsie[1087]: online
Dec  5 15:53:48 localhost whoopsie[1087]: online
Dec  5 15:54:58  whoopsie[1087]: last message repeated 2 times
Dec  5 15:56:25 localhost whoopsie[1087]: online
Dec  5 15:57:28  whoopsie[1087]: last message repeated 2 times
Dec  5 15:59:41 localhost whoopsie[1087]: online
Dec  5 16:00:42 localhost whoopsie[1087]: online
Dec  5 16:01:58  whoopsie[1087]: last message repeated 2 times
Dec  5 16:02:58  whoopsie[1087]: last message repeated 2 times
Dec  5 16:04:08 localhost whoopsie[1087]: online
```

I think this debugging command is for signal issues:
```
$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: <redacted MAC>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"MY_SSID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=<hex number>
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: <hex number>
                        ... a few of these ... 
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: <hex number>
                        ... a few of these ... 
          Cell 02 - Address: <MAC REDACTED>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"MY_SSID"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=<hex number>
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: <hex number>
                        ... a few of these ... 
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: <hex number>
                        ... a few of these ... 

```

---

### Post by Jim_Granite on 2013-12-05
I'm still debugging, to see where the problem lies.

To doublecheck the SSID, I typed:
```
$ iwgetid
wlan0     ESSID:"MY_SSID"
```

Interestingly, I watched the pings die, and then ran nm-tool command, and it *still* said it was connected! 
```

$ nm-tool 
NetworkManager Tool
State: connected (global)
- Device: wlan0  [MY_SSID]
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC>
  Capabilities:
    Speed:           54 Mb/s
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points (* = current AP)
    *MY_SSID: Infra, <MAC1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 61 WPA2 
    SSID2:    Infra, <MAC2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    SSID3:    Infra, <MAC3>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA2
  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1

```

EDIT: I found out what the "units" were in the signal strength above ([over here]("http://www.cyberciti.biz/tips/linux-find-out-wireless-network-speed-signal-strength.html")).
```

$ iwconfig wlan0 | grep -i --color quality
Link Quality=54/70  Signal level=-56 dBm  
```
> 
54/70 is is an aggregate value, and depends totally on the driver and hardware.





Googling, I couldn't find what the strength figure units are, but, I found a way to get dBm out of Ubuntu:
```
$ watch -n1 iwconfig <=== updates every second
$ iwconfig
eth0      no wireless extensions.
lo        no wireless extensions.
wlan0     IEEE 802.11abg  ESSID:"MY_SSID"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC>
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:491   Missed beacon:0
```

I found another way to get real-time signal strength updates out of Ubuntu:
```

**$ watch -n 1 "awk 'NR==3 {print \"WiFi Signal Strength = \" \$3 \"00 %\"}''' /proc/net/wireless"**
WiFi Signal Strength = 43.00 %
WiFi Signal Strength = 52.00 %
WiFi Signal Strength = 45.00 %
etc.

```

These provide similar information:
```

$ watch -n 1 "awk 'NR==3 {print \"WiFi Signal Strength = \" (\$3/70)*100 \" %\"}''' /proc/net/wireless"
$ watch -n 1 cat /proc/net/wireless
NOTE: I can't figure out how to capture this output to copy and paste here.

```

---

### Post by Jim_Granite on 2013-12-06
> **praseodym said:**
> Please show
```

iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```

Here is the resolv.conf file:
```

$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```

The iwlist scan results have been reported earlier in this thread.

Here is the iwlist output:
```

$ iwlist chan
eth0      no frequency information.
lo        no frequency information.
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)
```

```

$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```

$ dmesg | grep iwl
[   14.097113] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.097269] iwlwifi 0000:03:00.0: irq 57 for MSI/MSI-X
[   14.308249] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   14.324456] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   14.324461] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   14.324464] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   14.324468] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   14.324472] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   14.324575] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   14.343264] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.261069] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   18.267806] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   18.496496] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   18.503199] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
```

```

$ iwevent
Waiting for Wireless Events from interfaces...
23:23:35.057962   wlan0    Scan request completed

```

---

### Post by praseodym on 2013-12-06
Tried an earlier kernel? Did it work with that?

---

### Post by Jim_Granite on 2013-12-06
> **praseodym said:**
> Tried an earlier kernel? Did it work with that?

I appreciate the advice, and suggestion.
I'm not sure what the question asks though. 
I've never dealt with a "kernel" before, so, I can't really answer the question.
I *assume* something changed in Ubuntu update ... so ... if that's what you mean, it might be what had happened.
But, I don't know how to "revert" back to a lower kernel. 
Will google...

---

### Post by praseodym on 2013-12-07
Reboot and press the SHIFT-key during that. You will enter the Grub2 menu. Choose "previous ubuntu versions" there and choose an earlier kernel (not the "recovery mode" one, though)

---

### Post by Jim_Granite on 2013-12-08
> **praseodym said:**
> Reboot and press the SHIFT-key during that. You will enter the Grub2 menu. Choose "previous ubuntu versions" there and choose an earlier kernel (not the "recovery mode" one, though)

Thanks for taking the time to clarify how to reboot to an earlier Ubuntu version.
It turns out I have not needed to do that.
The problem, seems to have resolved itself.
I tried so many things, I can't say *what* made it work again (nor what had made it drop out).
But, for now, I'll mark this solved - but - unfortunately - I can't tell you *how* it was solved.
Luckily I had listed above most of the debugging changes that I had made, so, if anyone else finds this in the future, they can follow in our footsteps.

Thank you all for your very kind help!

---

