---
title: "[SOLVED] Strange problem..."
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by finalrequiem on 2008-09-23
I upgraded to 8.04 from Studio (7.10, I think) without a hitch, wired and wireless connections worked without any trouble.  I just went with a fresh install of 8.04 because I wanted to completely wipe my HDD and start fresh.  Now my wireless works but there is no wired connection.  Not even showing one in Network Manager...  Not sure where to go from here...

   T61p, by the way...

---

### Post by Crafty Kisses on 2008-09-23
I'd like to see the results of this command:
```
ifconfig
```
Does anything show up when you plug an Ethernet cord in the Ethernet port?

---

### Post by finalrequiem on 2008-09-23
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123670 (120.7 KB)  TX bytes:123670 (120.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:66:a5:6d  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe66:a56d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:244314996 (232.9 MB)  TX bytes:8471622 (8.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-66-A5-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


My wife is using the ethernet with her laptop at the moment so it isn't plugged into mine right now. But nothing appeared and no messages pop up when I plug it in...  Exact opposite problem that I had when I first installed Studio (7.10)...

---

### Post by willca on 2008-09-24
that output of ifconfig you posted did not show any eth0 in there.

Try this and see if it even detects the hardware

lspci | grep Ethernet

You might also want to check the bootup log for any messages about it. So do this, right after booting up 

dmesg | more

Scan for the error messages.

---

### Post by finalrequiem on 2008-09-24
-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:66:a5:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

---

### Post by finalrequiem on 2008-09-25
Any ideas from looking at the results from that command?

---

### Post by willca on 2008-09-26
At least it does show that you wired nic is recognized or the chipset thereof.

So reboot and run this as soon as its up in a terminal

sudo dmesg | egrep "82566DC|Intel"

Also can you post /etc/network/interfaces

---

### Post by finalrequiem on 2008-09-27
[   18.500610] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[   18.589007] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[   21.545862] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   21.545864] Copyright (c) 1999-2006 Intel Corporation.
[   24.455637] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.0/input/input2
[   24.520093] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.1-1
[   28.614743] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   28.614746] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   28.614908] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   28.697613] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)




Got "permission denied" when I tried to /etc/network/interfaces

---

### Post by finalrequiem on 2008-09-27
auto lo
iface lo inet loopback


there

---

### Post by finalrequiem on 2008-09-27
that was the output of /etc/network/interfaces

---

### Post by finalrequiem on 2008-09-28
anyone have any ideas?  please?  desperation is setting in...

---

### Post by charonred on 2008-09-28
ditto with desperation;

I have similar problem with networking on several PCs
[my post here]("http://ubuntuforums.org/showthread.php?t=931994")

---

### Post by lavinog on 2008-09-28
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555")
I think it was disabled for safety reasons:

> In some circumstances it appears possible for the 2.6.27-rc kernels to corrupt the NVRAM used by some Intel network parts to store data such as MAC addresses.
This is limited to the new e1000e driver, and reports have only appeared from users of "82566 and 82567 based LAN parts (ich8 and ich9)" (to quote Intel). The reports seem to be isolated to laptops, but it is not clear if this is because desktop/server parts are not vulnerable, or if use cases simply increase the chances of laptop users being hit.

Once this corruption has occurred, recovery may be possible via a BIOS update, but may well require replacement of the hardware. Use of Intel's IABUTIL.EXE is strongly discouraged, as it will worsen the problem to the point where the network part will no longer appear on the PCI bus.

(this is a new description, the original one was based on too much guesswork. Below are the URLs originally referenced)
(the driver i blacklisted in Ubuntu for 2.6.27-rc in the latest releases, so if your network is not working, it doesn't have to be damaged, but just disabled in order to prevent any accidents until this bug is solved, don't wary!)

What kernel are you using?
```
uname -a
```

---

### Post by finalrequiem on 2008-09-28
Linux joey-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

For some reason I thought that problem was exclusive to the Intrepid alpha releases...

---

### Post by lavinog on 2008-09-28
> **finalrequiem said:**
> Linux joey-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

For some reason I thought that problem was exclusive to the Intrepid alpha releases...

I thought so too, but it is very coincidental.

---

### Post by finalrequiem on 2008-09-28
is there any command to run that would show it as disabled?

---

### Post by lavinog on 2008-09-28
Does it work with the live cd?
(Make sure the hardware still works, since the bug claims to cause damage to the hardware.)
If it works with the live cd, it should be safe to assume that the driver was dissabled. You may want to try booting with the previous kernel image and see if it works again...if so stick with the previous kernel image until another update is released.

---

### Post by lavinog on 2008-09-28
> **finalrequiem said:**
> is there any command to run that would show it as disabled?

> *-network DISABLED
It looks like lspci already showed it.

---

### Post by finalrequiem on 2008-09-29
Oh, I see.  I missed that.  Wonder when it will be fixed... It's killing me not being able to use my wired access...

---

### Post by finalrequiem on 2008-09-29
Haven't tried with the live CD.  I'm afraid to now...  Can I update my bios using linux?  It's a thinkpad t61p and the lenovo website only gives windows versions of their updates...

---

### Post by lavinog on 2008-09-29
> **finalrequiem said:**
> Haven't tried with the live CD.  I'm afraid to now...  Can I update my bios using linux?  It's a thinkpad t61p and the lenovo website only gives windows versions of their updates...

There should be no problem if you use the live cd (hardy) since you already have used it...if you don't want to use the live cd then try booting to an older kernel...It should already be installed unless you manually removed it. press esc when grub loads and select the next kernel down that isn't a recovery kernel.

You can update your bios with a bootable cd (windows not needed): on the lenovo bios update page for your model there is a section "Additional Information" that has a link for the bios bootable update cd.

---

### Post by finalrequiem on 2008-09-29
The reason I'm scared is because I'm afraid I'll find out my hardware is ruined...  I will check into updated my bios...

---

### Post by finalrequiem on 2008-09-30
Ok, I updated my Bios (didn't work with the liveCD either...) and here are the new outputs of the various commands, some have changed.

_ifconfig:_
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117500 (114.7 KB)  TX bytes:117500 (114.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.110.1  Bcast:172.16.110.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.193.1  Bcast:192.168.193.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:66:a5:6d  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe66:a56d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:795716 (777.0 KB)  TX bytes:153361 (149.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-66-A5-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

_lspci | grep Ethernet_
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 03)

_sudo dmesg|egrep "82566DC|Intel"_
[   20.879706] Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[   23.044550] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   23.044554] Copyright (c) 1999-2006 Intel Corporation.
[   28.211566] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.0/input/input2
[   28.212245] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.1-1
[   30.661782] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.481096] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   31.481099] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   31.482073] iwl4965: Detected Intel Wireless WiFi Link 4965AGN

_/etc/network/interfaces_
auto lo
iface lo inet loopback


Any other ideas?  Not showing as disabled but still nothing showing in network manager or anything...

---

### Post by lavinog on 2008-09-30
You should start a new thread with a title:
"Intel 82566DC network interface not working on lenovo T61P"

I am out of ideas, and the people that might have the answer are not going to read a thread titled "Strange problem"

I also don't know why you have vmnet1 and vmnet8, but it is interesting that updating the bios changed that.

---

### Post by lavinog on 2008-09-30
I think you should try and see if your network card works anywhere else. My desktop has a bios feature that can do network diagnostics. Although not likely to exist on you laptop there may be something similar.

I still wonder if this is related to that bug report even if it isn't the same kernel.

---

### Post by finalrequiem on 2008-09-30
The VMnet actually has something to do with vmware on my machine.  I went ahead and started a new thread already actually.  I'm gonna mark this as solved.  Thanks for all of your help!

---

