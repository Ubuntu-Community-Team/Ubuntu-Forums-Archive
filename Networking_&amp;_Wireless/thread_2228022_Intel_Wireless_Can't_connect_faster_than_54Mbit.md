---
title: "Intel Wireless: Can't connect faster than 54Mbit"
date: 2014-06-05
forum: Networking &amp; Wireless
---

### Post by khmm12 on 2014-06-05
Intel(R) Centrino(R) Advanced-N 6235.
In Windows 8.1 I have more than ~80mbs download/upload (checked in speedtest), but in Ubuntu 14.04 ~44 mbs download, ~16mbs upload. Router use WPA2.
11n_disable = 0. What is wrong?

dmesg | grep iwl
```
[    3.586707] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.587304] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[    3.598498] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    3.653068] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.653071] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.653073] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.653075] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[    3.653176] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    3.686300] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.424247] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    5.430273] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[    5.712171] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    5.718422] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0

```

iwconfig
```
wlan0     IEEE 802.11abgn  ESSID:"Anonymous_Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <>  
          Bit Rate=270 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

nm-tool
```
- Device: wlan0  [Anonymous_Network] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:       <>


  Capabilities:
    Speed:           270 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    DIR-615:         Infra, <>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Somov:           Infra, <>, Freq 2472 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Asus4:           Infra, <>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA
    *Anonymous_Network: Infra, <>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2
    Kak xochy:       Infra, <>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    ASUS:            Infra, <>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2

```

---

### Post by varunendra on 2014-06-05
Welcome to the forums khmm12 !

Please try -
```
echo "options iwlwifi swcrypto=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
..followed by a reboot. Does it make the speed any better? If not, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

And how do you determine the speed?

---

### Post by khmm12 on 2014-06-05
No, the speed is still slow :(

> And how do you determine the speed?
speedtest.net and transferring files in a local network

---

### Post by varunendra on 2014-06-06
A few suggestions, in no particular order of importance, but try them in the following order -

[indent]**1)** Try disabling IPv6 following [this post]("http://ubuntuforums.org/showpost.php?p=12640479"), or at least try setting it to "Ignore" in Network Manager.

**2)** If the router has 'QoS' enabled, more importantly, if it has 'IOMMU' feature and is enabled, disable it. Also try disabling 'QoS' itself. Disabling 'IOMMU' is a strong suggestion, disabling 'QoS' is just a shot in the dark.

**3)** Try two more driver parameters (temporarily), one at a time -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi bt_coex_active=N
sudo modprobe -v iwldvm
```
If this doesn't help, re-run the commands, replacing the second one with -
```
sudo modprobe -v iwlwifi wd_disable=2
```
Note that instead of writing these parameters to the .conf file, we are loading them directly. As such, they would take effect immediately, but would be lost at next boot. If they seem to help, we can add them to the conf file to make them permanent.

**4)** This may not be related, but seems a bit abnormal to me. Is your notebook an Acer or a Lenovo? Because acpi/wmi drivers for both have been loaded. I believe there should be only one. As per the 'lspci' output, it seems it is Lenovo. If yes, try blacklisting 'acer_wmi' -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
But if it is indeed an Acer, you should try blacklisting "ideapad_laptop" instead. The blacklisting would take effect after a reboot.[/indent]

No more ideas for now, hope we may get lucky with one of the above.

---

### Post by khmm12 on 2014-09-08
[http://ubuntuforums.org/showthread.php?t=2205924&p=13051099#post13051099](http://ubuntuforums.org/showthread.php?t=2205924&p=13051099#post13051099)
This solution helps me me :-). Thanks to Lekensteyn.

---

### Post by jeremy31 on 2014-09-08
> **khmm12 said:**
> [http://ubuntuforums.org/showthread.php?t=2205924&p=13051099#post13051099](http://ubuntuforums.org/showthread.php?t=2205924&p=13051099#post13051099)
This solution helps me me :-). Thanks to Lekensteyn.

The 11n_disable=8 is a newer option that was introduced because having AMPDU enabled created problems with some users previously

Nice that you found a fix

---

