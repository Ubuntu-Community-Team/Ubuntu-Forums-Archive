---
title: "X201 - intel 6200 wifi, potentially interesting problem"
date: 2014-06-16
forum: Networking &amp; Wireless
---

### Post by ttr398 on 2014-06-16
Hi all, 

Searching around I've seen a few threads on the 6200 causing problems, but here's a hopefully original spin on the topic. 

Just got a hold of an X201 and installed Ubuntu. 

I get a variety of symptoms,

on AC power, from start up the wifi will quite often work. For, usually, less than half an hour. Connection drops and it wont pick back up again, quite often no networks will be listed. When the wifi is about to go the whole system has a tendancy to lock up. Other times I'll have no working wifi on start up, sometimes showing networks othertimes not. 

On battery, the above manifests, but it seems to feature more locking up than on AC, and I've had two kernel panics. 

All symptoms disappear if I give up trying to connect and plug in the ethernet cable.

Caveat: relatively inexperienced with linux. 

I ran dmesg | grep iwl a couple of times around the time of failure, or attempted connect. I see this quite often: 

```

dmesg | grep iwl: 


[  484.528169] iwlwifi 0000:02:00.0: iwl_trans_wait_tx_queue_empty bad state = 0
[  484.528915] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  484.595575] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[  490.243989] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  490.243998] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  490.244007] iwlwifi 0000:02:00.0: Failed to start RT ucode: -110
[  491.958409] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[  493.689328] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[  495.453417] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[  497.184326] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[  498.889323] iwlwifi 0000:02:00.0: Unable to initialize device.
[  498.889748] iwlwifi 0000:02:00.0: Request scan called when driver not ready.
[  602.531475] iwlwifi 0000:02:00.0: Request scan called when driver not ready.
[  602.553472] iwlwifi 0000:02:00.0: Request scan called when driver not ready.


```

At the moment, I've got 50 odd lines of 'Request scan called when driver not ready', and no networks showing up. 

```

sudo lshw -C network:
 *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 18:3d:a2:56:29:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:f2400000-f2401fff




```

Any pointers on where to go next? 

Cheers!

---

### Post by ttr398 on 2014-06-18
Bump - assistance required!

I've disabled BT_coex and 11n in iwlwifi.conf. 

In both cases I restarted and had stable WiFi for 6+hrs thereafter, but eventually it returned to an unreliable state. 

Rfkill list is false for hard and soft.

Out of ideas! Would like to rule out software before I drop cash on a new card. Are Intel 5300 chips better with Ubuntu generally? I can get one to try..

---

### Post by jeremy31 on 2014-06-18
See if installing linux-firmware helps

---

### Post by ttr398 on 2014-06-18
```

linux-firmware is already the newest version.
linux-firmware set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by ttr398 on 2014-06-18
I tried tweaking router settings per posts from Chilli555 on the topic. I have turned off mixed mode WPA, disabled WPS &  WDS and set the router to 20Hz frequency band. So far so good, I will mark as solved when I'm a bit more confident in the fix. 

I've noticed that setting iw reg doesn't stick - a get call immediately after returns 00, is this normal? Is this something I should do regardless of whether or not tweaking router settings has fixed the issue? 

Pre-emptive thank you for any help you guys might offer!

---

### Post by jeremy31 on 2014-06-18
> **ttr398 said:**
> I tried tweaking router settings per posts from Chilli555 on the topic. I have turned off mixed mode WPA, disabled WPS &  WDS and set the router to 20Hz frequency band. So far so good, I will mark as solved when I'm a bit more confident in the fix. 

I've noticed that setting iw reg doesn't stick - a get call immediately after returns 00, is this normal? Is this something I should do regardless of whether or not tweaking router settings has fixed the issue? 

Pre-emptive thank you for any help you guys might offer!

So you have used ```
iw reg set
``` with your country/region code?  It might change if the frequencies from the router don't match, hacked router or router made for a different country.  If you get it fixed, thank chilli555

---

### Post by ttr398 on 2014-06-19
Aye, iw reg set UK, then iw reg get returns 00. 

Sadly the fix didn't work. Few hours on from my post wifi dropped, rebooted a few times with no luck - each time lspci failed to show the wifi card. 

At this point should I be assuming hardware?

---

### Post by jeremy31 on 2014-06-19
Try ```
gksudo gedit /etc/default/crda
``` and change it there and save

---

### Post by ttr398 on 2014-06-19
Will give it a punt, but I assume it will have no effect given that lspci cannot even see the card on last count. Away from the laptop at the moment, but what should I infer from this condition?

---

### Post by jeremy31 on 2014-06-19
I would power down, remove the card and put it back in and try it again. Then look in bios for any networking settings and see what happens.  The card might have faulted

---

