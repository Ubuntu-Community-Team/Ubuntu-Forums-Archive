---
title: "Ubuntu 16.04 Bluetooth issues. Tired of fixing."
date: 2018-10-27
forum: Networking &amp; Wireless
---

### Post by rajatar08 on 2018-10-27
I have been dealing with a lot of issues with Bluetooth on my Lenovo Y510P. I have tried many things which fix it temporarily but can't really get to the bottom of the issue why it keeps occurring again. Not able to connect anything to Bluetooth on my laptop :(


Here is some information to get started with:


```
# rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


```
 # hcitool dev
Devices:

```


```
 # bluetoothctl 
[bluetooth]# power on
No default controller available
[bluetooth]# list
[bluetooth]# 

```


```

systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2018-10-27 14:05:12 PDT; 29min ago
     Docs: man:bluetoothd(8)
 Main PID: 1384 (bluetoothd)
   Status: "Running"
    Tasks: 1
   Memory: 1.1M
      CPU: 11ms
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1384 /usr/lib/bluetooth/bluetoothd


Oct 27 14:05:12 talksick-Lenovo-IdeaPad-Y510P systemd[1]: Starting Bluetooth service...
Oct 27 14:05:12 talksick-Lenovo-IdeaPad-Y510P bluetoothd[1384]: Bluetooth daemon 5.37
Oct 27 14:05:12 talksick-Lenovo-IdeaPad-Y510P bluetoothd[1384]: Unknown key AutoEnable in main.conf
Oct 27 14:05:12 talksick-Lenovo-IdeaPad-Y510P bluetoothd[1384]: Starting SDP server
Oct 27 14:05:12 talksick-Lenovo-IdeaPad-Y510P systemd[1]: Started Bluetooth service.
Oct 27 14:05:13 talksick-Lenovo-IdeaPad-Y510P bluetoothd[1384]: Bluetooth management interface 1.14 initialized

```


```
 # lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 755M] (rev ff)
07:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
08:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```




Any kind of help is appreciated!

---

### Post by jeremy31 on 2018-10-27
Post results for ```
uname -a; lsusb; dmesg | egrep -i 'blue|firm'; lsmod | grep blue
```

---

### Post by rajatar08 on 2018-10-27
Here:

```
 # uname -a; lsusb; dmesg | egrep -i 'blue|firm'; lsmod | grep blue

Linux talksick-Lenovo-IdeaPad-Y510P 4.15.0-38-generic #41~16.04.1-Ubuntu SMP Wed Oct 10 20:16:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.031084] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.067914] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    2.068310] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    2.374199] usb 3-7: Product: Bluetooth USB Host Controller
[    2.661257] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f01)
[   20.398942] Bluetooth: Core ver 2.22
[   20.398957] Bluetooth: HCI device and connection manager initialized
[   20.398960] Bluetooth: HCI socket layer initialized
[   20.398961] Bluetooth: L2CAP socket layer initialized
[   20.398964] Bluetooth: SCO socket layer initialized
[   23.452085] Bluetooth: hci0: command 0x0c52 tx timeout
[   25.468086] Bluetooth: hci0: command 0x0c45 tx timeout
[   27.484087] Bluetooth: hci0: command 0x0c58 tx timeout
[   29.500055] Bluetooth: hci0: command 0x1004 tx timeout
[   39.089056] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.089057] Bluetooth: BNEP filters: protocol multicast
[   39.089060] Bluetooth: BNEP socket layer initialized
bluetooth             557056  13 btrtl,btintel,btbcm,bnep,ath3k,btusb
ecdh_generic           24576  1 bluetooth

```

---

### Post by jeremy31 on 2018-10-27
That might require a shutdown and cold boot to fix.  I am not sure why that happens at times myself.  I know some earlier kernels from 4.15 messed that bluetooth device up

---

### Post by rajatar08 on 2018-10-27
> **jeremy31 said:**
> That might require a shutdown and cold boot to fix. I am not sure why that happens at times myself. I know some earlier kernels from 4.15 messed that bluetooth device up

Cold boot gives me this error while searching for devices in blueman-applet :
```
 Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available 
```

I tried the following:
```
# pactl load-module module-bluetooth-discover 
```

But blueman results in the following:
```
 Connection Failed: blueman.bluez.errors.DBusFailedError: Host is down 
```

---

### Post by jeremy31 on 2018-10-27
You could try an old fix ```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/bluetooth.conf
echo "blacklist ath3k" | sudo tee -a /etc/modprobe.d/bluetooth.conf
```
Then after reboot, do
```
sudo modprobe ath3k
sudo modprobe btusb
```
See if that works

---

### Post by rajatar08 on 2018-10-27
> **jeremy31 said:**
> You could try an old fix ```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/bluetooth.conf
echo "blacklist ath3k" | sudo tee -a /etc/modprobe.d/bluetooth.conf
```
Then after reboot, do
```
sudo modprobe ath3k
sudo modprobe btusb
```
See if that works

Tried this. I seem to be getting "No adapters found" when trying to pair new device on blueman-applet. Can any logs help?

---

### Post by jeremy31 on 2018-10-27
I don't know at this point as I have the same wifi/bluetooth device on this laptop using Ubuntu 18.04 and I can connect to bluetooth headphones and use them

---

### Post by rajatar08 on 2018-10-27
> **jeremy31 said:**
> I don't know at this point as I have the same wifi/bluetooth device on this laptop using Ubuntu 18.04 and I can connect to bluetooth headphones and use them

Thats great. Did you do any fixes to get it working smoothly?

---

### Post by mc4man on 2018-10-27
Using about or maybe exactly same laptop, bluetooth works fine here ootb in 16.04. 
Noting I just use it for a speaker and there are a few little things to do so auto discover & auto connect work.
Why are you using blueman?

```
$  inxi -SCNG
System:    Host: doug-Lenovo-IdeaPad-Y510P Kernel: 4.15.0-36-generic x86_64 bits: 64 Desktop: Unity 
           Distro: Ubuntu 16.04.5 LTS (Xenial Xerus) 
CPU:       Topology: Quad Core model: Intel Core i7-4700MQ bits: 64 type: MT MCP L2 cache: 6144 KiB 
           Speed: 1996 MHz min/max: 800/3400 MHz Core speeds (MHz): 1: 1996 2: 1999 3: 1996 4: 2001 5: 1995 
           6: 1995 7: 1995 8: 1999 
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 v: kernel 
           Card-2: NVIDIA GK107M [GeForce GT 755M] driver: nouveau v: kernel 
           Display: x11 server: X.Org 1.19.6 driver: intel resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile v: 4.5 Mesa 18.0.5 
Network:   Card-1: Qualcomm Atheros QCA8171 Gigabit Ethernet driver: alx 
           Card-2: Intel Wireless 7260 driver: iwlwifi 

```

---

### Post by jeremy31 on 2018-10-27
> **mc4man said:**
> Using about or maybe exactly same laptop, bluetooth works fine here ootb in 16.04. 
Noting I just use it for a speaker and there are a few little things to do so auto discover & auto connect work.
Why are you using blueman?

```
$  inxi -SCNG
System:    Host: doug-Lenovo-IdeaPad-Y510P Kernel: 4.15.0-36-generic x86_64 bits: 64 Desktop: Unity 
           Distro: Ubuntu 16.04.5 LTS (Xenial Xerus) 
CPU:       Topology: Quad Core model: Intel Core i7-4700MQ bits: 64 type: MT MCP L2 cache: 6144 KiB 
           Speed: 1996 MHz min/max: 800/3400 MHz Core speeds (MHz): 1: 1996 2: 1999 3: 1996 4: 2001 5: 1995 
           6: 1995 7: 1995 8: 1999 
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 v: kernel 
           Card-2: NVIDIA GK107M [GeForce GT 755M] driver: nouveau v: kernel 
           Display: x11 server: X.Org 1.19.6 driver: intel resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile v: 4.5 Mesa 18.0.5 
Network:   Card-1: Qualcomm Atheros QCA8171 Gigabit Ethernet driver: alx 
           Card-2: Intel Wireless 7260 driver: iwlwifi 

```

But you have a different wifi card and different bluetooth device.  With the Intel 7260 wifi, there is a good chance that the bluetooth shows in lsusb results as 8088:07dc when the poster has the Atheros AR9485 wifi with AR3012 bluetooth with ID 0cf3:3004

---

### Post by rajatar08 on 2018-10-27
> **mc4man said:**
> Using about or maybe exactly same laptop, bluetooth works fine here ootb in 16.04. 
Noting I just use it for a speaker and there are a few little things to do so auto discover & auto connect work.
Why are you using blueman?


I have been trying to get it working for so long, don't even remember when I got onto blueman. Anyway, which tool should I be using instead of blueman?

And also, my info (pretty close):

```
 # inxi -SCNG               

System:    Host: talksick-Lenovo-IdeaPad-Y510P Kernel: 4.15.0-38-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.5 Distro: Ubuntu 16.04 xenial
CPU:       Quad core Intel Core i7-4700MQ (-HT-MCP-) cache: 6144 KB 
           clock speeds: max: 3400 MHz 1: 1464 MHz 2: 2692 MHz 3: 2877 MHz
           4: 2864 MHz 5: 2912 MHz 6: 2977 MHz 7: 2971 MHz 8: 2744 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 755M]
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@59.93hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile
           GLX Version: 3.0 Mesa 18.0.5
Network:   Card-1: Qualcomm Atheros QCA8171 Gigabit Ethernet driver: alx
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k

```

---

### Post by mc4man on 2018-10-27
> **jeremy31 said:**
> But you have a different wifi card and different bluetooth device.  With the Intel 7260 wifi, there is a good chance that the bluetooth shows in lsusb results as 8088:07dc when the poster has the Atheros AR9485 wifi with AR3012 bluetooth with ID 0cf3:3004
Yep, missed that, didn't   scroll down his lspci fully..

---

### Post by rajatar08 on 2018-11-05
> **jeremy31 said:**
> You could try an old fix ```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/bluetooth.conf
echo "blacklist ath3k" | sudo tee -a /etc/modprobe.d/bluetooth.conf
```
Then after reboot, do
```
sudo modprobe ath3k
sudo modprobe btusb
```
See if that works

So this kinda worked for me, but this seems to be needed after every reboot. So I started looking in this direction and found a related post here: [https://ubuntuforums.org/showthread.php?t=2350200&page=2&p=13731981#post13731981](https://ubuntuforums.org/showthread.php?t=2350200&page=2&p=13731981#post13731981)

Also, in addition to it, I added [COLOR=#000000][FONT=&amp]modprobe btusb.

[/FONT][/COLOR]```

sleep 30
modprobe ath3k
sleep 30
modprobe btusb

```

---

