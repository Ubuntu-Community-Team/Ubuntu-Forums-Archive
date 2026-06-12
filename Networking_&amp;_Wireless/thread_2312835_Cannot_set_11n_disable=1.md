---
title: "Cannot set 11n_disable=1"
date: 2016-02-07
forum: Networking &amp; Wireless
---

### Post by Eric_Stroczynski on 2016-02-07
A few weeks after installing Ubuntu 14.04 on my ASUS UX305L laptop with an Intel 7265 wireless card (originally ran Windows 10 with no access problems) I began noticing that:

 1) the signal drops immediately after connecting to my home network, then (might) regain connection ~1 hour later and works fine
2) while connected to any network, the signal strength is significantly lower than previously experienced while running Windows 10 in the same locations (house, campus networks)

I've read in multiple posts that there's a bug in the driver for the 802.11n wifi mode, and people who've disabled it restored wifi access. So I tried to do the same, but despite my efforts I could not do so. Here's what I tried:

```
sudo ifconfig wlan0 down
```

Then I disabled wifi from my desktop manually for good measure

Next I tried reloading iwlwifi and disabling 11n

```
sudo sh -c 'modprobe -r iwlwifi && modprobe iwlwifi 11n_disable=1'
```

I still received this error afterwards:

```
modprobe: FATAL: Module iwlwifi is in use.
```

Any ideas on how to disable iwlwifi, or if this is my problem in the first place? Thanks!

---

### Post by jeremy31 on 2016-02-07
Just try
```
sudo modprobe -r iwlwifi
```

Wait a little while to give the module time to unload then
```
sudo modprobe iwlwifi 11n_disable=?
```

11n_disable=8 might gain more than 11n_disable=1

---

### Post by Eric_Stroczynski on 2016-02-07
I already tried that and I still the the "FATAL: iwlwifi is in use" response

---

### Post by Eric_Stroczynski on 2016-02-07
I tried that and get the FATAL error

---

### Post by jeremy31 on 2016-02-07
```
cat /etc/modprobe.d/iwlwifi.conf
```

---

### Post by Eric_Stroczynski on 2016-02-07
I tried doing this before with the iwlwifi.conf file so this is all that's in there:

```
options iwlwifi 11n_disable=1
```

---

### Post by jeremy31 on 2016-02-07
After a reboot, the option should be set if it is in that file however it should also contain ```
# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

If that had been there, you would not see FATAL: iwlwifi is in use

I will ask you to run the wireless info script from [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the results

---

### Post by Eric_Stroczynski on 2016-02-07
Script output: [http://pastebin.com/rWZ3Rm28](http://pastebin.com/rWZ3Rm28)

---

### Post by jeremy31 on 2016-02-07
I would ```
echo "options 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo iwconfig wlan0 power off
```

Set the router for a different 5Ghz channel

Reboot

---

