---
title: "Acer Aspire 5552G can't connect to wifi"
date: 2018-11-25
forum: Networking &amp; Wireless
---

### Post by tackskull on 2018-11-25
Hi there, I got from my father his old Acer Aspire 5552G laptop, he wasn't using it anymore so I decided to install Kubuntu 18.10 on it.

After installation and the update via ethernet cable I tried to connect the pc via wifi. I can see wifi networks on the wifi menu, but once I connect to my modem, and after I inserted the password, two notifications pop up on the desktop saying something like "impossible to connect" (Trying again the notifications don't pop up anymore), and I am not able to connect  the pc to the internet via wifi. 

Can you guys help me with this?

Here some pc information

```
tackskull@tackskull-Aspire-5552G:~$ inxi -F
System:
  Host: tackskull-Aspire-5552G Kernel: 4.18.0-11-generic x86_64 bits: 64 
  Desktop: KDE Plasma 5.13.5 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Laptop System: Acer product: Aspire 5552G v: V2.02 serial: <root required> 
  Mobo: Acer model: JE51_DN v: V2.02 serial: <root required> BIOS: Acer v: 2.02 
  date: 09/30/2010 
Battery:
  ID-1: BAT1 charge: 36.5 Wh condition: 36.5/47.5 Wh (77%) 
CPU:
  Topology: Dual Core model: AMD Athlon II P320 bits: 64 type: MCP 
  L2 cache: 1024 KiB 
  Speed: 800 MHz min/max: 800/2100 MHz Core speeds (MHz): 1: 800 2: 800 
Graphics:
  Device-1: AMD Park [Mobility Radeon HD 5430/5450/5470] driver: radeon v: kernel 
  Display: x11 server: X.Org 1.20.1 driver: ati,radeon 
  unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD CEDAR (DRM 2.50.0 / 4.18.0-11-generic LLVM 7.0.0) 
  v: 3.3 Mesa 18.2.2 
Audio:
  Device-1: AMD SBx00 Azalia driver: snd_hda_intel 
  Device-2: AMD Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series] 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-11-generic 
Network:
  Device-1: Broadcom and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe 
  driver: tg3 
  IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: 1c:75:08:11:14:1f 
  Device-2: Qualcomm Atheros AR9287 Wireless Network Adapter driver: ath9k 
  IF: wlp8s0 state: down mac: 4c:0f:6e:95:85:e1 
Drives:
  Local Storage: total: 465.76 GiB used: 6.89 GiB (1.5%) 
  ID-1: /dev/sda vendor: HGST (Hitachi) model: HTS545050A7E380 size: 465.76 GiB 
Partition:
  ID-1: / size: 456.50 GiB used: 6.89 GiB (1.5%) fs: ext4 dev: /dev/dm-0 
  ID-2: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1 
Sensors:
  System Temperatures: cpu: 45.2 C mobo: N/A gpu: radeon temp: 45 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 151 Uptime: 12m Memory: 3.85 GiB used: 1.08 GiB (28.0%) Shell: bash 
  inxi: 3.0.24 

```


Thanks guys

---

### Post by praseodym on 2018-11-25
Please run the wireless script from the sticky thread and show the outputs

---

### Post by tackskull on 2018-11-25
Here

[https://pastebin.com/89q75QLZ](https://pastebin.com/89q75QLZ)

---

### Post by praseodym on 2018-11-25
```
wlp8s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]3[/COLOR] dBm  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
Way too less current. Lets try
```

sudo iwconfig wlp8s0 txpower 15
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service

```

---

### Post by tackskull on 2018-11-25
I tried what you said on terminal but it doesn't work, after reboot too. 

I got a couple of photo of what happend when I try to connect to the wifi

First it ask me for the administrator password [https://www.dropbox.com/s/ne62hbe83bhd2qp/20181125_221722.jpg?dl=0](https://www.dropbox.com/s/ne62hbe83bhd2qp/20181125_221722.jpg?dl=0)

Then this 2 notifycations pop up [https://www.dropbox.com/s/gmtdoknnafaksyw/20181125_221736.jpg?dl=0](https://www.dropbox.com/s/gmtdoknnafaksyw/20181125_221736.jpg?dl=0)

---

### Post by praseodym on 2018-11-26
Does your network show up at all?
```

sudo iwlist scan
```

---

### Post by tackskull on 2018-11-26
```
tackskull@tackskull-Aspire-5552G:~$ sudo iwlist scan
[sudo] password for tackskull: 
wlp8s0    Scan completed :
          Cell 01 - Address: F0:84:2F:42:F9:70
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"FASTWEB-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a9d52df095
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0009464153545745422D31
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A3C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD940050F204104A00011010440001021041000100103B0001031047001048E434D2D8FB5A0FBF5772917EC20DCB1021000D4144422042726F616462616E64102300064441323230301024000D353433303154303038343935341042000D35343330315430303834393534105400080006D4D18404000110110006444132323030100800020000103C0001011049000600372A000120
                    IE: Unknown: DD090010180203000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057200010000
          Cell 02 - Address: F0:84:2F:42:F9:73
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"WOW FI - FASTWEB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a9d52e08ba
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0010574F57204649202D2046415354574542
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A3C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD090010180200000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057200010000
          Cell 03 - Address: 78:81:02:99:56:6B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"TIM-83869866"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000220b453d507
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000C54494D2D3833383639383636
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706495420010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B0506000F0000
                    IE: Unknown: 46053208010000
                    IE: Unknown: 2D1ABC091BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD800050F204104A0001101044000102103B000103104700101A4BE63D7038231F5A7185BBB4C34B111021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020106103C0001031049000600372A000120
                    IE: Unknown: DD090010180206000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```

---

### Post by tackskull on 2018-11-30
No solution for this?

---

### Post by tackskull on 2018-11-30
I tried right now, and wifi is working.... thanks a lot

---

