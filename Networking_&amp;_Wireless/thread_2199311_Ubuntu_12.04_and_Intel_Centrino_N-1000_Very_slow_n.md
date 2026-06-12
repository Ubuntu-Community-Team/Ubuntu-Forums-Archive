---
title: "Ubuntu 12.04 and Intel Centrino N-1000 Very slow network"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by igor.shaldev on 2014-01-13
Hello, 

I am having trouble reaching normal connection speeds on this laptop when running Linux (Ubuntu 12.04). When booting in Windows download speeds are normal, but in linux the computer cannot pass 2Mbps. I tried creating a file /etc/modprobe.d/iwlwifi.conf and add the line options iwlwifi 11n_disable=1 But nothing changed. I also installed new firmware from [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi) but again nothing changed. Also I noticed that some networks are not visible at all. Any ideas?

```
[COLOR=#000000][I]# lspci | grep Network
[/I][/COLOR]04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
```

```
# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"***"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:281  Invalid misc:3925   Missed beacon:0
```

```
# dmesg | grep iwl
[    8.112523] iwlwifi 0000:04:00.0: irq 50 for MSI/MSI-X
[    8.334091] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
[    8.832685] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    8.832686] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    8.832687] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    8.832688] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    8.832689] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_P2P disabled
[    8.832691] iwlwifi 0000:04:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    8.832825] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[    8.840179] iwlwifi 0000:04:00.0: RF_KILL bit toggled to enable radio.
[    8.858149] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.259857] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   13.267226] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   13.407778] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   13.415142] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
```

---

### Post by praseodym on 2014-01-13
Deactivate the N-mode (bug) of the driver:
```

echo "options 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Edit: I just saw you tried it. Change the encryption mode to pure WPA2-AES and a fixed channel

---

### Post by igor.shaldev on 2014-01-13
Thanks for the reply
I already tried that, rebooted and nothing changed.

---

### Post by ukbeast on 2014-01-13
Also try updating kernel [http://ubuntuhandbook.org/index.php/2013/12/install-kernel-3-12-6-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2013/12/install-kernel-3-12-6-ubuntu-linux-mint/)

 sudo apt-get install linux-headers-generic build-essential 
   wget [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2)
   tar xvf backports-3.12.2-1.tar.bz2
   cd backports-3.12.2-1
   make defconfig-wifi
   make
   sudo make install

---

### Post by igor.shaldev on 2014-01-14
I just compiled and installed the new modules. Again the same speed. Does not pass 2Mb/s. 

Another note: I tried running ubuntu 13 live cd and fedora 20, both connected at the same speed. So it's probably broken driver.

> **ukbeast said:**
> Also try updating kernel [http://ubuntuhandbook.org/index.php/2013/12/install-kernel-3-12-6-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2013/12/install-kernel-3-12-6-ubuntu-linux-mint/)

 sudo apt-get install linux-headers-generic build-essential 
   wget [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2)
   tar xvf backports-3.12.2-1.tar.bz2
   cd backports-3.12.2-1
   make defconfig-wifi
   make
   sudo make install

---

### Post by praseodym on 2014-01-14
Shouldnt it had been

```
 make defconfig-iwlwifi
```
?!

---

### Post by igor.shaldev on 2014-01-14
I think it also compiled iwlwifi, among others.

```
modinfo iwlwifi
filename:       /lib/modules/3.8.0-35-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        backported from Linux (v3.12.2-0-g050dcf4) using backports v3.12.2-1-0-gb4b7ee5
....
```

> **praseodym said:**
> Shouldnt it had been

```
 make defconfig-iwlwifi
```
?!

---

### Post by chili555 on 2014-01-14
> I think it also compiled iwlwifi, among others.Correct. defconfig-wifi compiles all the wireless drivers; defconfig-iwlwifi compiles only the iwlwifi suite, skipping,among others ath9k, b43, rtlwifi, etc., etc.

I hope my friend praseodym won't mind if I offer a suggestion or two.

The driver iwlwifi and its associated firmware are tricky; when they work, they are wonderful and when they don't, they are difficult to tweak and get going correctly. I myself have and use two iwlxx devices. I have become convinced, because I have owned two different routers and traveled extensively with one iwlwifi laptop; thereby attaching to many different brands and types of routers, that the device is somewhat router dependent. I suggest you experiment with settings in the router. If yours offers channel width Auto, try 20 MHz only. If it offers Auto channel, try setting it on a fixed channel, 11, perhaps. If it offers 2.4 GHz or 5.8 GHz, try limiting it to 2.4. If it offers mixed mode B, G and N, try setting it to B and G only. 

If you find that magic combination of settings that fixes the issue, be sure to report so that all the rest of us can benefit from your experience.

---

### Post by praseodym on 2014-01-14
Any firmware errors?
```
egrep -i 'fw|firm' /var/log/syslog 
dmesg | egrep 'iwl|[F]irm'
```
You could update the firmware via:```

wget de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.116_all.deb
sudo dpkg -i linux-firmware_1.116_all.deb 
```
and reboot.

Of course, check also chili555's recommendations with your router settings.

---

### Post by igor.shaldev on 2014-01-14
I will try to change the router settings, but I don't think I can do that with all networks.

egrep -i 'fw|firm' /var/log/syslog
```
Jan 13 12:46:02 shaldev-xps kernel: [    0.254985] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 13 12:46:02 shaldev-xps kernel: [    8.519602] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 13 12:46:02 shaldev-xps kernel: [    8.610828] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 13 12:46:02 shaldev-xps kernel: [    9.401596] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 13 12:46:05 shaldev-xps NetworkManager[950]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 13 12:57:59 shaldev-xps kernel: [    0.255937] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 13 12:57:59 shaldev-xps kernel: [    8.535415] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 13 12:57:59 shaldev-xps kernel: [    8.571617] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 13 12:57:59 shaldev-xps kernel: [    9.159227] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 13 12:58:04 shaldev-xps NetworkManager[968]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 13 13:16:53 shaldev-xps NetworkManager[968]: <info> kernel firmware directory '/lib/firmware' changed
Jan 13 13:21:54 shaldev-xps NetworkManager[968]: <info> kernel firmware directory '/lib/firmware' changed
Jan 13 13:23:59 shaldev-xps kernel: [    0.256480] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 13 13:23:59 shaldev-xps kernel: [    8.579037] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 13 13:23:59 shaldev-xps kernel: [    9.198354] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 13 13:23:59 shaldev-xps kernel: [    9.399284] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 13 13:24:02 shaldev-xps NetworkManager[961]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 13 13:36:43 shaldev-xps NetworkManager[961]: <info> kernel firmware directory '/lib/firmware' changed
Jan 13 13:44:44 shaldev-xps kernel: [    0.255294] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 13 13:44:44 shaldev-xps kernel: [    7.946617] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 13 13:44:44 shaldev-xps kernel: [    8.045725] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 13 13:44:44 shaldev-xps kernel: [    9.120458] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 13 13:44:47 shaldev-xps NetworkManager[964]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 13 13:57:14 shaldev-xps kernel: [    0.255628] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 13 13:57:14 shaldev-xps kernel: [    8.334091] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 13 13:57:14 shaldev-xps kernel: [    8.721552] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 13 13:57:14 shaldev-xps kernel: [    9.198640] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 13 13:57:17 shaldev-xps NetworkManager[947]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 13 15:29:16 shaldev-xps kernel: [    0.255663] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 13 15:29:16 shaldev-xps kernel: [    8.509757] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 13 15:29:16 shaldev-xps kernel: [    8.820978] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 13 15:29:16 shaldev-xps kernel: [    9.207172] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 13 15:29:18 shaldev-xps NetworkManager[916]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 20:51:22 shaldev-xps kernel: [    0.255279] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 14 20:51:22 shaldev-xps kernel: [    8.825120] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 14 20:51:22 shaldev-xps kernel: [    8.840983] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 14 20:51:22 shaldev-xps kernel: [    9.338034] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 14 20:51:27 shaldev-xps NetworkManager[971]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 20:56:29 shaldev-xps NetworkManager[971]: <info> kernel firmware directory '/lib/firmware' changed
Jan 14 20:58:16 shaldev-xps kernel: [    0.255263] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 14 20:58:16 shaldev-xps kernel: [    9.073514] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138
Jan 14 20:58:16 shaldev-xps kernel: [    9.351789] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 14 20:58:16 shaldev-xps kernel: [   11.184538] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 14 20:58:19 shaldev-xps NetworkManager[938]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 21:16:22 shaldev-xps kernel: [    0.259467] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 14 21:16:22 shaldev-xps kernel: [    9.250816] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
Jan 14 21:16:22 shaldev-xps kernel: [    9.448402] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
Jan 14 21:16:23 shaldev-xps kernel: [   11.442234] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jan 14 21:16:25 shaldev-xps NetworkManager[949]: <info> monitoring kernel firmware directory '/lib/firmware'.
```

dmesg | egrep 'iwl|[F]irm'
```
[    0.259467] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    9.220541] iwlwifi 0000:04:00.0: irq 50 for MSI/MSI-X
[    9.250816] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[    9.883001] iwlwifi 0000:04:00.0: CPTCFG_IWLWIFI_DEBUG disabled
[    9.883007] iwlwifi 0000:04:00.0: CPTCFG_IWLWIFI_DEBUGFS disabled
[    9.883009] iwlwifi 0000:04:00.0: CPTCFG_IWLWIFI_DEVICE_TRACING disabled
[    9.883012] iwlwifi 0000:04:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.883113] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   10.086216] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.442234] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   14.003079] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   14.010449] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   14.044852] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   14.052247] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[ 3580.711214] iwlwifi 0000:04:00.0: RF_KILL bit toggled to enable radio.
[ 3584.107285] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 3584.114668] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
```

---

### Post by igor.shaldev on 2014-01-14
This is the first improvement I saw. Wifi is now connected at 12Mb/s

> **praseodym said:**
> 
You could update the firmware via:```

wget de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.116_all.deb
sudo dpkg -i linux-firmware_1.116_all.deb 
```
and reboot.

Of course, check also chili555's recommendations with your router settings.

---

### Post by igor.shaldev on 2014-01-15
I noticed another thing. If I run a bandwidth speed test, again the bit rate drops. I also tried changing the wifi router settings. But nothing changed. On some channels the bandwidth test was even slower. I chose a channel which has the least number of routers available in range.

---

### Post by igor.shaldev on 2014-01-21
Any new ideas? Today I will try switching the wifi network card. I hope it will help.

---

