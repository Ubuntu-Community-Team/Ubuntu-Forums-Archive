---
title: "Ubuntu 22.04 WiFi Only Connecting at 72Mb/s"
date: 2023-06-02
forum: Networking &amp; Wireless
---

### Post by anspectrum on 2023-06-02
My laptop WiFi had no issue to connect at higher speeds in the past. Yesterday, I just checked while connecting to 802.11ac Access Point that laptop is not connecting higher than 72Mb/s. There is no problem with Access Point since my mobile is also connected to same AP with 433Mb/s. I suspect that in past when Ubuntu updated its kernel that resulted in breaking some WiFi features. Please suggest where I can look for to try fixing it.

lspci output
```
05:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth (rev 99)
```

inxi output
```
System:
  Host: OS Kernel: 5.15.0-73-generic x86_64 bits: 64 compiler: gcc v: 11.3.0
    Desktop: MATE 1.26.0 Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 20KN0002AD v: ThinkPad E480
    serial: <superuser required>
  Mobo: LENOVO model: 20KN0002AD v: SDK0J40697 WIN
    serial: <superuser required> UEFI-[Legacy]: LENOVO v: R0PET35W (1.12 )
    date: 01/22/2018
Battery:
  ID-1: BAT0 charge: 39.4 Wh (94.3%) condition: 41.8/45.3 Wh (92.3%)
    volts: 12.4 min: 11.1 model: SMP 01AV446 status: Charging
CPU:
  Info: quad core model: Intel Core i7-8550U bits: 64 type: MT MCP
    arch: Coffee Lake rev: A cache: L1: 256 KiB L2: 1024 KiB L3: 8 MiB
  Speed (MHz): avg: 800 min/max: 400/4000 cores: 1: 800 2: 800 3: 800
    4: 800 5: 800 6: 800 7: 800 8: 800 bogomips: 31999
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel UHD Graphics 620 vendor: Lenovo driver: i915 v: kernel
    bus-ID: 00:02.0
  Device-2: AMD Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X]
    vendor: Lenovo driver: amdgpu v: kernel bus-ID: 02:00.0
  Device-3: Acer SunplusIT Integrated Camera type: USB driver: uvcvideo
    bus-ID: 1-6:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: amdgpu,ati,modesetting unloaded: fbdev,vesa gpu: i915
    resolution: 1366x768~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2)
    v: 4.6 Mesa 22.2.5 direct render: Yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Lenovo driver: r8169 v: kernel port: c000 bus-ID: 03:00.0
  IF: enp3s0 state: down mac: 8c:16:45:38:12:d8
  Device-2: Intel Dual Band Wireless-AC 3165 Plus Bluetooth driver: iwlwifi
    v: kernel bus-ID: 05:00.0
  IF: wlp5s0 state: up mac: f8:63:3f:96:1b:c6
  Device-3: Intel Bluetooth wireless interface type: USB driver: btusb
    bus-ID: 1-5:4
  IF-ID-1: docker0 state: down mac: 02:42:5e:04:4b:98
  IF-ID-2: virbr0 state: down mac: 52:54:00:0c:81:28
```

iwconfig output
         ```
 IEEE 802.11  ESSID:"C511_5G"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: 04:F3:52:0E:27:04   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0
```

---

### Post by jeremy31 on 2023-06-02
I don't think the iwlwifi driver likes power management being on ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo iwconfig wlp5s0 power off
```
See if that works better

---

### Post by anspectrum on 2023-06-03
Earlier I had already tried that powersave option and it had not worked. This time I tried again and even restarted the laptop, speed is still 72Mb/s.

---

### Post by jeremy31 on 2023-06-03
See the wireless script link in my signature and post results

---

### Post by anspectrum on 2023-06-03
Script info is uploaded [here]("https://pastebin.com/65NypHMb")

---

### Post by jeremy31 on 2023-06-03
Can you change the encryption on the 5GHz AP?  It shows TKIP being used and that isn't recommended
See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) on how to set your country code as that may help with something in the results
> wlp5s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded

---

### Post by anspectrum on 2023-06-04
Changing country code did not help. Neither changing the encryption on AP to AES. Based on following dmesg
```
 wlp5s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded 
```                         
 
Ive also tried changing channels on AP as was mentioned [here]("https://bbs.archlinux.org/viewtopic.php?id=230231") but still no luck.

---

### Post by jeremy31 on 2023-06-04
Run the script again and post new results
```
./wireless-info
```

---

### Post by anspectrum on 2023-06-04
[Here]("https://pastebin.com/jNtvtihM") is the new script output.

---

### Post by jeremy31 on 2023-06-04
See if you can disable WPA on the router, leave WPA2 on and turn off IPv6 in Network Manager settings for the connection

---

### Post by anspectrum on 2023-06-04
Now using WPA2 only and IPv6 is disabled but still same speed and getting same message in dmesg.
```
  wlp5s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
```

---

### Post by jeremy31 on 2023-06-05
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlopt.conf
```
reboot

---

### Post by anspectrum on 2023-06-05
@jeremy31, thanks for all the support. But it seems we are looking in different direction. Still same result. Afresh output from script is [here]("https://pastebin.com/c7jiHxba").

---

### Post by jeremy31 on 2023-06-05
Post results for ```
iw dev
```

---

### Post by anspectrum on 2023-06-05
Here it is

```
iw dev
phy#0
    Unnamed/non-netdev interface
        wdev 0x3
        addr f8:63:3f:96:1b:c7
        type P2P-device
        txpower 0.00 dBm
    Interface wlp5s0
        ifindex 3
        wdev 0x1
        addr f8:63:3f:96:1b:c6
        ssid C511_5G
        type managed
        channel 149 (5745 MHz), width: 20 MHz, center1: 5745 MHz
        txpower 22.00 dBm
        multicast TXQ:
            qsz-byt    qsz-pkt    flows    drops    marks    overlmt    hashcoltx-bytes    tx-packets
            0    0    0    0    0    0    0    00

```

---

### Post by jeremy31 on 2023-06-06
Can you set the routers 5GHz channel to 42 or 58?  Is there some option on the router to set the country you are in?

It seems this problem is from Location Aware Regulatory that is in the iwlwifi driver and possibly others and it is ignoring the fact that we set the country code to JP and limits the channel bandwidth to 20 MHz

I am not sure what this LAR searches for but it could be using your set time zone/location and that is not set to Japan
If my recommended channels don't work see if you can find a channel that is allowed on the router that is outside the frequencies of this list
```
phy#0 (self-managed)
country ID: DFS-UNSET
	(2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
	(2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
	(2447 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
	(5735 - 5815 @ 20), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
```

If it thinks you are in Indonesia then it won't allow channels 96-144 which is what the results look like. changing time zone or having the router use a channel in that range might work

---

### Post by anspectrum on 2023-06-06
> **jeremy31 said:**
> Can you set the routers 5GHz channel to 42 or 58?  Is there some option on the router to set the country you are in?

There is no option to set channels 42 or 58 or any other channel that is listed as 80MHz on [wiki]("https://en.wikipedia.org/wiki/List_of_WLAN_channels"). Even 40MHz channels selection not an option. I suppose end devices do some channels bundling like mobile is showing 433Mb/s. So Ubuntu is failing to bundle channels.

> **jeremy31 said:**
> It seems this problem is from Location Aware Regulatory that is in the iwlwifi driver and possibly others and it is ignoring the fact that we set the country code to JP and limits the channel bandwidth to 20 MHz

I am setting the country code to ID. I've tried other codes as well including US, JP, AE but nothing works. Below command ```
sudo iw reg set XX
``` only changes the global parameters and not the phy#0. Does below output mean that no 40MHz/80MHz are allowed/supported for this particular frequency range ? ```
(5735 - 5815 @ 20), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ

``` 

> **jeremy31 said:**
> IIf my recommended channels don't work see if you can find a channel that is allowed on the router that is outside the frequencies of this list

If I select a different channel on AP by changing the region which is outside the range of phy#0 list then laptop fails to scan it.

Am I correct in understanding that for below output, global is what we set manually which only shows the corresponding parameters of frequnecies, bands, DFS etc. But actual working of driver is based on phy#0 ?

```
sudo iw reg get
global
country ID: DFS-JP
    (2400 - 2483 @ 40), (N/A, 26), (N/A), NO-OUTDOOR
    (5150 - 5350 @ 80), (N/A, 23), (N/A), NO-OUTDOOR
    (5725 - 5825 @ 80), (N/A, 23), (N/A), NO-OUTDOOR

phy#0 (self-managed)
country ID: DFS-UNSET
    (2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
    (2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
    (2447 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
    (5735 - 5815 @ 20), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
```

How can we change phy#0 country from ID to some other? The laptop was not bought from Indonesia.

---

### Post by jeremy31 on 2023-06-07
You may have to change the wifi channel/time zone and reboot.  It seems that some of the information is in iwlwifi firmware but the driver uses info from AP beacons to determine country [https://bugzilla.kernel.org/show_bug.cgi?id=205695#c6](https://bugzilla.kernel.org/show_bug.cgi?id=205695#c6)
The iw reg get info shows that only 20MHz bandwidth is allowed in the 5735-5815 range

---

### Post by anspectrum on 2023-06-07
I can not make anymore testing with that AP since going to leave this place. Will keep this thread open for any update.
Thanks for all the time and help @jeremy31.

---

### Post by anspectrum on 2023-06-14
I am in a different city now and connected to a 5G WiFi. Now my laptop is connected at 433 Mbps. Ive already reverted all the changes that were suggested earlier in this thread but still its connecting at high speed. Few outputs posted here for reference.

```
iw reg get
global
country 00: DFS-UNSET
    (755 - 928 @ 2), (N/A, 20), (N/A), PASSIVE-SCAN
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

phy#0 (self-managed)
country US: DFS-UNSET
    (2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
    (2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
    (2447 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
    (5170 - 5190 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5190 - 5210 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5210 - 5230 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5230 - 5250 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5250 - 5270 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5270 - 5290 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5290 - 5310 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5310 - 5330 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5490 - 5510 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5510 - 5530 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5530 - 5550 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5550 - 5570 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5570 - 5590 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5590 - 5610 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5610 - 5630 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5630 - 5650 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5650 - 5670 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5670 - 5690 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5690 - 5710 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5710 - 5730 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5735 - 5755 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5755 - 5775 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5775 - 5795 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5795 - 5815 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5815 - 5835 @ 20), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ, PASSIVE-SCAN
```

```
iwconfig wlp5s0 
wlp5s0    IEEE 802.11  ESSID:"XXXX"  
          Mode:Managed  Frequency:5.765 GHz  Access Point: C0:74:AD:19:7A:D6   
          Bit Rate=433.3 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0
```

Gonna mark the thread as SOLVED.

---

