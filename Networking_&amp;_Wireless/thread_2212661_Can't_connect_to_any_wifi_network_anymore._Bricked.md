---
title: "Can't connect to any wifi network anymore. Bricked wifi?"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by b-j-van-der-weij on 2014-03-22
It seems like my Wifi card is bricked but I can't figure out why. The symptoms started after a suspend/resume though I;m not sure if that's connected. I was just browsing and suddenly the connection dropped. The symptoms:


1. Unable to connect to any wifi network (open or secure)
2. Scanning for networks works fine
3. Secure networks ask for a password and security type is recognised
4. Issues started seemingly spontaneously
5. Rebooting/turning hardware switch on and off doesn't fix it.


Other info:


1. Ubuntu 13.10 amd 64
2. Wifi hardware: 04:00.0 Network controller: Intel Corporation WiFi Link 5100
3. dmesg output while connecting (same for open or secure networks):
```

 wlan0: authenticate with xx:xx:xx:xx:xx:xx
 wlan0: direct probe to xx:xx:xx:xx:xx:xx (try 1/3)
 wlan0: direct probe to xx:xx:xx:xx:xx:xx (try 2/3)
 wlan0: direct probe to xx:xx:xx:xx:xx:xx (try 3/3)
 wlan0: authentication with xx:xx:xx:xx:xx:xx timed out

```
4.  lspci -vv -s 04:00.0

```

04:00.0 Network controller: Intel Corporation WiFi Link 5100
    Subsystem: Intel Corporation WiFi Link 5100 AGN
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort->SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 46
    Region 0: Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi

```
5. sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-18-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f8000000-f8001fff

```


6. sudo modinfo iwlwifi
```

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     4E0989C8DF6E607C718E63C
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
...
.... and much more of this
...
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

```


Is there any way to confirm that the device is bricked? Or can I fix this?

---

### Post by chili555 on 2014-03-22
Your device is certainly not bricked. Let's look at some additional diagnostics:```
dmesg | grep iwl
sudo iwlist wlan0 scan
```For the scan, just pick out your preferred network and post the details. Please obscure the MAC address something like this:```
wlan0     Scan completed :
          Cell 01 - [COLOR="#FF0000"]Address: xx:D7:19:41:54:xx[/COLOR]
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001392932126f
                    Extra: Last beacon: 144ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

---

### Post by b-j-van-der-weij on 2014-03-22
Good to hear! Here you go:

dmesg | grep iwl
```

[    3.336919] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.336983] iwlwifi 0000:04:00.0: irq 46 for MSI/MSI-X
[    3.370102] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    3.402744] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.402749] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.402751] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.402754] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_P2P disabled
[    3.402757] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    3.408813] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[    3.492316] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2566.224293] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 2566.227369] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[ 2566.327560] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 2566.330703] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[ 4337.574663] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 4337.577746] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[ 5268.070169] iwlwifi 0000:04:00.0: RF_KILL bit toggled to disable radio.
[ 5268.070522] iwlwifi 0000:04:00.0: Not sending command - RF KILL
[ 5268.070534] iwlwifi 0000:04:00.0: Not sending command - RF KILL
[ 5268.070571] iwlwifi 0000:04:00.0: Not sending command - RF KILL
[ 5268.070592] iwlwifi 0000:04:00.0: Not sending command - RF KILL
[ 5268.120045] iwlwifi 0000:04:00.0: Not sending command - RF KILL
[ 5270.446578] iwlwifi 0000:04:00.0: RF_KILL bit toggled to enable radio.
[ 5270.449224] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 5270.452498] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0

```
iwlist scan output
```

         Cell 07 - Address: xx:xx:xx:xx:xx:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"DeepThought"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a9f19a1b7
                    Extra: Last beacon: 3004ms ago
                    IE: Unknown: 000B4465657054686F75676874
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 050C000100000000000000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by chili555 on 2014-03-22
I own and use successfully two Intel wireless devices. I have honed a few techniques in years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit. If these changes do not help, please try:```
sudo modprobe -r iwldvm
sudo modprobe iwlwifi 11n_disable=1
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

---

### Post by b-j-van-der-weij on 2014-03-22
Thanks for your reply!

> **chili555 said:**
> I own and use successfully two Intel wireless devices. I have honed a few techniques in years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1 or 11, rather than automatic channel selection. After making these changes, reboot the router.


My CISCO router doesn't seem to support any other security protocol. I'm pretty sure though that the wifi issues are not network specific. I can't connect to *any* network. Not at home, not at uni, and not to open wifi networks (such as the android hotspot I created for testing this). The puzzling thing is that it used to work just fine...

> 
Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit. If these changes do not help, please try:```
sudo modprobe -r iwldvm
sudo modprobe iwlwifi 11n_disable=1
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

Doesn't seem to have any effect, my connection attempts still time out :(

---

### Post by chili555 on 2014-03-22
Let's see if the logs have any clues:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```Ideally, run as you are trying to connect and any ethernet cable is detached.

---

### Post by b-j-van-der-weij on 2014-03-22
Here you go. There are some suspicious lines there but they don't seem to immediately indicate the problem:

Activation (wlan0/wireless): association took too long, failing activation.


(wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]

 I'd have to do some googling. I'll look into it more tomorrow!

```

Mar 23 00:28:49 xxx kernel: [  622.716117] wlan0: authentication with xx:xx:xx:xx:xx:xx timed out
Mar 23 00:28:49 xxx NetworkManager[665]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 23 00:28:49 xxx NetworkManager[665]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 23 00:29:00 xxx wpa_supplicant[979]: wlan0: SME: Trying to authenticate with xx:xx:xx:xx:xx:xx (SSID='DeepThought' freq=2462 MHz)
Mar 23 00:29:00 xxx kernel: [  634.040062] wlan0: authenticate with xx:xx:xx:xx:xx:xx
Mar 23 00:29:00 xxx kernel: [  634.045501] wlan0: direct probe to xx:xx:xx:xx:xx:xx (try 1/3)
Mar 23 00:29:00 xxx NetworkManager[665]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 23 00:29:00 xxx kernel: [  634.248126] wlan0: direct probe to xx:xx:xx:xx:xx:xx (try 2/3)
Mar 23 00:29:01 xxx kernel: [  634.452096] wlan0: direct probe to xx:xx:xx:xx:xx:xx (try 3/3)
Mar 23 00:29:01 xxx kernel: [  634.656282] wlan0: authentication with xx:xx:xx:xx:xx:xx timed out
Mar 23 00:29:01 xxx NetworkManager[665]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 23 00:29:01 xxx NetworkManager[665]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 23 00:29:02 xxx NetworkManager[665]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Mar 23 00:29:02 xxx NetworkManager[665]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Mar 23 00:29:02 xxx NetworkManager[665]: <info> Marking connection 'DeepThought' invalid.
Mar 23 00:29:02 xxx NetworkManager[665]: <warn> Activation (wlan0) failed for connection 'DeepThought'
Mar 23 00:29:02 xxx NetworkManager[665]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 23 00:29:02 xxx NetworkManager[665]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 23 00:29:02 xxx NetworkManager[665]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Mar 23 00:29:02 xxx NetworkManager[665]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```

---

### Post by Jeroen115 on 2014-03-23
I had exactly the same issue with an HP625 laptop with Ubuntu 12.04, just today 23 mar I could not connect to the wlan at home.
Using a wired connection, applied the latest updates incl. the newest kernel to the system.
This did not solve the problem.
I managed to get it working again in a very strange way: booted off an Ubuntu 12.10 DVD and choosed "try ubuntu", then connected to my wlan in the usual way (WPA2 PSK).
This proved the hardware and wlan were OK.
Then just rebooted the machine (without powering off) off the HDD with 12.04.
Could connect to the wlan without any issue.
Cannot check whether just a powercycle would do the same, maybe it does.
Maybe the hardware indeed was bricked in some way, driver issue?

---

### Post by chili555 on 2014-03-23
Let's dig a bit deeper; after a fresh reboot so we have a clean slate:```
dmesg | grep -e iwl -e 04:00
```I include this solely for completeness, but I've seen two similar cases where the device wiggled a bit loose and one where the antenna wires were not firmly attached. Can you check the hardware? On some laptops, there is a door on the bottom that you can use to access the wireless card. If you decide to check, I'd download the repair and maintenance manual and carefully follow all the safety and grounding precautions.

[http://beta.ivc.no/wiki/images/thumb/3/34/Eee_wifi_connector.jpg/400px-Eee_wifi_connector.jpg](http://beta.ivc.no/wiki/images/thumb/3/34/Eee_wifi_connector.jpg/400px-Eee_wifi_connector.jpg) It may be similar but not exactly like this.

---

### Post by b-j-van-der-weij on 2014-03-23
```

[    0.200281] pci 0000:04:00.0: [8086:4232] type 00 class 0x028000
[    0.200341] pci 0000:04:00.0: reg 0x10: [mem 0xf8000000-0xf8001fff 64bit]
[    0.200540] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    2.914716] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.914827] iwlwifi 0000:04:00.0: irq 48 for MSI/MSI-X
[    3.038988] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    3.077632] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.077638] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.077640] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.077643] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_P2P disabled
[    3.077645] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    3.078280] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[    3.185839] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.091555] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   18.096982] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   18.199306] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   18.202540] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0

```

I'll have a look inside my laptop. It might indeed be that! 

I think I've also tried a 13.04 liveusb in which my wifi (worryingly) didn't work either. I'll try again shortly to verify.

---

### Post by b-j-van-der-weij on 2014-03-23
It was quite easy to locate my wifi card and it did seem that one of the antenna's was a little loose. Unfortunately, putting it in place didn't solve the issue. The card itself sat firmly in it's mini pci slot, secured by a screw so that seems not to be the issue either.

---

### Post by b-j-van-der-weij on 2014-03-25
So I'm still dragging cables around my house! I tried booting into a liveusb containing the current unstable version of ubuntu 14.04 and confirmed that wifi is not working there either, that seems worrying right? Anyone a clue?

---

