---
title: "RTL8187 (AWUS036H) + hostpad = not possible in Linux?"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by altjx on 2015-11-18
I've been battling this issue literally all day long, and I know it's pretty embarrassing. I've been trying to get hostapd-wpe working for the last 7-8 hours and I've been constantly googling and trying various things, and it's mentally draining after all of this time.

So as opposed to posting all of the millions of things that I've tried thus far, I'll just post the issue that I'm having. I'm using an AWUS036H Alfa USB Wireless card and trying to get it to host a WPA2 + Enterprise network. I can successfully host WEP/WPA/WPA2 using the Alfa LAN Utility software on Windows, but Linux acts like the device can't host APs at all. running hostapd-wpe gives me this issue:

```
alt@ubuntu:~/Desktop/hostapd-2.2/hostapd$ sudo ./hostapd-wpe -dd hostapd-wpe.conf 
random: Trying to read entropy from /dev/random
Configuration file: hostapd-wpe.conf
ctrl_interface_group=0
rfkill: initial event: idx=2 type=2 op=0 soft=0 hard=0
rfkill: initial event: idx=3 type=1 op=0 soft=0 hard=0
nl80211: Supported cipher 00-0f-ac:1
nl80211: Supported cipher 00-0f-ac:5
nl80211: Supported cipher 00-0f-ac:2
nl80211: Supported cipher 00-0f-ac:4
nl80211: Supported cipher 00-0f-ac:10
nl80211: Supported cipher 00-0f-ac:8
nl80211: Supported cipher 00-0f-ac:9
nl80211: Using driver-based off-channel TX
nl80211: interface wlx00c0ca823130 in phy phy1
nl80211: Set mode ifindex 4 iftype 3 (AP)
nl80211: Failed to set interface 4 to mode 3: -95 (Operation not supported)
nl80211: Try mode change after setting interface down
nl80211: Set mode ifindex 4 iftype 3 (AP)
nl80211: Failed to set interface 4 to mode 3: -95 (Operation not supported)
^Cnl80211: Interface mode change to 3 from 0 failed
nl80211: Could not configure driver mode
nl80211: Remove monitor interface: refcount=0
netlink: Operstate: ifindex=4 linkmode=0 (kernel-control), operstate=6 (IF_OPER_UP)
nl80211: Set mode ifindex 4 iftype 2 (STATION)
nl80211 driver initialization failed.
hostapd_interface_deinit_free(0x11a3e10)
hostapd_interface_deinit_free: num_bss=1 conf->num_bss=1
hostapd_interface_deinit(0x11a3e10)
hostapd_bss_deinit: deinit bss wlx00c0ca823130
hostapd_cleanup(hapd=0x11a77c0 (wlx00c0ca823130))
hostapd_free_hapd_data: Interface wlx00c0ca823130 wasn't started
hostapd_interface_deinit_free: driver=(nil) drv_priv=(nil) -> hapd_deinit
hostapd_interface_free(0x11a3e10)
hostapd_interface_free: free hapd 0x11a77c0
hostapd_cleanup_iface(0x11a3e10)
hostapd_cleanup_iface_partial(0x11a3e10)
hostapd_cleanup_iface: free iface=0x11a3e10



```

I'm so out of ideas right now it's ridiculous. I've tried rfkill, unblocking the wireless card, tried installing compat-wireless (not sure if this installed correctly, but my wireless card didn't show up after rebooting), rebooting a few times, and even tried downloading the RTL8187 drivers from Realtek's website -- this didn't compile correctly and not sure what that issue was all about.

I thought I had this working a few months ago, and now all of a sudden I can't get it to work for the life of me.

Any help would be seriously appreciated here. I really need to get this working before tomorrow and it's extremely frustrating dealing with all these annoying driver issues.

---

### Post by howefield on 2015-11-18
Thread moved to the "*Networking & Wireless*" forum, probably a better fit for your query.

---

### Post by altjx on 2015-11-18
Thanks howefield.

---

### Post by chili555 on 2015-11-18
> nl80211: Set mode ifindex 4 iftype 3 (AP)
nl80211: Failed to set interface 4 to mode 3: -95 (Operation not supported)Not all hardware and driver combinations do all modes. You can check with:```
iw list
```My Intel card says:> Supported interface modes:
		 * IBSS
		 * managed
		 * monitor
No AP mode there. I also have an Atheros USB that reports: > Supported interface modes:
		 * IBSS
		 * managed
		 [COLOR="#FF0000"]* AP
		 * AP/VLAN[/COLOR]
		 * monitor
		 * mesh point
		 * P2P-client
		 * P2P-GO
What does yours report?

---

### Post by altjx on 2015-11-18
> **chili555 said:**
> Not all hardware and driver combinations do all modes. You can check with:```
iw list
```My Intel card says:No AP mode there. I also have an Atheros USB that reports: What does yours report?

Mine only reports back IBSS, Managed, and Monitor. Is there any reason why it wouldn't support AP in Linux when it clearly works in Windows? I mean it just sounds like a driver issue doesn't it? Any way I can get around that?

---

### Post by chili555 on 2015-11-18
>  Is there any reason why it wouldn't support AP in Linux when it clearly works in Windows?Because Linux is not Windows and vice versa. A great many things work well in one but not the other.

You might try the latest backports driver. The process is here. Download this package to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/15/backports-20151115.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/15/backports-20151115.tar.gz) Right-click it and select 'Extract Here.' Now, back to the terminal:

```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-20151115
make defconfig-rtlwifi
make
sudo make install
```Reboot.

Also, you have compiled the driver for your currently running kernel only. When Update Manager installs a newer linux-image, after the requested reboot, recompile:

```
cd ~/Desktop/backports-20151115
make clean
make defconfig-rtlwifi
make
sudo make install 
```
Please retain the file and these instructions for that time.

Whether this newer driver supports AP mode with your hardware is unknown to me; I haven't the device.

---

### Post by altjx on 2015-11-18
> **chili555 said:**
> Because Linux is not Windows and vice versa. A great many things work well in one but not the other.

You might try the latest backports driver. The process is here. Download this package to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/15/backports-20151115.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/15/backports-20151115.tar.gz) Right-click it and select 'Extract Here.' Now, back to the terminal:

```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-20151115
make defconfig-rtlwifi
make
sudo make install
```Reboot.

Also, you have compiled the driver for your currently running kernel only. When Update Manager installs a newer linux-image, after the requested reboot, recompile:

```
cd ~/Desktop/backports-20151115
make clean
make defconfig-rtlwifi
make
sudo make install 
```
Please retain the file and these instructions for that time.

Whether this newer driver supports AP mode with your hardware is unknown to me; I haven't the device.

Thanks for your help thus far. I tried this yesterday and just tried it again just now just to be on the safe side, and it seems like the card shows up in lsusb, but I can't do an "ifconfig wlan0 up" because it doesn't detect it. 

Hmm, any other suggestions here? Thanks again.

---

### Post by chili555 on 2015-11-18
Please confirm that you rebooted.

May I see:```
lsusb
modinfo rtl8187 | grep -i version
sudo modprobe rtl8187
dmesg | grep rtl
```

---

### Post by altjx on 2015-11-18
> **chili555 said:**
> Please confirm that you rebooted.

May I see:```
lsusb
modinfo rtl8187 | grep -i version
sudo modprobe rtl8187
dmesg | grep rtl
```

Yep -- I've rebooted. Here is the output of those commands.

```
#lsusb
Bus 002 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 001 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
# modinfo rtl8187 | grep -i version
vermagic:       4.0.0-kali1-amd64 SMP mod_unload modversions 

```
```
# modprobe rtl8187
modprobe: ERROR: could not insert 'rtl8187': Invalid argument

```

```
# dmesg | grep rtl
[   71.553894] rtl8187: disagrees about version of symbol ieee80211_queue_stopped
[   71.553896] rtl8187: Unknown symbol ieee80211_queue_stopped (err -22)
[   71.553922] rtl8187: disagrees about version of symbol ieee80211_free_hw
[   71.553923] rtl8187: Unknown symbol ieee80211_free_hw (err -22)
[   71.553929] rtl8187: disagrees about version of symbol ieee80211_register_hw
[   71.553930] rtl8187: Unknown symbol ieee80211_register_hw (err -22)
[   71.553932] rtl8187: disagrees about version of symbol ieee80211_ctstoself_duration
[   71.553933] rtl8187: Unknown symbol ieee80211_ctstoself_duration (err -22)
[   71.553941] rtl8187: Unknown symbol __ieee80211_get_radio_led_name (err 0)
[   71.553942] rtl8187: disagrees about version of symbol ieee80211_generic_frame_duration
[   71.553943] rtl8187: Unknown symbol ieee80211_generic_frame_duration (err -22)
[   71.553951] rtl8187: Unknown symbol __ieee80211_get_tx_led_name (err 0)
[   71.553953] rtl8187: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   71.553953] rtl8187: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[   71.553964] rtl8187: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   71.553964] rtl8187: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   71.553979] rtl8187: Unknown symbol __ieee80211_get_rx_led_name (err 0)
[   71.553986] rtl8187: disagrees about version of symbol ieee80211_queue_delayed_work
[   71.553986] rtl8187: Unknown symbol ieee80211_queue_delayed_work (err -22)
[   71.553987] rtl8187: disagrees about version of symbol wiphy_rfkill_stop_polling
[   71.553988] rtl8187: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[   71.553998] rtl8187: disagrees about version of symbol ieee80211_alloc_hw_nm
[   71.553999] rtl8187: Unknown symbol ieee80211_alloc_hw_nm (err -22)
[   71.554011] rtl8187: disagrees about version of symbol wiphy_rfkill_start_polling
[   71.554012] rtl8187: Unknown symbol wiphy_rfkill_start_polling (err -22)
[   71.554015] rtl8187: disagrees about version of symbol ieee80211_unregister_hw
[   71.554015] rtl8187: Unknown symbol ieee80211_unregister_hw (err -22)
[   71.554016] rtl8187: disagrees about version of symbol ieee80211_beacon_get_tim
[   71.554017] rtl8187: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   71.554021] rtl8187: disagrees about version of symbol ieee80211_rx_irqsafe
[   71.554021] rtl8187: Unknown symbol ieee80211_rx_irqsafe (err -22)
[   71.554023] rtl8187: disagrees about version of symbol ieee80211_rts_duration
[   71.554024] rtl8187: Unknown symbol ieee80211_rts_duration (err -22)
[  380.637215] rtl8187: disagrees about version of symbol ieee80211_queue_stopped
[  380.637219] rtl8187: Unknown symbol ieee80211_queue_stopped (err -22)
[  380.637268] rtl8187: disagrees about version of symbol ieee80211_free_hw
[  380.637270] rtl8187: Unknown symbol ieee80211_free_hw (err -22)
[  380.637283] rtl8187: disagrees about version of symbol ieee80211_register_hw
[  380.637285] rtl8187: Unknown symbol ieee80211_register_hw (err -22)
[  380.637289] rtl8187: disagrees about version of symbol ieee80211_ctstoself_duration
[  380.637291] rtl8187: Unknown symbol ieee80211_ctstoself_duration (err -22)
[  380.637308] rtl8187: Unknown symbol __ieee80211_get_radio_led_name (err 0)
[  380.637310] rtl8187: disagrees about version of symbol ieee80211_generic_frame_duration
[  380.637310] rtl8187: Unknown symbol ieee80211_generic_frame_duration (err -22)
[  380.637323] rtl8187: Unknown symbol __ieee80211_get_tx_led_name (err 0)
[  380.637326] rtl8187: disagrees about version of symbol ieee80211_tx_status_irqsafe
[  380.637326] rtl8187: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[  380.637342] rtl8187: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  380.637342] rtl8187: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[  380.637363] rtl8187: Unknown symbol __ieee80211_get_rx_led_name (err 0)
[  380.637372] rtl8187: disagrees about version of symbol ieee80211_queue_delayed_work
[  380.637373] rtl8187: Unknown symbol ieee80211_queue_delayed_work (err -22)
[  380.637375] rtl8187: disagrees about version of symbol wiphy_rfkill_stop_polling
[  380.637376] rtl8187: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[  380.637391] rtl8187: disagrees about version of symbol ieee80211_alloc_hw_nm
[  380.637392] rtl8187: Unknown symbol ieee80211_alloc_hw_nm (err -22)
[  380.637410] rtl8187: disagrees about version of symbol wiphy_rfkill_start_polling
[  380.637411] rtl8187: Unknown symbol wiphy_rfkill_start_polling (err -22)
[  380.637415] rtl8187: disagrees about version of symbol ieee80211_unregister_hw
[  380.637416] rtl8187: Unknown symbol ieee80211_unregister_hw (err -22)
[  380.637417] rtl8187: disagrees about version of symbol ieee80211_beacon_get_tim
[  380.637418] rtl8187: Unknown symbol ieee80211_beacon_get_tim (err -22)
[  380.637425] rtl8187: disagrees about version of symbol ieee80211_rx_irqsafe
[  380.637425] rtl8187: Unknown symbol ieee80211_rx_irqsafe (err -22)
[  380.637429] rtl8187: disagrees about version of symbol ieee80211_rts_duration
[  380.637429] rtl8187: Unknown symbol ieee80211_rts_duration (err -22)
[  392.482777] rtl8187: disagrees about version of symbol ieee80211_queue_stopped
[  392.482781] rtl8187: Unknown symbol ieee80211_queue_stopped (err -22)
[  392.482831] rtl8187: disagrees about version of symbol ieee80211_free_hw
[  392.482832] rtl8187: Unknown symbol ieee80211_free_hw (err -22)
[  392.482841] rtl8187: disagrees about version of symbol ieee80211_register_hw
[  392.482842] rtl8187: Unknown symbol ieee80211_register_hw (err -22)
[  392.482846] rtl8187: disagrees about version of symbol ieee80211_ctstoself_duration
[  392.482846] rtl8187: Unknown symbol ieee80211_ctstoself_duration (err -22)
[  392.482864] rtl8187: Unknown symbol __ieee80211_get_radio_led_name (err 0)
[  392.482865] rtl8187: disagrees about version of symbol ieee80211_generic_frame_duration
[  392.482866] rtl8187: Unknown symbol ieee80211_generic_frame_duration (err -22)
[  392.482878] rtl8187: Unknown symbol __ieee80211_get_tx_led_name (err 0)
[  392.482882] rtl8187: disagrees about version of symbol ieee80211_tx_status_irqsafe
[  392.482882] rtl8187: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[  392.482897] rtl8187: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  392.482898] rtl8187: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[  392.482918] rtl8187: Unknown symbol __ieee80211_get_rx_led_name (err 0)
[  392.482927] rtl8187: disagrees about version of symbol ieee80211_queue_delayed_work
[  392.482928] rtl8187: Unknown symbol ieee80211_queue_delayed_work (err -22)
[  392.482930] rtl8187: disagrees about version of symbol wiphy_rfkill_stop_polling
[  392.482931] rtl8187: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[  392.482946] rtl8187: disagrees about version of symbol ieee80211_alloc_hw_nm
[  392.482947] rtl8187: Unknown symbol ieee80211_alloc_hw_nm (err -22)
[  392.482966] rtl8187: disagrees about version of symbol wiphy_rfkill_start_polling
[  392.482967] rtl8187: Unknown symbol wiphy_rfkill_start_polling (err -22)
[  392.482971] rtl8187: disagrees about version of symbol ieee80211_unregister_hw
[  392.482972] rtl8187: Unknown symbol ieee80211_unregister_hw (err -22)
[  392.482973] rtl8187: disagrees about version of symbol ieee80211_beacon_get_tim
[  392.482974] rtl8187: Unknown symbol ieee80211_beacon_get_tim (err -22)
[  392.482980] rtl8187: disagrees about version of symbol ieee80211_rx_irqsafe
[  392.482981] rtl8187: Unknown symbol ieee80211_rx_irqsafe (err -22)
[  392.482984] rtl8187: disagrees about version of symbol ieee80211_rts_duration
[  392.482985] rtl8187: Unknown symbol ieee80211_rts_duration (err -22)



```

---

### Post by chili555 on 2015-11-18
> vermagic:       4.0.0-kali1-amd64 SMP mod_unload modversionsOooops!!

Let's try again with, instead:```
cd ~/Desktop/backports-20151115
make clean
make defconfig-[COLOR="#FF0000"]wifi[/COLOR]
make
sudo make install
```It takes a while, so please be patient.

Reboot.

These instructions are for Ubuntu; we know nothing about Kali.

---

### Post by altjx on 2015-11-18
No problem. Just switched to my new Ubuntu instance and trying everything you mentioned again (including the reboot). Here are the results again after coming back up: 

```

alton@ubuntu:~/Desktop$ lsusb 
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 002: ID 0e0f:000b VMware, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alton@ubuntu:~/Desktop$ modinfo rtl8187 | grep -i version
srcversion:     564CAEF8CA0228FB869CCFA
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
alton@ubuntu:~/Desktop$ sudo modprobe rtl8187
[sudo] password for alton: 
modprobe: ERROR: could not insert 'rtl8187': Invalid argument
alton@ubuntu:~/Desktop$ dmesg | grep rtl
[    3.026141] rtl8187: disagrees about version of symbol ieee80211_queue_stopped
[    3.026144] rtl8187: Unknown symbol ieee80211_queue_stopped (err -22)
[    3.026155] rtl8187: disagrees about version of symbol ieee80211_free_hw
[    3.026155] rtl8187: Unknown symbol ieee80211_free_hw (err -22)
[    3.026158] rtl8187: disagrees about version of symbol ieee80211_register_hw
[    3.026159] rtl8187: Unknown symbol ieee80211_register_hw (err -22)
[    3.026162] rtl8187: disagrees about version of symbol ieee80211_ctstoself_duration
[    3.026162] rtl8187: Unknown symbol ieee80211_ctstoself_duration (err -22)
[    3.026178] rtl8187: Unknown symbol __ieee80211_get_radio_led_name (err 0)
[    3.026179] rtl8187: disagrees about version of symbol ieee80211_generic_frame_duration
[    3.026180] rtl8187: Unknown symbol ieee80211_generic_frame_duration (err -22)
[    3.026187] rtl8187: Unknown symbol __ieee80211_get_tx_led_name (err 0)
[    3.026189] rtl8187: disagrees about version of symbol ieee80211_tx_status_irqsafe
[    3.026190] rtl8187: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[    3.026195] rtl8187: disagrees about version of symbol wiphy_rfkill_set_hw_state
[    3.026196] rtl8187: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[    3.026202] rtl8187: Unknown symbol __ieee80211_get_rx_led_name (err 0)
[    3.026205] rtl8187: disagrees about version of symbol ieee80211_queue_delayed_work
[    3.026205] rtl8187: Unknown symbol ieee80211_queue_delayed_work (err -22)
[    3.026207] rtl8187: disagrees about version of symbol wiphy_rfkill_stop_polling
[    3.026208] rtl8187: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[    3.026219] rtl8187: disagrees about version of symbol ieee80211_alloc_hw_nm
[    3.026219] rtl8187: Unknown symbol ieee80211_alloc_hw_nm (err -22)
[    3.026226] rtl8187: disagrees about version of symbol wiphy_rfkill_start_polling
[    3.026227] rtl8187: Unknown symbol wiphy_rfkill_start_polling (err -22)
[    3.026230] rtl8187: disagrees about version of symbol ieee80211_unregister_hw
[    3.026231] rtl8187: Unknown symbol ieee80211_unregister_hw (err -22)
[    3.026232] rtl8187: disagrees about version of symbol ieee80211_beacon_get_tim
[    3.026232] rtl8187: Unknown symbol ieee80211_beacon_get_tim (err -22)
[    3.026238] rtl8187: disagrees about version of symbol ieee80211_rx_irqsafe
[    3.026238] rtl8187: Unknown symbol ieee80211_rx_irqsafe (err -22)
[    3.026241] rtl8187: disagrees about version of symbol ieee80211_rts_duration
[    3.026242] rtl8187: Unknown symbol ieee80211_rts_duration (err -22)
[  122.156513] rtl8187: disagrees about version of symbol ieee80211_queue_stopped
[  122.156517] rtl8187: Unknown symbol ieee80211_queue_stopped (err -22)
[  122.156531] rtl8187: disagrees about version of symbol ieee80211_free_hw
[  122.156532] rtl8187: Unknown symbol ieee80211_free_hw (err -22)
[  122.156537] rtl8187: disagrees about version of symbol ieee80211_register_hw
[  122.156538] rtl8187: Unknown symbol ieee80211_register_hw (err -22)
[  122.156543] rtl8187: disagrees about version of symbol ieee80211_ctstoself_duration
[  122.156544] rtl8187: Unknown symbol ieee80211_ctstoself_duration (err -22)
[  122.156566] rtl8187: Unknown symbol __ieee80211_get_radio_led_name (err 0)
[  122.156569] rtl8187: disagrees about version of symbol ieee80211_generic_frame_duration
[  122.156570] rtl8187: Unknown symbol ieee80211_generic_frame_duration (err -22)
[  122.156580] rtl8187: Unknown symbol __ieee80211_get_tx_led_name (err 0)
[  122.156585] rtl8187: disagrees about version of symbol ieee80211_tx_status_irqsafe
[  122.156586] rtl8187: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[  122.156593] rtl8187: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  122.156594] rtl8187: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[  122.156604] rtl8187: Unknown symbol __ieee80211_get_rx_led_name (err 0)
[  122.156609] rtl8187: disagrees about version of symbol ieee80211_queue_delayed_work
[  122.156609] rtl8187: Unknown symbol ieee80211_queue_delayed_work (err -22)
[  122.156613] rtl8187: disagrees about version of symbol wiphy_rfkill_stop_polling
[  122.156614] rtl8187: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[  122.156629] rtl8187: disagrees about version of symbol ieee80211_alloc_hw_nm
[  122.156630] rtl8187: Unknown symbol ieee80211_alloc_hw_nm (err -22)
[  122.156639] rtl8187: disagrees about version of symbol wiphy_rfkill_start_polling
[  122.156640] rtl8187: Unknown symbol wiphy_rfkill_start_polling (err -22)
[  122.156646] rtl8187: disagrees about version of symbol ieee80211_unregister_hw
[  122.156646] rtl8187: Unknown symbol ieee80211_unregister_hw (err -22)
[  122.156649] rtl8187: disagrees about version of symbol ieee80211_beacon_get_tim
[  122.156650] rtl8187: Unknown symbol ieee80211_beacon_get_tim (err -22)
[  122.156660] rtl8187: disagrees about version of symbol ieee80211_rx_irqsafe
[  122.156661] rtl8187: Unknown symbol ieee80211_rx_irqsafe (err -22)
[  122.156667] rtl8187: disagrees about version of symbol ieee80211_rts_duration
[  122.156668] rtl8187: Unknown symbol ieee80211_rts_duration (err -22)
alton@ubuntu:~/Desktop$ 

```

Wireless card not showing up in ifconfig, but showing up in lsusb. Followed your next commands to use defconfig-wifi and here are the results from lsusb and such again.

```

alton@ubuntu:~$ lsusb
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 002: ID 0e0f:000b VMware, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alton@ubuntu:~$ modinfo rtl8187 | grep -i version
version:        backported from Linux (next-20151115-0-gf6cbb19) using backports backports-20151115-0-g732e101
srcversion:     242D8BC57301DDA4D4E4F56
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
alton@ubuntu:~$ sudo modprobe rtl8187
[sudo] password for alton: 
alton@ubuntu:~$ dmesg | grep rtl
[    4.661441] ieee80211 phy0: hwaddr 00:c0:ca:82:31:30, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[    4.756934] rtl8187: Customer ID is 0xFF
[    4.761406] rtl8187: wireless switch is on
[    4.761683] usbcore: registered new interface driver rtl8187
[    4.764517] rtl8187 1-2:1.0 wlx00c0ca823130: renamed from wlan0
alton@ubuntu:~$ 

```

It looks like it still doesn't support AP mode in here, but I think it was really great troubleshooting and giving it a shot. I've went ahead and ordered another Alfa card and an TP-LINK card with at9k chipsets. Won't be able to complete my tasks as today's the last day, but I sincerely appreciate your help man!

---

