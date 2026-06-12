---
title: "WiFi setup using Netplan"
date: 2019-10-18
forum: Networking &amp; Wireless
---

### Post by makem2 on 2019-10-18
I have a fresh install of Ubuntu.04.3 LTS (64 bit ARM) preinstalled server image on a Pi3.

I have configured the netplan settings as follows:

Contents of /etc/cloud/50-cloud-init.yaml:
```

network:     version: 2
    ethernets:
        eth0:
            optional: true
            dhcp4: true
    wifis:
      wlp2s0b1:
        dhcp4: no
        dhcp6: no
        addresses: [192.168.0.21/24]
        gateway4: 192.168.0.1
        nameservers:
          addresses: [192.168.0.1, 8.8.8.8]
        access-points:
          "network_ssid_name":
            password: "**********"
```

Then run sudo netplan apply. Followed by sudo netplan --debug apply:

```

ubuntu@ubuntu:~$ sudo netplan --debug apply
** (generate:1586): DEBUG: 19:39:51.996: Processing input file /etc/netplan/50-cloud-init.yaml..
** (generate:1586): DEBUG: 19:39:51.997: starting new processing pass
** (generate:1586): DEBUG: 19:39:51.998: wlan0: adding wifi AP '******GHz'
** (generate:1586): DEBUG: 19:39:51.998: wlan0: setting default backend to 1
** (generate:1586): DEBUG: 19:39:51.998: Configuration is valid
** (generate:1586): DEBUG: 19:39:51.998: eth0: setting default backend to 1
** (generate:1586): DEBUG: 19:39:51.998: Configuration is valid
** (generate:1586): DEBUG: 19:39:51.998: Generating output files..
** (generate:1586): DEBUG: 19:39:51.999: NetworkManager: definition eth0 is not for us (backend 1)
** (generate:1586): DEBUG: 19:39:51.999: wlan0: Creating wpa_supplicant configuration file run/netplan/wpa-wlan0.conf
** (generate:1586): DEBUG: 19:39:51.999: Creating wpa_supplicant service enablement link /run/systemd/system/systemd-networkd.service.wants/netplan-wpa@wlan0.service
** (generate:1586): DEBUG: 19:39:52.000: NetworkManager: definition wlan0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:eth0 not found in {}
DEBUG:wlan0 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    eth0:
      dhcp4: true
      match:
        macaddress: b8:27:eb:81:46:0e
      set-name: eth0
  vlans: {}
  wifis:
    wlan0:
      access-points:
        ********GHz:
          password: *********
      addresses:
      - 192.168.2.201/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.2.1
      nameservers:
        addresses:
        - 192.168.2.1
        - 8.8.8.8

DEBUG:Skipping non-physical interface: lo
DEBUG:device eth0 operstate is up, not changing
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for eth0
DEBUG:netplan triggering .link rules for wlan0
ubuntu@ubuntu:~$

```

This appears to be an error, "NetworkManager: definition wlan0 is not for us (backend 1)" and I cannot see why it occurs.

Extract from journalctl in respect of wlan0:

```

Oct 18 19:09:19 ubuntu systemd[1]: Starting Network Service...
Oct 18 19:09:19 ubuntu systemd[1]: Created slice system-netplan\x2dwpa.slice.
Oct 18 19:09:19 ubuntu systemd[1]: Started WPA supplicant for netplan wlan0.
Oct 18 19:09:19 ubuntu wpa_supplicant[1500]: Successfully initialized wpa_supplicant
Oct 18 19:09:19 ubuntu kernel: IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 19:09:19 ubuntu kernel: brcmfmac: power management disabled
Oct 18 19:09:19 ubuntu systemd-networkd[1499]: eth0: Gained IPv6LL
Oct 18 19:09:19 ubuntu systemd-timesyncd[1077]: Network configuration changed, trying to establish connection.
Oct 18 19:09:19 ubuntu systemd-networkd[1499]: Enumeration completed
Oct 18 19:09:19 ubuntu systemd[1]: Started Network Service.
Oct 18 19:09:19 ubuntu systemd-networkd[1499]: eth0: Link is not managed by us
Oct 18 19:09:19 ubuntu systemd-networkd[1499]: lo: Link is not managed by us
Oct 18 19:09:19 ubuntu sudo[1484]: pam_unix(sudo:session): session closed for user root
Oct 18 19:09:19 ubuntu systemd-timesyncd[1077]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).
Oct 18 19:09:19 ubuntu systemd-timesyncd[1077]: Network configuration changed, trying to establish connection.
Oct 18 19:09:19 ubuntu systemd-networkd[1499]: lo: Link is not managed by us
Oct 18 19:09:19 ubuntu systemd-networkd[1499]: eth0: DHCPv4 address 192.168.2.125/24 via 192.168.2.1
Oct 18 19:09:19 ubuntu dbus-daemon[1221]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostnam
Oct 18 19:09:19 ubuntu systemd[1]: Starting Hostname Service...
Oct 18 19:09:19 ubuntu systemd-networkd[1499]: eth0: Configured
Oct 18 19:09:19 ubuntu dbus-daemon[1221]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 18 19:09:19 ubuntu systemd[1]: Started Hostname Service.
Oct 18 19:09:21 ubuntu kernel: Under-voltage detected! (0x00050005)
Oct 18 19:09:25 ubuntu kernel: Voltage normalised (0x00000000)
Oct 18 19:09:29 ubuntu systemd-timesyncd[1077]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Oct 18 19:09:29 ubuntu systemd-timesyncd[1077]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).
Oct 18 19:09:30 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:36 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:41 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:46 ubuntu sudo[1509]:   ubuntu : TTY=pts/0 ; PWD=/etc/netplan ; USER=root ; COMMAND=/usr/sbin/netplan --debug
Oct 18 19:09:46 ubuntu sudo[1509]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=0)
Oct 18 19:09:46 ubuntu sudo[1509]: pam_unix(sudo:session): session closed for user root
Oct 18 19:09:47 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:36 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:41 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:46 ubuntu sudo[1509]:   ubuntu : TTY=pts/0 ; PWD=/etc/netplan ; USER=root ; COMMAND=/usr/sbin/netplan --debug
Oct 18 19:09:46 ubuntu sudo[1509]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=0)
Oct 18 19:09:46 ubuntu sudo[1509]: pam_unix(sudo:session): session closed for user root
Oct 18 19:09:47 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:52 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:09:58 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:04 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:09 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:15 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:20 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:26 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:31 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:37 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:42 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:48 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:53 ubuntu wpa_supplicant[1500]: wlan0: Failed to initiate sched scan
Oct 18 19:10:57 ubuntu sudo[1515]:   ubuntu : TTY=pts/0 ; PWD=/etc/netplan ; USER=root ; COMMAND=/usr/sbin/netplan --debug apply
Oct 18 19:10:57 ubuntu sudo[1515]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=0)
Oct 18 19:10:58 ubuntu systemd[1]: Stopping Network Service...
Oct 18 19:10:58 ubuntu systemd[1]: Stopping WPA supplicant for netplan wlan0...

```

Anybody can point me in the right direction?

---

### Post by chili555 on 2019-10-18
> NetworkManager: definition wlan0 is not for us (backend 1)Is Network Manager running and, more importantly, conflicting here??

Why not set your details in Network Manager?

---

### Post by makem2 on 2019-10-18
> **chili555 said:**
> Is Network Manager running and, more importantly, conflicting here??

Why not set your details in Network Manager?

[http://paste.ubuntu.com/p/dXzJNgqxCR/](http://paste.ubuntu.com/p/dXzJNgqxCR/)

Is Network Manager running? I don't know.

Conflicting? Again, I don't know

I considered using Network manager but it is so long since I did it, I am not confident, especially when netplan is involved and appears to need to be disabled.

Looking at the wireless-info.txt file it appears Networking is not even installed, let alone running!

Whats with a server without networking?? Or, is it down to bliddy netplan to set it up?

Edit: Installed NetworkManager and re run netplan settings.

New wireless-info: [http://paste.ubuntu.com/p/pcvbgDNJCR/](http://paste.ubuntu.com/p/pcvbgDNJCR/)

---

### Post by makem2 on 2019-10-19
Still no joy :(

No matter which suggestions I follow!

---

### Post by makem2 on 2019-10-19
Now the broadcom wifi has crashed.

brcmfmac: brcmf_cfg8021_get_tx_power: error (110) plus other output which all just keeps repeating.

---

### Post by chili555 on 2019-10-19
This, and not netplan and not Network Manager, is the issue:

```
[  288.738824] brcmfmac: brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -110
[  291.298850] brcmfmac: brcmf_run_escan: error (-110)
[  293.858868] brcmfmac: brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -110 (repeated 2 times)
[  298.978849] brcmfmac: brcmf_run_escan: error (-110)
[  301.538860] brcmfmac: brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -110 (repeated 2 times)
[  306.658919] brcmfmac: brcmf_run_escan: error (-110)
```We wonder if the driver brcmfmac is correct for your device, however, we are unable to identify it because:> ##### lspci #############################

pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.We are not quite sure what went wrong in your installation that prevents lspci from identifying your device.

lspci means 'list all of the PCI devices.'

Are there any clues in:```
dmesg | grep -e 14e4
```If you run a live session of Ubuntu fro a USB, does the device appear?```
lspci -nnk | grep 0280 -A3
```

---

### Post by makem2 on 2019-10-19
> **chili555 said:**
> This, and not netplan and not Network Manager, is the issue:

```
[  288.738824] brcmfmac: brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -110
[  291.298850] brcmfmac: brcmf_run_escan: error (-110)
[  293.858868] brcmfmac: brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -110 (repeated 2 times)
[  298.978849] brcmfmac: brcmf_run_escan: error (-110)
[  301.538860] brcmfmac: brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -110 (repeated 2 times)
[  306.658919] brcmfmac: brcmf_run_escan: error (-110)
```We wonder if the driver brcmfmac is correct for your device, however, we are unable to identify it because:We are not quite sure what went wrong in your installation that prevents lspci from identifying your device.

lspci means 'list all of the PCI devices.'

Are there any clues in:```
dmesg | grep -e 14e4
```If you run a live session of Ubuntu fro a USB, does the device appear?```
lspci -nnk | grep 0280 -A3
```

```

ubuntu@ubuntu:~$ dmesg | grep -e 14e4
ubuntu@ubuntu:~$

```

No output.

The error has probably been going on from day one and I did not notice it because the Pi was not attached to a screen until today. I am pleased you found it for me.

As for your second suggestion, I will do that tomorrow as I don't have a spare USB. However, I am wondering if it would be more convenient to just flash a new instance.

---

### Post by chili555 on 2019-10-19
If it were me, I'd reinstall. Please proceed.

---

### Post by makem2 on 2019-10-19
I will do that. Thanks for your input, it has saved me a lot of sweat. Hopefully this install will not have a problem.

---

### Post by makem2 on 2019-10-19
Fresh install, updated with Network Manager installed and netplan used to setup wifi.

Wireless settings:

[http://paste.ubuntu.com/p/PjZCSWJ83Q/](http://paste.ubuntu.com/p/PjZCSWJ83Q/)

Same error as before but I note:

**Using Network Manager as a renderer**

 Netplan  supports both networkd and Network Manager as backends. You can specify  which network backend should be used to configure particular devices by  using the renderer key. You can also delegate all configuration of the network to Network Manager itself by specifying only the renderer key:
         network:
  version: 2
  renderer: NetworkManager
     
As taken from netplan.io examples.

Is it really an error? Or is it because netplan is using networkd and not network-manager?

Example used in setting up netplan:

```

network:
  version: 2
  renderer: networkd
  wifis:
    wlp2s0b1:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.0.21/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [192.168.0.1, 8.8.8.8]
      access-points:
        "network_ssid_name":
          password: "**********"

```

Still no output from dmesg | grep -e 14e4

Would a pastebin post of the whole of journalctl -xb -1 be of any help?

Edit: I notice this in dmesg | grep brcmfmac:

```

ubuntu@ubuntu:~$ dmesg | grep brcmfmac
[   19.412744] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac43430-sdio.bin for chip 0x00a9a6(43430) rev 0x000001
[   19.454017] usbcore: registered new interface driver brcmfmac
[   19.678260] brcmfmac: brcmf_c_process_clm_blob: no clm_blob available(err=-2), device may have limited channels available
[   19.721368] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: Aug 29 2016 20:48:16 version 7.45.41.26 (r640327) FWID 01-4527cfab
[   20.254815] brcmfmac: power management disabled
[   32.034767] brcmfmac: brcmf_sdio_hostmail: mailbox indicates firmware halted
[   34.786895] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   37.346890] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   37.363952] brcmfmac: brcmf_pno_clean: failed code -110
[   45.026898] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   45.043934] brcmfmac: brcmf_run_escan: error (-110)
[   45.059984] brcmfmac: brcmf_cfg80211_scan: scan error (-110)
[   48.610882] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   48.628135] brcmfmac: brcmf_run_escan: error (-110)
[   48.644363] brcmfmac: brcmf_cfg80211_scan: scan error (-110)
[   52.194896] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout

```

Should power management be disabled?

```

ubuntu@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
ubuntu@ubuntu:~$

```

The netplan setup is for WPA Personal network. My network is WPA2-Personal, would that cause 'Access Point: Not-Associated'?

---

### Post by chili555 on 2019-10-20
> [34.786895] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   37.346890] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   37.363952] brcmfmac: brcmf_pno_clean: failed code -110
[   45.026898] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   45.043934] brcmfmac: brcmf_run_escan: error (-110)
[   45.059984] brcmfmac: brcmf_cfg80211_scan: scan error (-110)
[   48.610882] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   48.628135] brcmfmac: brcmf_run_escan: error (-110)You have exactly the same issues as before. Until we find and correct the reason for this, no amount of tinkering around in netplan nor Network Manager will help. Quite simply, the physical device, the driver and the firmware aren't happy together.

So far, searches on the internet for the errors haven't yielded anything useful.

May we see: ```
dmesg | grep -i -e sdio -e irmw
```

> Is it really an error? Or is it because netplan is using networkd and not network-manager?

netplan can use either. If NM is present and running, it is almost always preferable to us NM and set netplan to defer to it.

> The netplan setup is for WPA Personal network. My network is WPA2-Personal, would that cause 'Access Point: Not-Associated'?

No. Again, until we find and correct the error above, all this netplan tweaking and speculation is fruitless.

---

### Post by makem2 on 2019-10-20
Extract from dmesg:

```

[   17.892619] brcmfmac: [COLOR=#ff0000]brcmf_fw_map_chip_to_name: using brcm/brcmfmac43430-sdio.bin for chip 0x00a9a6(43430) rev 0x000001[/COLOR]
[   17.933509] usbcore: registered new interface driver brcmfmac
[   18.220814] brcmfmac: [COLOR=#ff0000]brcmf_c_process_clm_blob: no clm_blob available(err=-2), device may have limited channels available[/COLOR]
[   18.263214] brcmfmac: [COLOR=#ff0000]brcmf_c_preinit_dcmds: Firmware version = wl0: Aug 29 2016 20:48:16 version 7.45.41.26 (r640327) FWID 01-4527cfab
[/COLOR]
```[COLOR=#ff0000]

[/COLOR]Posted before seeing your reply[COLOR=#ff0000]
[/COLOR]

---

### Post by makem2 on 2019-10-20
ubuntu@ubuntu:~$ dmesg | grep -i -e sdio -e irmw
[    0.172382] dmi: Firmware registration failed.
[    0.172685] raspberrypi-firmware soc:firmware: Attached to firmware from 2019-02-12 19:42
[    4.400862] mmc1: new high speed SDIO card at address 0001
[   17.892619] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac43430-sdio.bin for chip 0x00a9a6(43430) rev 0x000001
[   18.263214] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: Aug 29 2016 20:48:16 version 7.45.41.26 (r640327) FWID 01-4527cfab
[   30.492485] brcmfmac: brcmf_sdio_hostmail: mailbox indicates firmware halted
[   32.994807] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   35.554798] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   43.234805] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   46.818800] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   50.402798] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   53.986818] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
ubuntu@ubuntu:~$

---

### Post by chili555 on 2019-10-20
Possibly relevant: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1836730](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1836730)

May we see: ```
sudo dpkg -s linux-firmware
sudo dpkg -s linux-firmware-raspi2
```

---

### Post by chili555 on 2019-10-20
Please try:

```
cd /lib/firmware/brcm
sudo wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm/brcmfmac43430-sdio.clm_blob
sudo wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm/brcmfmac43430-sdio.txt
```Reboot and show us:```
dmesg | grep brcm
```

---

### Post by makem2 on 2019-10-20
> **chili555 said:**
> Possibly relevant: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1836730](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1836730)

May we see: ```
sudo dpkg -s linux-firmware
sudo dpkg -s linux-firmware-raspi2
```

```

ubuntu@ubuntu:~$ sudo dpkg -s linux-firmware
Package: linux-firmware
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 312288
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Version: 1.173.9
Replaces: atmel-firmware, linux-firmware-snapdragon (<= 1.2-0ubuntu1), linux-restricted-common
Provides: atmel-firmware
Breaks: linux-firmware-snapdragon (<= 1.2-0ubuntu1)
Conflicts: atmel-firmware
Description: Firmware for Linux kernel drivers
 This package provides firmware used by Linux kernel drivers.
ubuntu@ubuntu:~$

```

```

ubuntu@ubuntu:~$ sudo dpkg -s linux-firmware-raspi2
Package: linux-firmware-raspi2
Status: install ok installed
Priority: optional
Section: multiverse/misc
Installed-Size: 12464
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: arm64
Version: 1.20190215-0ubuntu0.18.04.1
Description: RaspberryPi2/3 GPU firmware and bootloaders
 This package contains all the proprietary files necessary to boot a
 RaspberryPi2/3 board.
Homepage: https://github.com/raspberrypi/firmware
ubuntu@ubuntu:~$

```

---

### Post by makem2 on 2019-10-20
> **chili555 said:**
> Please try:

```
cd /lib/firmware/brcm
sudo wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm/brcmfmac43430-sdio.clm_blob
sudo wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm/brcmfmac43430-sdio.txt
```Reboot and show us:```
dmesg | grep brcm
```

```

ubuntu@ubuntu:~$ dmesg | grep brcm
[   19.128742] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac43430-sdio.bin for chip 0x00a9a6(43430) rev 0x000001
[   19.171772] usbcore: registered new interface driver brcmfmac
[   19.436727] brcmfmac: brcmf_sdio_hostmail: mailbox indicates firmware halted
[   21.986918] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   22.007569] brcmfmac: brcmf_c_process_clm_blob: clmload (7222 byte file) failed (-110); 
[   24.546967] brcmfmac: brcmf_sdio_bus_rxctl: resumed on timeout
[   24.567830] brcmfmac: brcmf_c_process_clm_blob: get clmload_status failed (-110)
[   24.589863] brcmfmac: brcmf_c_preinit_dcmds: download CLM blob file failed, -5
[   24.610770] brcmfmac: brcmf_bus_started: failed: -5
[   24.628632] brcmfmac: brcmf_sdio_firmware_callback: dongle is not responding
ubuntu@ubuntu:~$

```

---

### Post by makem2 on 2019-10-21
Would it be possible to completely disable on board wifi and use a USB dongle instead?

I read of problems with this chip in the Pi4 too and am thinking that to get on, I could use a dongle until the issue is resolved.

---

### Post by chili555 on 2019-10-21
Aside from the possibility of a faulty device, I regret that I haven't any other suggestions.> 
Would it be possible to completely disable on board wifi and use a USB dongle instead?
Certainly.

---

### Post by makem2 on 2019-10-21
May I ask if you will offer guidance in disabling the wifi please?

---

### Post by chili555 on 2019-10-21
> **makem2 said:**
> May I ask if you will offer guidance in disabling the wifi please?Simply blacklist the driver:

```
sudo -i
echo "blacklist brcmfmac"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r brcmfmac
exit
```

---

### Post by makem2 on 2019-10-21
Thank you.

---

