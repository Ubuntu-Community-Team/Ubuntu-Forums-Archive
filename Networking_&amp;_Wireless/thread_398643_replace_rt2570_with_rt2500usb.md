---
title: "replace rt2570 with rt2500usb?"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by wgandhi on 2007-04-01
HI All

I have been using the Feisty live CD for a week. It worked great with my wireless USB adapter (Dlink DWL G 122 Version B1). I finally decided to move my system to Feisty this morning. The first thing on install, the kernel got updated from 2.6.20-12-generic to 2.6.20-13-generic. Magically, the driver load for the wireless adapter changed to rt2570 from the rt2500usb it uses on the liveCD. The new driver for wireless does not work at all. I cannot connect. I went back to previous version of the kernel after reboot and the network is back on. How do I force the latest kernel to use the rt2500usb adapter?

Here is the lsub :
Bus 005 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]

Here is the lsmod on the working kernel:
rt2500usb              30592  0 
rt2x00lib              11904  1 rt2500usb
snd_seq_dummy           4740  0 
serio_raw               7940  0 
mac80211              175364  3 rc80211_simple,rt2500usb,rt2x00lib
snd_seq_oss            32896  0 
cfg80211               22664  1 mac80211


-Wish

---

### Post by grsing on 2007-04-01
I'm having the exact same problem; anybody have a solution? Thanks.

---

### Post by Floppyjoe on 2007-04-01
> **wgandhi said:**
> HI All

I have been using the Feisty live CD for a week. It worked great with my wireless USB adapter (Dlink DWL G 122 Version B1). I finally decided to move my system to Feisty this morning. The first thing on install, the kernel got updated from 2.6.20-12-generic to 2.6.20-13-generic. Magically, the driver load for the wireless adapter changed to rt2570 from the rt2500usb it uses on the liveCD. The new driver for wireless does not work at all. I cannot connect. I went back to previous version of the kernel after reboot and the network is back on. How do I force the latest kernel to use the rt2500usb adapter?

Here is the lsub :
Bus 005 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]

Here is the lsmod on the working kernel:
rt2500usb              30592  0 
rt2x00lib              11904  1 rt2500usb
snd_seq_dummy           4740  0 
serio_raw               7940  0 
mac80211              175364  3 rc80211_simple,rt2500usb,rt2x00lib
snd_seq_oss            32896  0 
cfg80211               22664  1 mac80211


-Wish

Does it work to blacklist the first module?
```
sudo gedit /etc/modprobe.d/blacklist
```
and add this:
```
blacklist rt2570
```
then
```
sudo rmmod rt2570
```
then
```
sudo modprobe rt2500usb
```

---

### Post by grsing on 2007-04-02
That works for me, thanks!

---

### Post by wgandhi on 2007-04-05
This works for me too. I had to add the rt2500usb module to /etc/modules.This seems like a workaround for a setup that worked with no problems on the live CD. Any ideas on why this just does not work?

---

### Post by Floppyjoe on 2007-04-06
> **wgandhi said:**
> This works for me too. I had to add the rt2500usb module to /etc/modules.This seems like a workaround for a setup that worked with no problems on the live CD. Any ideas on why this just does not work?
I think "They" make the OS this way so nerds like me have something to keep themselves busy with. :-)

---

### Post by AleXit on 2007-04-06
Ralink wireless driver in Ubuntu Kernel are made by [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) project.
Rt2500usb is a part of the "rt2x00" project, witch is still in development.

RT2570 is a legacy driver witch genarally works much better at the moment. But the configuration is slightly different:
Download this archive [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) and follow the readme.
Mainly, I think you have to copy the firmware in the right directory...
These legacy driver support also native wpa/wpa2 encryption, without wpasupplicant ;)

ps: I currently use a rt73 legacy driver

---

