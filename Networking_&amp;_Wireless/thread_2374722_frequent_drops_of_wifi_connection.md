---
title: "frequent drops of wifi connection"
date: 2017-10-18
forum: Networking &amp; Wireless
---

### Post by zeitalex on 2017-10-18
Hi,
After DSL-Router Firmware Update (and factory reset) I got this problem with wifi.
To get connection again I have to click each time in the List of available wifi's on my Router.
It happens on Ubuntu notebook only, other wifi devices do not loose connection
The Router is FritzBox 7330

uname -a:
```

Linux lenovo-g70-70 4.4.0-97-generic #120-Ubuntu SMP Tue Sep 19 17:28:18 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

Does it have something to do with this:
egrep -i 'net|eth|wlan|firm|reason' /var/log/syslog :
```

Oct 18 12:10:10 gg11-Lenovo-G70-70 wpa_supplicant[1254]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=TKIP]
Oct 18 12:20:10 gg11-Lenovo-G70-70 wpa_supplicant[1254]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=TKIP]
Oct 18 12:30:10 gg11-Lenovo-G70-70 wpa_supplicant[1254]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=TKIP]
Oct 18 12:39:49 gg11-Lenovo-G70-70 systemd[1]: Stopping Raise network interfaces...
Oct 18 12:39:49 gg11-Lenovo-G70-70 systemd[1]: Stopped Raise network interfaces.
Oct 18 12:39:49 gg11-Lenovo-G70-70 systemd[1]: Starting Raise network interfaces...
Oct 18 12:39:49 gg11-Lenovo-G70-70 systemd[1]: Started Raise network interfaces.
Oct 18 12:40:10 gg11-Lenovo-G70-70 wpa_supplicant[1254]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=TKIP]
Oct 18 12:42:40 gg11-Lenovo-G70-70 NetworkManager[1066]: <warn>  [1508323360.3518] device (wlan0): disconnecting connection 'FRITZ!Box 7330' for new activation request.
Oct 18 12:42:40 gg11-Lenovo-G70-70 NetworkManager[1066]: <info>  [1508323360.3518] device (wlan0): state change: activated -> deactivating (reason 'new-activation') [100 110 60]
Oct 18 12:42:40 gg11-Lenovo-G70-70 NetworkManager[1066]: <info>  [1508323360.3520] manager: NetworkManager state is now DISCONNECTING
Oct 18 12:42:40 gg11-Lenovo-G70-70 NetworkManager[1066]: <info>  [1508323360.4337] device (wlan0): disconnecting for new activation request.

```

any help will be highly appreciated.

---

### Post by chili555 on 2017-10-19
I hate this:> wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=TKIP]And I hate it because: [https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)> TKIP uses the same underlying mechanism as WEP, and consequently is vulnerable to a number of similar attacks. The message integrity check, per-packet key hashing, broadcast key rotation, and a sequence counter discourage many attacks. The key mixing function also eliminates the WEP key recovery attacks.

Notwithstanding these changes, the weakness of some of these additions have allowed for new, although narrower, attacks.

I assume that the router, after the firmware upgrade, reset to the lowest common denominator defaults, including TKIP.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. I also don't like this much:> disconnecting connection 'FRITZ!Box 7330' for new activation request.I have seen quite a few cases where a space in the name of the SSID prevented reliable connections. I suggest that you change the name to FRITZ!Box7330 or FRITZ!Box_7330 or something without a space.

After making these changes, reboot the router. Then let us know if there is any improvement.

---

### Post by zeitalex on 2017-10-24
Thanks a lot for your answer.
In my router there are following options:
```
WPA (TKIP)
WPA2 (CCMP)
WPA+WPA2
```
WPA+WPA2 was chosen originally
When I select WPA2 (CCMP) (which is as far as I know based on AES) then wifi connection to Lubuntu Notebook disappears. Again all other devices do not loose connection.
How can I install WPA2 (CCMP) support on my notebook?

---

### Post by chili555 on 2017-10-24
Please select WPA2-CCMP in the router. Next, power-cycle the router.

Now reboot the Ubuntu computer and show us:```
lspci -nnk | grep 0280 -A3
```And also:```
lsusb
```

---

### Post by zeitalex on 2017-10-26
Now connection dissappears not so often. and I got
cat /var/log/syslog|grep CCMP
```

Oct 26 12:28:20 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]
Oct 26 12:28:23 gg11-Lenovo-G70-70 wpa_supplicant[1319]: message repeated 3 times: [ wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]]
Oct 26 12:28:28 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Key negotiation completed with 24:65:11:a2:51:82 [PTK=CCMP GTK=CCMP]
Oct 26 12:38:20 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]
Oct 26 12:48:20 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]
Oct 26 12:58:20 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]
Oct 26 13:08:20 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]
Oct 26 13:08:22 gg11-Lenovo-G70-70 wpa_supplicant[1319]: message repeated 2 times: [ wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]]
Oct 26 13:08:23 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Group rekeying completed with 24:65:11:a2:51:82 [GTK=CCMP]
Oct 26 13:08:28 gg11-Lenovo-G70-70 wpa_supplicant[1319]: wlan0: WPA: Key negotiation completed with 24:65:11:a2:51:82 [PTK=CCMP GTK=CCMP]

```

lspci -nnk | grep 0280 -A3:
```

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

lsusb:
```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 003 Device 004: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 003 Device 003: ID 0bc2:ab38 Seagate RSS LLC 
Bus 003 Device 002: ID 0bc2:ab45 Seagate RSS LLC 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 8087:07dc Intel Corp. 
Bus 002 Device 005: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 002 Device 002: ID 0bc2:ab44 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by chili555 on 2017-10-26
May we also see:```
dmesg | grep iwl
```Did you change the name of the SSID (router)?

---

### Post by zeitalex on 2017-10-26
dmesg | grep iwl:
[https://paste.ubuntu.com/25824434/](https://paste.ubuntu.com/25824434/) 

I just changed the SSID of my router to FRITZ_Box_7330

---

### Post by zeitalex on 2017-10-30
Connection drops occurs only when there is no active connection (e.g active download, or opened stream).

---

### Post by chili555 on 2017-10-31
> [54696.177060] iwlwifi 0000:02:00.0: Queue 2 stuck for 10000 ms.
[54696.177096] iwlwifi 0000:02:00.0: Current SW read_ptr 4 write_ptr 54
[54696.177143] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[54696.177173] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[54696.177200] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc011007b
[54696.177225] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[54696.177251] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x803000c7
[54696.177277] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[54696.177303] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[54696.177329] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[54696.177356] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x007090cf
[54696.177422] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [200,200]
[54696.177487] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[54696.177551] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [4,54]
[54696.177615] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[54696.177680] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[54696.177745] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]Yikes! You have an unhappy device there!

First, let's try a driver parameter to see if it helps:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is any improvement.

Next, we see this:> Loaded firmware version: 17.459231.0Let's check to be certain that the firmware file is not incomplete or corrupted:```
md5sum /lib/firmware/iwlwifi-3160-17.ucode
```We hope we see:```

$ md5sum /lib/firmware/iwlwifi-3160-17.ucode
[COLOR="#FF0000"]a96c63dcd6f3ee7e79939e2b453b7066 [/COLOR] /lib/firmware/iwlwifi-3160-17.ucode
```Finally, if there are still disconnects, you might check here: [https://unix.stackexchange.com/questions/356368/wifi-intel-7265-error-disconnecting-iwlwifi-fail-to-flush-all-tx-fifo-queue/372754](https://unix.stackexchange.com/questions/356368/wifi-intel-7265-error-disconnecting-iwlwifi-fail-to-flush-all-tx-fifo-queue/372754)

If your router is a mixed mode 2.4 gHz and 5 gHz model, you might experiment by giving the two segments different names such as  FRITZ_Box_7330_2.4 for the 2.4 gHz segment and FRITZ_Box_7330_5 for the 5 gHz segment. Try connecting to either. In this case, the router and your wireless are not channel hopping hoping for a better connection.

I use that method for my Intel wireless and it's perfect:```

wlp3s0    IEEE 802.11  ESSID:"[COLOR="#FF0000"]GBR5[/COLOR]"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:2B:B0:DC:45:xx
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:445   Missed beacon:0


```If you do this, in order to connect to the 5 gHz segment, we'll need to redo the driver parameter above.

---

### Post by zeitalex on 2017-11-04
> **chili555 said:**
> 
First, let's try a driver parameter to see if it helps:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

It seems to solve the problem. Thank you very much indeed!!!

---

