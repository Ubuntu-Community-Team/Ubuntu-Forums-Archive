---
title: "Qualcomm Atheros QCA9565 / AR9565, when BLuetooth is on used Wifi is slowed"
date: 2019-01-06
forum: Networking &amp; Wireless
---

### Post by yencool on 2019-01-06
Hello, 

I know that Qualcomm Atheros QCA9565 / AR9565 manage Bluetooth and Wifi,  when I connect my bluetooth headset the wifi decrease and/or does not  response.
I'm also new to Ubuntu.

Some info:

```
root@yendroid:/home/jean-christophe# inxi -Fxz
System:    Host: yendroid Kernel: 4.18.0-13-generic x86_64 bits: 64 compiler: gcc v: 8.2.0 
           Desktop: Gnome 3.30.1 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:   Type: Laptop System: ASUSTeK product: X751LJ v: 1.0 serial: <filter> 
           Mobo: ASUSTeK model: X751LJ v: 1.0 serial: <filter> UEFI: American Megatrends v: X751LJ.706 
           date: 12/07/2015 
Battery:   ID-1: BAT0 charge: 30.7 Wh condition: 32.2/37.4 Wh (86%) model: ASUSTeK ASUS Battery 
           status: Not charging 
           Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M560 charge: 0% status: Discharging 
CPU:       Topology: Dual Core model: Intel Core i5-5200U bits: 64 type: MT MCP arch: Broadwell rev: 4 
           L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 17575 
           Speed: 1076 MHz min/max: 500/2700 MHz Core speeds (MHz): 1: 850 2: 871 3: 846 4: 854 
Graphics:  Device-1: Intel HD Graphics 5500 driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GK208BM [GeForce 920M] driver: nvidia v: 390.87 bus ID: 04:00.0 
           Display: server: X.Org 1.20.1 driver: modesetting,nvidia unloaded: fbdev,nouveau,vesa 
           resolution: 1600x900~60Hz 
           OpenGL: renderer: GeForce 920M/PCIe/SSE2 v: 4.6.0 NVIDIA 390.87 direct render: Yes 
Audio:     Device-1: Intel Broadwell-U Audio driver: snd_hda_intel v: kernel bus ID: 00:03.0 
           Device-2: Intel Wildcat Point-LP High Definition Audio driver: snd_hda_intel v: kernel 
           bus ID: 00:1b.0 
           Sound Server: ALSA v: k4.18.0-13-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 v: 2.3LK-NAPI 
           port: e000 bus ID: 02:00.1 
           IF: enp2s0f1 state: down mac: <filter> 
           Device-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k v: kernel 
           bus ID: 03:00.0 
           IF: wlp3s0 state: up mac: <filter> 
Drives:    Local Storage: total: 465.76 GiB used: 9.49 GiB (2.0%) 
           ID-1: /dev/sda vendor: Crucial model: CT500MX500SSD1 size: 465.76 GiB temp: 37 C 
Partition: ID-1: / size: 456.96 GiB used: 9.49 GiB (2.1%) fs: ext4 dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 49.0 C mobo: 27.8 C gpu: nvidia temp: 47 C 
           Fan Speeds (RPM): cpu: 2100 
Info:      Processes: 245 Uptime: 1h 01m Memory: 11.60 GiB used: 2.63 GiB (22.7%) Init: systemd runlevel: 5 
           Compilers: gcc: 8.2.0 Shell: bash v: 4.4.19 inxi: 3.0.24 
root@yendroid:/home/jean-christophe# 
```

```
root@yendroid:/home/jean-christophe#  rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@yendroid:/home/jean-christophe# 

```

```
root@yendroid:/home/jean-christophe# systool -vm ath9k
Module = "ath9k"

  Attributes:
    coresize            = "151552"
    initsize            = "0"
    initstate           = "live"
    refcnt              = "0"
    srcversion          = "893A0832FB72FDD7D4005A5"
    taint               = ""
    uevent              = <store method only>

  Parameters:
    blink               = "0"
    bt_ant_diversity    = "0"
    btcoex_enable       = "1"
    led_active_high     = "-1"
    nohwcrypt           = "0"
    ps_enable           = "0"
    use_chanctx         = "0"
    use_msi             = "0"

  Sections:
    .bss                = "0xffffffffc06c6a00"
    .data               = "0xffffffffc06c6000"
    .exit.text          = "0xffffffffc06bfcc5"
    .gnu.linkonce.this_module= "0xffffffffc06c66c0"
    .init.rodata        = "0xffffffffc045d000"
    .init.text          = "0xffffffffc045c000"
    .note.gnu.build-id  = "0xffffffffc06c0000"
    .parainstructions   = "0xffffffffc06c5c30"
    .rodata             = "0xffffffffc06c0040"
    .rodata.str1.1      = "0xffffffffc06c4ab7"
    .rodata.str1.8      = "0xffffffffc06c4210"
    .smp_locks          = "0xffffffffc06c5a10"
    .strtab             = "0xffffffffc0463598"
    .symtab             = "0xffffffffc045e000"
    .text               = "0xffffffffc06a7000"
    .text.unlikely      = "0xffffffffc06bfcef"
    __bug_table         = "0xffffffffc06c6518"
    __mcount_loc        = "0xffffffffc06c38c0"
    __param             = "0xffffffffc06c5ac8"

root@yendroid:/home/jean-christophe# 

```


```
root@yendroid:/home/jean-christophe# service bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2019-01-06 19:03:46 CET; 1h 8min ago
     Docs: man:bluetoothd(8)
 Main PID: 859 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   Memory: 2.9M
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;859 /usr/lib/bluetooth/bluetoothd

janv. 06 19:03:46 yendroid systemd[1]: Starting Bluetooth service...
janv. 06 19:03:46 yendroid bluetoothd[859]: Bluetooth daemon 5.50
janv. 06 19:03:46 yendroid bluetoothd[859]: Starting SDP server
janv. 06 19:03:46 yendroid bluetoothd[859]: Bluetooth management interface 1.14 initialized
janv. 06 19:03:46 yendroid systemd[1]: Started Bluetooth service.
janv. 06 19:04:02 yendroid bluetoothd[859]: Endpoint registered: sender=:1.307 path=/MediaEndpoint/A2DPSource
janv. 06 19:04:02 yendroid bluetoothd[859]: Endpoint registered: sender=:1.307 path=/MediaEndpoint/A2DPSink
janv. 06 19:05:34 yendroid bluetoothd[859]: Unable to get Headset Voice gateway SDP record: Host is down
janv. 06 19:24:44 yendroid bluetoothd[859]: /org/bluez/hci0/dev_CC_98_8B_3D_E2_AB/fd0: fd(37) ready
root@yendroid:/home/jean-christophe# 
```

```
root@yendroid:/home/jean-christophe# dpkg -l | grep blue
rc  blueman                                    2.0.5-1ubuntu1                                amd64        Graphical bluetooth manager
ii  bluez                                      5.50-0ubuntu1                                 amd64        Bluetooth tools and daemons
ii  bluez-cups                                 5.50-0ubuntu1                                 amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                5.50-0ubuntu1                                 amd64        bluez obex daemon
ii  gir1.2-gnomebluetooth-1.0:amd64            3.28.2-2                                      amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth                            3.28.2-2                                      amd64        GNOME Bluetooth tools
ii  libbluetooth3:amd64                        5.50-0ubuntu1                                 amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth13:amd64                 3.28.2-2                                      amd64        GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth                1:12.2-0ubuntu4                               amd64        Bluetooth module for PulseAudio sound server
root@yendroid:/home/jean-christophe# 

```

I followed the advice from [https://wireless.wiki.kernel.org/en/users/drivers/ath9k/btcoex](https://wireless.wiki.kernel.org/en/users/drivers/ath9k/btcoex)
I tried to add in /etc/modprobe/ a conf file as ath9k.conf with the  btcoex_enable=1 and reboot but this did not fix my issue. 
I also tried :
> btcoex_enable=1
bt_ant_diversity=1
and 
> 
btcoex_enable=1
bt_ant_diversity=1
nohwcrypt=1

I also try to blacklist asus_nd_wmi, without any success.

Do you have an idea to solve my problem?

Thank you very much.

---

### Post by nilandj-nilandsplace on 2019-06-27
Perhaps the text is wrong
Try; options ath9k nohwcrypt=1
and; options ath9k btcoex_enable=1
Source: [https://askubuntu.com/questions/440256/how-do-i-create-a-system-file-etc-modprobe-d-ath9k-conf](https://askubuntu.com/questions/440256/how-do-i-create-a-system-file-etc-modprobe-d-ath9k-conf)
-James

---

### Post by deckard11223344 on 2020-05-06
Hello.

I have the same hardware. I experienced similar issues as you. In my case, even the wifi signal got lost and I had to disconnect and connect again to the network to fix the issue. Additionally, the audio of my bluetooth headphones, working fine at the beginning, after pausing the audio source and resuming after some seconds, sometimes, began to work strangely, stuttering and de-syncronized.

I wanted to share that, after some research, I could fix the issue with the modification suggested in 

[https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Bluetooth_headset_replay_problems](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Bluetooth_headset_replay_problems)

I hope that this can help you too in solving your issues.

Best Regards.

---

