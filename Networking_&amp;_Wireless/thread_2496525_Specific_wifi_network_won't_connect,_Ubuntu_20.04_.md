---
title: "Specific wifi network won't connect, Ubuntu 20.04 LTS"
date: 2024-04-01
forum: Networking &amp; Wireless
---

### Post by teknodude2 on 2024-04-01
[SIZE=3][FONT=arial]I have Dell XPS 13 (9350 model) with dual boot Ubuntu 20.04 and Win 10. Ubuntu fails to connect to a specific wifi network and constantly requests to re enter the password. Other networks like my phone hotspot and home wifi will connect successfully. I have tried loading Ubuntu 22.04 on usb and the connection problem is the same. My windows 10 boot and android phone will connect to this wifi network with no problem.

I had previously used this wifi network 3 months ago on Ubuntu 20.04 and it was fine. The only difference in that 3 month duration was that I had downloaded the system updates when prompted, so maybe that’s the issue.  I don’t have access to the router, so I can’t look into the specific wifi settings. When log into this wifi network in windows 10, I do get a pop-up that the connected network is using an outdated encryption. This led to me being suspicious that maybe Ubuntu doesn’t like outdated networks. The wifi info in windows 10 shows WIFI 4, 802.11n and TKIP encryption. I have an old Linksys router with DD-wrt installed, so I tested whether Ubuntu could connect with WEP and WPA2-TkIp. It connected fine.

Other things I tried from googling

[/FONT][/SIZE]
[LIST]
[*][SIZE=3][FONT=arial]nm-connection-editor to delete and create the connection with settings, but the result is the same. I tried different manual settings for 2.4 and 5 Ghz. Also I tried random mac address.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]nm-cli terminal command to connect[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]&#8203;[/FONT][/SIZE]
[/LIST]
[SIZE=3][FONT=arial]The logs don't show anything to help trouble shoot


```
journalctl -b -9 -o json-pretty -u NetworkManager | grep NetworkName
    "MESSAGE" : "<info>  [1711926934.0907] device (wlp58s0): Activation: (wifi) access point 'NetworkName' has security, but secrets are required.",
    "MESSAGE" : "<info>  [1711926939.8669] device (wlp58s0): Activation: (wifi) connection 'NetworkName' has security, and secrets exist.  No new secrets needed.",
    "MESSAGE" : "<info>  [1711926939.8686] Config: added 'ssid' value 'NetworkName'",
    "MESSAGE" : "<info>  [1711926966.3185] device (wlp58s0): Activation: (wifi) connection 'NetworkName' has security, and secrets exist.  No new secrets needed.",
    "MESSAGE" : "<info>  [1711926966.3185] Config: added 'ssid' value 'NetworkName'",
    "MESSAGE" : "<info>  [1711926994.6790] device (wlp58s0): Activation: (wifi) connection 'NetworkName' has security, and secrets exist.  No new secrets needed."
    "MESSAGE" : "<info>  [1711926994.6791] Config: added 'ssid' value 'NetworkName'",
    "MESSAGE" : "<warn>  [1711927020.0488] device (wlp58s0): Activation: failed for connection 'NetworkName'",

```

```
lspci -knn | grep Net -A33a:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4350 802.11ac Wireless Network Adapter [14e4:43a3] (rev 08)
    Subsystem: Dell BCM4350 802.11ac Wireless Network Adapter [1028:0023]
    Kernel driver in use: brcmfmac
    Kernel modules: brcmfmac



```

There is an error message when the the wifi driver is loaded, but I believe it's normal. The default driver doesn't load, so it falls back on another one. I checked the package and the correct driver is included in the Ubuntu distribution.

```
 journalctl -b -9 -o json-pretty  | grep brcm    "MESSAGE" : "usbcore: registered new interface driver brcmfmac",
    "MESSAGE" : "brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac4350-pcie for chip BCM4350/8",
    "MESSAGE" : "brcmfmac 0000:3a:00.0: Direct firmware load for brcm/brcmfmac4350-pcie.Dell Inc.-XPS 13 9350.bin failed with error -2",
    "MESSAGE" : "brcmfmac 0000:3a:00.0: Direct firmware load for brcm/brcmfmac4350-pcie.Dell Inc.-XPS 13 9350.txt failed with error -2",
    "MESSAGE" : "brcmfmac 0000:3a:00.0: Direct firmware load for brcm/brcmfmac4350-pcie.txt failed with error -2",
    "MESSAGE" : "brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac4350-pcie for chip BCM4350/8",
    "MESSAGE" : "brcmfmac: brcmf_c_process_clm_blob: no clm_blob available (err=-2), device may have limited channels available",
    "MESSAGE" : "brcmfmac: brcmf_c_preinit_dcmds: Firmware: BCM4350/8 wl0: Oct 22 2015 06:16:26 version 7.35.180.119 (r594535) FWID 01-e791c176",
    "MESSAGE" : "Bluetooth: hci0: BCM4350C5 'brcm/BCM-0a5c-6412.hcd' Patch",
    "MESSAGE" : "<info>  [1711924540.7509] rfkill0: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.4/0000:3a:00.0/ieee80211/phy0/rfkill0) (driver brcmfmac)",
    "MESSAGE" : "brcmfmac 0000:3a:00.0 wlp58s0: renamed from wlan0",



```

[COLOR=#000000]I’m at loss now on the problem. Again I can connect to this wifi network with no issue with windows and android. I know my Ubuntu wifi works because I can login to other wifi networks. For some reason, this specific network will not connect with Ubuntu. I might try downloading an older version like 18.04 and load it on live usb to test.[/COLOR][/FONT][/SIZE]

---

### Post by jeremy31 on 2024-04-01
See the wireless script link in my signature and post results

---

### Post by teknodude2 on 2024-04-01
> **jeremy31 said:**
> See the wireless script link in my signature and post results

Here you go

[HTML]https://paste.ubuntu.com/p/8RXsxqk6d2/[/HTML]

---

### Post by jeremy31 on 2024-04-01
Can you change router encryption settings to allow only WPA2 AES without TKIP?

---

### Post by teknodude2 on 2024-04-01
No, unfortunately I don't have any control over how that wifi router is set.

---

### Post by teknodude2 on 2024-04-07
I tried loading Ubuntu 18.04 on live usb and it still won't connect to that specific wifi network. I'm out of ideas. The owner of the router must have changed settings or installed a new router. In the past, I have successfully connected to that same network with previous versions of Ubuntu ( 16.04, 18.04, 20.04) with the same laptop.

---

### Post by teknodude2 on 2024-05-27
[COLOR=#000000][FONT=Arial]I had given up and just used my phone as a hotspot for some time. It turns out the owner of the wifi had changed the wifi network name and pass, but forgot to post it. The owner was actually surprised when I told him that the old wifi was still broadcasting. My laptop Ubuntu would not connect, but my android phone and windows 10 would connect fine. Also my friend's Windows 11 laptop with Intel AX200 wifi card would connect, but the connection only lasted a few seconds. The connection would go through this connect and disconnect loop.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]From looking at my Ubuntu system logs, it seems like the old wifi was connecting to a Cisco cable modem based on the gateway and mac address. With the new one, I'm connecting to a separate router now.  [/FONT][/COLOR]

---

