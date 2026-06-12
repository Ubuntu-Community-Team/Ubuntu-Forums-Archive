---
title: "stuck on getting DWL-G122 to work"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by wrathkeg on 2007-05-21
Hi All,
I am trying to set up a wireless network using the DLink DSL-G624T router and DWL-G122 (Rev C1) USB dongle under Feisty.  I can connect to the net if I plug straight into the router, but I can't seem to get the wireless network to work.  I have been following these instructions which have been very helpful:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)

I can get as far as step 6, but no further.  I have edited the /etc/network/interfaces file for dynamic address assignment, and issued the 'sudo modprobe rt73' command, but 'iwconfig' comes back only with this (even after rebooting):

lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:""  Nickname:""
          Mode:Auto  Channel=8  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off

Does anyone have a clue what I might be missing here?
Thanks in advance,
WK

---

### Post by Kobalt on 2007-05-21
If you use Network-Manager you cannot edit the /etc/network/interfaces file, as NM needs it to be almost blank. Try to skip this part and configure your connection straight from NM or remove it with Synaptic (which I've ended up doing).

---

### Post by wrathkeg on 2007-05-21
Thanks for the suggestion. I tried uninstalling network manager, but that didn't seem to have an effect:  when I run

iwconfig

I still get 

rausb0    RT73 WLAN  ESSID:""  Nickname:""
          Mode:Auto  Frequency=1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off

Any other suggestions?
TIA
WK

---

### Post by Kobalt on 2007-05-22
Did you properly edited your /etc/network/interfaces file then ? Try this : ```
sudo /etc/init.d/networking restart
```

---

