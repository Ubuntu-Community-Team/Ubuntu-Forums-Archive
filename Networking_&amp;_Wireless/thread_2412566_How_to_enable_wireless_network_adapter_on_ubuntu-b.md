---
title: "How to enable wireless network adapter on ubuntu-budgie 18.10"
date: 2019-02-14
forum: Networking &amp; Wireless
---

### Post by maramsumanth on 2019-02-14
I am having Dual boot with Windows 10 and Ubuntu-Budgie 18.10

Here is my output for  lshw -C network

  ***-network          //This is enabled, I am fine with the wired Ethernet **     
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 15
       serial: 18:60:24:14:51:04
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=172.25.14.156 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:16 ioport:3000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff



**  *-network DISABLED            //How to enable this thing?**
       description: Wireless interface
       product: Dual Band Wireless-AC 3168NGW [Stone Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlo1
       version: 10
       serial: a0:af:bd:eb:13:f6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.18.0-15-generic firmware=29.1044073957.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:129 memory:b1000000-b1001fff


Following is my Wireless adapter information:-
      03:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] (rev 10)

---

### Post by chili555 on 2019-02-14
Please run and post:```
rfkill list all
```How is the Airplane Mode switch set today?

---

### Post by maramsumanth on 2019-02-14
Here is my output for rfkill list all

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2019-02-14
Any clues in the log? ```
dmesg | grep wl
```

---

### Post by maramsumanth on 2019-02-15
I an new to ubuntu, following is my output for  [COLOR=#000000][FONT=&quot]dmesg | grep wl[/FONT][/COLOR]

[    1.108680] Loaded UEFI:db cert 'Hewlett-Packard Company: HP UEFI Secure Boot 2013 DB key: 1d7cf2c2b92673f69c8ee1ec7063967ab9b62bec' linked to secondary sys keyring
[   15.397370] iwlwifi 0000:03:00.0: loaded firmware version 29.1044073957.0 op_mode iwlmvm
[   15.896967] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3168, REV=0x220
[   15.916887] iwlwifi 0000:03:00.0: base HW address: a0:af:bd:eb:13:f6
[   16.057128] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   16.191475] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0

---

### Post by chili555 on 2019-02-15
Looks perfectly fine so far. I wonder what Network Manager is doing. Please detach the ethernet and then run and post:```
cat /var/log/syslog | grep -e etwork -e wlo1 | tail -n25
```Does it scan?```
sudo iwlist wlo1 scan
```

---

### Post by maramsumanth on 2019-02-15
Output for [COLOR=#000000][FONT=&amp]cat /var/log/syslog | grep -e etwork -e wlo1 | tail -n25 :- (when ethernet is detached)[/FONT][/COLOR]

Feb 15 17:56:27 sumanth NetworkManager[947]: <info>  [1550233587.5813] manager: NetworkManager state is now CONNECTED_SITE
Feb 15 17:56:27 sumanth NetworkManager[947]: <info>  [1550233587.5820] policy: set 'Wired connection 1' (eno1) as default for IPv4 routing and DNS
Feb 15 17:56:27 sumanth NetworkManager[947]: <info>  [1550233587.5849] device (eno1): Activation: successful, device activated.
Feb 15 17:56:27 sumanth NetworkManager[947]: <info>  [1550233587.5887] manager: NetworkManager state is now CONNECTED_GLOBAL
Feb 15 17:56:27 sumanth dbus-daemon[939]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.13' (uid=0 pid=947 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Feb 15 17:56:27 sumanth systemd[1]: Configuration file /lib/systemd/system/NetworkManager-dispatcher.service is marked executable. Please remove executable permission bits. Proceeding anyway.
Feb 15 17:56:27 sumanth systemd[1]: Configuration file /lib/systemd/system/NetworkManager-dispatcher.service is marked world-writable. Please remove world writability permission bits. Proceeding anyway.
Feb 15 17:56:27 sumanth systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 15 17:56:27 sumanth nm-dispatcher: find-scripts: Cannot execute '/etc/NetworkManager/dispatcher.d/01-ifupdown': writable by group or other, or set-UID.
Feb 15 17:56:27 sumanth nm-dispatcher: find-scripts: Cannot execute '/etc/NetworkManager/dispatcher.d/01-ifupdown': writable by group or other, or set-UID.
Feb 15 17:56:27 sumanth systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 15 17:56:27 sumanth whoopsie[1890]: [17:56:27] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/3
Feb 15 17:56:27 sumanth whoopsie[1890]: [17:56:27] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/3
Feb 15 17:56:27 sumanth whoopsie[1890]: [17:56:27] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/3
Feb 15 19:39:39 sumanth NetworkManager[947]: <info>  [1550239779.9046] device (eno1): state change: activated -> unavailable (reason 'carrier-changed', sys-iface-state: 'managed')
Feb 15 19:39:39 sumanth NetworkManager[947]: <info>  [1550239779.9227] dhcp4 (eno1): canceled DHCP transaction, DHCP client pid 5923
Feb 15 19:39:39 sumanth NetworkManager[947]: <info>  [1550239779.9228] dhcp4 (eno1): state changed bound -> done
Feb 15 19:39:39 sumanth NetworkManager[947]: <info>  [1550239779.9432] manager: NetworkManager state is now DISCONNECTED
Feb 15 19:39:40 sumanth dbus-daemon[939]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.13' (uid=0 pid=947 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Feb 15 19:39:40 sumanth systemd[1]: Configuration file /lib/systemd/system/NetworkManager-dispatcher.service is marked executable. Please remove executable permission bits. Proceeding anyway.
Feb 15 19:39:40 sumanth systemd[1]: Configuration file /lib/systemd/system/NetworkManager-dispatcher.service is marked world-writable. Please remove world writability permission bits. Proceeding anyway.
Feb 15 19:39:40 sumanth systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 15 19:39:40 sumanth systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 15 19:39:40 sumanth nm-dispatcher: find-scripts: Cannot execute '/etc/NetworkManager/dispatcher.d/01-ifupdown': writable by group or other, or set-UID.
Feb 15 19:39:40 sumanth nm-dispatcher: find-scripts: Cannot execute '/etc/NetworkManager/dispatcher.d/01-ifupdown': writable by group or other, or set-UID.


Output for [COLOR=#000000][FONT=&amp]sudo iwlist wlo1 scan :- (Both situations when ethernet is attached and also ethernet is detached)

[/FONT][/COLOR]wlo1      Interface doesn't support scanning : Network is down[COLOR=#000000][FONT=&amp]


[/FONT][/COLOR]

---

### Post by chili555 on 2019-02-15
My favorite kind of problem: everything looks fine except it doesn't work!

Let's dig deeper:```
dmesg | grep 03.00
cat /var/log/syslog | grep wlo1
```So far, we see nothing wrong and therefore fixable.

---

### Post by maramsumanth on 2019-02-15
Output for [COLOR=#000000][FONT=&quot]dmesg | grep 03.00 :-

[/FONT][/COLOR][    0.000000] ACPI: SSDT 0x000000007CFEF000 000046 (v02 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000007CFEA000 003898 (v02 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000007CF99000 0017AE (v02 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.113717] ACPI: SSDT 0xFFFF8D2134F3C800 0006B4 (v02 PmRef  Cpu0Ist  00003000 INTL 20160527)
[    0.117538] ACPI: SSDT 0xFFFF8D213614B000 000D14 (v02 PmRef  ApIst    00003000 INTL 20160527)
[    0.119095] ACPI: SSDT 0xFFFF8D2134919800 00030A (v02 PmRef  ApCst    00003000 INTL 20160527)
[    0.164426] pci 0000:00:02.0: [8086:5916] type 00 class 0x030000
[    0.180160] pci 0000:01:00.0: [1002:6660] type 00 class 0x038000
[    0.181142] pci 0000:03:00.0: [8086:24fb] type 00 class 0x028000
[    0.181243] pci 0000:03:00.0: reg 0x10: [mem 0xb1000000-0xb1001fff 64bit]
[    0.181585] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.287055] system 00:00: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.287056] system 00:00: [mem 0xfe03d000-0xfe3fffff] has been reserved
[   15.397370] iwlwifi 0000:03:00.0: loaded firmware version 29.1044073957.0 op_mode iwlmvm
[   15.896967] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3168, REV=0x220
[   15.916887] iwlwifi 0000:03:00.0: base HW address: a0:af:bd:eb:13:f6
[   16.191475] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0



Output for [COLOR=#000000][FONT=&quot]cat /var/log/syslog | grep wlo1 :- [B]//It is too big to paste here, So I am pasting the last few lines

[/B][/FONT][/COLOR]Feb 13 23:13:22 sumanth kernel: [41699.560428] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
Feb 14 01:54:23 sumanth kernel: [   17.557552] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 14 01:54:36 sumanth NetworkManager[928]: <info>  [1550089472.7013] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 01:54:36 sumanth NetworkManager[928]: <info>  [1550089472.7038] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 02:24:12 sumanth NetworkManager[5186]: <info>  [1550091252.9147] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 02:24:12 sumanth NetworkManager[5186]: <info>  [1550091252.9152] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 02:24:37 sumanth NetworkManager[5269]: <info>  [1550091277.7514] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 02:24:37 sumanth NetworkManager[5269]: <info>  [1550091277.7519] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 02:25:54 sumanth kernel: [   17.738859] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 14 02:26:00 sumanth NetworkManager[970]: <info>  [1550091359.9831] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 02:26:00 sumanth NetworkManager[970]: <info>  [1550091359.9851] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 14:19:38 sumanth kernel: [   16.197874] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 14 14:19:43 sumanth NetworkManager[944]: <info>  [1550134183.3360] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 14:19:43 sumanth NetworkManager[944]: <info>  [1550134183.3370] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 14:34:35 sumanth kernel: [  938.548622] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
Feb 14 14:49:19 sumanth kernel: [   17.275405] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 14 14:49:23 sumanth NetworkManager[975]: <info>  [1550135963.4439] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 14:49:23 sumanth NetworkManager[975]: <info>  [1550135963.4464] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 14:52:45 sumanth NetworkManager[975]: <info>  [1550136165.2796] wifi-nl80211: (wlo1): using nl80211 for WiFi device control
Feb 14 19:58:08 sumanth kernel: [   18.534591] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 14 19:58:23 sumanth NetworkManager[962]: <info>  [1550154495.2425] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 19:58:23 sumanth NetworkManager[962]: <info>  [1550154495.2434] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 20:04:33 sumanth kernel: [   20.115308] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 14 20:04:46 sumanth NetworkManager[814]: <info>  [1550154879.7979] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 20:04:46 sumanth NetworkManager[814]: <info>  [1550154879.7986] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 21:29:50 sumanth kernel: [   15.989321] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 14 21:29:56 sumanth NetworkManager[950]: <info>  [1550159996.8895] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 14 21:29:56 sumanth NetworkManager[950]: <info>  [1550159996.8911] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 14 23:56:07 sumanth NetworkManager[950]: <info>  [1550168767.9229] wifi-nl80211: (wlo1): using nl80211 for WiFi device control
Feb 15 12:14:23 sumanth kernel: [   16.191475] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
Feb 15 12:14:26 sumanth NetworkManager[947]: <info>  [1550213066.2688] manager: (wlo1): 'wifi' plugin not available; creating generic device
Feb 15 12:14:26 sumanth NetworkManager[947]: <info>  [1550213066.2716] manager: (wlo1): new Generic device (/org/freedesktop/NetworkManager/Devices/3)
Feb 15 12:41:50 sumanth NetworkManager[947]: <info>  [1550214710.1675] wifi-nl80211: (wlo1): using nl80211 for WiFi device control


[COLOR=#000000][FONT=&quot]

[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]

[/FONT][/COLOR]

---

### Post by maramsumanth on 2019-02-15
I am really getting tensed now.
Earlier it was working fine, one fine day I just rebooted the system and then it stopped working. :( :sad:
Also I cannot see the WiFI option in the Network, but when I type explicitly wifi in search option it shows **No wifi adapter found make sure you have a wifi adapter plugged and turned on**

---

### Post by chili555 on 2019-02-16
> **maramsumanth said:**
> I am really getting tensed now.
Earlier it was working fine, one fine day I just rebooted the system and then it stopped working. :( :sad:
Also I cannot see the WiFI option in the Network, but when I type explicitly wifi in search option it shows **No wifi adapter found make sure you have a wifi adapter plugged and turned on**Is the driver loaded?```
lsmod | grep iwl
```If not, load it:```
sudo modprobe iwlwifi
```Check the log for errors or warnings:```
dmesg | grep iwl
```

---

### Post by maramsumanth on 2019-02-16
**Output for lsmod | grep iwl**

iwlmvm                368640  0
mac80211              794624  1 iwlmvm
iwlwifi               294912  1 iwlmvm
cfg80211              663552  3 iwlmvm,iwlwifi,mac80211

[B]Executed [COLOR=#000000][FONT=&amp]sudo modprobe iwlwifi

[/FONT][/COLOR]Output for [COLOR=#000000][FONT=&amp]dmesg | grep iwl

[/FONT][/COLOR][/B][   17.480524] iwlwifi 0000:03:00.0: loaded firmware version 29.1044073957.0 op_mode iwlmvm
[   18.032904] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3168, REV=0x220
[   18.053588] iwlwifi 0000:03:00.0: base HW address: a0:af:bd:eb:13:f6
[   18.118385] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   18.374475] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0


And then rebooted the system, after this also I cannot see wifi networks list :(

---

### Post by chili555 on 2019-02-16
So the driver was loaded and there were no alarming errors in the log. 

For what reason did you decide to reboot?

We need to see the results of my terminal commands just above when it is *NOT *working.

---

### Post by maramsumanth on 2019-02-16
I rebooted just to check whether running those commands have produced any change.
So, what should I do now?

---

### Post by chili555 on 2019-02-16
Is it working now? Post the results of the terminal commands above in post #12 above.

---

### Post by maramsumanth on 2019-02-16
No, still it isn't working, The results of terminal commands now are same as in #12.

---

### Post by maramsumanth on 2019-02-17
By browsing internet , I came across this-

Output for nmcli

**I am showing only the wireless part**

wlo1: unmanaged
        "Intel Wireless-AC 3168NGW"
        wifi (iwlwifi), A0:AF:BD:EB:13:F6, **plugin missing**, hw, mtu 1500

As there is something called plugin missing above, how to solve this?

---

### Post by chili555 on 2019-02-17
> **maramsumanth said:**
> By browsing internet , I came across this-

Output for nmcli

**I am showing only the wireless part**

wlo1: unmanaged
        "Intel Wireless-AC 3168NGW"
        wifi (iwlwifi), A0:AF:BD:EB:13:F6, **plugin missing**, hw, mtu 1500

As there is something called plugin missing above, how to solve this?Very interesting!

Let's have a look at:

```
sudo updatedb && locate libnm-device-plugin
journalctl -r -u NetworkManager.service | grep plugin-wifi | tail -n10

```
I wonder if libnm-device-plugin-wifi.so is somehow missing.

---

### Post by maramsumanth on 2019-02-17
It still didn't work.

**Output for **[COLOR=#000000][FONT=&quot]**sudo updatedb && locate libnm-device-plugin** :-

[/FONT][/COLOR]/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-adsl.so
/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-bluetooth.so
/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-team.so
/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so
/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wwan.so


[COLOR=#000000][FONT=&quot]

**Output for **[/FONT][/COLOR][COLOR=#000000][FONT=&quot]**journalctl -r -u NetworkManager.service | grep plugin-wifi | tail -n10** :-

[/FONT][/COLOR]Feb 09 13:41:12 sumanth-hp-laptop NetworkManager[13636]: <info>  [1549699872.9019] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Feb 09 13:27:58 sumanth-hp-laptop NetworkManager[10839]: <info>  [1549699078.1104] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Feb 09 12:06:59 sumanth-hp-laptop NetworkManager[925]: <info>  [1549694219.8410] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Feb 09 07:55:37 Sumanth-HP-Laptop-15g-br0xx NetworkManager[990]: <info>  [1549679137.2380] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Feb 09 07:47:50 Sumanth-HP-Laptop-15g-br0xx NetworkManager[911]: <info>  [1549678670.2847] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Feb 09 01:30:32 Sumanth-HP-Laptop-15g-br0xx NetworkManager[800]: <info>  [1549656032.0337] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Jan 27 00:36:28 Sumanth-HP-Laptop-15g-br0xx NetworkManager[924]: <info>  [1548529588.7488] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Jan 27 00:00:12 Sumanth-HP-Laptop-15g-br0xx NetworkManager[927]: <info>  [1548527412.2180] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Jan 26 11:33:56 Sumanth-HP-Laptop-15g-br0xx NetworkManager[937]: <info>  [1548482636.0864] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)
Jan 26 10:49:20 Sumanth-HP-Laptop-15g-br0xx NetworkManager[803]: <info>  [1548479960.7019] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)


[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by chili555 on 2019-02-18
Previously, in post #5, your log said:

> Feb 15 12:14:26 sumanth NetworkManager[947]: <info> [1550213066.2688] manager: (wlo1):[COLOR="#FF0000"] 'wifi' plugin not available;[/COLOR] creating generic device

In your reply just above, it now says:

> Feb 09 13:41:12 sumanth-hp-laptop NetworkManager[13636]: <info> [1549699872.9019] [COLOR="#FF0000"]Loaded device plugin:[/COLOR] NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.12.4/libnm-device-plugin-wifi.so)

Did it work on February 9 and now it doesn't work?

What is the exact nmcli command you used that shows: **plugin missing**?

---

### Post by maramsumanth on 2019-02-18
Yes, exactly it worked on Feb 9th, after that I tried to install wine to run my windows program,but it was unsuccessful **(so I manually deleted all files containing name wine in it)** and I updated with sudo apt-get update, the next day when I started my laptop, wifi didn't work.

---

### Post by maramsumanth on 2019-02-18
Below is my output for nmcli:-

eno1: connected to Wired connection 1
        "Realtek RTL8111/8168/8411"
        ethernet (r8169), 18:60:24:14:51:04, hw, mtu 1500
        ip4 default
        inet4 172.25.14.156/24
        route4 0.0.0.0/0
        route4 172.25.14.0/24
        inet6 fe80::fa58:9ba0:bbcb:29d4/64
        route6 fe80::/64
        route6 ff00::/8


lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536


wlo1: unmanaged
        "Intel Wireless-AC 3168NGW"
        wifi (iwlwifi), A0:AF:BD:EB:13:F6, plugin missing, hw, mtu 1500


DNS configuration:
        servers: 192.168.121.12 192.168.121.14
        domains: iitr.ernet.in
        interface: eno1


Use "nmcli device show" to get complete information about known devices and
"nmcli connection show" to get an overview on active connection profiles.


Consult nmcli(1) and nmcli-examples(5) manual pages for complete usage details.

---

### Post by chili555 on 2019-02-18
Is wpa_supplicant running?

```
ps aux | grep wpa

```
Is it installed?

```
sudo dpkg -s wpasupplicant
```

Any clues in the log?

```
grep wpa /var/log/syslog | tail -n10
```

---

### Post by maramsumanth on 2019-02-19
**Output for **[COLOR=#000000][FONT=&quot]**ps aux | grep wpa:-**

[/FONT][/COLOR]root       821  0.0  0.0  21276  4388 ?        Ss   Feb18   0:00 /sbin/wpa_supplicant -u -s -O /run/wpa_supplicant
maramsu+ 12541  0.0  0.0  14020   900 pts/0    S+   19:05   0:00 grep --color=auto wpa

**Output for **[COLOR=#000000][FONT=&quot]**sudo dpkg -s wpasupplicant:-**

[/FONT][/COLOR]Package: wpasupplicant
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 2701
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: wpa
Version: 2:2.6-18ubuntu1
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.9.14), libnl-3-200 (>= 3.2.7), libnl-genl-3-200 (>= 3.2.7), libpcsclite1 (>= 1.0.0), libreadline7 (>= 6.0), libssl1.1 (>= 1.1.0), lsb-base, adduser
Suggests: wpagui, libengine-pkcs11-openssl
Breaks: initscripts (<< 2.88dsf-13.3)
Conffiles:
 /etc/dbus-1/system.d/wpa_supplicant.conf 8d90aeffce60b60c62d385874c304dc6
 /etc/wpa_supplicant/action_wpa.sh 41b2e273d616b1c7e7b605bbe8648d8b
 /etc/wpa_supplicant/functions.sh 29834d0d67a65585b71e231832884174
 /etc/wpa_supplicant/ifupdown.sh 4c82dbf7e1d8c5ddd70e40b9665cfeee
Description: client support for WPA and WPA2 (IEEE 802.11i)
 WPA and WPA2 are methods for securing wireless networks, the former
 using IEEE 802.1X, and the latter using IEEE 802.11i. This software
 provides key negotiation with the WPA Authenticator, and controls
 association with IEEE 802.11i networks.
Homepage: [http://w1.fi/wpa_supplicant/](http://w1.fi/wpa_supplicant/)
Original-Maintainer: Debian wpasupplicant Maintainers <wpa@packages.debian.org>


**Output for **[COLOR=#000000][FONT=&quot]**grep wpa /var/log/syslog | tail -n10:-**

[/FONT][/COLOR]Feb 17 15:51:24 sumanth systemd[1]: Configuration file /lib/systemd/system/wpa_supplicant.service is marked world-writable. Please remove world writability permission bits. Proceeding anyway.
Feb 17 10:21:07 sumanth systemd[1]: Configuration file /lib/systemd/system/wpa_supplicant.service is marked executable. Please remove executable permission bits. Proceeding anyway.
Feb 17 10:21:07 sumanth systemd[1]: Configuration file /lib/systemd/system/wpa_supplicant.service is marked world-writable. Please remove world writability permission bits. Proceeding anyway.
Feb 17 10:21:12 sumanth systemd[1]: Configuration file /lib/systemd/system/wpa_supplicant.service is marked executable. Please remove executable permission bits. Proceeding anyway.
Feb 17 10:21:12 sumanth systemd[1]: Configuration file /lib/systemd/system/wpa_supplicant.service is marked world-writable. Please remove world writability permission bits. Proceeding anyway.
Feb 17 10:21:26 sumanth systemd[1]: Configuration file /lib/systemd/system/wpa_supplicant.service is marked executable. Please remove executable permission bits. Proceeding anyway.
Feb 17 10:21:26 sumanth systemd[1]: Configuration file /lib/systemd/system/wpa_supplicant.service is marked world-writable. Please remove world writability permission bits. Proceeding anyway.
Feb 17 12:33:10 sumanth wpa_supplicant[938]: Successfully initialized wpa_supplicant
Feb 17 20:34:17 sumanth wpa_supplicant[1006]: Successfully initialized wpa_supplicant
Binary file /var/log/syslog matches

---

### Post by maramsumanth on 2019-02-19
Now I am unable to open whole ubuntu :( , when I boot ubuntu it takes me to a black screen having something called tty1 on it. How to go back to GUI, also Ctrl+Alt+F7 isn't working. I am writing this message from Windows. :(

---

### Post by chili555 on 2019-02-20
> **maramsumanth said:**
> Now I am unable to open whole ubuntu :( , when I boot ubuntu it takes me to a black screen having something called tty1 on it. How to go back to GUI, also Ctrl+Alt+F7 isn't working. I am writing this message from Windows. :(Is there a command prompt available? A blinking cursor? You might try to see what the error is:```
grep -i error /var/log/syslog | tail -n15
```Often, the error is related to video.

---

### Post by maramsumanth on 2019-03-11
Solved by reinstalling ubuntu budgie

---

