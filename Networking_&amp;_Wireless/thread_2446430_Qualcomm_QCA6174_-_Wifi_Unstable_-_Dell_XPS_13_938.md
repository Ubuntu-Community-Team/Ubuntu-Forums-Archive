---
title: "Qualcomm QCA6174 - Wifi Unstable - Dell XPS 13 9380 - Ubuntu 20.04 Focal"
date: 2020-06-30
forum: Networking &amp; Wireless
---

### Post by pasueno on 2020-06-30
I have Ubuntu 20.04 installed on Dell XPS 13 9380 (Service Tag: 8SGZPV2) with Qualcomm QCA6174 wifi chip. Every 2-5 minutes, the wifi signal drops off then comes back online after a few seconds. This is a fresh install of Ubuntu Desktop through the usual methods (ie, not a custom OS/kernel build). The original OS was Windows 10 (no wifi problems), and Ubuntu was installed after a hard drive wipe (ie, ***not ***a dual-boot).

Here is my wifi hardware.
```
$ lspci
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
$ dmesg | grep ath
[   23.571480] ath10k_pci 0000:02:00.0: enabling device (0000 -> 0002)
[   23.579850] ath10k_pci 0000:02:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[   23.862206] ath10k_pci 0000:02:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:143a
[   23.862209] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   23.862620] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.4.4.1-00140-QCARMSWPZ-1 api 6 features wowlan,ignore-otp,mfp crc32 29eb8ca1
[   23.927110] ath10k_pci 0000:02:00.0: board_file api 2 bmi_id N/A crc32 4ac0889b
[   24.000120] ath10k_pci 0000:02:00.0: unsupported HTC service id: 1536
[   24.020001] ath10k_pci 0000:02:00.0: htt-ver 3.60 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   24.108647] ath: EEPROM regdomain: 0x6c
[   24.108647] ath: EEPROM indicates we should expect a direct regpair map
[   24.108648] ath: Country alpha2 being used: 00
[   24.108649] ath: Regpair used: 0x6c
[   24.115986] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   25.553827] ath10k_pci 0000:02:00.0: unsupported HTC service id: 1536
```

Here is my OS set up.
```
$ lsb_release -d
Description:    Ubuntu 20.04 LTS
$ uname -r
5.4.0-39-generic
$ apt list --installed | grep "linux-generic"
linux-generic-hwe-20.04/focal-updates,focal-security,now 5.4.0.39.42 amd64 [installed]
```

I've done these steps already: [https://askubuntu.com/questions/878097/more-wifi-issues-qualcomm-atheros-qca6174-ath10k-pci](https://askubuntu.com/questions/878097/more-wifi-issues-qualcomm-atheros-qca6174-ath10k-pci)

This includes:
```
sudo apt-get install --reinstall linux-firmware
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
There were no errors. I rebooted. And the problem persisted.

Another thread ([https://askubuntu.com/questions/870412/wifi-dell-xps-13-9360-keeps-disconnecting-with-qca6174-802-11ac-wireless-network](https://askubuntu.com/questions/870412/wifi-dell-xps-13-9360-keeps-disconnecting-with-qca6174-802-11ac-wireless-network)) said to install a custom kernel module. I downloaded the most recent module (**firmware-6.bin...**) in github directory [**ath10k-firmware/QCA6174/hw3.0/4.4.1.c3/**]("https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw3.0/4.4.1.c3"). And replaced the **/lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin** file with the one just downloaded. I then ran the following commands.
```
sudo modprobe -r ath10k_pci ath10k_core
sudo modprobe ath10k_pci
sudo modprobe ath10k_core
```

The problem of the wifi signal dropping and coming back up persisted.

Another thread ([https://askubuntu.com/questions/1200550/qualcomm-qca6174-unstable-wifi-and-bluetooth](https://askubuntu.com/questions/1200550/qualcomm-qca6174-unstable-wifi-and-bluetooth)) also mentioned installing a custom firmware ([https://github.com/thebitstick/surfacego-wifi](https://github.com/thebitstick/surfacego-wifi)). 

I fear bricking my laptop if I try something for a different device altogether. And so I haven't installed any custom kernel modules or firmware. Is this really the answer? If so, which one?

Please help.

---

### Post by nemethda on 2020-10-18
Hey paseuno,
 
Did you manage to resolve your issue? I'm having the same problem that I posted here: [https://ubuntuforums.org/showthread.php?t=2452107](https://ubuntuforums.org/showthread.php?t=2452107). So far I also came to the conclusion that my wifi chip is the problem, I have the same firmware for it:

```
[    9.097092] systemd[1]: /lib/systemd/system/dbus.socket:5: ListenStream= references a path below legacy directory /var/run/, updating /var/run/dbus/system_bus_socket &#8594; /run/dbus/system_bus_socket; please update the unit file accordingly.[    9.139326] systemd[1]: /lib/systemd/system/docker.socket:6: ListenStream= references a path below legacy directory /var/run/, updating /var/run/docker.sock &#8594; /run/docker.sock; please update the unit file accordingly.
[    9.831157] ath10k_pci 0000:04:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[   10.141870] ath10k_pci 0000:04:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
[   10.141873] ath10k_pci 0000:04:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   10.142300] ath10k_pci 0000:04:00.0: firmware ver WLAN.RM.4.4.1-00140-QCARMSWPZ-1 api 6 features wowlan,ignore-otp,mfp crc32 29eb8ca1
[   10.207281] ath10k_pci 0000:04:00.0: board_file api 2 bmi_id N/A crc32 4ac0889b
[   10.295028] ath10k_pci 0000:04:00.0: unsupported HTC service id: 1536
[   10.314528] ath10k_pci 0000:04:00.0: htt-ver 3.60 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   10.416195] ath: EEPROM regdomain: 0x6c
[   10.416196] ath: EEPROM indicates we should expect a direct regpair map
[   10.416198] ath: Country alpha2 being used: 00
[   10.416198] ath: Regpair used: 0x6c
[   10.419781] ath10k_pci 0000:04:00.0 wlp4s0: renamed from wlan0
[   61.179810] ath10k_pci 0000:04:00.0: unsupported HTC service id: 1536

```

I've personally tried this suggestion too: [https://github.com/thebitstick/surfacego-wifi/issues](https://github.com/thebitstick/surfacego-wifi/issues) but didn't work. I'm also cautious to fiddle with firmware.. So I was wondering if you managed to resolve the issue since your post?

Thanks!

---

