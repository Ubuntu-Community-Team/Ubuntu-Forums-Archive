---
title: "Edimax card problem"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by NerdyRukia on 2008-04-26
hey, it has been a while...
I haven't done anything in linux since I got it installed due to lack of internet connection.
I'm using (a probably old version) ubuntu
Today I decided to look up for some drivers for my wireless pen (edimax ew-7318ug) and couldn't find any useful info for it :(

I actually consulted the 'supported wireless cards list' thread and mine wasn't listed there. is there any chance that it is supported now? or am I barking at the wrong tree and I should just give up?

thanks in advance for any info you can give 
:)

---

### Post by geezerone on 2008-06-14
It is supported with inbuilt drivers for Hardy but not without its problems as I am finding after getting it to work.

---

### Post by chili555 on 2008-06-14
I believe this uses the rt73usb module, however there is an improved version here:```
sudo apt-get install linus-backports-modules-hardy-generic
```After doing this, please do:```
sudo modprobe rt73usb
```Does your device come to life?

---

### Post by geezerone on 2008-06-15
I did the above and installed module but when trying to modprobe I get error:

```
WARNING: Error inserting rt2x_mac80211 (/lib/modules/2.6.24-18-generic/updates/wireless/rt2x00/mac80211/rt2x_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```dmesg shows:

```
[ 2079.299493] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2079.299499] Pid: 9629, comm: modprobe Tainted: P        2.6.24-18-generic #1
[ 2079.299503]  [<c0215973>] kobject_add+0x113/0x1b0
[ 2079.299509]  [<c021542f>] kobject_get+0xf/0x20
[ 2079.299516]  [<c0215a41>] kset_register+0x21/0x50
[ 2079.299522]  [<c028347f>] class_register+0x9f/0x140
[ 2079.299532]  [<d0cc3146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2079.299539]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2079.299577]  [<c018e960>] __kmalloc+0x0/0x110
[ 2079.299591]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2079.299608]  =======================
[ 2079.327228] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2079.327473] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2079.327894] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2079.327989] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2079.328194] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2079.328628] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2079.328760] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2079.329083] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2079.329195] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2083.725039] wlan0: no IPv6 routers present
```

---

### Post by ibutho on 2008-06-15
What is the output of running
```
sudo lspci | grep -i net
```
and
```
sudo lshw -C network
```

---

### Post by chili555 on 2008-06-15
> **geezerone said:**
> I did the above and installed module but when trying to modprobe I get error:

```
WARNING: Error inserting rt2x_mac80211 (/lib/modules/2.6.24-18-generic/updates/wireless/rt2x00/mac80211/rt2x_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```dmesg shows:

```
[ 2079.299493] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2079.299499] Pid: 9629, comm: modprobe Tainted: P        2.6.24-18-generic #1
[ 2079.299503]  [<c0215973>] kobject_add+0x113/0x1b0
---snip---
```I wonder if we need to unload the old module and its dependencies first. The easiest way is to reboot.

---

### Post by geezerone on 2008-06-15
Rebooted and now can't connect to WPA2 network at all. Doesn't even show any green light in the nm applet. Keeps asking for password but no green light.

Carried out apt-get autoremove (removed 24-17 module) but still not working.

:(

WICD doesn't install either.

---

