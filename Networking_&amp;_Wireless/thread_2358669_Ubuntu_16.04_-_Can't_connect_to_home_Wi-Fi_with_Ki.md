---
title: "Ubuntu 16.04 - Can't connect to home Wi-Fi with Killer 1535 (QCA6174)"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by arogachev on 2017-04-16
Recently I installed Ubuntu 16.04 on MSI GS63VR laptop with dual boot (with Windows 10). This laptop has Killer 1535 Wi-Fi adapter (QCA6174 to be specific). I followed [instructions]("http://www.killernetworking.com/driver-downloads/knowledge-base?view=topic&id=2") on their official site:

> **Ubuntu 16.04**

The built in drivers should work without any changes, though you may need to update your wireless firmware:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.162_all.deb
sudo dpkg -i linux-firmware*.deb
sudo modprobe -r ath10k_pci && sudo modprobe ath10k_pci
```

One remark though - the [mentioned file]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.162_all.deb") does not exist anymore and thus info is a bit outdated. So I checked [the whole list]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/") and used [the latest available version]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164_all.deb") instead.

Even Wi-Fi networks are visible, unfortunately I can't connect to my home Wi-Fi. I checked the password multiple times, it's correct for sure.

The relevant output of:

```
sudo lshw -c network
```

is:

```
description: Wireless interface
product: QCA6174 802.11ac Wireless Network Adapter
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:3e:00.0
logical name: wlp62s0
version: 32
serial: **:**:**:**:**:**
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath10k_pci driverversion=4.8.0-36-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 ip=***.***.**.* latency=0 link=yes multicast=yes wireless=IEEE 802.11
resources: irq:132 memory:df200000-df3fffff
```

The output of:

```
dmesg | grep ath10k
```

is:

```
[    3.086898] ath10k_pci ****:**:**.*: enabling device (0000 -> 0002)
[    3.087198] ath10k_pci ****:**:**.*: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    3.372179] ath10k_pci ****:**:**.*: Direct firmware load for ath10k/pre-cal-pci-****:**:**.*.bin failed with error -2
[    3.372184] ath10k_pci ****:**:**.*: Direct firmware load for ath10k/cal-pci-****:**:**.*.bin failed with error -2
[    3.372360] ath10k_pci ****:**:**.*: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.372361] ath10k_pci ****:**:**.*: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    3.373277] ath10k_pci ****:**:**.*: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    3.373277] ath10k_pci ****:**:**.*: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.373623] ath10k_pci ****:**:**.*: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    3.436610] ath10k_pci ****:**:**.*: board_file api 2 bmi_id N/A crc32 8c15898f
[    5.561030] ath10k_pci ****:**:**.*: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    5.656429] ath10k_pci ****:**:**.* wlp62s0: renamed from wlan0
```

The strange thing is that I can connect to my Android hotspot set on smartphone. Also other devices at home can connect to this Wi-Fi without any problems, and it works fine on Windows 10 on the same laptop. So I'm forced to use Android hotspot as a temporary workaround now.

Here is the log of connection to Android hotspot:

```
[  107.007374] wlp62s0: authenticate with **:**:**:**:**:**
[  107.057897] wlp62s0: send auth to **:**:**:**:**:** (try 1/3)
[  107.059728] wlp62s0: authenticated
[  107.061296] wlp62s0: associate with **:**:**:**:**:** (try 1/3)
[  107.064661] wlp62s0: RX AssocResp from **:**:**:**:**:** (capab=0x411 status=0 aid=1)
[  107.067985] wlp62s0: associated
[  107.068042] IPv6: ADDRCONF(NETDEV_CHANGE): wlp62s0: link becomes ready
```

And here is the log of connection to home Wi-Fi:

```
[  101.628172] wlp62s0: authenticate with **:**:**:**:**:**
[  101.674946] wlp62s0: send auth to **:**:**:**:**:** (try 1/3)
[  101.679850] wlp62s0: send auth to **:**:**:**:**:** (try 2/3)
[  101.684955] wlp62s0: send auth to **:**:**:**:**:** (try 3/3)
[  101.690259] wlp62s0: authentication with **:**:**:**:**:** timed out
[  102.308700] IPv6: ADDRCONF(NETDEV_UP): wlp62s0: link is not ready
```

I used:

```
dmesg | grep wlp62s0
```

command to retrieve this information.

> **Important note:** Before posting this I searched a lot and tried what is suggested in similar questions. None of those advices worked for me.

Many of them recommend to replace firmware files from [kvalo/ath10k-firmware ]("https://github.com/kvalo/ath10k-firmware/")repo so I decided to give it a try too:

```
cd ~/programs/
git clone https://github.com/kvalo/ath10k-firmware.git
sudo rm -rf /lib/firmware/ath10k/QCA6174/
sudo cp -r ath10k-firmware/QCA6174 /lib/firmware/ath10k/
cd /lib/firmware/ath10k/QCA6174/hw2.1/
sudo mv firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 firmware-5.bin
cd ../hw3.0
sudo mv firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1 firmware-4.bin
sudo modprobe -r ath10k_pci && sudo modprobe ath10k_pci
reboot
```

Unfortunately this did not help too.

> **Important note:** At some point of trial and error I managed to connect to home Wi-Fi but noticed a huge packet loss and bad connection speed. Then I was unable to load web pages at all. Currently I can't connect to home network at all.

Any help and advices is appreciated. If you need more info, please let me know.

---

### Post by arogachev on 2017-04-16
**Update 1:** I disabled IPv6 using [this method]("https://askubuntu.com/questions/309461/how-to-disable-ipv6-permanently/337736#337736"). Now these kind of errors - "IPv6: ADDRCONF(NETDEV_UP): wlp62s0: link is not ready" are gone, but  authentication is still timing out:

  ```
[   93.019254] wlp62s0: authenticate with **:**:**:**:**:**
[   93.065501] wlp62s0: send auth to **:**:**:**:**:** (try 1/3)
[   93.070345] wlp62s0: send auth to **:**:**:**:**:** (try 2/3)
[   93.075515] wlp62s0: send auth to **:**:**:**:**:** (try 3/3)
[   93.083312] wlp62s0: authentication with **:**:**:**:**:** timed out
```

---

### Post by chili555 on 2017-04-16
Let's have a look at: ```
sudo iwlist scan
```Just show us your home wifi, not all the neighbors. Thanks.

---

### Post by arogachev on 2017-04-16
**chili555**, thanks for the reply. The output of```


sudo iwlist scan
```

 is:

```
Cell 03 - Address: **:**:**:**:**:**

Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=33/70  Signal level=-77 dBm  
Encryption key:on
ESSID:"home"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000148c514fb6e
Extra: Last beacon: 6408ms ago
IE: Unknown: 000869646E65742D3134
IE: Unknown: 010882840B160C121824
IE: Unknown: 030103
IE: Unknown: 050401020000
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: 2D1A2C181EFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1603000000000000000000000000000000000000000000
IE: WPA Version 1
    Group Cipher : CCMP
    Pairwise Ciphers (1) : CCMP
    Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
    Group Cipher : CCMP
    Pairwise Ciphers (1) : CCMP
    Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C332C181EFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3403000000000000000000000000000000000000000000
IE: Unknown: DD0600E04C020160
IE: Unknown: DD0E0050F204104A0001101044000102
```

---

### Post by arogachev on 2017-04-16
**Update 2:** I also asked this question on [Ask Ubuntu]("https://askubuntu.com/questions/905363/ubuntu-16-04-cant-connect-to-home-wi-fi-with-killer-1535-qca6174") and got advice by **Jeremy31**. I changed power management settings as suggested by **Jeremy31** in [this answer]("https://askubuntu.com/questions/884922/wifi-on-lenovo-ideapad-running-ubuntu-16-04/884987#884987"). Now sometimes the process goes a bit further:
  
```
[   76.352810] wlp62s0: authenticate with **:**:**:**:**:**
[   76.400120] wlp62s0: send auth to **:**:**:**:**:** (try 1/3) 
[   76.405250] wlp62s0: authenticated
[   76.407644] wlp62s0: associate **:**:**:**:**:** (try 1/3) 
[   76.418128] wlp62s0: RX AssocResp from **:**:**:**:**:** (capab=0x431 status=0 aid=2)
[   76.421150] wlp62s0: associated 
[  122.364346] wlp62s0: deauthenticating **:**:**:**:**:** by local choice (Reason: 3=DEAUTH_LEAVING)
```

  In other cases I get timeout like in **Update 1**.

---

### Post by jeremy31 on 2017-04-16
Post results for ```
iwconfig; iw reg get
```

---

### Post by arogachev on 2017-04-16
**jeremy 31**, the result of:

```
ifconfig; iw reg get
```

- when Wi-Fi is disconnected or when I'm trying to connect to home Wi-Fi:

```
enp61s0    no wireless extensions.

lo    no wireless extensions.

wlp62s0    IEEE 802.11  ESSID:off/any  
    Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
    Retry short limit:7   RTS thr:off   Fragment thr:off
    Power Management:off
          
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
```

- when I'm connected to Android Access Point:

```
enp61s0    no wireless extensions.

lo    no wireless extensions.

wlp62s0    IEEE 802.11  ESSID:"AndroidAP"  
    Mode:Managed  Frequency:2.462 GHz  Access Point: C0:BD:D1:EF:13:69   
    Bit Rate=1 Mb/s   Tx-Power=20 dBm   
    Retry short limit:7   RTS thr:off   Fragment thr:off
    Power Management:off
    Link Quality=67/70  Signal level=-43 dBm  
    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
    Tx excessive retries:0  Invalid misc:16   Missed beacon:0

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
```

I guess it's somehow related with unspecified country?

---

### Post by arogachev on 2017-04-17
**Update 3:** Followed Jeremy's advice in comments for [Ask Ubuntu question]("https://askubuntu.com/questions/905363/ubuntu-16-04-cant-connect-to-home-wi-fi-with-killer-1535-qca6174"):

 > Your post on UF shows that WPA and WPA2 are enabled on the router, can you disable WPA and leave just WPA2 encryption.

After leaving just WPA2 encryption I was able to connect to home Wi-Fi once, but noticed pretty big packet loss and delays during ping. Then again authentication started to time out.
[B]
Update 4:[/B] I set wireless regulatory domain to my country code (KZ, stands for Kazakhstan) as advised in [this topic]("https://ubuntuforums.org/showthread.php?t=2259037"):

```
sudo iw reg set KZ
```

Also I modified "/etc/default/crda" file to contain "REGDOMAIN=KZ" setting (default was empty).

Again, was able to connect couple of times, but with big packet loss and delays during ping.
[B]
Update 5:[/B] Another Jeremy's advice in comments for [Ask Ubuntu question]("https://askubuntu.com/questions/905363/ubuntu-16-04-cant-connect-to-home-wi-fi-with-killer-1535-qca6174") was:

> also try moving closer to the access point

I came closely to the router and was surprised. As soon as I opened up the laptop's lid and entered password to unlock system, I was instantly connected to my home Wi-Fi. Then I started to testing connection quality and speed and it was good - small response rates, almost no packet loss.

Once I came back to my room, results remained good for small amount of time and then again, big packet loss and delays and I even was disconnected.

Then again, authentication was timing out and I was not able to connect again. And I noticed one thing that when I can connect, connection initially can be pretty good (first minute for example) then getting worse and worse.

Now I'm not able to connect again.

So, bottom line is:

- Connection works good if I move laptop closer to the router. That means I have the option of moving router to other room. But, at the same time, I have the same ping results on the same laptop from the same distance using Windows, so I'm still thinking it's Ubuntu specific problem or drivers / router settings specific to Ubuntu. Also other devices such as my smartphone can connect to this network without any problems with the same distance.

I'm confused a little bit. :(

**Update 6:** Just for testing purposes I grabbed the laptop and came to doorway (about 1 meter closer to router). I was able to connect and connection was pretty good at this point. Once I came back to working table, connection became way worse. But again on Windows it works fine while laptop is placed on the working table.

---

### Post by chili555 on 2017-04-17
> Cell 03 - Address: **:**:**:**:**:**

Channel:3
Frequency:2.422 GHz (Channel 3)
[COLOR="#FF0000"]Quality=**33**/70[/COLOR]  Signal level=-77 dBm  
Encryption key:on
ESSID:"home"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master> I came closely to the router and was surprised. As soon as I opened up the laptop's lid and entered password to unlock system, I was instantly connected to my home Wi-Fi. Then I started to testing connection quality and speed and it was good - small response rates, almost no packet loss.
This suggests a few possibilities. First, and this may be a bit remote, is that one of the antenna wires is not securely attached to the wireless card. Can you check?

The second is that the router may need to be rearranged to get a bit more range. Can it be on a higher shelf? A lower shelf? Are there obstructions that may be removed? Is reception improved if the router sits vertically rather than horizontally? Are there antennae that can be rearranged?

Next, channel 3 is a rather unusual choice. If you selected it, I recommend a channel with less overlap; ideally 1, 6 or 11. [http://www.metageek.com/training/resources/why-channels-1-6-11.html](http://www.metageek.com/training/resources/why-channels-1-6-11.html) If channel 3 was chosen by the router by auto channel selection then, again, I recommend a fixed channel, either 1, 6 or 11. You can get an idea of the congestion in your area with:```
sudo nmcli dev wifi list
```Here is a sample from my machine:```
*  SSID        MODE   CHAN  RATE       SIGNAL  BARS  SECURITY  
   GBR1        Infra  6     54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2      
*  GBR5        Infra  149   54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2      
   nx2.4       Infra  6     54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2 
   MAHB Wi-Fi  Infra  11    54 Mbit/s  39      &#9602;&#9604;__  WPA2      
   MAHB Wi-Fi  Infra  11    54 Mbit/s  30      &#9602;___  WPA2      
   MAHB Wi-Fi  Infra  11    54 Mbit/s  27      &#9602;___  WPA2  
```Please notice that nobody uses channel 1. That's what I'd select if I were starting over. 

Finally, your router may have a setting to increase transmission power:  [https://www.howtogeek.com/wp-content/uploads/2011/03/tx-power.png](https://www.howtogeek.com/wp-content/uploads/2011/03/tx-power.png) If so, please try increasing it in gentle steps. Increasing it to the maximum may stress the wireless radio in the router and shorten its life. I believe that one or two small steps may be fine.

---

### Post by arogachev on 2017-04-19
> First, and this may be a bit remote, is that one of the antenna wires is  not securely attached to the wireless card. Can you check?

There are no problems with antennas on router. If you mean laptop's wi-fi card, unfortunately I can't disassemble it to verify that. But if it's fine on Windows, I don't think this is the issue.

> The second is that the router may need to be rearranged to get a bit  more range. Can it be on a higher shelf? A lower shelf? Are there  obstructions that may be removed? Is reception improved if the router  sits vertically rather than horizontally? Are there antennae that can be  rearranged?

Router was given for free and set by  provider employees (it's mounted on the wall, about meter and a half  from the floor). Optical fiber is used for connection and it has fixed  length so I can't move it anywhere without making request to provider.  Such service is paid and I'm considering this option as a last resort  only.

The router model is ECI B-FOCuS 0-4G2PWM. There is almost no info and mentions of it in internet.

> Next,  channel 3 is a rather unusual choice. If you selected it, I recommend a  channel with less overlap; ideally 1, 6 or 11. [http://www.metageek.com/training/res...ls-1-6-11.html]("http://www.metageek.com/training/resources/why-channels-1-6-11.html")  If channel 3 was chosen by the router by auto channel selection then,  again, I recommend a fixed channel, either 1, 6 or 11. You can get an  idea of the congestion in your area with:

The channel is  set to "auto" in router settings so that's why channel 3 was selected. I  tried changing it to fixed (1, 6, 11), this did not help much. Now I  set it back to "auto" and it's on channel 1. I noticed signal strength  is a bit improved after that.

> Finally, your router may have a setting to increase transmission power:  [https://www.howtogeek.com/wp-content...3/tx-power.png]("https://www.howtogeek.com/wp-content/uploads/2011/03/tx-power.png")  If so, please try increasing it in gentle steps. Increasing it to the  maximum may stress the wireless radio in the router and shorten its  life. I believe that one or two small steps may be fine.

There  are only 2 options in "Channel bandwidth" - 20 MHz and 40MHz (no mixed  mode). The value was 20 MHz. I tried changing it to 40 MHz and  connection became even worse. Another related option is set to 100%  (forgot exact name, sorry).
[B]
Update 7:[/B] I  contacted provider support, they recommended to manually set address,  network, gateway and DNS in connection properties and try to change  router settings (mode, fixed channel for example). Default mode is "auto (b / g / n)" Tried to change to "b /g". That didn't help.

Again,  in Windows 10 I have no problems with Wi-Fi from the same exact spot,  so I still believe it has something to do with Ubuntu specific settings  or drivers.

---

### Post by chili555 on 2017-04-19
>  I still believe it has something to do with Ubuntu specific settings or drivers.I fully agree; however, the manufacturers, Atheros in this case, devote many hours, dollars and tests to be certain that the Windows driver is as perfect as possible. Linux, not so much. Some manufacturers do a better job than others. I am particularly a fan of Intel.

All we can do is the best job we can with the limited tools available.

I have but two further suggestions. First, let's set a module parameter.```
sudo -i
echo "options ath10k_pci skip_otp=y  >  /etc/modprobe.d/ath10k.conf
exit 
```Second, I notice in your *dmesg* that the driver looks for and fails to find firmware-5.bin. I haven't any idea whether this is better, worse or the same as the firmware it ultimately finds and loads. I also notice that, on my 17.04 install, that and several other ath10k firmware files exist. I suggest that you install the very latest linux-firmware to see if it helps.```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot and tell us if connectivity has improved.

---

### Post by arogachev on 2017-04-20
> 
First, let's set a module parameter.

```
sudo -i
echo "options ath10k_pci skip_otp=y  >  /etc/modprobe.d/ath10k.conf
exit
```


You skipped a closing quote here. Anyway I tried that. Nothing changed. Also I noticed the following line in the logs after applying that:

```
[    3.381182] ath10k_pci: unknown parameter 'skip_otp' ignored
```

By the way there was no */etc/modprobe.d/ath10k.conf *file initially. Also during research I found several advices about applying this option. What it does?

> I suggest that you install the very latest linux-firmware to see if it helps.

I already have this version (please read my very first post) Also I compared the files with the current ones from kernel [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k/QCA6174](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k/QCA6174), the amount and size of files is exactly the same. I also tried to install [linux-firmware_1.157.9_all.deb]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.9_all.deb") and noticed that speed became worse even when connected to Android access point so I reverted it to 1.164.

Also after setting country code I noticed this info in the logs:

```
[    5.958257] ath: EEPROM regdomain: 0x6c
[    5.958258] ath: EEPROM indicates we should expect a direct regpair map
[    5.958259] ath: Country alpha2 being used: 00
[    5.958259] ath: Regpair used: 0x6c
[    5.963073] ath10k_pci 0000:3e:00.0 wlp62s0: renamed from wlan0
```

---

### Post by arogachev on 2017-04-20
Tried to solve these errors:

```
[    3.596450] ath10k_pci 0000:3e:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.596451] ath10k_pci 0000:3e:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
```

by copying and renaming *firmware-5.bin *from [https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw3.0/4.4](https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw3.0/4.4).

Then instead of available wireless connections "device not ready" message was shown. Reverted this change.

---

### Post by chili555 on 2017-04-20
> You skipped a closing quote here. Anyway I tried that. Nothing changed. Also I noticed the following line in the logs after applying that:

Code:
[    3.381182] ath10k_pci: unknown parameter 'skip_otp' ignored
By the way there was no /etc/modprobe.d/ath10k.conf file initially. Also during research I found several advices about applying this option. What it does?
Ah, ha! Newer versions of the driver have the option built in; older do not. Older versions of the driver often benefit from the addition of the option. Here is a rather cryptic explanation of the parameter: [https://groups.google.com/a/chromium.org/forum/#!topic/chromium-os-reviews/0ae8vRJAEd0](https://groups.google.com/a/chromium.org/forum/#!topic/chromium-os-reviews/0ae8vRJAEd0)

It was not apparent to me which version you had. I have no 4.8.0-xx machine available to compare. Since the newer driver evidently includes the change by default, let's remove the needless file:```
sudo rm /etc/modprobe.d/ath10k.conf
```> by copying and renaming firmware-5.bin from [https://github.com/kvalo/ath10k-firm...6174/hw3.0/4.4](https://github.com/kvalo/ath10k-firm...6174/hw3.0/4.4).

Then instead of available wireless connections "device not ready" message was shown. Reverted this change.Just because the logs show that the driver looked for and didn't find a particular firmware file does not mean that the file is better or that it even exists for your exact device. I have myself experimented with downloading and renaming firmware files. It has never helped. It doesn't cost a penny to try, as you've seen, but I'm skeptical that it ever helps.

I am still very concerned that the problem is exactly this:> Cell 03 - Address: **:**:**:**:**:**

Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=[COLOR="#FF0000"]**33**[/COLOR]/70 Signal level=-77 dBm 
Encryption key:on
ESSID:"home"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master

---

### Post by arogachev on 2017-04-20
> let's remove the needless file

Done.

> but I'm skeptical that it ever helps

Yes, me too. That was a part of trial and error because of the lack of better solutions.

> I am still very concerned that the problem is exactly this:

```
Quality=[COLOR=#FF0000]**33**[/COLOR]/70
```

Yes, seems like the drivers don't use full potential of Wi-Fi card. On Windows I see a better signal.

---

### Post by chili555 on 2017-04-20
One last grasp at straws:```
sudo -i
echo "options ath10k_core cryptmode=1"  >  /etc/modprobe.d/ath10k.conf
modprobe -r ath10k_pci
modprobe -r ath10k_core
modprobe ath10k_pci
exit
```When you try to remove ath10k_core, it may or may not be present. In either case, just proceed. 

Is there any improvement?```
sudo iwlist scan
```I will be very surprised if there is. If there is not, simply remove the file as in my previous post.

Aside from this, I regret that I haven't any further suggestions.

---

### Post by arogachev on 2017-04-20
Here are the thoughts of my friend:

> Looks like the driver doesn't work with MIMO. Like you've got more than one antenna in the laptop and it doesn't use those.

I found this [https://bbs.archlinux.org/viewtopic.php?id=222796](https://bbs.archlinux.org/viewtopic.php?id=222796)

Yeah that card has some advanced MIMO stuff, I guess that's the issue that the driver doesn't handle it well.

And did you see this? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1670041](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1670041)

So go ahead and try out Arch Linux. it has a newer kernel, It might make a difference, I don't know.

The current output of:

```
uname -a
```

is:

```
Linux msi-gs63vr 4.8.0-46-generic #49~16.04.1-Ubuntu SMP Fri Mar 31 14:51:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Maybe try to upgrade kernel? Is it worth it?

Also some people recommend to use Intel cards (for example 8260), seems like they are more Linux friendly. Here is a video of changing Wi-Fi card to Intel 8265 on the same laptop - [https://www.youtube.com/watch?v=A1EN-b8ZK1E](https://www.youtube.com/watch?v=A1EN-b8ZK1E). But I'm not sure if it will be fine on the same distance.

**chili555**, thanks. I'll try this and report about results.

---

### Post by arogachev on 2017-04-20
**chili555**, tried your solution with "options ath10k_core cryptmode=1". This results in empty networks list and these lines in the log:

```
[    3.285288] ath10k_pci 0000:3e:00.0: enabling device (0000 -> 0002)
[    3.285782] ath10k_pci 0000:3e:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    3.580434] ath10k_pci 0000:3e:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:3e:00.0.bin failed with error -2
[    3.580440] ath10k_pci 0000:3e:00.0: Direct firmware load for ath10k/cal-pci-0000:3e:00.0.bin failed with error -2
[    3.580606] ath10k_pci 0000:3e:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.580607] ath10k_pci 0000:3e:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    3.581836] ath10k_pci 0000:3e:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    3.581837] ath10k_pci 0000:3e:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.582223] ath10k_pci 0000:3e:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    3.645158] ath10k_pci 0000:3e:00.0: board_file api 2 bmi_id N/A crc32 19644295
[    3.645159] ath10k_pci 0000:3e:00.0: cryptmode > 0 requires raw mode support from firmware
[    3.645161] ath10k_pci 0000:3e:00.0: fatal problem with firmware features: -22
[    3.645176] ath10k_pci 0000:3e:00.0: could not probe fw (-22)
```

Reverted this change too.

---

### Post by chili555 on 2017-04-20
> Also some people recommend to use Intel cards (for example 8260), seems like they are more Linux friendly. Here is a video of changing Wi-Fi card to Intel 8265 on the same laptop - [https://www.youtube.com/watch?v=A1EN-b8ZK1E](https://www.youtube.com/watch?v=A1EN-b8ZK1E). But I'm not sure if it will be fine on the same distance.What is the distance? I am about 9.5 meters from my router and use an Intel 7260. My scan says:>  Cell 01 - Address: xx:2B:B0:DC:45:xx
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=[COLOR="#FF0000"]59/70[/COLOR]  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    <snip>My speedtest from the same location is: [http://www.dslreports.com/speedtest/7109859](http://www.dslreports.com/speedtest/7109859)

Changing the card is certainly within the capability of most of us. I have done it and would do it again. I would certainly try to find the hardware maintenance manual on line and try to do each step very carefully in order.

In fact, within three weeks of receiving this current laptop from Lenovo, I had changed the wireless card, added RAM and changed the hard drive for an SSD.> Maybe try to upgrade kernel? Is it worth it?
I doubt it, but, as before, it doesn't cost a penny to try. Post back if you'd like a step-by-step.

---

### Post by arogachev on 2017-04-21
> What is the distance?

About 8-9 meters.

> I would certainly try to find the hardware maintenance manual on line

Do you mean contact laptop manufacturer support? I already sent e-mail to Rivet Networks (manufacturer of Killer 1535 Wi-Fi card), no response yet. Going to contact MSI as well soon.

---

### Post by chili555 on 2017-04-21
> Do you mean contact laptop manufacturer support? I'd try to Google the model number and `service manual` or `maintenance manual` to see if a PDF is available to download. If not, then I'd ask MSI. There is often a prescribed procedure to remove certain screws to access the wireless card, RAM, etc. Too often, I think, people start just unscrewing everything in sight and hope that they will eventually burrow down to the wireless card.

In the case of my Lenovo, it was necessary to remove the battery and just two screws to get to the wireless. As in many things in life, if you know how it's done, it's easy. The maintenance manual makes it very clear.

---

### Post by arogachev on 2017-04-22
I found a person who has the same exact laptop and also set up dual boot (WIndows 10 / Ubuntu 16.04). Here is what he said:

> I don't remember the firmware. The distances I was from my router at home are from half a meter to 10-15 meters. No issues both with Killer and Intel.

That's weird. He said that everything worked out of the box. Maybe try older firmware?

---

