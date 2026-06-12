---
title: "iwl3945 wireless too sleepy to wake?"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by bodselecta on 2008-06-23
I've had ubuntu now for 2 weeks and managed to get it all working with a lot of development tools on it now, but the one problem i still have is driving me crazy.
I got a new dell xps laptop 2 weeks ago too which has an intel 3945ABG internal card and while i'm using it from ubuntu at the moment, it takes a hellavu long time for ubuntu to recognize the card (it's always fine in vista).
It's been taking longer the last few days, sometime 7 reboots, but i've noticed that sometimes it gets recognized quicker if i boot into vista then reboot to ubuntu (not all the time though).
is the iwl3945 driver having problems when the card's been idle? 

dmesg when the card is down 
```

[   35.007203] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   35.007206] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   35.007295] PCI: Enabling device 0000:0b:00.0 (0000 -> 0002)
[   35.007305] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.007325] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   35.007344] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   36.578640] iwl3945: MAC is in deep sleep!
[   36.578668] iwl3945: Unable to int nic

```

It's usually worse from a cold start but it has stopped when it's been working and in use. An ifdown ifup has brought it back, but again not always. Sometimes it reports that the wlan device can't be found so off i go again on a rebooting session.

I don't want to try ndiswrapper as when this card works it's fine. 
I'd done a wee bit of research before getting the laptop but i hadn't realised that wireless cards were such a problem (i should have looked a bit harder eh).

There seems to be loads of reported issues with this card and linux so is this a common problem or a lot of separate issues? i've got the latest kernel so the driver is built in.
It just seems a bit strange that if it is the driver, then thats also co-written with intel, so why is it such a problem?
Is the open source driver way behind the commercial driver?


And does mean i'll have to always keep vista on my new laptop just to get my card out of bed?     ](*,)   ](*,)    ](*,)

---

### Post by Zorael on 2008-06-24
You could try to install a newer version of the module. I use the script found over at [http://www.linuxwireless.org/en/users/Download](http://www.linuxwireless.org/en/users/Download) when my iwl3945 card won't play nice. You may want to make a backup of your /lib/modules/*(kernel version)* directory to be able to completely revert any changes it makes.

If you get 'unknown symbol' errors when trying to start the module (which the script automatically does for you if you call '**make load**'), try a reboot first. If it doesn't appear at all in iwconfig, download an older snapshot from that linuxwireless.org and try that one instead. If you rely on iwl3945 to get your internet access, download a whole bunch of them before you start tinkering. Older versions available at [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/).

If things go completely down the drain and you can't revert back to your first module version, just delete that /lib/modules/*(kernel version)* directory and replace it with your backup.

---

### Post by sdennie on 2008-06-24
There are a couple of things you could try to bring it back to life:

```

sudo iwconfig wlan0 power off

```

That should turn off power savings for the wireless card.  The other thing you could try would be:

```

sudo sh -c "echo 6 > /sys/bus/pci/drivers/iwl3945/0000\:0b\:00.0/power_level"

```

Which is another way to turn off the power savings for the iwl3945 driver.  (The value of 6 means turn off power savings).

---

### Post by bodselecta on 2008-06-24
zorael and vor, thanks to you both for the advice....
i'll give them a try, though probably vors first as that seems a bit less 'destructive'
i've been on vista all night as there's no novell citrix client for linux and hey presto i reboot back to ubuntu for the first time today and the cards recognized straight away. 

it seems to be pointing towards some kind of idling problem with the driver..
too late now, but i'll let you know how i get on and i'll probably ask you both a few more questions!
cheers

(ps, is it worth posting something on launchpad as i've not googled anything re power saving with the 3945?)

---

### Post by mlissner on 2009-09-23
I'm curious if this ever got resolved. I have the following card:
```
% lspci | grep -i networ
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

And I have a message in dmesg that says: ```
[205161.575023] iwlagn: MAC is in deep sleep!

```

Simultaneously, my network card comes and goes. My current solution is a script that I've mapped to a keyboard shortcut. The contents of which is:```
sudo rmmod iwlagn && sudo modprobe iwlagn
```

The script fixes things, but only until the next time. I just tried the ifconfig wlan0 power off command. I'm curious to see if it will work. It looks like a temporary measure. Is there a way (if it works), to apply it permanently?

---

### Post by mlissner on 2009-09-23
OK, the above didn't work. My wireless just died again. Here's the relevant dmesg:```
[215092.648541] pci 0000:00:02.0: power state changed by ACPI to D0
[215092.648669] pci 0000:00:02.0: power state changed by ACPI to D0
[215092.648677] pci 0000:00:02.0: setting latency timer to 64
[215092.650299] PM: resume devices took 3.148 seconds
[215092.650321] PM: Finishing wakeup.
[215092.650323] Restarting tasks ... <6>synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[215092.728682] done.
[215094.465333] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[215094.521148] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[215094.521495] ADDRCONF(NETDEV_UP): eth0: link is not ready
[215094.740250] Registered led device: iwl-phy17:radio
[215094.740280] Registered led device: iwl-phy17:assoc
[215094.740295] Registered led device: iwl-phy17:RX
[215094.740310] Registered led device: iwl-phy17:TX
[215094.786495] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[215094.842035] wlan0: direct probe to AP 00:1a:e3:7b:ee:20 try 1
[215094.855193] wlan0: direct probe to AP 00:1a:e3:7b:ee:20 try 1
[215095.056283] wlan0: direct probe to AP 00:1a:e3:7b:ee:20 try 2
[215095.329591] wlan0: direct probe to AP 00:1a:e3:7b:ee:20 try 3
[215095.528235] wlan0: direct probe to AP 00:1a:e3:7b:ee:20 timed out
[215095.568099] usb 3-1: new full speed USB device using uhci_hcd and address 32
[215095.745549] usb 3-1: configuration #1 chosen from 1 choice
[215096.977300] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[215103.422310] wlan0: direct probe to AP 00:22:90:c5:74:10 try 1
[215105.996857] wlan0: authenticate with AP 00:23:04:03:ad:40
[215106.001989] wlan0: authenticate with AP 00:23:04:03:ad:40
[215106.002727] wlan0: authenticated
[215106.002734] wlan0: associate with AP 00:23:04:03:ad:40
[215106.003814] wlan0: RX AssocResp from 00:23:04:03:ad:40 (capab=0x1 status=0 aid=244)
[215106.003819] wlan0: associated
[215106.022844] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[215167.063048] wlan0 direct probe responded
[215167.063059] wlan0: authenticate with AP 00:23:04:03:ad:40
[215167.096364] wlan0: authenticate with AP 00:22:90:c5:74:10
[215167.103789] wlan0: authenticate with AP 00:22:90:c5:74:10
[215167.105361] wlan0: authenticated
[215167.105370] wlan0: associate with AP 00:22:90:c5:74:10
[215167.107995] wlan0: RX ReassocResp from 00:22:90:c5:74:10 (capab=0x421 status=0 aid=210)
[215167.108037] wlan0: associated
[216358.537010] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[216358.573799] iwlagn: MAC is in deep sleep!
[216358.807290] Registered led device: iwl-phy17:radio
[216358.807333] Registered led device: iwl-phy17:assoc
[216358.807370] Registered led device: iwl-phy17:RX
[216358.807407] Registered led device: iwl-phy17:TX
[216380.205182] iwlagn 0000:03:00.0: PCI INT A disabled
[216380.349769] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[216380.349773] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[216380.349883] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[216380.349925] iwlagn 0000:03:00.0: setting latency timer to 64
[216380.350248] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[216380.390593] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[216380.390710] iwlagn 0000:03:00.0: irq 2296 for MSI/MSI-X
[216380.392207] phy18: Selected rate control algorithm 'iwl-agn-rs'
[216380.393248] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[216380.622521] Registered led device: iwl-phy18:radio
[216380.622563] Registered led device: iwl-phy18:assoc
[216380.622601] Registered led device: iwl-phy18:RX
[216380.622639] Registered led device: iwl-phy18:TX
[216380.663719] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[216380.846983] iwlagn: MAC is in deep sleep!
[216385.763048] Registered led device: iwl-phy18:radio
[216385.763112] Registered led device: iwl-phy18:assoc
[216385.773742] Registered led device: iwl-phy18:RX
[216385.773792] Registered led device: iwl-phy18:TX
[216385.895277] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[216385.922221] wlan0: authenticate with AP 00:22:90:c5:74:10
[216385.972175] wlan0: authenticate with AP 00:22:90:c5:74:10
[216386.173033] wlan0: authenticate with AP 00:22:90:c5:74:10
[216386.174484] wlan0: authenticated
[216386.174489] wlan0: associate with AP 00:22:90:c5:74:10
[216386.177495] wlan0: RX AssocResp from 00:22:90:c5:74:10 (capab=0x421 status=0 aid=9)
[216386.177499] wlan0: associated
[216386.196314] phy18: failed to restore operational channel after scan
[216386.196489] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[216386.197395] wlan0: disassociating by local choice (reason=3)
[216386.198482] wlan0: deauthenticated
[216386.207161] phy18: failed to restore operational channel after scan
[216386.209487] phy18: failed to restore operational channel after scan
[216386.240523] wlan0: authenticate with AP 00:02:2d:0c:f1:39
[216386.262650] wlan0: authenticate with AP 00:02:2d:0c:f1:39
[216386.267273] wlan0: authenticate with AP 00:02:2d:0c:f1:39
[216386.267354] iwlagn: index 0 not used in uCode key table.
[216386.282727] wlan0: authenticated
[216386.282733] wlan0: associate with AP 00:02:2d:0c:f1:39
[216386.284746] wlan0: RX AssocResp from 00:02:2d:0c:f1:39 (capab=0x11 status=0 aid=29)
[216386.284748] wlan0: associated
[216396.412101] wlan0: no IPv6 routers present
[218136.373399] iwlagn: index 0 not used in uCode key table.
[218136.390656] wlan0: authenticate with AP 00:02:2d:02:12:57
[218136.395742] wlan0: authenticate with AP 00:02:2d:02:12:57
[218136.402331] wlan0: authenticated
[218136.402339] wlan0: associate with AP 00:02:2d:02:12:57
[218136.404394] wlan0: RX ReassocResp from 00:02:2d:02:12:57 (capab=0x11 status=0 aid=14)
[218136.404400] wlan0: associated
[218376.718037] iwlagn: index 0 not used in uCode key table.
[218376.745538] iwlagn: index 0 not used in uCode key table.
[218376.752224] wlan0: authenticate with AP 00:02:2d:2e:50:6e
[218376.760421] wlan0: authenticate with AP 00:02:2d:2e:50:6e
[218376.960707] wlan0: authenticate with AP 00:02:2d:2e:50:6e
[218377.161144] wlan0: authenticate with AP 00:02:2d:2e:50:6e
[218377.360151] wlan0: authentication with AP 00:02:2d:2e:50:6e timed out
[218386.774322] iwlagn: index 0 not used in uCode key table.
[218386.815802] wlan0: authenticate with AP 00:02:2d:02:12:57
[218386.824594] wlan0: authenticated
[218386.824603] wlan0: associate with AP 00:02:2d:02:12:57
[218386.831933] wlan0: RX ReassocResp from 00:02:2d:02:12:57 (capab=0x11 status=0 aid=14)
[218386.831939] wlan0: associated
[218495.539275] iwlagn: index 0 not used in uCode key table.
[218495.556108] wlan0: authenticate with AP 00:02:2d:0c:f1:39
[218495.562872] wlan0: authenticate with AP 00:02:2d:0c:f1:39
[218495.568332] wlan0: authenticated
[218495.568340] wlan0: associate with AP 00:02:2d:0c:f1:39
[218495.570672] wlan0: RX ReassocResp from 00:02:2d:0c:f1:39 (capab=0x11 status=0 aid=29)
[218495.570678] wlan0: associated
[218798.007252] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[218798.044386] iwlagn: MAC is in deep sleep!
[218798.301117] Registered led device: iwl-phy18:radio
[218798.301170] Registered led device: iwl-phy18:assoc
[218798.301208] Registered led device: iwl-phy18:RX
[218798.301247] Registered led device: iwl-phy18:TX

```

---

### Post by CJay554 on 2010-02-11
Aye, i've just run into this exact problem with the 4965 card, i've heard its a kernel problem and it works with kernels like 2.6.25 and less, not sure how to resolve this...

---

### Post by donboling on 2010-04-29
I too am having this issue with 10.04 (this was a fresh install of the RC last week, so I don't know if this laptop would have had the problem on 9.10) ...

I tried to turn off power management using ..

sudo iwconfig wlan0 power off

but it says "Operation not supported"

I have all the symptoms listed in this thread. I do notice that when I have the network connected, 

'iwlist wlan0 power'

returns

'wlan0   Current mode;off' (adjusted post to work around damned smilies)

Which it sounds like power management is already 'off' from reading the 'man iwlist' page...

any ideas?
Thanks
Don

---

### Post by jmjohn on 2010-06-27
I had this a similar problem with iwl3945 not connecting to wireless after resume from suspend, and fixed it with:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by letoasty on 2012-07-10
I have a Lenovo Thinkpad T510 using the iwlagn driver and have had the exact same symptoms: frequent dropping of WLAN where only rebooting would fix it and the 'MAC is in deep sleep!' error.

It was quickly solved by disabling the N features of the driver:
```
sudo echo 'options iwlagn 11n_disable50=1 11n_disable=1' > /etc/modprobe.d/iwlagn.conf
```And then resetting the iwlagn driver (if this doesn't work for you, just reboot one last time):
```
sudo rmmod iwlagn && sudo modprobe iwlagn 
```

---

### Post by wildmanne39 on 2012-07-10
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

