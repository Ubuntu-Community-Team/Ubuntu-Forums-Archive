---
title: "WiFi Authentication loop with Atheros [168:0042] on Xubuntu"
date: 2016-12-01
forum: Networking &amp; Wireless
---

### Post by jared28 on 2016-12-01
Whenever I try to connect to my home network (WPA2 AES encrypted - I changed this after reading that WPA & WPA 2 mixed was a problem, and that I should use AES instead of "both" or "TKIP"), I get a network authentication prompt. I'll enter the password (which I know is correct, I've copy pasted it from the router page itself, and there are no spaces), it waits a few seconds, and then prompts again. I have this same problem on my Arch partition with KDE Plasma 5 installed, where it would repeat the prompt and say "No Secrets Provided" when canceled. I believe these two problems are essentially the same. I've tried everything I could find through some Googleing for at least 3 hours this morning, including setting the local code to "US", deleting the entry and remaking it, etc.

My laptop is an Acer Aspire E15

Here's the information from the debugging script:
[http://paste.ubuntu.com/23564077/](http://paste.ubuntu.com/23564077/)

Any help would be greatly appreciated!

---

### Post by jared28 on 2016-12-02
I re-installed everything from scratch, this time making a list of everything I've tried. Hopefully it helps:

```
1.  Enable for all users in networkmanager settings
2.  Using WiCD to connect to it (WPA 1/2)
3.  It's set to AES encryption and WPA2-Personal only
4.  Ran "sudo iw reg set US"
5.  I've edited the /etc/default/crda file to read "REGDOMAIN=US"
6.  IPV6 is set to "Ignore" in NetworkManager
7.  Reboot
8.  See that WiCD is still installed, uninstall
9.  Reboot again
10. Ran "echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf" after running "sudo -i"
11. Reboot
12. Ran "sudo iwconfig wlp3s0 power off"
13. Ran "sudo modprobe -r iwlwifi" (returned an error, decided to continue anyway)
14. Ran "sudo modprobe -v iwlwifi 11n_disable=1"
15. Ran "systemctl stop dhcpcd"
16. Ran "systemctl disable dhcpcd" (error: "Failed to execute operation: No such file or directory")
17. Ran "systemctl restart wpa_suplicant"
18. Ran "systemctl disable NetworkManager-wait-online.service"
19. Ran "systemctl disable net-auto-wired.service" (error: "Failed to execute operation: No such file or directory")
20. Ran "systemctl disable net-auto-wireless.service" (error: "Failed to execute operation: No such file or directory")
21. Searched dmesg, saw "4-way handshake failed - pre-shared key may be incorrect
22. Tried using the hashed pass key (discovered by running "wpa_passphrase myssid mypassword")
23. Followed the instructions on [https://digitz.org/blog/wifi-issue-on-acer-laptops-running-linux-qualcomm-atheros-device-0042/](https://digitz.org/blog/wifi-issue-on-acer-laptops-running-linux-qualcomm-atheros-device-0042/) to install a driver to the kernel (or something of the sort)
```

None of the above have worked so far, and it's all the info I could find so far

I should add that I've successfully connected to my phone's WiFi hotspot, and the config file under /etc/NetworkManager looks identical (except for the channel, MAC address, SSID, psk, etc. of course). Both have the same kind of encryption (CCMP). It seems like it's a problem with JUST the router we have at home (the SSID we use at home is "worst_wireless_ever"). I've read that there isn't such thing as a router that's incompatible with Linux, and this seems to make sense (Android is heavily modified linux and it works fine).

---

### Post by chili555 on 2016-12-03
First, a little rant for all the searchers out there who blindly implement changes, "fixes", etc. If you are not sure, really sure, completely sure that you are making a change for your exact driver, then don't. See what the hard-working, earnest Mr./Ms. jared28 has done here?> 13. Ran "sudo modprobe -r iwlwifi" (returned an error, decided to continue anyway)
14. Ran "sudo modprobe -v iwlwifi 11n_disable=1"However, his driver is not iwlwifi, it is:> acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
[COLOR="#FF0000"]ath10k_pci   [/COLOR]          45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
mxm_wmi                16384  1 nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  40960  3 i915_bpo,acer_wmi,nouveauA lot of the time, these things are harmless, but sometimes you can wreck your system and end up doing *_another_* re-install, only to repeat the mistake again. If in doubt, STOP and ask.

End rant. I feel better now.

First, I suggest that you install the latest firmware:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux*.deb
```Reboot with the ethernet detached and tell us if the wireless connected.

I'd also like to see:```
dmesg | grep ath
sudo iwlist scan
```

---

### Post by jared28 on 2016-12-03
Thank you for your reply! I'll try harder next time to make sure I know exactly what I'm running before I run it.

I installed the latest firmware like you suggested and rebooted, and the problem still exists. Here's the output of dmesg | grep ath:

```
[    2.054623] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.283269] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    4.224443] ath10k_pci 0000:03:00.0: qca9377 hw1.1 (0x05020001, 0x003821ff sub 105b:e0a1) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[    4.224447] ath10k_pci 0000:03:00.0: debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[    4.225836] ath: EEPROM regdomain: 0x69
[    4.225839] ath: EEPROM indicates we should expect a direct regpair map
[    4.225841] ath: Country alpha2 being used: 00
[    4.225842] ath: Regpair used: 0x69
[    4.251243] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[   14.269870] ath10k_pci 0000:03:00.0 wlp3s0: disabling HT as WMM/QoS is not supported by the AP
[   14.269872] ath10k_pci 0000:03:00.0 wlp3s0: disabling VHT as WMM/QoS is not supported by the AP
[   25.560081] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   30.008720] ath10k_pci 0000:03:00.0 wlp3s0: disabling HT as WMM/QoS is not supported by the AP
[   30.008723] ath10k_pci 0000:03:00.0 wlp3s0: disabling VHT as WMM/QoS is not supported by the AP
[   41.535206] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   41.637657] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   41.740055] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   41.842450] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   41.944830] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   42.047322] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   42.149658] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   42.252072] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   42.354509] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   42.456697] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   90.720274] ath10k_warn: 28 callbacks suppressed
[   90.720280] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[  169.083459] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!


```

And "sudo iwlist scan":

```
wlp3s0    Scan completed :
          Cell 01 - Address: 40:4A:03:DF:D0:3B
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"worst_wireless_ever"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008ffaae69b
                    Extra: Last beacon: 4130ms ago
                    IE: Unknown: 0013776F7273745F776972656C6573735F65766572
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010555555550000C0A80001404A03DFD03B102100055A7958454C1023000F5A7958454C2057464144657669636510240007504B353030305A1042000830303030303030311054000800060050F20400011011000A504B353030305A20415010080002008C
          Cell 02 - Address: 02:20:60:F5:6B:99
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:off
                    ESSID:"HPJ610a.89DAA7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000544ebab5e0
                    Extra: Last beacon: 4024ms ago
                    IE: Unknown: 000E48504A363130612E383944414137
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 78:4B:87:FB:D5:D9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"Verizon-SM-G900V-D5D9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002999814
                    Extra: Last beacon: 3828ms ago
                    IE: Unknown: 0015566572697A6F6E2D534D2D47393030562D44354439
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2D0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 7F080400008001000040
                    IE: Unknown: DD050016328000
                    IE: Unknown: DD1E00904C0408BF0C3258810FFAFF0000FAFF0000C005000B000000C3020010
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


```


Should I be masking those addresses at all, or do we need it for debugging purposes? If so, I'll edit this post.

---

