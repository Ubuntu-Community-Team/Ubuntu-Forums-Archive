---
title: "Intel Pro/Wireless 3945 on a Pavilion dv6000 not working"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by NinjaMidget25 on 2008-04-21
I installed Ubuntu 8.04 rc on my Pavilion dv6000 laptop this weekend.   I cannot get my wireless card up and running.   I have searched the forum and found some similar problems, but no solutions.

The laptop has a wireless switch on the front and an led that is blue when the wireless is on, amber when it's not.  It is amber at the moment, no matter what position the switch is in.

I am fairly new to linux...meaning, I know next to nothing about troubleshooting problems, but I am comfortable with navigating around at the command line and things like that.   I am using this laptop as a testbed to teach myself linux so I can be 100% microsoft-free by the time XP is EOL'd.

Any and all help and pointers is much appreciated

---

### Post by am_dumb on 2008-04-21
i have same problem with my laptop. i have lenovo 3000 y410, with intel pro/wireless 3945A. 
am very-very new in linux and ubuntu...

thanks for reply...

---

### Post by chili555 on 2008-04-21
From a terminal, please let us see:```
lsmod | grep 3945
```If this produces no result, do:```
sudo modprobe iwl3945 disable=0
iwconfig
```Please post the results.

---

### Post by NinjaMidget25 on 2008-04-21
when I run lsmod | grep 3945, I get;

iwl3945                        89844    0
iwlwifi mac80211       219108    1   iwl3945

---

### Post by chili555 on 2008-04-21
And iwconfig?

---

### Post by NinjaMidget25 on 2008-04-21
oops..thought it was one or the other.   iwconfig is'

lo no wireless extensions
eth0 no wireless extensions
wmaster0 no wireless extensions
wlan0  IEEE 802.11g ESSID:""  Nickname:""
            Mode:Managed  Frequency:2.412 ghz Access Point: Not Associated
            Tx-Power=27dBm
            Retry min limit:7  RTS thr:off  Fragment thr=2346 B
            Power Management: off
            Link Quality:0    Signal Level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0  Missed beacon:0

---

### Post by chili555 on 2008-04-21
Looks good! This should be as easy as:```
sudo iwlist wlan0 scan
```

Learn your case-sensitive ESSID```
sudo iwconfig wlan0 essid <what_u_found>
sudo iwconfig wlan0 key <any_encryption_here?>
sudo dhclient wlan0
```Let us know.

---

### Post by NinjaMidget25 on 2008-04-21
Ok, when I run sudo iwlist wlan0 scan, I get this message;

Wlan0 Interface doesn't support scanning : Network is down

I still have an amber led for the wireless indicator on the laptop even though the switch is in the "on" position.

---

### Post by marcog on 2008-04-21
I have the same problem. Wireless hasn't been working for about 3-4 weeks now on hardy, but was working after the initial upgrade.

```
marco@marco:~$ lsmod | grep 3945
iwl3945               100596  0 
iwlwifi_mac80211      251876  1 iwl3945

marco@marco:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

marco@marco:~$ sudo iwlist wlan0_rename scan
wlan0_rename  Interface doesn't support scanning : Network is down
```

---

### Post by NinjaMidget25 on 2008-04-22
Still no wireless.   I'm wondering if I should not have installed 8.4.  Should I go to 7.10 instead?

---

