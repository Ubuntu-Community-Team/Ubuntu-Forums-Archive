---
title: "Trouble loacting problem"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Stonehambey on 2008-05-05
Hi everyone :),

I just installed Ubuntu 8.04 (the herron one) yesterday. 

My wireless network manager can see a host of networks (incuding mine) and when I try to conect to mine it says it's encripted and asks for the network key - so far so good. 

However after I enter the key, the network manager says it's locating the network key and after a while asks me for the key again. This will keep happening until I stop trying to connect. 

I've read up a but on this and I realise I'm not the first person to be having troubles like this, and I didn't want to jump straight to the forums if I was asking a trite question :). I ran the following command to ascertain details about my wireless card. 

```
lspci -v | less
```

and I found the following 

```
Intel corporation PRO/Wireless 4965 AG or AGN Network connection (rev61)

Subsystem: Intel corporation unknown device 1101

Flag: bus master, fast devsel, latency 0, IRQ216
```

But I will hold my hands up and say that I don't know what this means :P

Given the description of the problem and the wireless card, can anyone point me in the right direction as to how to go about solving this problem? Is it a driver issue or something else?

Thanks for your time, 

Kind Regards,

Stonehambey

---

### Post by Ayuthia on 2008-05-05
If you have a wired connection, you can try installing linux-backports-modules-hardy-generic
```
sudo aptitude install linux-backports-modules-hardy-generic
```

---

### Post by Stonehambey on 2008-05-05
Thanks, what does that do exactly? 

Sorry if it's obvious :)

---

### Post by Ayuthia on 2008-05-05
It is going to install additional modules that are related to your wireless.  Here are the things that it will install:
```
/lib/firmware/2.6.24-16-generic/iwlwifi-4965-1-lbm.ucode
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/mac80211/rt2x_mac80211.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2x00lib.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2x00pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2x00usb.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt61pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt73usb.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/wireless/rt2x_cfg80211.ko
/usr/share/doc/linux-backports-modules-2.6.24-16-generic/changelog.Debian.gz
/usr/share/doc/linux-backports-modules-2.6.24-16-generic/copyright
```

Only the first few lines are going to be used by your wireless the others are for another wireless card.

---

### Post by Stonehambey on 2008-05-05
Ok I connected my laptop to my router via an ethernet cable and typed the command you said, this is what I got 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "linux-backports-modules-hardy-generic"
Couldn't find any package whose name or description matched "linux-backports-modules-hardy-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done 
```

It doesn't appear to have solved the problem, have I missed out a step somewhere?

Thanks for your time :)

---

### Post by Ayuthia on 2008-05-05
Have you run an update on Hardy yet?
```
sudo aptitude update
```

If so, you might check /etc/apt/sources.list and make sure that the repositories are not commented out (commented lines have a # in front).  The file should have over 10 different deb sites.

Worst case, you can go to [http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic) and download the package into your home directory and install it there.

---

