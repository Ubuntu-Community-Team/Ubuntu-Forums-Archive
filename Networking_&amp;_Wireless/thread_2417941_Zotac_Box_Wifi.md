---
title: "Zotac Box Wifi"
date: 2019-04-29
forum: Networking &amp; Wireless
---

### Post by mn_voyageur on 2019-04-29
I installed 18.04 on a Zotac Box.

Everything is working fine ... except the wifi.

The system sees all of the networks in the neighborhood.  The settings match my laptop.  (Ideapad 330) But the Zotac Box won't log on.

dmesg|grep wifi
[    5.318074] iwlwifi 0000:01:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
[    5.378896] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    5.412689] iwlwifi 0000:01:00.0: base HW address: a0:88:69:35:ff:0c

Thanks,
MarkN

---

### Post by howefield on 2019-04-29
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by chili555 on 2019-04-29
Let's see:```
dmesg | grep iwl
iwconfig
rfkill list all
```> 
The settings match my laptop.
Which settings where?

Thanks.

---

### Post by mn_voyageur on 2019-04-30
I loaded 18.04 on a new Ideapad 330 and the Zotac box.

Ideapad works fine.  Zotac Box will not connect either wired or wireless.

Below is the information you requested.

Thanks,
MarkN

dmesg | grep iwl
[    5.634014] iwlwifi 0000:01:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
[    5.699216] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    5.721310] iwlwifi 0000:01:00.0: base HW address: a0:88:69:35:ff:0c
[    5.866998] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'

iwconfig
eth1      no wireless extensions.

wlan0     IEEE 802.11  ESSID:"indelec_5"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: B0:39:56:6A:94:84   
          Bit Rate=433.3 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

lo        no wireless extensions.

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

---

### Post by chili555 on 2019-05-01
> 
wlan0 IEEE 802.11 ESSID:"indelec_5" 
Mode:Managed Frequency:5.2 GHz Access Point: B0:39:56:6A:94:84 
Bit Rate=433.3 Mb/s Tx-Power=22 dBm 
Retry short limit:7 RTS thr:off Fragment thr:off
Power Management:on
Link Quality=60/70 Signal level=-50 dBm 
I'm confused. You appear to be connected perfectly. What exactly is wrong?

---

### Post by mn_voyageur on 2019-05-01
The router sees the Zotac box on the Connected Devices GUI.

But I cannot access the internet via Firefox.   Also, the network icon has a "?" in the middle of it (wired) or just a "?" (Wireless).

---

### Post by mn_voyageur on 2019-05-01
This is very confusing ...

I am able to ping Google.  (ping 8.8.8.8)

---

### Post by chili555 on 2019-05-01
> 
I am able to ping Google. (ping 8.8.8.8)

That suggests that you are connected but DNS name resolution is not working correctly.

What does this tell us?

```
lsb_release -a
ls -al /etc/resolv.conf
```

---

### Post by mn_voyageur on 2019-05-01
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic

ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 29 Jan 15  2015 /etc/resolv.conf -> .../run/resolvconf/resolv.conf

---

### Post by chili555 on 2019-05-01
I believe this is the problem: [https://askubuntu.com/questions/1071252/no-internet-after-16-04-lts-18-04-01-upgrade/1071812#1071812](https://askubuntu.com/questions/1071252/no-internet-after-16-04-lts-18-04-01-upgrade/1071812#1071812)

---

### Post by mn_voyageur on 2019-05-01
This did not resolve the issue.

Tracepath appears to work.(tracepath 8.8.8.8)

New ls -al:
ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 32 May  1 11:10 /etc/resolv.conf -> /run/systemd/resolve/resolv.conf

---

### Post by mn_voyageur on 2019-05-01
Should I just blow away and re-install?

---

### Post by mn_voyageur on 2019-05-01
Tried sudo apt-get update

"Failed to fetch ...."

---

### Post by chili555 on 2019-05-01
Did you reboot after recreating the symbolic link? Please do.

---

### Post by mn_voyageur on 2019-05-01
Yes.  I rebooted each time.

---

### Post by mn_voyageur on 2019-05-01
Just rebooted again.

---

### Post by mn_voyageur on 2019-05-01
I worked, unsuccessfully, with a friend who programs super computers.  

He recommended re-installing.  Which I did.

Everything is working.  Thanks for the help.

MarkN

---

