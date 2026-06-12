---
title: "No wifi with QCA6174 ubuntu 18.04 and Samsung Book 10.6"
date: 2018-04-09
forum: Networking &amp; Wireless
---

### Post by office-liquid-light on 2018-04-09
Hello everybody,  
I run into a problem with a Qualcomm QCA and every Ubuntu version. Because of missing energy saving modes I have to use Ubuntu 18.04. For the QCA6174 version there is no version that works out of the box.  

```
@Gbook:~$ dmesg | grep ath
[   19.976284] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[   19.978746] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[   20.308519] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[   20.308533] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[   20.324391] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c150
[   20.324393] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   20.324971] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00079-QCARMSWPZ-1 api 6 features wowlan,ignore-otp crc32 fd869beb
[   20.398416] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 20d869c3
[   20.978092] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   20.981099] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   20.981700] ath10k_pci 0000:01:00.0: htt-ver 3.47 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   21.066080] ath: EEPROM regdomain: 0x5f
[   21.066082] ath: EEPROM indicates we should expect a direct regpair map
[   21.066082] ath: invalid regulatory domain/country code 0x5f
[   21.066083] ath: Invalid EEPROM contents
[   21.066089] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[   21.066091] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)
```


As far as I understood from several threads the problem is 'EPROM regdomain: 0x5f' that ins't patched correctly for quite a while. The only thing is that I'm not a programmer and not able to patch a driver or backport or what every is needed. The problem seems to be the same as in the thread below '[xubuntu] WiFi driver for Samsung Galaxy Book'. The backport works for ubuntu 16.04 that I cant't use because of energy saving problems.  

Any help is welcome 
Yu Kei

---

### Post by office-liquid-light on 2018-04-10
For solution please see

[https://ubuntuforums.org/showthread.php?t=2384640&page=4&p=13755642#post13755642](https://ubuntuforums.org/showthread.php?t=2384640&page=4&p=13755642#post13755642)

---

### Post by testing990 on 2018-11-14
Hi, unfortunately the solution that was posted on the link does not work on the Galaxy book 10.6, but only on the Galaxy book 12.

I have therefore opened a new thread describing the problem 

[https://ubuntuforums.org/showthread.php?t=2405871](https://ubuntuforums.org/showthread.php?t=2405871)

---

### Post by testing990 on 2018-11-29
I shall clarify, the problem doesnt seem to be different from the galaxy book 12 or 10.6, it is rather that the driver in the links have not been updated to work with Kernel 4.18 it seems

---

