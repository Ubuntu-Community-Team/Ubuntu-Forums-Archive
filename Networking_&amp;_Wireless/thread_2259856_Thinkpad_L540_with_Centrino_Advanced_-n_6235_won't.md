---
title: "Thinkpad L540 with Centrino Advanced -n 6235 won't connect WiFi"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by EmilyRose on 2015-01-07
Hi there, 

My husband has a Thinkpad L540 which he's had issues with the WiFi with off and on for a while now. It connects to our (unprotected) WiFi network at home fine, but only connects to password protected networks sporadicly - instead of connecting it often just repeatedly asks for a the password and then tries and tries to connect and asks for a password, over and over and over. 

lspci -nn | grep 0280 output is:

intel corporation centrino advanced -n 6235 [8086:088s] (rev 24) 

ETA: He's currently running Ubuntu 14.04 

Thanks in advance.

---

### Post by chili555 on 2015-01-07
> **EmilyRose said:**
> Hi there, 

My husband has a Thinkpad L540 which he's had issues with the WiFi with off and on for a while now. It connects to our (unprotected) WiFi network at home fine, but only connects to password protected networks sporadicly - instead of connecting it often just repeatedly asks for a the password and then tries and tries to connect and asks for a password, over and over and over. 

lspci -nn | grep 0280 output is:

intel corporation centrino advanced -n 6235 [8086:088s] (rev 24) 

ETA: He's currently running Ubuntu 14.04 

Thanks in advance.I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

---

### Post by EmilyRose on 2015-01-07
Unfortuantly the router's he's trying to connect to and which gives him problems semi-regularly neither of us has access to change any settings on (tis at his job). But we'll give the rest of your suggestions a shot :) Thanks!

---

### Post by EmilyRose on 2015-01-13
Initially changing to ignore IpV6 seemed to fix it. But the next time he started up his system, it was back to cycling. Neither of the next suggestions appears to be having any effect.

---

### Post by chili555 on 2015-01-13
> **EmilyRose said:**
> Initially changing to ignore IpV6 seemed to fix it. But the next time he started up his system, it was back to cycling. Neither of the next suggestions appears to be having any effect.Let's keep trying.```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the last line from:```
options iwlwifi 11n_disable=8
```To:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close the text editor.

Reboot and let us hear your report. If it is still not working as expected, please let us see:```
dmesg | grep -e iwl -e wlan
```Thanks.

---

### Post by EmilyRose on 2015-01-13
No change.

---

### Post by chili555 on 2015-01-13
> **EmilyRose said:**
> No change. If it is still not working as expected, please let us see:
```
dmesg | grep -e iwl -e wlan
```
Thanks.

---

### Post by EmilyRose on 2015-01-13
output of dmesg | grep -e iwl -e wlan is: 

```
 kevin@wreck-it-ralph:~$ dmesg | grep -e iwl -e wlan
[   15.614585] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   15.614732] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[   15.859831] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   16.085825] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.085826] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.085827] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.085829] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[   16.085944] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   16.130865] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.667038] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   21.672651] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[   21.945554] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   21.951044] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[   24.030772] iwlwifi 0000:02:00.0: Error sending REPLY_TX_POWER_DBM_CMD: time out after 2000ms.
[   24.030776] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 27 write_ptr 28
[   24.031039] iwlwifi 0000:02:00.0: Loaded firmware version: 18.168.6.1
[   24.031074] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   24.031076] iwlwifi 0000:02:00.0: CSR values:
[   24.031078] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   24.031084] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00484b00
[   24.031090] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[   24.031095] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[   24.031100] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   24.031106] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   24.031111] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000030
[   24.031117] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[   24.031122] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403cd
[   24.031128] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X000000b0
[   24.031133] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X42110ffd
[   24.031139] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X90000801
[   24.031144] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X00030001
[   24.031150] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
[   24.031155] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X0000000e
[   24.031161] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   24.031166] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   24.031172] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   24.031177] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000040
[   24.031183] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8811a43b
[   24.031188] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   24.031194] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   24.031199] iwlwifi 0000:02:00.0:      CSR_MONITOR_STATUS_REG: 0X6bf7f757
[   24.031205] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   24.031210] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[   24.031212] iwlwifi 0000:02:00.0: FH register values:
[   24.031228] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[   24.031229] iwlwifi 0000:02:00.0: Status: 0x0000204C, count: 6
[   24.031231] iwlwifi 0000:02:00.0: 0x00000066 | NMI_INTERRUPT_HOST         
[   24.031233] iwlwifi 0000:02:00.0: 0x00010564 | uPc
[   24.031234] iwlwifi 0000:02:00.0: 0x0001054E | branchlink1
[   24.031236] iwlwifi 0000:02:00.0: 0x00010580 | branchlink2
[   24.031237] iwlwifi 0000:02:00.0: 0x0000DBEA | interruptlink1
[   24.031239] iwlwifi 0000:02:00.0: 0x00000402 | interruptlink2
[   24.031240] iwlwifi 0000:02:00.0: 0x00000001 | data1
[   24.031241] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X11a46500
[   24.031243] iwlwifi 0000:02:00.0: 0x07030000 | data2
[   24.031245] iwlwifi 0000:02:00.0: 0x000260A4 | line
[   24.031246] iwlwifi 0000:02:00.0: 0x000189BC | beacon time
[   24.031248] iwlwifi 0000:02:00.0: 0x00000644 | tsf low
[   24.031252] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[   24.031253] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[   24.031255] iwlwifi 0000:02:00.0: 0x00011C59 | time gp2
[   24.031256] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[   24.031258] iwlwifi 0000:02:00.0: 0x754312A8 | uCode version
[   24.031259] iwlwifi 0000:02:00.0: 0x000000B0 | hw version
[   24.031261] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X011a4640
[   24.031262] iwlwifi 0000:02:00.0: 0x00484B00 | board version
[   24.031263] iwlwifi 0000:02:00.0: 0x091A0013 | hcmd
[   24.031264] iwlwifi 0000:02:00.0: 0x00022080 | isr0
[   24.031266] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[   24.031267] iwlwifi 0000:02:00.0: 0x00000602 | isr2
[   24.031268] iwlwifi 0000:02:00.0: 0x0145D4C0 | isr3
[   24.031270] iwlwifi 0000:02:00.0: 0x00000000 | isr4
[   24.031271] iwlwifi 0000:02:00.0: 0x01000112 | isr_pref
[   24.031272] iwlwifi 0000:02:00.0: 0x000260A4 | wait_event
[   24.031274] iwlwifi 0000:02:00.0: 0x00000000 | l2p_control
[   24.031275] iwlwifi 0000:02:00.0: 0x00000000 | l2p_duration
[   24.031276] iwlwifi 0000:02:00.0: 0x00000000 | l2p_mhvalid
[   24.031278] iwlwifi 0000:02:00.0: 0x00000000 | l2p_addr_match
[   24.031279] iwlwifi 0000:02:00.0: 0x00000004 | lmpm_pmg_sel
[   24.031280] iwlwifi 0000:02:00.0: 0x13011136 | timestamp
[   24.031282] iwlwifi 0000:02:00.0: 0x00001828 | flow_handler
[   24.031335] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000018
[   24.031361] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[   24.031387] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   24.031400] iwlwifi 0000:02:00.0: Start IWL Event Log Dump: display last 1 entries
[   24.031413] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   24.031430] iwlwifi 0000:02:00.0: EVT_LOGT:0000072793:0x0000010c:0123
[   24.031469] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   24.031482] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   24.031506] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   24.031515] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.031935] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   24.037392] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[   48.877497] wlan0: authenticate with c0:ea:e4:5d:a8:85
[   48.879755] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[   48.882019] wlan0: authenticated
[   48.882192] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[   51.715358] wlan0: authenticate with c0:ea:e4:5d:a8:85
[   51.716929] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[   51.718954] wlan0: authenticated
[   51.719085] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[   54.922349] wlan0: authenticate with c0:ea:e4:5d:a8:85
[   54.925695] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[   54.927720] wlan0: authenticated
[   54.927821] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[   58.630596] wlan0: authenticate with c0:ea:e4:5d:a8:85
[   58.633110] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[   58.635210] wlan0: authenticated
[   58.635384] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[   76.646987] wlan0: authenticate with c0:ea:e4:5d:a8:85
[   76.649531] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[   76.651580] wlan0: authenticated
[   76.651706] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[   89.388340] wlan0: authenticate with c0:ea:e4:5d:a8:85
[   89.390522] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[   89.392633] wlan0: authenticated
[   89.392797] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[  104.678630] wlan0: authenticate with c0:ea:e4:5d:a8:85
[  104.680371] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[  104.683642] wlan0: authenticated
[  104.683777] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[  117.390895] wlan0: authenticate with c0:ea:e4:5d:a8:85
[  117.393408] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[  117.395494] wlan0: authenticated
[  117.395666] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[  131.816417] wlan0: authenticate with c0:ea:e4:5d:a8:85
[  131.818648] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[  131.823033] wlan0: authenticated
[  131.823169] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[  144.564937] wlan0: authenticate with c0:ea:e4:5d:a8:85
[  144.567461] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[  144.569561] wlan0: authenticated
[  144.569689] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85
[  165.655809] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.656014] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.656243] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.656499] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.656964] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.657171] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.657847] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.658090] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  165.658415] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.970835] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.971032] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.971211] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.971431] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.971791] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.971990] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.972508] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.972688] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  203.973034] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  215.736744] wlan0: authenticate with c0:ea:e4:5d:a8:85
[  215.740344] wlan0: send auth to c0:ea:e4:5d:a8:85 (try 1/3)
[  215.742553] wlan0: authenticated
[  215.742640] wlan0: waiting for beacon from c0:ea:e4:5d:a8:85

```

---

### Post by chili555 on 2015-01-13
> [   24.031074] iwlwifi 0000:02:00.0: [COLOR="#FF0000"]Microcode SW error detected.  Restarting[/COLOR] 0x2000000.
[   24.031076] iwlwifi 0000:02:00.0: CSR values:
[   24.031078] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   24.031084] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00484b00
[   24.031090] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[   24.031095] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[   24.031100] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   24.031106] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   24.031111] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000030
[   24.031117] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[   24.031122] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403cd
[   24.031128] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X000000b0
[   24.031133] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X42110ffdAh, haaa!!!

This is a fairly regularly reported error that prevents connection. Unfortuneatly, the perfect fix is never reported. I suggest we try a few things and see if we stumble on to a fix. First, let's see if the firmware on your system is uncorrupt:```
md5sum /lib/firmware/iwlwifi-6000g2b-6.ucode 
```On my system, it returns:```
[COLOR="#FF0000"]1f1763dfd472a487c3d61eac0a12b766[/COLOR]  /lib/firmware/iwlwifi-6000g2b-6.ucode
```If yours doesn't return exactly the same, reinstall the firmware package:```
sudo apt-get install  --reinstall linux-firmware
```Reboot and check:```
dmesg | grep iwl
```If that doesn't help; that is, the microcode error remains, we will install a later kernel and its included driver. In order to propose a newer kernel, we need to know which you have now:```
uname -r
```

---

### Post by EmilyRose on 2015-01-13
Interestingly it randomly started to work an hour or so ago. I had him check the above stuff out anyhow though, and md5sum /lib/firmware/iwlwifi-6000g2b-6.ucode returns the same result as yours, while dmesg is still spitting out the above Microcode SW error. 

He's currently running: 

3.16.2-031602-generic

(I updated the kernel a couple days ago in hopes that would help, but no such luck.)

---

### Post by chili555 on 2015-01-13
I've read...and written!...dozens of posts about iwlwifi microcode. One suggested that unloading and reloading iwldvm might help. The next time it won't connect, try:```
sudo modprobe -r iwldvm
sudo modprobe iwldvm
```Does it magically spring to life? If not, we get out the heavy equipment and perform a major rehab.

If it does help, we can automate the process during boot.

---

