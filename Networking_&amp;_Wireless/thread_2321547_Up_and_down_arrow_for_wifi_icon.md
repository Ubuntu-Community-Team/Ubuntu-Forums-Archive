---
title: "Up and down arrow for wifi icon"
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by Mapring on 2016-04-23
I have got an up and down arrow as my wifi icon. I believe this is a bug, and because of this, I cannot see other wifi access through the icon. My only option is to go the network settings from the system configuration.

[URL="http://imgur.com/jeagJdD"]
[ATTACH=CONFIG]268552[/ATTACH][/URL]

Edit: I only have this icon when I am connected to a wifi access.

---

### Post by coffeecat on 2016-04-23
The up and down arrows icon means that you are connected via ethernet. Click on the icon, and then click on "Disconnect" under where it says "Wired Connection 1". If you are connected both by ethernet and by wireless, the up and down icon takes precedence. Once you are disconnected from ethernet, you will see the wireless icon.

---

### Post by DuckHook on 2016-04-23
**Moved**

You will have better chance for an answer to your question in the Networking & Wireless forum

---

### Post by RobGoss on 2016-04-23
This is ***not a bug, ***it's letting you view all the Wifi connections available for you to choose...

---

### Post by circus42 on 2016-09-28
I'm having the same issue. I am not connected via ethernet. Wifi is still working thou, it just doesn't show up in the networks tab (when I click the up-and-down arrow symbol). So not much of an issue... just confounding.

---

### Post by Keith_Helms on 2016-09-29
The up and down arrows usually mean you're connected to ethernet.  There   is a network manager bug I also ran into where the wifi sometimes was  connected, but had lost the capability to show other  networks and was  displaying the up and down arrows instead of the signal  strength  "arcs".  I resolved the problem on my system by disabling  power  managment on the wifi adapter.  Like just about anything on Linux,   there are half a dozen suggested ways to do this and some work for some   people and don't work for others.

One recommendation was to create a file named /etc/pm/power.d/wireless   and put the following in it (I think I added the sleep command):
```
#!/bin/bash

sleep 20
/sbin/iwconfig wlp3s0 power off
```

And then mark the file as executable:
```
sudo chmod +x /etc/pm/power.d/wireless
```

That solution didn't work for me, so I added the script to the system crontab
```
sudo crontab -e
```
then add a line at the bottom
```
@reboot /etc/pm/power.d/wireless
```
I believe it's the following sequence to save the updated crontab
ctrl-o
enter
ctrl-x

---

### Post by jeremy31 on 2016-09-29
This was a bug that I thought was fixed in newer updates, this command should still fix it
```
systemctl restart NetworkManager.service
```

---

### Post by pedmer on 2016-10-10
> **jeremy31 said:**
> This was a bug that I thought was fixed in newer updates, this command should still fix it
```
systemctl restart NetworkManager.service
```

Solved it. Thank you!

---

### Post by mick3lson on 2016-11-25
> **jeremy31 said:**
> This was a bug that I thought was fixed in newer updates, this command should still fix it
```
systemctl restart NetworkManager.service
```

This command solve the issue but when I restart or shutdown the system the arrow icon there are again. My wireless adapter is BCM94352HMB
on Ubuntu 16.10.

---

### Post by jeremy31 on 2016-11-25
> **mick3lson said:**
> This command solve the issue but when I restart or shutdown the system the arrow icon there are again. My wireless adapter is BCM94352HMB
on Ubuntu 16.10.

It can probably be fixed by editing grub to prevent the wireless interface from being renamed
```
sudo -H gedit /etc/default/grub
```

Got to the line with 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

And add ```
net.ifnames=0
```
inside of the quotes so that it is
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ifnames=0"
```
Save and exit gedit, then
```
sudo update-grub
```

Reboot

---

### Post by mick3lson on 2016-11-25
I've update grub but without success, this is my grub conf:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0    
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ifnames=0"
GRUB_CMDLINE_LINUX=""

```

---

### Post by jeremy31 on 2016-11-26
What are the results from ```
iwconfig; cat /proc/cmdline
```

---

### Post by mick3lson on 2016-11-26
This is the result:

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 14:DA:E9:FA:CD:10   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
BOOT_IMAGE=/boot/vmlinuz-4.8.0-27-generic.efi.signed root=UUID=c9a824a2-32a0-4769-a860-fb514020dc17 ro quiet splash net.ifnames=0 vt.handoff=7

```

---

### Post by jeremy31 on 2016-11-26
Are you also connected to an ethernet cable?

---

### Post by mick3lson on 2016-11-26
Absolutely not, only wifi.

---

### Post by jeremy31 on 2016-11-26
I would see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) and report a bug against network-manager.  I haven't had any issues with this happening on my computers but one of the first bug reports stated that it was an issue with the interfaces being renamed and that is not the case now since your device is wlan0

---

### Post by mick3lson on 2016-11-26
Ok this point I would know if is possible to install correctly the wifi driver for BCM4352, or there are problem with broadcom drivers. I tried  another wifi card and all work smoothly included bluetooth.
Only with BCM4352 I'm having this issue with wifi and bluetooth, I'm using this card for for reasons of compatibility with MacOS Sierra, currently my laptop has a system with dual-boot Ubuntu and Mac Osx.

Sincerely

---

### Post by jeremy31 on 2016-11-26
Post results for ```
lspci -nnk | grep -iA2 net
```
I know a lot of the wifi cards used in Mac's are only supported by the wl module from broadcom, also known as broadcom-sta/bcmwl-kernel-source

If another card works perfectly in Ubuntu it would push me more to file a bug report

---

### Post by mick3lson on 2016-11-27
This is the results:
```

03:00.0 Network controller [0280]: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    DeviceName: WLAN
    Subsystem: AzureWave BCM4352 802.11ac Wireless Network Adapter [1a3b:2123]
    Kernel driver in use: wl
    Kernel modules: bcma, wl
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:17f6]
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by jeremy31 on 2016-11-27
That is a device supported only by wl, hopefully a bug report will result in a fix

---

### Post by mick3lson on 2016-11-27
It's possible to load this command:

```
systemctl restart NetworkManager.service
``` 

with a script or other when boot ubuntu.

---

### Post by jeremy31 on 2016-11-27
It is possible that putting the command in /etc/rc.local above the exit 0 line might work

---

### Post by mick3lson on 2016-11-27
Ok thank's, now all work well with wifi icon, only bluetooth not work, I don't know if is possible to solve this issue.

---

### Post by jeremy31 on 2016-11-27
For the bluetooth issue post results for ```
lsusb; lsmod | grep blue; dmesg | egrep -i 'blue|firm'; rfkill list all
```

---

### Post by mick3lson on 2016-11-27
```
Bus 002 Device 003: ID 13d3:3404 IMC Networks 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b370 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bluetooth             552960  31 btrtl,btintel,bnep,btbcm,rfcomm,btusb
[    0.154555] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    9.492303] [Firmware Bug]: ACPI(DGFX) defines _DOD but not _DOS
[   12.137261] Bluetooth: Core ver 2.21
[   12.137283] Bluetooth: HCI device and connection manager initialized
[   12.137318] Bluetooth: HCI socket layer initialized
[   12.137320] Bluetooth: L2CAP socket layer initialized
[   12.137326] Bluetooth: SCO socket layer initialized
[   12.373039] Bluetooth: hci0: BCM: chip id 63
[   12.395511] Bluetooth: hci0: BCM20702A
[   12.397031] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[   12.427530] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-13d3-3404.hcd failed with error -2
[   12.427534] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-13d3-3404.hcd not found
[   13.393168] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.393170] Bluetooth: BNEP filters: protocol multicast
[   13.393173] Bluetooth: BNEP socket layer initialized
[   17.237934] Bluetooth: RFCOMM TTY layer initialized
[   17.237940] Bluetooth: RFCOMM socket layer initialized
[   17.237945] Bluetooth: RFCOMM ver 1.11
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by jeremy31 on 2016-11-28
Might be an easy fix
```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-13d3-3404.hcd
sudo modprobe -r btusb
sudo modprobe btusb
```

---

### Post by moteprime on 2016-11-28
It's a bug, you can't do anything about it but workarounds.
There's several reports on launchpad, but it's not getting fixed.

---

### Post by mick3lson on 2016-11-28
> **jeremy31 said:**
> Might be an easy fix
```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-13d3-3404.hcd
sudo modprobe -r btusb
sudo modprobe btusb
```



I tried it and it works partially, my mouse bluetooth work perfectly but I can not send and receive files from other devices, for example my smartphone android, although if they are paired.

---

### Post by moteprime on 2016-11-28
@mick3lson
Are you getting the a ethernet arrows instead of Wifi icon when you wakeup you laptop after suspend?

---

### Post by mick3lson on 2016-11-28
> **moteprime said:**
> @mick3lson
Are you getting the a ethernet arrows instead of Wifi icon when you wakeup you laptop after suspend?

All work smoothly in suspend mode, but sometimes when restart the laptop the arrows icon reappear despite I have entered  on rc.local 

```

#!/bin/bash 

service network-manager restart
 
exit 0

```

---

### Post by moteprime on 2016-11-28
There's several hundred users that has problems with the nm.-applet not working after coming back from suspend.

---

### Post by Rrory on 2016-11-28
I upgraded to Yakety Yak, just had an update today and now my wifi icon totally disappeared. How do I get it back please?

---

### Post by wildmanne39 on 2016-11-28
Do you see the double lines? or is networking applet missing completely?

---

### Post by Rrory on 2016-11-28
the applet entirely disappeared!
I had to go and find the Network folder  to get connected to my wifi, thank god Ubuntu is so user friendly for the semi-clueless

---

### Post by wildmanne39 on 2016-11-28
Please do:

```
sudo apt-get install --reinstall network-manager-gnome 
```
That should make the applet show in the panel again.

---

### Post by Rrory on 2016-11-28
It's back! Worked like a charm
thank you:D

---

### Post by wildmanne39 on 2016-11-28
> **Rrory said:**
> It's back! Worked like a charm
thank you:DGlad it worked!
Enjoy!

---

### Post by jeremy31 on 2016-11-29
> **mick3lson said:**
> I tried it and it works partially, my mouse bluetooth work perfectly but I can not send and receive files from other devices, for example my smartphone android, although if they are paired.

Search Dash for Personal File Sharing and see if receive files over bluetooth is enabled

---

### Post by mick3lson on 2016-11-29
> **jeremy31 said:**
> Search Dash for Personal File Sharing and see if receive files over bluetooth is enabled

Yes is enabled, when the connection bluetooth is active there is a padlock near the bluetooth icon, I don't know if it's normal.

---

### Post by wesselsnaak on 2017-01-04
The bug doesn't seems to appear when there is no WiFi connection established before and during the installation of Ubuntu (Ubuntu 16.04 LTS, AC-8260)

---

### Post by tebbens on 2017-03-11
Just did a new install of 16.04 LTS and now I also get the up/down arrows.
During a 'Try Ubuntu' it came up with the normal connection status, but with a complete install I get the 2 arrows:

> 
lspci -nnk | grep -iA2 net


> 
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection I219-LM [8086:156f] (rev 21)
	Subsystem: Dell Ethernet Connection I219-LM [1028:071c]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Wireless 8260 [8086:0050]
	Kernel driver in use: iwlwifi


UPDATE:
After the first reboot, no more up/down arrows... I get the normal signal strength icon....cool!

---

