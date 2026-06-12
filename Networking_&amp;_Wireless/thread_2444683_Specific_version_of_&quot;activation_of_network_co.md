---
title: "Specific version of &quot;activation of network connection failed&quot; under Ubuntu 18.04"
date: 2020-06-02
forum: Networking &amp; Wireless
---

### Post by mingzian on 2020-06-02
I have found many earlier questions here that at first glance, describe the same problem I am facing: I get the error message `activation of network connection failed` when trying to connect to any Wi-Fi network.

However, in comparison to earlier questions I have found, my case is rather particular in a few ways:


[LIST]
[*]this problem appeared out of a sudden, after I rebooted my computer - that is, everything was working fine for more more than an year until minutes ago (also, I did **not** install any new software recently); 
[/LIST]


[LIST]
[*]I can still see all available Wi-Fi connections listed, but upon selection any, I get the above mentioned error message (I did try forgetting/re-entering connections); 
[/LIST]


[LIST]
[*]my Wi-Fi card (the one that has smoothly worked in the last year) is a PCI Express Wi-Fi adapter (so the discussion  [https://askubuntu.com/questions/1214881/ubuntu-18-04-activation-of-network-connection-failed](https://askubuntu.com/questions/1214881/ubuntu-18-04-activation-of-network-connection-failed) does not help). More specifically, it is a FebSmart Wireless Dual Band N600 (2.4GHz 300Mbps or 5GHz 300Mbps). For reference, a `lshw` gives me the following wi-fi network (i.e. omitting Ethernet cards): 
[/LIST]


 ```

 *-network
  description: Wireless interface
  product: AR93xx Wireless Network Adapter
  vendor: Qualcomm Atheros
  physical id: 0
  bus info: pci@0000:02:00.0
  logical name: wlp2s0
  version: 01
  serial: e0:ca:94:c5:b0:57
  width: 64 bits
  clock: 33MHz
  capabilities: bus_master cap_list rom ethernet physical wireless
  configuration: broadcast=yes driver=ath9k driverversion=5.3.0-53-generic firmware=N/A latency=0 link=no
  multicast=yes wireless=IEEE 802.11
  resources: irq:16 memory:dfe00000-dfe1ffff memory:dfe20000-dfe2ffff
```

Other relevant outputs:

 ```
description: Computer
  width: 64 bits
  capabilities: smp vsyscall32   *-core
  description: Motherboard
  physical id: 0
  *-memory
  description: System memory
  physical id: 0
  size: 251GiB

  *-cpu:0
  product: Intel(R) Xeon(R) CPU E5-2697 v2 @ 2.70GHz
  vendor: Intel Corp.
  physical id: 1
  bus info: cpu@0
  size: 1611MHz
  capacity: 3500MHz
  width: 64 bits
  capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge > mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq

  *-cpu:1
  product: Intel(R) Xeon(R) CPU E5-2697 v2 @ 2.70GHz
  vendor: Intel Corp.
  physical id: 2
  bus info: cpu@1
  size: 2130MHz
  capacity: 3500MHz
  width: 64 bits
  capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq

```

And a `iwconfig`gives me:

```
 wlp2s0    IEEE 802.11  ESSID:off/any  
  Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
  Retry short limit:7   RTS thr:off   Fragment thr:off
  Power Management:off
  enp6s0    no wireless extensions.
  
  enp7s0    no wireless extensions.
  
  lo        no wireless extensions.
  
  enp9s0    no wireless extensions.
  
  enp10s0   no wireless extensions.
```


 
[LIST]
[*]differently from many questions on this issue one can find online (e.g. [https://askubuntu.com/questions/1062390/activation-of-network-connection-failed-for-ethernet-connection](https://askubuntu.com/questions/1062390/activation-of-network-connection-failed-for-ethernet-connection)), I am **not** doing dual boot (that is, Ubuntu 18.04 64bits is the only OS I have installed) and I am also **not** connecting through a VPN (like in [https://askubuntu.com/questions/1087194/ubuntu-18-04-activation-of-network-connection-failed-ubuntu](https://askubuntu.com/questions/1087194/ubuntu-18-04-activation-of-network-connection-failed-ubuntu)). Also, my computer does **not** have a wrong system date (like in [https://askubuntu.com/questions/1058719/no-wifi-activation-of-network-connection-failed-ubuntu-16-04-18-04](https://askubuntu.com/questions/1058719/no-wifi-activation-of-network-connection-failed-ubuntu-16-04-18-04)). 
[/LIST]


[LIST]
[*]I tried manually re-compiling my `ath9k` driver like in [https://askubuntu.com/a/407250/1090328](https://askubuntu.com/a/407250/1090328), but it did not help. 
[/LIST]
 

[LIST]
[*]importantly, I have borrowed a USB TP-LINK Wi-Fi adapter (model TL-WN722N) from a friend and plugged into my machine - and with it, I can connect immediately to any Wi-Fi network; 
[/LIST]
 

So, my question to my fellow Ubuntu users: what should I do to try to restore access through my PCI Express card, as I was just having minutes ago?

---

### Post by wildmanne39 on 2020-06-02
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Hi, please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created.

---

### Post by mingzian on 2020-06-02
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Hi, please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created.

Apologies for the originally wrong tag and thanks both for correcting it and for pointing me to the mentioned script.
Here you have my pastebin link: [https://pastebin.com/ZKZ9zfVb](https://pastebin.com/ZKZ9zfVb)

Whoever looks at that log: be aware that, as described in the OP, I am using a borrowed USB TP-Link Wi-Fi adapter to connect to internet while I solve this issue. Hence, in the logs, you may see such a device as well. But the help I need is for making everything work, as it was working until a few hours ago, with the PCI Express Wi-Fi adapter you see in the logs.


Thanks in advance for any help you or other may be able to provide.

---

### Post by mingzian on 2020-06-04
Hi all, just to add so those who can potentially help me have this extra  information. A new symptom showed up: now with the borrowed USP adapter  described above, from time to time all Wi-Fi connections stop being  recognized and I have to manually restart the Network Manager.

---

### Post by mingzian on 2020-06-11
I am still have the same issues. Help is desperately needed, so I am bumping this up.

---

### Post by mingzian on 2020-07-02
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Hi, please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created.

Hi there. I wonder if it would be possible for me to delete this thread and re-post it in a more well-editted, more round-up fashion? I did not get any answers and I am still desperately needing any small bit of help anyone could hopefully give me. I really just do not know what to try and do any longer.

---

### Post by TheFu on 2020-07-02
I'm not a wifi guru any more and never was on linux, but there are some things that look odd to me in the output.  Not sure that anything below is actually helpful.

[LIST]
[*]There are 4 beautiful intel PRO/1000 wired ethernet ports on that machine and you aren't using them?  Blasphemy!  No way would i use wifi when those are available.
[*]The environment is full of wifi APs too many running on the same channels (11 and 36).  if you control those devices, change to channel 6 and any other 5.8Ghz channel for better connectivity.
[*]Why are both network-manager and wicd installed? That seems like a bad idea. Pick one.
[*]I’m not a fan of resolvconf or systemd-resolved.  i always remove both and manually setup the /etc/resolv.conf as desired.  This is about DNS only, not connectivity.  Don't think you should do anything about it.
[/LIST]

The Via VL812 USB hub needed a patch to work correctly with Linux. That patch can only be installed via Windows through a USB3 port.  Check that you have the patch and install it.  Hopefully, that hub has nothing to do with wifi adaptors.  Those need to be directly connected to the MB.

Disable any power management on wifi adaptors.

Some other considerations: Verify that the channel wide of the AP and the wifi cards are set to the same values.  APs can be tuned to widen or shrink the channel sizes to encourage use of specific types of wifi protocols.  Summer is when businesses and schools change their global settings to setup support for new AP standards and remove support for older standards.  For example, i've disabled 802.11a/b/g protocols on my APs.  i'm thinking about disabling "N" protocol now that wifi-6 and AC have taken over.  Newer protocols are faster and share channels better than N and earlier protocols.

Did the AP settings change?  There have been some recent Netgear patches to fix about 50% of the known security problems with specific models. Does the Netgear AP have anything to do with this?

if you go to a library or outside a fast food place with wifi, does the problem persist?

---

### Post by mingzian on 2020-07-03
> **TheFu said:**
> I'm not a wifi guru any more and never was on linux, but there are some things that look odd to me in the output.  Not sure that anything below is actually helpful.

[LIST]
[*]There are 4 beautiful intel PRO/1000 wired ethernet ports on that machine and you aren't using them?  Blasphemy!  No way would i use wifi when those are available. 
[*]The environment is full of wifi APs too many running on the same channels (11 and 36).  if you control those devices, change to channel 6 and any other 5.8Ghz channel for better connectivity. 
[*]Why are both network-manager and wicd installed? That seems like a bad idea. Pick one. 
[*]I’m not a fan of resolvconf or systemd-resolved.  i always remove both and manually setup the /etc/resolv.conf as desired.  This is about DNS only, not connectivity.  Don't think you should do anything about it. 
[/LIST]

The Via VL812 USB hub needed a patch to work correctly with Linux. That  patch can only be installed via Windows through a USB3 port.  Check that  you have the patch and install it.  Hopefully, that hub has nothing to  do with wifi adaptors.  Those need to be directly connected to the MB.

Disable any power management on wifi adaptors.

Some other considerations: Verify that the channel wide of the AP and  the wifi cards are set to the same values.  APs can be tuned to widen or  shrink the channel sizes to encourage use of specific types of wifi  protocols.  Summer is when businesses and schools change their global  settings to setup support for new AP standards and remove support for  older standards.  For example, i've disabled 802.11a/b/g protocols on my  APs.  i'm thinking about disabling "N" protocol now that wifi-6 and AC  have taken over.  Newer protocols are faster and share channels better  than N and earlier protocols.

Did the AP settings change?  There have been some recent Netgear patches  to fix about 50% of the known security problems with specific models.  Does the Netgear AP have anything to do with this?

if you go to a library or outside a fast food place with wifi, does the problem persist?

First of all, many thanks for replying to my cry for help!

I will address your points above in order:

- unfortunately, my desktop is in a position such I cannot use the wired connection. I wish I could!

- I do not control the many wifi APs.

- network-manager were and wicd both installed because I tried both to see if the problem persisted. It does: with either one, I can only connect to wi-fi using the borrowed TP-Link USB Wi-fi adapater, not my PCI Wi-fi card. After that, I uninstalled wicd.

- I will follow your advice on resolv.conf later on.

- the VL812 USB hub works fine and, again: I had Wi-fi working perfectly via my PCI wifi card together to the USB hub for more than an year. It suddenly stopped.

- I disabled power management on wifi adaptors - no luck.

- about the other suggestions: while I tried playing with channel wide, nothing worked. And I do have internet when I use the borrowed USB adaptor, so no need to make changes on the router side, or to try connections elsewhere.


This problem is really maddening me. Thanks for trying to help me out!

---

### Post by TheFu on 2020-07-04
> **mingzian said:**
>  
- I do not control the many wifi APs.
 
- about the other suggestions: while I tried playing with channel wide, nothing worked. And I do have internet when I use the borrowed USB adaptor, so no need to make changes on the router side, or to try connections elsewhere. 

The old and new wifi are not the same.  They have different features.  What are those differences?  Make a table, compare both. I bet the newer one supports 802.11ac.  That would be an important different and a change in the AP settings would easily prevent older wifi from working.

Did the driver used recently change?  Check the date/time on the driver file.  Check the APT update log file.

---

