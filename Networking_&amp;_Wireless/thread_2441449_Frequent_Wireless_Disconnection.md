---
title: "Frequent Wireless Disconnection"
date: 2020-04-23
forum: Networking &amp; Wireless
---

### Post by wyattwhiteeagle on 2020-04-23
My Wireless Network Adapter seems to detect a wireless access point that is about 100 yards away. The router in my house, the adapter frequently disconnects every 2 minutes and goes into the hidden networks every 30-60 minutes.

The access point at the 100 yard location is at someone else's home and it needs an authentication key to gain access. It seems to be a very stable and consistent detection.

I've talked with the owner of the access point that I have permission to access. They said they haven't made any changes to the router and that they are having no issues with frequent automatic disconnect.

Why can't my adapter detect the closest one with more consistent stability?

---

### Post by wyattwhiteeagle on 2020-04-24
Sorry for the long wait

```

wyatt@wyatt-Aspire-5733Z:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2020-04-24 01:55:04--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 140.82.113.4
Connecting to github.com (github.com)|140.82.113.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2020-04-24 01:55:04--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.204.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.204.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  17.04K  --.-KB/s    in 0.01s   

Last-modified header missing -- time-stamps turned off.
2020-04-24 01:55:04 (1.22 MB/s) - ‘wireless-info’ saved [17452/17452]


Results saved in "/home/wyatt/wireless-info.txt".

Results also archived in "/home/wyatt/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

wyatt@wyatt-Aspire-5733Z:~$ 


```

---

### Post by CelticWarrior on 2020-04-24
The results of the script is what matters. It's the file 
/home/wyatt/wireless-info.txt

---

### Post by wyattwhiteeagle on 2020-04-24
```

########## wireless info START ##########

Report from: 24 Apr 2020 01:55 EDT -0400

Booted last: 24 Apr 2020 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.3.0-46-generic #38~18.04.1-Ubuntu SMP Tue Mar 31 04:17:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] NetLink BCM57780 Gigabit Ethernet PCIe [1025:0601]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lite-On Communications Inc AR9285 Wireless Network Adapter (PCI-Express) [11ad:6631]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 001 Device 003: ID 0402:7675 ALi Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

acer_wmi               24576  0
sparse_keymap          16384  1 acer_wmi
wmi_bmof               16384  0
mxm_wmi                16384  0
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k_common,ath9k
ath                    36864  3 ath9k_common,ath9k,ath9k_hw
mac80211              847872  1 ath9k
cfg80211              704512  4 ath9k_common,ath9k,ath,mac80211
libarc4                16384  1 mac80211
video                  49152  2 acer_wmi,i915
wmi                    32768  3 acer_wmi,wmi_bmof,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback
```

---

### Post by wildmanne39 on 2020-04-24
The wireless info file that you posted is missing a lot of the information but the driver you are using usually requires the following parameter to work properly, please run the commands one line at a time:
> echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9kLet us know if that resolves the issue.

---

### Post by wyattwhiteeagle on 2020-04-24
> **CelticWarrior said:**
> The results of the script is what matters. It's the file 
/home/wyatt/wireless-info.txt

Wow

Took me a few times to figure out how to get the full results viewable.

I finally got it. Here's the link...

```

https://paste.ubuntu.com/p/tFRgRsxzdS/

```

---

### Post by wildmanne39 on 2020-04-24
First run the commands that I asked in my first post, then please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
That will turn of power management, then you have many networks all on channel 6 with your network, go into your router settings and set your channel to 1 not auto, you should see a lot of improvement, if my memory serves me correctly the wireless device you have does not have the strongest of signals even with all the changes but I have had the same one in an old laptop and it worked well anyway, make sure you do not have walls or anything between your laptop and the wireless router to degrade the signal if possible.

---

### Post by wyattwhiteeagle on 2020-04-25
[QUOTE=wildmanne39]...please run the commands one line at a time:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
Let us know if that resolves the issue.[/QUOTE]

I just did what you have instructed.

I'm not sure if this has anything to do with those commands but after rebooting I came back here using Firefox browser and got a message about a browser extension added. Unsure if I should click Disable or not.
[QUOTE=]**More secure, encrypted DNS lookups** Your privacy matters. Firefox now securely routes your DNS requests whenever possible to a service provided by Cloudflare to protect you while you browse.[/QUOTE]
We'll see how it goes.  :)

---

### Post by wildmanne39 on 2020-04-25
> More secure, encrypted DNS lookups Your privacy matters. Firefox now securely routes your DNS requests whenever possible to a service provided by Cloudflare to protect you while you browse. That message is from firefox, it is an upgrade they have recently implemented, it has nothing to do with the commands you ran.

---

### Post by wyattwhiteeagle on 2020-04-26
> **wildmanne39 said:**
> That message is from firefox, it is an upgrade they have recently implemented, it has nothing to do with the commands you ran.

Oh ok

BTW, some hours have past. Just watching the wi-fi notification pop-ups (so far, there hasn't been any) and the signal detection, running those commands seems to have done the trick.

Is there a way to check and make sure?

In Settings>Wi-fi>Visible Networks the List is frequently changing. Is that list ordered by signal percentage or is it trying to connect to multiple access points?

---

