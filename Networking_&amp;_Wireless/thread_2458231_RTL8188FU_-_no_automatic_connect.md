---
title: "RTL8188FU - no automatic connect"
date: 2021-02-19
forum: Networking &amp; Wireless
---

### Post by angelo16 on 2021-02-19
Lubuntu 20.04

After compiling drivers, it started to work and I can see the SSID networks in the range, I can connect to my network. However, if I turn off or reboot the system, it does not auto reconnects to my network. 

I have to  select my network and enter with my login and password  every time.

---

### Post by angelo16 on 2021-02-20
**journalctl -b -k --no-page -l | grep rtl8188fu**
```
dell@dell-inspiron1525:~$ journalctl -b -k --no-page -l | grep rtl8188fu
fev 20 18:58:27 dell-inspiron1525 kernel: RTL871X: rtl8188fu v4.3.23.6_20964.20170110
fev 20 18:58:27 dell-inspiron1525 kernel: usb 2-3: request firmware rtlwifi/rtl8188fufw.bin
fev 20 18:58:27 dell-inspiron1525 kernel: usb 2-3: request firmware rtlwifi/rtl8188fufw.bin loaded
fev 20 18:58:27 dell-inspiron1525 kernel: usbcore: registered new interface driver rtl8188fu
fev 20 18:58:27 dell-inspiron1525 kernel: rtl8188fu 2-3:1.0 wlx00e04ce39dad: renamed from wlan0
fev 20 18:58:53 dell-inspiron1525 kernel: RTL871X: rtl8188fu_hal_init in 644ms
fev 20 18:58:55 dell-inspiron1525 kernel: RTL871X: ==> rtl8188fu_hal_deinit
fev 20 18:58:56 dell-inspiron1525 kernel: RTL871X: rtl8188fu_hal_init in 636ms
fev 20 18:58:58 dell-inspiron1525 kernel: RTL871X: ==> rtl8188fu_hal_deinit
fev 20 18:58:59 dell-inspiron1525 kernel: RTL871X: rtl8188fu_hal_init in 672ms
fev 20 18:59:01 dell-inspiron1525 kernel: RTL871X: ==> rtl8188fu_hal_deinit
fev 20 18:59:22 dell-inspiron1525 kernel: RTL871X: rtl8188fu_hal_init in 628ms
fev 20 18:59:24 dell-inspiron1525 kernel: RTL871X: ==> rtl8188fu_hal_deinit
fev 20 18:59:55 dell-inspiron1525 kernel: RTL871X: rtl8188fu_hal_init in 632ms
fev 20 18:59:57 dell-inspiron1525 kernel: RTL871X: ==> rtl8188fu_hal_deinit
fev 20 19:00:38 dell-inspiron1525 kernel: RTL871X: rtl8188fu_hal_init in 636ms
fev 20 19:00:40 dell-inspiron1525 kernel: RTL871X: ==> rtl8188fu_hal_deinit
fev 20 19:01:31 dell-inspiron1525 kernel: RTL871X: rtl8188fu_hal_init in 628ms
fev 20 19:01:33 dell-inspiron1525 kernel: RTL871X: ==> rtl8188fu_hal_deinit
dell@dell-inspiron1525:~$ 

```
[B]

journalctl -b -u NetworkManager --no-page -l[/B]
```
dell@dell-inspiron1525:~$ journalctl -b -u NetworkManager --no-page -l
-- Logs begin at Thu 2021-02-11 15:17:33 -03, end at Sat 2021-02-20 19:00:40 -03. --
fev 20 18:58:30 dell-inspiron1525 systemd[1]: Starting Network Manager...
fev 20 18:58:41 dell-inspiron1525 NetworkManager[586]: <info>  [1613858321.3463] NetworkManager (version 1.22.10) is starting... (for the first time)
fev 20 18:58:41 dell-inspiron1525 NetworkManager[586]: <info>  [1613858321.3464] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
fev 20 18:58:41 dell-inspiron1525 NetworkManager[586]: <info>  [1613858321.7720] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
fev 20 18:58:41 dell-inspiron1525 systemd[1]: Started Network Manager.
fev 20 18:58:41 dell-inspiron1525 NetworkManager[586]: <info>  [1613858321.9041] manager[0x559fb3327020]: monitoring kernel firmware directory '/lib/firmware'.
fev 20 18:58:41 dell-inspiron1525 NetworkManager[586]: <info>  [1613858321.9043] monitoring ifupdown state file '/run/network/ifstate'.
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7403] hostname: hostname: using hostnamed
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7404] hostname: hostname changed from (none) to "dell-inspiron1525"
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7409] dns-mgr[0x559fb3307290]: init: dns=systemd-resolved rc-manager=symlink, plugin=systemd-resolved
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7427] rfkill0: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/ieee80211/phy0/rfkill0) (driver wl)
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7437] rfkill1: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/net/wlp11s0/rfkill1) (driver wl)
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7443] rfkill2: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/ieee80211/phy1/rfkill2) (driver rtl8188fu)
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7453] manager[0x559fb3327020]: rfkill: Wi-Fi hardware radio set enabled
fev 20 18:58:43 dell-inspiron1525 NetworkManager[586]: <info>  [1613858323.7453] manager[0x559fb3327020]: rfkill: WWAN hardware radio set enabled
fev 20 18:58:46 dell-inspiron1525 NetworkManager[586]: <info>  [1613858326.3242] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wwan.so)
fev 20 18:58:46 dell-inspiron1525 NetworkManager[586]: <info>  [1613858326.3427] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wifi.so)
fev 20 18:58:46 dell-inspiron1525 NetworkManager[586]: <info>  [1613858326.5930] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-team.so)
fev 20 18:58:49 dell-inspiron1525 NetworkManager[586]: <info>  [1613858329.1640] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-bluetooth.so)
fev 20 18:58:49 dell-inspiron1525 NetworkManager[586]: <info>  [1613858329.1926] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-adsl.so)
fev 20 18:58:49 dell-inspiron1525 NetworkManager[586]: <info>  [1613858329.1933] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
fev 20 18:58:49 dell-inspiron1525 NetworkManager[586]: <info>  [1613858329.1935] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
fev 20 18:58:49 dell-inspiron1525 NetworkManager[586]: <info>  [1613858329.1936] manager: Networking is enabled by state file
fev 20 18:58:49 dell-inspiron1525 NetworkManager[586]: <info>  [1613858329.1938] dhcp-init: Using DHCP client 'internal'
fev 20 18:58:51 dell-inspiron1525 NetworkManager[586]: <info>  [1613858331.1367] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-settings-plugin-ifupdown.so")
fev 20 18:58:51 dell-inspiron1525 NetworkManager[586]: <info>  [1613858331.1368] settings: Loaded settings plugin: keyfile (internal)
fev 20 18:58:51 dell-inspiron1525 NetworkManager[586]: <info>  [1613858331.1369] ifupdown: management mode: unmanaged
fev 20 18:58:51 dell-inspiron1525 NetworkManager[586]: <warn>  [1613858331.3941] ifupdown: interfaces file /etc/network/interfaces doesn't exist                                                                                
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.5885] device (lo): carrier: link connected
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.5896] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.5923] manager: (enp9s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.7816] settings: (enp9s0): created default wired connection 'Wired connection 1'
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.9304] device (enp9s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.9381] manager: (wlp11s0): new 802.11 Wi-Fi device (/org/freedesktop/NetworkManager/Devices/3)
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.9396] device (wlp11s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.9432] device (wlx00e04ce39dad): driver supports Access Point (AP) mode
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.9444] manager: (wlx00e04ce39dad): new 802.11 Wi-Fi device (/org/freedesktop/NetworkManager/Devices/4)
fev 20 18:58:52 dell-inspiron1525 NetworkManager[586]: <info>  [1613858332.9464] device (wlx00e04ce39dad): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
fev 20 18:58:53 dell-inspiron1525 NetworkManager[586]: <warn>  [1613858333.6297] Error: failed to open /run/network/ifstate                                                                                                     
fev 20 18:58:53 dell-inspiron1525 NetworkManager[586]: <info>  [1613858333.7557] supplicant: wpa_supplicant running
fev 20 18:58:53 dell-inspiron1525 NetworkManager[586]: <info>  [1613858333.7559] device (wlx00e04ce39dad): supplicant interface state: init -> starting
fev 20 18:58:53 dell-inspiron1525 NetworkManager[586]: <info>  [1613858333.7560] device (wlp11s0): supplicant interface state: init -> starting
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3437] sup-iface[0x559fb3333210,wlx00e04ce39dad]: supports 5 scan SSIDs
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3475] device (wlx00e04ce39dad): supplicant interface state: starting -> ready
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3480] Wi-Fi P2P device controlled by interface wlx00e04ce39dad created
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3488] manager: (p2p-dev-wlx00e04ce39dad): new 802.11 Wi-Fi P2P device (/org/freedesktop/NetworkManager/Devices/5)
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3495] device (p2p-dev-wlx00e04ce39dad): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3523] sup-iface[0x559fb3333120,wlp11s0]: supports 1 scan SSIDs
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3534] device (p2p-dev-wlx00e04ce39dad): state change: unavailable -> disconnected (reason 'none', sys-iface-state: 'managed')
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3542] device (wlx00e04ce39dad): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <warn>  [1613858336.3562] sup-iface: failed to cancel p2p connect: P2P cancel failed                                                                                     
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3617] device (wlp11s0): supplicant interface state: starting -> ready
fev 20 18:58:56 dell-inspiron1525 NetworkManager[586]: <info>  [1613858336.3623] device (wlp11s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
fev 20 18:58:57 dell-inspiron1525 NetworkManager[586]: <info>  [1613858337.0123] modem-manager: ModemManager not available
fev 20 18:58:57 dell-inspiron1525 NetworkManager[586]: <info>  [1613858337.0241] modem-manager: ModemManager now available
fev 20 18:58:58 dell-inspiron1525 NetworkManager[586]: <info>  [1613858338.9356] manager: startup complete
```

---

### Post by angelo16 on 2021-02-20
[B]ls /lib/firmware/rtlwifi/rtl8188fufw.bin
[/B]
```
dell@dell-inspiron1525:~$ ls /lib/firmware/rtlwifi/rtl8188fufw.bin
/lib/firmware/rtlwifi/rtl8188fufw.bin
```



[B]cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
[/B]
```
dell@dell-inspiron1525:~$ cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
[connection]
wifi.powersave = 3
```[B]


cat /etc/modprobe.d/rtl8188fu.conf
[/B]
```
dell@dell-inspiron1525:~$ cat /etc/modprobe.d/rtl8188fu.conf
cat: /etc/modprobe.d/rtl8188fu.conf: No such file or directory
```

Is this last message related to my problem ?

---

### Post by guiverc on 2021-02-20
> **angelo16 said:**
> 
However, if I turn off or reboot the system, it does not auto reconnects to my network. 

I have to  select my network and enter with my login and password  every time.

Are you using the *Network Manager* item in the tray to connect to your network?  In my experience and testing, that always saves your login & password so it doesn't need to be re-entered.

If a wireless network isn't connected during install, it isn't by default subsequently auto-connected in my experience, but even that doesn't fit your description as I read it.

How are you connecting your wifi?  Have you made any changes to get your wifi to work? (autologin scripts run, as needing to re-enter login/password should not be necessary)

[https://manual.lubuntu.me/stable/3/3.1/3.1.5/nm-tray.html?highlight=wifi](https://manual.lubuntu.me/stable/3/3.1/3.1.5/nm-tray.html?highlight=wifi)

---

### Post by angelo16 on 2021-02-20
Hi guiverc.

To use wifi, I have always to use the Network manager to select the SSID and pwd. I can see the details of the wifi connection and passowrd to connect to the SSID is saved, as well as it is checked to automatic reconnection but for some reason it is not.

The driver, I had to follow  the instructions to compile that I found in another post here in Ubuntu Foruns. I did not change any script.

---

### Post by angelo16 on 2021-02-21
Guys, I have installed the drivers following the instructions here
[https://github.com/ulli-kroll/rtl8188fu](https://github.com/ulli-kroll/rtl8188fu)

I just found another driver at
[https://github.com/kelebek333/rtl8188fu](https://github.com/kelebek333/rtl8188fu)


How do I remove the first one ?  Do I need to remove the first one before I try the second one ?

---

### Post by drjdmartin on 2021-02-21
I'd remove the first one if you want to try the second one. Try to run **sudo make uninstall** from the build directory of the ulli-kroll driver.

The kelebek driver is working well for me.

The error you are getting from **cat /etc/modprobe.d/rtl8188fu.conf** just means that file doesn't exist. No big deal if the driver is being loaded.

---

### Post by angelo16 on 2021-02-21
Uninstalled, rebooted, installed the driver as instructions on [https://github.com/kelebek333/rtl8188fu](https://github.com/kelebek333/rtl8188fu)

but the problem persists. No automatic connection after restart. Every time I had to select the SSID and enter with the passwd. Strange behavior is the NetworkManager that shows the list of known connections with my SSID repeated by the number of times I had to  select the SSID. It seems that nm  does not recognize the previous SSID on the available networks to connect

---

### Post by drjdmartin on 2021-02-23
Seems like the computer thinks there is something different about the connection each time. Are you sure that the system is giving your wifi dongle the same device identifier each boot up?

I.e. if you do **iwconfig** is the wlan always wlx00e04ce39dad for this device?

---

### Post by gigabyte56 on 2021-03-20
I'm experiencing the same problems as angelo16 (see [https://ubuntuforums.org/showthread.php?t=2458878](https://ubuntuforums.org/showthread.php?t=2458878)), and I too see multiple entries in the 'Visible Networks' panel, ie my SSID followed by an integer value. To answer drjdmartin 's question, iwconfig (on my machine) displays a different value for the device after each boot (eg. wlx00e04c508a9a -> wlx00e04c050c6f)

---

### Post by gigabyte56 on 2021-03-21
It does seem that you can prevent the interface being renamed (from wlan0), and that this does resolve the problem around passwords not being saved. See [https://ubuntuforums.org/showthread.php?t=2458878](https://ubuntuforums.org/showthread.php?t=2458878) for details.

---

