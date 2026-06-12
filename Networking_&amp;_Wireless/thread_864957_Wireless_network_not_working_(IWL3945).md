---
title: "Wireless network not working (IWL3945)"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by ceesiebo on 2008-07-20
Hi people,

I've checked the internet forums numerous times, but my wireless is still not working like it should. I use a Dell M1530 XPS with an Intel IPW3945 and use Ubuntu Hardy 8.04. I also upgraded a while ago to BIOS A08.

Although I think it has nothing to do with the BIOS or the fact that it's a Dell laptop. I've tried several distro's but all have the same problem. First I got it to work using the noapic parameter in my menu.lst. But this is not a good solution since it doesn't work all the time (I hate rebooting until it works :)). Also noapic seems to stop using the second core.

I've read the remarks from chili555 with the backports-modules and somehow that doesn't do it for me. I've installed the backports-modules. According to synaptic I now have the following backports-modules installed :
- linux-backports-modules-2.6.24-19-generic
- linux-backports-modules-hardy
- linux-backports-modules-hardy-generic
Maybe that's a bit too much. My wireless LED also doesn't come up.

After the installation of the backports-modules Network-manager gives me the opportunity to select wireless networks (which is an improvement), but no wireless networks are listed.

Coding sudo rmmod -f iwl3945;sudo modprobe iwl3945 disable_hw_scan=1 also doesn't change anything.

When coding iwlist wlan0 scan I get the result :
wlan0 No scan results

When coding sudo iwlist wlan0 scan I get the result :
wlan0 Interface doesn't support scanning : Network is down

This is the output of iwconfig for wlan0 :
wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is the output of dmesg | grep iwl :
[   28.531401] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   28.531404] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   28.681108] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   28.754784] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[  472.188635] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[  472.188641] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[  472.189107] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  472.195787] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

So everything looks almost okay, but somehow I'm missing something. My adapter doesn't seem to connect to my AP even when I try to do it directly via network-manager (Connect to other wireless network) and filling in the ESSID and WEP-password phrase.

The kill-switch is always off (so wireless/bluetooth is enabled).

Can anybody see what I'm doing wrong here?

---

### Post by ceesiebo on 2008-07-20
By the way, here is my lshw -C network output :
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3f:7a:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.15 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: ff:ff:ff:ff:ff:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a

Strangely the network for my wireless is DISABLED.

---

### Post by chili555 on 2008-07-20
> Strangely the network for my wireless is DISABLEDI wonder if your wireless kill switch is indeed on or off. Please do:```
sudo cat /var/log/messages | grep switch
```Also, Network Manager will not activate your wireless as long as you have an active IP address with wired ethernet, which you do:> ip=192.168.1.15Please see [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager) , especially:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managedOnce you determine the switch is indeed in the correct position, please detach the wire and try again.

---

### Post by ceesiebo on 2008-07-20
The output of the cat command is :
Jul 20 12:22:36 ceesiebo-laptop kernel: [   12.029586] SMP alternatives: switching to UP code
Jul 20 12:22:36 ceesiebo-laptop kernel: [   12.378958] SMP alternatives: switching to SMP code
Jul 20 12:41:51 ceesiebo-laptop kernel: [   13.246366] SMP alternatives: switching to UP code
Jul 20 12:41:51 ceesiebo-laptop kernel: [   13.596507] SMP alternatives: switching to SMP code
Jul 20 15:38:05 ceesiebo-laptop kernel: [   11.440049] SMP alternatives: switching to UP code
Jul 20 15:38:05 ceesiebo-laptop kernel: [   11.789310] SMP alternatives: switching to SMP code
Jul 20 15:56:04 ceesiebo-laptop kernel: [   11.189349] SMP alternatives: switching to UP code
Jul 20 15:56:04 ceesiebo-laptop kernel: [   11.540771] SMP alternatives: switching to SMP code
Jul 20 16:03:33 ceesiebo-laptop kernel: [   12.432663] SMP alternatives: switching to UP code
Jul 20 16:03:33 ceesiebo-laptop kernel: [   12.782699] SMP alternatives: switching to SMP code
Jul 20 19:27:25 ceesiebo-laptop kernel: [   12.376892] SMP alternatives: switching to UP code
Jul 20 19:27:25 ceesiebo-laptop kernel: [   12.726056] SMP alternatives: switching to SMP code
Jul 20 19:27:56 ceesiebo-laptop kernel: [   47.444293] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x21ef000a
Jul 20 19:43:03 ceesiebo-laptop kernel: [   11.138657] SMP alternatives: switching to UP code
Jul 20 19:43:03 ceesiebo-laptop kernel: [   11.489220] SMP alternatives: switching to SMP code
Jul 20 19:52:13 ceesiebo-laptop kernel: [   11.885789] SMP alternatives: switching to UP code
Jul 20 19:52:13 ceesiebo-laptop kernel: [   12.236948] SMP alternatives: switching to SMP code
Jul 20 19:52:36 ceesiebo-laptop kernel: [   44.356557] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x21ef000a

There doesn't seem to be a statement about the killswitch. It is in the right position. When I add the noapic parameter in my menu.lst the wireless adapter works okay. I've done a clean install by the way with the 32bits version before I posted this thread. The noapic parameter now seems to have no influence on the dualcore (when I used the 64bits version with noapic, the second core disappeared when checking system info).

I've pulled the networkcable out of the laptop and this is the result of lshw -C network :
*-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3f:7a:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: ff:ff:ff:ff:ff:ff
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a

By the way, what I find strange is that wireless=IEEE 802.11a. I thought my networkprotocol was 802.11g.

---

### Post by ceesiebo on 2008-07-20
I've put the noapic parameter in again. This is the output of lshw -C network :

*-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3f:7a:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:d3:c3:c2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.9 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

Like I thougth, the wireless network should be 802.11g. The network is also not disabled anymore. But this is all thanks to the noapic parameter. When I remove this, wireless doesn't work anymore (and I rather leave it out).

---

### Post by ceesiebo on 2008-07-21
Yesterday I booted again, and wireless worked without noapic. But this morning it was gone again. It seems that for me the whole backports-modules solution only forced the wireless card in a working state, but the essential problem still isn't solved. Without the backports-modules I got the 'MAC in deep sleep' and 'Unable to int NIC' messages and these are now gone.

When the wireless doesn't work I see a net-manager message in the syslog saying that it can't scan for wireless networks because the network is down. But it doesn't say WHAT network. I'm trying to join a network :(. Why does it need a network to be up when I'm trying to join a network. It's frustrating. Also the network protocoll is set to 802.11a which should be 802.11g.

So basically sometimes it works and sometimes it doesn't. The noapic parameter works for the time being, but the iwl3945 driver still isn't working okay.

If any of you have other ideas please comment my thread.

---

### Post by ceesiebo on 2008-07-21
Here is my logging from syslog. Maybe it shows some hints to you. I still don't understand the warning :

Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'iwl3945'. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jul 21 16:20:43 ceesiebo-laptop kernel: [   34.909720] sky2 eth0: enabling interface
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  Deactivating device eth0. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <debug> [1216650043.774229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_UJ_875S'). 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Jul 21 16:20:43 ceesiebo-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
Jul 21 16:20:46 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul 21 16:21:03 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul 21 16:21:12 ceesiebo-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Jul 21 16:21:20 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul 21 16:25:29 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 

This bug is also described at the following link :[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190664](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190664)
It seems that for a lot of people the backports-modules and modprobe trick works but also a lot of people can't use it.

What I find strange is that when I code 'sudo ifconfig wlan0 up' I get the message 'SIOCSIFFLAGS: Invalid argument'. I'm going to investigate this further but if one of you have good tips, please post :).

---

### Post by ceesiebo on 2008-07-22
I browsed through my warnings again in syslog and this was a funny message :

Jul 22 17:14:57 ceesiebo-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one.

Ubuntu basically says my wireless card stinks :lolflag:

Anyway, I'm still not very happy about this. Ubuntu just shows random behaviour. I've started up and now even no wireless adapter is shown in lshw -C network. As soon as I reboot again it will be there. This evening I had to reboot multiple times (even with noapic parameter) to get the wireless adapter to work. I haven't even changed anything in the settings. When I start up I can get three different kind of situations : 1. No adapter, 2. A not-working adapter, 3. A working adapter.

I would get the idea that my adapter is broken, but under Vista it works like a charm. I've never seen it fail there, so the wireless card is okay.

Do you guys have suggestions about other settings or going back to older versions of Ubuntu (or other distro's)?

---

### Post by chili555 on 2008-07-22
Please let us see:```
sudo iwlist wlan0 scan
```Then, please do:```
sudo rmmod iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwlist wlan0 scan
```Any difference in the scan result?

Also, I note this:> Will activate wired connection 'eth0' because it now has a link.As I said above, Network Manager is not going to activate your wireless as long as wired ethernet is available. Please continue your efforts with the cable detached.

---

### Post by ceesiebo on 2008-07-23
Hi chili555,

I appreciate the help. When I code your suggestions, I just get the message :
wlan0 Interface doesn't support scanning : Network is down.

This also happens after I do the rmmod/modprobe statements. Same message.

This is the output of syslog :

Jul 23 15:44:36 ceesiebo-laptop kernel: [   27.210265] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jul 23 15:44:36 ceesiebo-laptop kernel: [   27.210434] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jul 23 15:44:36 ceesiebo-laptop NetworkManager: <info>  starting... 
Jul 23 15:44:38 ceesiebo-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'iwl3945'. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jul 23 15:44:40 ceesiebo-laptop kernel: [   34.623528] sky2 eth0: enabling interface
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  Deactivating device eth0. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <debug> [1216820680.639935] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_UJ_875S'). 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Jul 23 15:44:40 ceesiebo-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
Jul 23 15:44:43 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul 23 15:44:57 ceesiebo-laptop kernel: [   41.962307] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 23 15:45:00 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul 23 15:45:04 ceesiebo-laptop NetworkManager: <info>  Updating allowed wireless network lists. 

I didn't have the networkcable connected, but still networkmanager comes up with the message 'Will activate wired connection 'eth0' because it now has a link.'. This is very strange since I don't have the cable connected.

Maybe I should switch to Wicd, but I already tried that before and it didn't help. But maybe then I can see different messages. Should I try that or should I first do something else?

---

### Post by chili555 on 2008-07-24
I have read more about this problem than about any issue I have tried to solve. I am convinced it IS a Dell issue. When you Google/linux for *Error getting killswitch power*, it is always, as far as I have seen, a Dell machine. Here is a promising looking post: [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/deb32237d1e7eaa4](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/deb32237d1e7eaa4)

I suggest you go to Synaptic and install *libsmbios-bin* and any dependencies. Then, as suggested, *sudo gedit /usr/lib/hal/scripts/linux/hal-system-killswitch-get-power-linux* and amend as mentioned in the post. I would then, just to be safe and sure, reboot. Then see if your wireless works and, if not, what do your logs have to say.

---

### Post by ceesiebo on 2008-07-24
I've installed the libsmbios-bin. Wireless still doesn't come up. This is the output of syslog :

Jul 24 17:46:46 ceesiebo-laptop kernel: [   27.530246] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jul 24 17:46:46 ceesiebo-laptop kernel: [   27.530250] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jul 24 17:46:46 ceesiebo-laptop kernel: [   27.530405] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jul 24 17:46:46 ceesiebo-laptop kernel: [   27.590416] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'iwl3945'. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jul 24 17:46:50 ceesiebo-laptop kernel: [   35.098582] sky2 eth0: enabling interface
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  Deactivating device eth0. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <debug> [1216914410.645755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_UJ_875S'). 
Jul 24 17:46:50 ceesiebo-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
Jul 24 17:46:53 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul 24 17:47:07 ceesiebo-laptop kernel: [   42.263395] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 24 17:47:10 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul 24 17:47:14 ceesiebo-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Jul 24 17:47:27 ceesiebo-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 

The 'error getting killswitch power' is gone now, but this 'Network is down' message is still there.

Also the 'Will activate wired connection 'eth0' because it now has a link' is still there. Although it also says 'eth0: link is not ready'

---

### Post by ceesiebo on 2008-07-28
Well, I think I'll skip Ubuntu now. My harddisk broke and I suspect (after googling about it) that Ubuntu is responsible for it. I've got a SATA AHCI hard drive and it seems that Ubuntu Hardy can't handle it without a work-around. I've never heard about the work-around and now my hard drive is broken. Luckily I still had waranty so Dell sent me a new one. But this problem together with the wireless problems leaves me 1 conclusion : Ubuntu is not good enough. I'll keep Ubuntu on my desktop, but I'll return to Vista on my laptop. Maybe another Linux distro doesn't have all these problems.

---

### Post by DJF5 on 2008-08-21
I believe this is NOT a Dell issue, as I am experiencing the same problems on my HP NC6320 laptop with the (ofcourse) IPW3945 PCI-E card.

I am also having problems putting my laptop in Suspend of Hibernate mode (That may have something to do with it, I remember Windows can't get into standby if you haven't got your videocard drivers installed :S)

I am actually getting some messages about the killswitch

```

root@laptop:/# sudo cat /var/log/messages | grep switch
[   22.795707] SMP alternatives: switching to UP code
[   23.236862] SMP alternatives: switching to SMP code
[   23.500440] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.725031] SMP alternatives: switching to UP code
[   16.165945] SMP alternatives: switching to SMP code
[   16.430112] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 2194.313656] SMP alternatives: switching to UP code
[   52.547702] SMP alternatives: switching to SMP code
[  150.705926] Kill switch must be turned off for wireless networking to work.
[   14.931803] SMP alternatives: switching to UP code
[   15.372760] SMP alternatives: switching to SMP code
[   15.636886] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   40.022133] Kill switch must be turned off for wireless networking to work.
[ 1309.218108] Kill switch must be turned off for wireless networking to work.
[ 1530.678927] SMP alternatives: switching to UP code
[    0.231879] SMP alternatives: switching to SMP code
[    3.721246] Kill switch must be turned off for wireless networking to work.
[   25.291220] Kill switch must be turned off for wireless networking to work.
[   26.533333] Kill switch must be turned off for wireless networking to work.
[   37.688747] Kill switch must be turned off for wireless networking to work.
[  208.371311] Kill switch must be turned off for wireless networking to work.
[   15.380968] SMP alternatives: switching to UP code
[   15.821859] SMP alternatives: switching to SMP code
[   16.085676] ACPI: EC: non-query interrupt received, switching to interrupt mode

```

Is it just my logic? or does the wifi switch needs to be ENABLED to use wireless?
It only loses wireless connection after comming back from standby

---

### Post by jasonkirk2006 on 2008-10-08
For sure, there is something special in Dell computers. But the problem is with the linux kernel, or the iwl3945 module: they do not sense the radio kill switch (try tail -f /var/log/messages when turning the rf_kill switch on and off) on Dell machines and on a few other brands.

Linux kernel or the iwl3945 module should sense the position of the kill switch. Windows operating systems sense it alright, and wireless works without any issues.

Syslog messages change with the linux kernel but one thing remains the same: hw address is FF:FF:FF:FF:FF:FF if there is a problem. After that point nothing comes as a workaround and we should reboot until it senses it somehow. You can check hw address by

```

lshw -C network

```

or

```

ifconfig -a

```

And if hw address is displayed right but the device is said to be DISABLED, then try

```

sudo ifconfig wlan0 up

```

as long as your wireless name is wlan0 (change it if otherwise).

---

### Post by cakmin on 2008-10-08
Gents,

I also have wireless problem with my laptops. First I thought it was only my wife's ACER 5920 that has the problem (because it has PRO/Intel 3945a/b/g), however later on I found out that my old Compaq that uses Belkin G adapter also giving me some troubles. 

Anyway, I tried to follow the steps suggested in this forum, especially those told by Chilli555, unfortunately, I still cannot solve the wireless problem in my wife's ACER 5920. The network manager kept attempting to join my wireless router and prompting password window, but the connection always failed.

Here are some information that I gathered while I unplugged my wired network (cable):

1. When the wireless button was switched off

```
ninalia@diamond:~$ sudo iwlist wlan0 scan

wlan0     Interface doesn't support scanning : Network is down

```

```
ninalia@diamond:~$ sudo lshw -C network

  *-network DISABLED      

       description: Wireless interface

       product: PRO/Wireless 3945ABG Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:06:00.0

       logical name: wmaster0

       version: 02

       serial: 00:1c:bf:15:6b:22

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

  *-network

       description: Ethernet interface

       product: NetLink BCM5787M Gigabit Ethernet PCI Express

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:08:00.0

       logical name: eth0

       version: 02

       serial: 00:1b:24:88:5e:79

       size: 100MB/s

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s


```

2. After wireless button was switched on:

```
ninalia@diamond:~$ sudo ifconfig wlan0 up

ninalia@diamond:~$ dmesg | grep iwl

[   25.889832] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25

[   25.889837] iwl3945: Copyright(c) 2003-2007 Intel Corporation

[   25.890035] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection

[   26.034212] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

[   33.286186] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels

[   33.312639] Registered led device: iwl-phy0:RX

[   33.312662] Registered led device: iwl-phy0:TX

[  720.666711] iwl3945: Radio Frequency Kill Switch is On:

[  720.774708] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC

[  720.824557] iwl3945: MAC is in deep sleep!

[  720.824614] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC

[  720.884435] iwl3945: MAC is in deep sleep!

[  720.884470] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC

[  720.944312] iwl3945: MAC is in deep sleep!

[  721.054486] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC

[  764.333377] iwl3945: Radio disabled by HW RF Kill switch

[  766.036877] Registered led device: iwl-phy0:RX

[  766.036912] Registered led device: iwl-phy0:TX

[  777.308233] Registered led device: iwl-phy0:RX

[  777.308268] Registered led device: iwl-phy0:TX


```

```
ninalia@diamond:~$ sudo cat /var/log/messages | grep switch

Oct  8 14:48:25 diamond kernel: [   10.157848] SMP alternatives: switching to UP code

Oct  8 14:48:25 diamond kernel: [   10.613761] SMP alternatives: switching to SMP code

Oct  8 14:48:25 diamond kernel: [   10.881851] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 19:08:06 diamond kernel: [   10.336650] SMP alternatives: switching to UP code

Oct  8 19:08:06 diamond kernel: [   10.791383] SMP alternatives: switching to SMP code

Oct  8 19:08:06 diamond kernel: [   11.056965] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 20:59:36 diamond kernel: [   10.174842] SMP alternatives: switching to UP code

Oct  8 20:59:36 diamond kernel: [   10.626096] SMP alternatives: switching to SMP code

Oct  8 20:59:36 diamond kernel: [   10.890676] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 21:07:31 diamond kernel: [    9.786433] SMP alternatives: switching to UP code

Oct  8 21:07:31 diamond kernel: [   10.243539] SMP alternatives: switching to SMP code

Oct  8 21:07:31 diamond kernel: [   10.510282] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 21:23:24 diamond kernel: [  200.394649] Kill switch must be turned off for wireless networking to work.

Oct  8 21:33:18 diamond kernel: [    9.749425] SMP alternatives: switching to UP code

Oct  8 21:33:18 diamond kernel: [   10.198870] SMP alternatives: switching to SMP code

Oct  8 21:33:18 diamond kernel: [   10.465289] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 21:44:32 diamond kernel: [  280.543118] Kill switch must be turned off for wireless networking to work.

Oct  8 21:44:35 diamond kernel: [  281.521021] iwl3945: Radio disabled by HW RF Kill switch

Oct  8 21:52:01 diamond kernel: [  359.726363] Kill switch must be turned off for wireless networking to work.

Oct  8 21:56:17 diamond kernel: [    9.798865] SMP alternatives: switching to UP code

Oct  8 21:56:17 diamond kernel: [   10.250081] SMP alternatives: switching to SMP code

Oct  8 21:56:17 diamond kernel: [   10.514770] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 22:08:06 diamond kernel: [    9.822921] SMP alternatives: switching to UP code

Oct  8 22:08:06 diamond kernel: [   10.281716] SMP alternatives: switching to SMP code

Oct  8 22:08:06 diamond kernel: [   10.546818] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 22:12:12 diamond kernel: [    9.817652] SMP alternatives: switching to UP code

Oct  8 22:12:12 diamond kernel: [   10.278931] SMP alternatives: switching to SMP code

Oct  8 22:12:12 diamond kernel: [   10.545547] ACPI: EC: non-query interrupt received, switching to interrupt mode

Oct  8 23:06:12 diamond kernel: [  720.666716] Kill switch must be turned off for wireless networking to work.

Oct  8 23:10:47 diamond kernel: [  764.333377] iwl3945: Radio disabled by HW RF Kill switch


```

Can someone please kindly help me solve this problem? Many thanks.

---

### Post by cakmin on 2008-10-11
Strangely, the laptop that was previously not able to connect to a wireless router, now can connect to a router without encryption. But this connection belongs to someone else, not mine. I could not connect to my own encrypted router through the wireless. Any comment from those who are expert on this matter? Please?

---

### Post by cakmin on 2008-10-17
It's solved!!!

I don't really know which steps that actually did help me, but this is what I just did:

1. Change the encryption of my Router (Zyxel P660HW-D1) from WEP 128 bits to WPA Personal
2. Afterwards, I applied what's written on this thread:

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

:guitar:

---

### Post by salous on 2009-01-07
I have encountered exactly the same problem the original poster had. I have found the solution:
just type following command to bring the interface up
```
ifconfig wlan0 up
```
and the problem is solved.
Enjoy! :D

---

