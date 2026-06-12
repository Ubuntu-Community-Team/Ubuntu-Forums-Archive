---
title: "Intel AX200 rev 1a - won't find or connect to wifi"
date: 2024-08-26
forum: Networking &amp; Wireless
---

### Post by hertzquake on 2024-08-26
Hi all,

I am on a fresh install of Ubuntu 24.04, and I can't manage to connect to my wifi router

My "modem router" has a dual 2.4/5Ghz bandwidth. I am one floor above it and I managed to connect all of my other devices to it without any issue
This computer was just moved to a new house, it hadn't been used for while, but the wifi was working before moving it (on the previous OS installed, which was Pop OS 21)
Once set up, wifi didn't worked on the previous OS, and after trying a few things I decided to install the latest ubuntu, I upgraded everything, checked drivers etc. but it still doesn't work

The router won't appear most of the time, sometimes it does, but trying to connect to it results in a "Activation of network connection failed" error
I managed to connect to the wifi hotspot of a friend's phone (Android) but I can't manage to connect to the hotspot of mine (iOS), it finds it consistently though
The only thing working right now is using my phone's 4G via bluetooth, which gives a terrible bandwidth

I attached the result of the wireless-info script to the post

Thanks in advance for your help

Note: I had to manually redact the WPA key of my router, it was not masked by the script, should I report this?

---

### Post by jeremy31 on 2024-08-26
Can you test my version of the script and see if that issue with password still exists ```
wget -N -t 5 -T 10 https://github.com/jeremyb31/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
For the wifi try ```
sudo iwconfig wlp7s0 power off
```
Reboot

---

### Post by hertzquake on 2024-08-26
Your version of the script does seem to properly remove the password!

But for the wifi, it looks like it fixed the "activation network" error
Now, when the router decides to show up, I manage to connect but the connection doesn't really work: 
running a speedtest starts at 1mbps and keeps getting lower, down to 0.2, and fails while trying the upload
As a reference, the speedtest on my macbook pro gives 220mbps of download & 77mpbs of upload

---

### Post by jeremy31 on 2024-08-26
Try```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi 11n_disable=8
```
See if enabling aggressive tx helps

---

### Post by hertzquake on 2024-08-26
Not sure if it's random but I just enabled aggressive tx and got the "Activation of network connection failed" error, after waiting for a while (more than 2 minutes) for the router to finally appear in my list of networks

Edit: One of the 2 commands did fix the phone issue (I can now connect to my iPhone hotspot and I have a decent connection)

---

### Post by jeremy31 on 2024-08-26
The first part of the command unloaded the module that made the wifi work so it could be reloaded with the 11n_disable=8 option as a test
Since that command did help ```
echo "options iwlwifi 11n_disable=8"|sudo tee /etc/modprobe.d/iwlopt.conf
```
Post results for ```
ls -al /etc/netplan/
```

---

### Post by hertzquake on 2024-08-27
Understood thanks!

here the result for the ls command
```

total 32
drwxr-xr-x   2 root root  4096 Aug 26 16:29 .
drwxr-xr-x 143 root root 12288 Aug 26 16:33 ..
-rw-r--r--   1 root root    49 Aug 18 09:59 01-network-manager-all.yaml.dpkg-backup
-rw-------   1 root root   686 Aug 26 16:29 90-NM-4c09925c-06a8-4c75-b861-d2994dcce058.yaml
-rw-------   1 root root   754 Aug 26 10:52 90-NM-6b553f36-bb87-4e1c-b936-0074dcd2e147.yaml
-rw-------   1 root root   567 Aug 26 10:04 90-NM-c12fc02b-3aef-4059-b019-c597dc931f06.yaml

```

---

### Post by hertzquake on 2024-08-29
Hey, thanks a lot for your help
just wanting to know if you had any other ideas to fix the remaining issue?

---

### Post by hertzquake on 2024-08-29
If the router shows up in the network list I get
"Device 'wlp7s0' successfully activated with <UUID>"
if not I get
"Error: No network with SSID <SSID> found."

It seems that something helped on the "finding" of the router, but I still have a terrible bandwidth/no bandwidth at all, there's 0-1 "bar" and I have 0-1mbps, whereas all my other devices have a good signal/bandwidth
The wifi hotspot works perfectly now though

---

### Post by hertzquake on 2024-09-03
Here's what I got (the one in use is my phone, which is less than a meter away from my computer)
```

NAME   SSID      SSID-HEX          BSSID              MODE   CHAN  FREQ      RATE        BANDWIDTH  SIGNAL  BARS  SECURITY   WPA-FLAGS                 RSN-FLAGS                     DEVICE  ACTIVE  IN-USE  DBUS-PATH                                     
AP[1]  hertz  686572747A        "Some mac addr"    Infra  149   5745 MHz  270 Mbit/s  80 MHz     44      &#9602;&#9604;__  WPA2 WPA3  (none)                    pair_ccmp group_ccmp psk sae  wlp7s0  yes     *       /org/freedesktop/NetworkManager/AccessPoint/3 
AP[2]  SFR    5346525F45323846  "Some mac addr"    Infra  100   5500 MHz  540 Mbit/s  80 MHz     15      &#9602;___  WPA1 WPA2  pair_ccmp group_ccmp psk  pair_ccmp group_ccmp psk      wlp7s0  no              /org/freedesktop/NetworkManager/AccessPoint/5 

```

---

### Post by jeremy31 on 2024-09-03
If this is a desktop computer, see if the antennas are attached

---

### Post by hertzquake on 2024-09-03
It seems like the antennas were the issues! it now works perfectly, thanks a lot for your help!

---

