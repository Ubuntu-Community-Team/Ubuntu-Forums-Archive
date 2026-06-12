---
title: "wifi broken by xubuntu update on toshiba laptop with Intel 3160"
date: 2021-04-14
forum: Networking &amp; Wireless
---

### Post by c88anfi on 2021-04-14
[FONT=arial]Yesterday I ran a system update on my Toshiba satellite laptop, running xubuntu.  After reboot today, the wifi will no longer connect to internet, although the network and router are visible, and working fine with several other connected devices.

I connected with an ethernet cable directly, and ran:[/FONT]
sudo apt update
sudo apt dist-upgrade

[FONT=arial]after reboot, the issue persisted.

I ran the [wireless info script ]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info")[/FONT] [FONT=arial]which generated a large text file, although I can not see a link to how to share an online version of this (if there is a specific bit that would help, let me know!).

Wireless data from iwconfig as follows:[/FONT]

wlp7s0    IEEE 802.11  ESSID:"PLUSNET-K5KG"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: <MAC 'PLUSNET-K5KG' [AC1]>   
          Bit Rate=433.3 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### lspci #############################

07:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev cb)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8170]
    Kernel driver in use: iwlwifi

[FONT=arial]I can see that yesterday's update modified the wifi firmware and renamed it:[/FONT]

sudo dmesg -T |grep wifi
[Wed Apr 14 18:27:42 2021] iwlwifi 0000:07:00.0: loaded firmware version 17.3216344376.0 3160-17.ucode op_mode iwlmvm
[Wed Apr 14 18:27:42 2021] iwlwifi 0000:07:00.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[Wed Apr 14 18:27:43 2021] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[Wed Apr 14 18:27:43 2021] iwlwifi 0000:07:00.0: base HW address: xxxxxxxxxxxxxxxxxxxxxxx
[Wed Apr 14 18:27:43 2021] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0

[FONT=arial]Can anyone advise how to return the wifi to its previous settings, or otherwise get it working again?[/FONT]

---

### Post by chili555 on 2021-04-14
Please run and post:

```
ls -al /etc/resolv.conf
ping -c3 8.8.8.8
```Please post the result of the wireless script here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by c88anfi on 2021-04-15
Many thanks!   Here's the link to the pastebin: [https://paste.ubuntu.com/p/kCn5K45dbT/](https://paste.ubuntu.com/p/kCn5K45dbT/)

And here's the output of those commands:

> ~$ ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Apr  6 09:01 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=15.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=117 time=15.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=117 time=15.4 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 15.430/15.614/15.802/0.151 ms


---

### Post by c88anfi on 2021-04-15
Well this is weird... and now wifi is working again :/  Unsure what has happened here...  errors that fix themselves are troubling.  No actions taken other than described in this thread.

Ran the script again: [https://paste.ubuntu.com/p/mDdwZZbSR7/h](https://paste.ubuntu.com/p/mDdwZZbSR7/h)

at a glance, dmseg output seems radically different.

---

