---
title: "Can't get Linksys AE1200 working with Ubuntu 14.04"
date: 2014-06-29
forum: Networking &amp; Wireless
---

### Post by nickyc on 2014-06-29
Hi All, 

I cannot get my Linksys AE1200 usb drive to work with Ubuntu 14.04. I managed to get the thing working with Lubuntu but cannot get it working at all with Ubuntu 14.04. 

I have installed ndisgtk and have loaded the Vista driver successfully. I have then setup the wireless connection using network manager and have rebooted and nothing happens. 

Please help!

---

### Post by chili555 on 2014-06-29
> I have installed ndisgtk and have loaded the ***Vista*** driver successfully. Are you certain? What does this tell us?```
dmesg | grep ndis
ndiswrapper -l
```Here is a snip from the manual page:> ndiswrapper is two parts: user space tool that is used to install  Windows  **XP** drivers and kernel module to load the Windows **XP** drivers. Both are called ndiswrapper.

---

### Post by nickyc on 2014-06-30
Thanks for the response Chili555 - much appreciated. Below is the output from the queries -

dmesg | grep ndis - 

[   12.476390] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   12.515446] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.781877] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[   13.781989] usbcore: registered new interface driver ndiswrapper

bcmwlhigh6 : driver installed
	device (13B1:0039) present

Hope this helps.

---

### Post by chili555 on 2014-06-30
> ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh[COLOR="#FF0000"]5[/COLOR]; check system log for messages from 'loadndisdriver'But then...> bcmwlhigh[COLOR="#FF0000"]6[/COLOR] : driver installed
device (13B1:0039) presentDid you try both 5 and 6? I think the 'couldn't load driver' means it wants the XP inf and sys files; not Vista. Do you have them appropriate to your architecture; either 32- or 64-bit?

---

### Post by nickyc on 2014-06-30
I tried loading the XP driver using ndisgtk however it came up with, "Invalid Driver". I then installed the Vista driver which didn't come up with this error. I have installed the 64bit version of Ubuntu 14.04. I have an x86-based PC, maybe this is the issue. I thought this wouldn't cause any issues. The drivers available on the Linksys site only provide one driver and not x86 or 64bit drivers.

---

### Post by chili555 on 2014-06-30
> **nickyc said:**
> I tried loading the XP driver using ndisgtk however it came up with, "Invalid Driver". I then installed the Vista driver which didn't come up with this error. I have installed the 64bit version of Ubuntu 14.04. I have an x86-based PC, maybe this is the issue. I thought this wouldn't cause any issues. The drivers available on the Linksys site only provide one driver and not x86 or 64bit drivers.Do you have a link? Maybe we can glean something from the inf wording.

---

### Post by nickyc on 2014-07-01
[http://support.linksys.com/en-eu/support/adapters/AE1200](http://support.linksys.com/en-eu/support/adapters/AE1200)

If you go to the above link then click on Downloads and then choose the drop down, "Version 1.0". Here are the links to the drivers. 

Thanks again for your help.

---

### Post by chili555 on 2014-07-01
You want the XP (or its functional equivalent, NT) files for use in ndiswrapper. The XP files at the site you linked says, in part:> ;-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) - WinXP
;
[Cisco.NTamd64]
	%Linksys_AE1200_DeviceDesc% = Linksys_AE1200, USB\VID_13B1&PID_0039
	%Linksys_AE2500_DeviceDesc% = Linksys_AE2500, USB\VID_13B1&PID_003A
;-----------------------------------------------------------------
; x86 - Win2K, WinXP
;
[Cisco]
	%Linksys_AE1200_DeviceDesc% = Linksys_AE1200, USB\VID_13B1&PID_0039
	%Linksys_AE2500_DeviceDesc% = Linksys_AE2500, USB\VID_13B1&PID_003A
   
;-----------------------------------------------------------------You can see your 13b1:0039 device specifically listed and that it purports to be for both 32- and 64-bit. Are those the files you loaded and for which you got 'invalid driver'?

What does this say?```
ls /etc/ndiswrapper
```I wonder if this is the actual problem:>  I have installed the 64bit version of Ubuntu 14.04. I have an x86-based PC, maybe this is the issue.

---

### Post by nickyc on 2014-07-01
running the command - ls /etc/ndiswrapper I get the below - 

bcmwlhigh6

---

### Post by chili555 on 2014-07-01
Are the XP files from the Linksys site containing bcmwlhigh5.inf the ones you loaded and for which you got 'invalid driver'? I would like to erase what you have and try them but it's useless if you already did.

---

### Post by nickyc on 2014-07-01
I've removed all of the drivers and loaded the xp driver (from the Linksys site) via ndiskgtk however the same issue occurs and i still get the same, "Invalid Driver" error. Yes this was the bcmwlhigh5.inf file you mentioned is the one that fails for me!

---

### Post by chili555 on 2014-07-01
And now the contents of /etc/ndiswrapper is only bcmwlhigh5? Any clues here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by nickyc on 2014-07-01
running /etc/ndiswrapper and now just get bcmwlhigh5 yes. 

Below are the results from sudo modprobe ndiswrapper
dmesg | grep ndis

--------------------

[   12.225457] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   12.226639] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   12.882836] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   12.882894] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   12.882940] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   12.882990] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   12.883040] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   12.883084] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   12.883134] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   12.883183] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   12.883227] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   12.883270] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   12.883324] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   12.883371] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   12.883418] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   12.883466] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   12.883513] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   12.883556] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   12.883604] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   12.883649] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   12.883695] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   12.883743] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   12.883789] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   12.883841] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   12.883884] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   12.883931] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   12.883984] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   12.884055] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   12.884118] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   12.884160] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   12.884201] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[   12.885028] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[   12.885141] usbcore: registered new interface driver ndiswrapper
[  322.854698] usbcore: deregistering interface driver ndiswrapper
[  322.868964] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  323.127668] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[  323.127721] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2014-07-02
>  ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'Let's have a look:```
cat /var/log/syslog | grep ndis | tail -n20
```

---

### Post by nickyc on 2014-07-02
results from cat /var/log/syslog | grep ndis | tail -n20 - 


nick@nick-OptiPlex-755:~$ cat /var/log/syslog | grep ndis | tail -n20
Jul  2 19:47:06 nick-OptiPlex-755 kernel: [   11.860959] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
Jul  2 19:47:06 nick-OptiPlex-755 kernel: [   11.861966] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
Jul  2 19:47:06 nick-OptiPlex-755 kernel: [   12.725277] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
Jul  2 19:47:06 nick-OptiPlex-755 kernel: [   12.725390] usbcore: registered new interface driver ndiswrapper

---

### Post by nickyc on 2014-07-02
Good news!!! I installed Ubuntu 14.04 32 bit and installed the XP driver from the Linksys site and it works!!! Thanks for your help Chili555!!!

---

### Post by nickyc on 2014-07-02
However... After further testing I am coming across the same issue I had with Lubuntu 14.04. The wireless connection works but when downloading a torrent the torrent crashes out the internet connection to the Operating System. I do not have this issue with the same wireless usb using Windows 7. Please help!

---

### Post by chili555 on 2014-07-02
Man! ndiswrapper is the bad boy of Linux. We usually don't question that it works well or very well; we question that it works *at all!!* It hasn't been updated since last November and Ubuntu uses the latest version available, 1.59. There are very few manipulable parameters:```
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

```Other than hangcheck, I doubt any are relevant to your problem. I'd check syslog to see if there is any clue as to the crash:```
cat /var/log/syslog | grep -e wlan -e ndis
```Ideally run immediately after the crash.

Have you tried throttling the torrent client? I understand that throttling is a curse-word in the torrent world, but if it gets a stable download, it may be worth the effort. [https://raw.githubusercontent.com/feralhosting/feralfilehosting/master/Feral%20Wiki/General/Completing%20a%20data%20transfer/transmission%202.png](https://raw.githubusercontent.com/feralhosting/feralfilehosting/master/Feral%20Wiki/General/Completing%20a%20data%20transfer/transmission%202.png)

---

### Post by nickyc on 2014-07-03
I have throttled both my bittorrent clients deluge and transmission and tested. Once throttled the connection stays up for a few seconds more and then crashes. The below is the output from cat /var/log/syslog | grep -e wlan -e ndis. 

Jul  3 20:35:01 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): bringing up device.
Jul  3 20:35:01 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): preparing device.
Jul  3 20:35:01 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul  3 20:35:01 nick-OptiPlex-755 kernel: [   17.528304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  3 20:35:01 nick-OptiPlex-755 kernel: [   17.528661] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  3 20:35:02 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0) supports 1 scan SSIDs
Jul  3 20:35:02 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  3 20:35:02 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  3 20:35:02 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jul  3 20:35:02 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0) supports 1 scan SSIDs
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) starting connection 'PlusnetWirelessCA8D45'
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0/wireless): connection 'PlusnetWirelessCA8D45' has security, and secrets exist.  No new secrets needed.
Jul  3 20:35:12 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  3 20:35:22 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: Trying to associate with 58:98:35:ca:8d:45 (SSID='PlusnetWirelessCA8D45' freq=2412 MHz)
Jul  3 20:35:22 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: inactive -> associating
Jul  3 20:35:23 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: Associated with 58:98:35:ca:8d:45
Jul  3 20:35:23 nick-OptiPlex-755 kernel: [   39.097645] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  3 20:35:23 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jul  3 20:35:23 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: WPA: Key negotiation completed with 58:98:35:ca:8d:45 [PTK=CCMP GTK=TKIP]
Jul  3 20:35:23 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: CTRL-EVENT-CONNECTED - Connection to 58:98:35:ca:8d:45 completed [id=0 id_str=]
Jul  3 20:35:23 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: Trying to associate with 58:98:35:ca:8d:45 (SSID='PlusnetWirelessCA8D45' freq=2412 MHz)
Jul  3 20:35:23 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: 4-way handshake -> associating
Jul  3 20:35:25 nick-OptiPlex-755 avahi-daemon[647]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c2c1:c0ff:fe69:81e8.
Jul  3 20:35:25 nick-OptiPlex-755 avahi-daemon[647]: New relevant interface wlan0.IPv6 for mDNS.
Jul  3 20:35:25 nick-OptiPlex-755 avahi-daemon[647]: Registering new address record for fe80::c2c1:c0ff:fe69:81e8 on wlan0.*.
Jul  3 20:35:33 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: Authentication with 58:98:35:ca:8d:45 timed out.
Jul  3 20:35:33 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:98:35:ca:8d:45 reason=3 locally_generated=1
Jul  3 20:35:33 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul  3 20:35:33 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <warn> Activation (wlan0/wireless): association took too long.
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0/wireless): connection 'PlusnetWirelessCA8D45' has security, and secrets exist.  No new secrets needed.
Jul  3 20:35:38 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  3 20:35:43 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: Trying to associate with 58:98:35:ca:8d:45 (SSID='PlusnetWirelessCA8D45' freq=2412 MHz)
Jul  3 20:35:43 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: scanning -> associating
Jul  3 20:35:44 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: Associated with 58:98:35:ca:8d:45
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jul  3 20:35:44 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: WPA: Key negotiation completed with 58:98:35:ca:8d:45 [PTK=CCMP GTK=TKIP]
Jul  3 20:35:44 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: CTRL-EVENT-CONNECTED - Connection to 58:98:35:ca:8d:45 completed [id=0 id_str=]
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'PlusnetWirelessCA8D45'.
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul  3 20:35:44 nick-OptiPlex-755 avahi-daemon[647]: Withdrawing address record for fe80::c2c1:c0ff:fe69:81e8 on wlan0.
Jul  3 20:35:44 nick-OptiPlex-755 avahi-daemon[647]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::c2c1:c0ff:fe69:81e8.
Jul  3 20:35:44 nick-OptiPlex-755 avahi-daemon[647]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul  3 20:35:44 nick-OptiPlex-755 dhclient: Listening on LPF/wlan0/c0:c1:c0:69:81:e8
Jul  3 20:35:44 nick-OptiPlex-755 dhclient: Sending on   LPF/wlan0/c0:c1:c0:69:81:e8
Jul  3 20:35:44 nick-OptiPlex-755 dhclient: DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67 (xid=0x3d8749ba)
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul  3 20:35:44 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul  3 20:35:44 nick-OptiPlex-755 avahi-daemon[647]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.66.
Jul  3 20:35:44 nick-OptiPlex-755 avahi-daemon[647]: New relevant interface wlan0.IPv4 for mDNS.
Jul  3 20:35:44 nick-OptiPlex-755 avahi-daemon[647]: Registering new address record for 192.168.1.66 on wlan0.IPv4.
Jul  3 20:35:45 nick-OptiPlex-755 avahi-daemon[647]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c2c1:c0ff:fe69:81e8.
Jul  3 20:35:45 nick-OptiPlex-755 avahi-daemon[647]: New relevant interface wlan0.IPv6 for mDNS.
Jul  3 20:35:45 nick-OptiPlex-755 avahi-daemon[647]: Registering new address record for fe80::c2c1:c0ff:fe69:81e8 on wlan0.*.
Jul  3 20:35:45 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul  3 20:35:45 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul  3 20:35:45 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul  3 20:35:45 nick-OptiPlex-755 NetworkManager[664]: <info> Policy set 'PlusnetWirelessCA8D45' (wlan0) as default for IPv4 routing and DNS.
Jul  3 20:35:45 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) successful, device activated.
Jul  3 20:36:04 nick-OptiPlex-755 NetworkManager[664]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul  3 20:36:04 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul  3 20:36:04 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul  3 20:36:04 nick-OptiPlex-755 NetworkManager[664]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul  3 20:44:53 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 58:98:35:ca:8d:45 [GTK=TKIP]
Jul  3 20:44:56 nick-OptiPlex-755 wpa_supplicant[988]: message repeated 3 times: [ wlan0: WPA: Group rekeying completed with 58:98:35:ca:8d:45 [GTK=TKIP]]
Jul  3 20:44:56 nick-OptiPlex-755 wpa_supplicant[988]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   13.076579] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   13.077629] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.196668] ndiswrapper: driver bcmwlhigh5 (Cisco Consumer Products LLC,03/28/2011, 5.100.68.46) loaded
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202467] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f973c000, 16000, 4
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202473] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f973fe80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202477] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9743d00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202480] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9747b80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202483] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f974ba00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202486] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f974f880, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202489] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9753700, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202492] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9757580, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202496] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f975b400, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202499] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f975f280, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202502] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9763100, 16000, 4
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202505] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9766f80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202508] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f976ae00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202512] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f976ec80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202515] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9772b00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202518] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9776980, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202521] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f977a800, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202524] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f977e680, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202528] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9782500, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202531] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9786380, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202533] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f978a200, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202536] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f978e080, 16000, 4
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202539] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9791f00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202542] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9795d80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202545] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9799c00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202548] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f979da80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202551] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97a1900, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202554] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97a5780, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202558] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97a9600, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202561] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97ad480, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202564] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97b1300, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202567] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97b5180, 16000, 4
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202573] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97b9000, 16000, 4
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202576] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97bce80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202579] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97c0d00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202582] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97c4b80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202585] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97c8a00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202588] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97cc880, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202591] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97d0700, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202594] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97d4580, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202597] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97d8400, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202600] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97dc280, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202603] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97e0100, 16000, 4
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202606] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97e3f80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202609] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97e7e00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202613] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97ebc80, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202616] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97efb00, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202619] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97f3980, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202622] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97f7800, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.202624] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f97fb680, 16000, 5
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.220901] ndiswrapper (ndis_encode_setting:383): unknown type: 3
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.479010] wlan0: ethernet device c0:c1:c0:69:81:e8 using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 13B1:0039.F.conf
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.486310] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
Jul  3 20:50:02 nick-OptiPlex-755 kernel: [   14.488744] usbcore: registered new interface driver ndiswrapper
Jul  3 20:50:03 nick-OptiPlex-755 NetworkManager[667]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan0, iface: wlan0)
Jul  3 20:50:03 nick-OptiPlex-755 NetworkManager[667]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): using WEXT for WiFi device control
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): bringing up device.
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): preparing device.
Jul  3 20:50:04 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul  3 20:50:04 nick-OptiPlex-755 kernel: [   16.665421] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  3 20:50:04 nick-OptiPlex-755 kernel: [   16.665736] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  3 20:50:05 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0) supports 1 scan SSIDs
Jul  3 20:50:05 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  3 20:50:05 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  3 20:50:05 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jul  3 20:50:05 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0) supports 1 scan SSIDs
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) starting connection 'PlusnetWirelessCA8D45'
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0/wireless): connection 'PlusnetWirelessCA8D45' has security, and secrets exist.  No new secrets needed.
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  3 20:50:15 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jul  3 20:50:25 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: Trying to associate with 58:98:35:ca:8d:45 (SSID='PlusnetWirelessCA8D45' freq=2412 MHz)
Jul  3 20:50:25 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: inactive -> associating
Jul  3 20:50:25 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: Associated with 58:98:35:ca:8d:45
Jul  3 20:50:25 nick-OptiPlex-755 kernel: [   37.782977] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  3 20:50:25 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jul  3 20:50:25 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: WPA: Key negotiation completed with 58:98:35:ca:8d:45 [PTK=CCMP GTK=TKIP]
Jul  3 20:50:25 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: CTRL-EVENT-CONNECTED - Connection to 58:98:35:ca:8d:45 completed [id=0 id_str=]
Jul  3 20:50:25 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: Trying to associate with 58:98:35:ca:8d:45 (SSID='PlusnetWirelessCA8D45' freq=2412 MHz)
Jul  3 20:50:25 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: 4-way handshake -> associating
Jul  3 20:50:27 nick-OptiPlex-755 avahi-daemon[644]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c2c1:c0ff:fe69:81e8.
Jul  3 20:50:27 nick-OptiPlex-755 avahi-daemon[644]: New relevant interface wlan0.IPv6 for mDNS.
Jul  3 20:50:27 nick-OptiPlex-755 avahi-daemon[644]: Registering new address record for fe80::c2c1:c0ff:fe69:81e8 on wlan0.*.
Jul  3 20:50:35 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: Authentication with 58:98:35:ca:8d:45 timed out.
Jul  3 20:50:35 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:98:35:ca:8d:45 reason=3 locally_generated=1
Jul  3 20:50:35 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul  3 20:50:35 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <warn> Activation (wlan0/wireless): association took too long.
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0/wireless): connection 'PlusnetWirelessCA8D45' has security, and secrets exist.  No new secrets needed.
Jul  3 20:50:40 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  3 20:50:45 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: Trying to associate with 58:98:35:ca:8d:45 (SSID='PlusnetWirelessCA8D45' freq=2412 MHz)
Jul  3 20:50:45 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: scanning -> associating
Jul  3 20:50:46 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: Associated with 58:98:35:ca:8d:45
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jul  3 20:50:46 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: WPA: Key negotiation completed with 58:98:35:ca:8d:45 [PTK=CCMP GTK=TKIP]
Jul  3 20:50:46 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: CTRL-EVENT-CONNECTED - Connection to 58:98:35:ca:8d:45 completed [id=0 id_str=]
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'PlusnetWirelessCA8D45'.
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul  3 20:50:46 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul  3 20:50:46 nick-OptiPlex-755 avahi-daemon[644]: Withdrawing address record for fe80::c2c1:c0ff:fe69:81e8 on wlan0.
Jul  3 20:50:46 nick-OptiPlex-755 avahi-daemon[644]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::c2c1:c0ff:fe69:81e8.
Jul  3 20:50:46 nick-OptiPlex-755 avahi-daemon[644]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul  3 20:50:47 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul  3 20:50:47 nick-OptiPlex-755 dhclient: Listening on LPF/wlan0/c0:c1:c0:69:81:e8
Jul  3 20:50:47 nick-OptiPlex-755 dhclient: Sending on   LPF/wlan0/c0:c1:c0:69:81:e8
Jul  3 20:50:47 nick-OptiPlex-755 dhclient: DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67 (xid=0x782ed517)
Jul  3 20:50:48 nick-OptiPlex-755 avahi-daemon[644]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c2c1:c0ff:fe69:81e8.
Jul  3 20:50:48 nick-OptiPlex-755 avahi-daemon[644]: New relevant interface wlan0.IPv6 for mDNS.
Jul  3 20:50:48 nick-OptiPlex-755 avahi-daemon[644]: Registering new address record for fe80::c2c1:c0ff:fe69:81e8 on wlan0.*.
Jul  3 20:50:50 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Jul  3 20:50:52 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: completed -> 4-way handshake
Jul  3 20:50:51 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Jul  3 20:50:52 nick-OptiPlex-755 wpa_supplicant[828]: wlan0: WPA: Key negotiation completed with 58:98:35:ca:8d:45 [PTK=CCMP GTK=TKIP]
Jul  3 20:50:52 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jul  3 20:50:55 nick-OptiPlex-755 dhclient: message repeated 2 times: [ DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67 (xid=0x782ed517)]
Jul  3 20:50:55 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul  3 20:50:55 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul  3 20:50:55 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul  3 20:50:55 nick-OptiPlex-755 avahi-daemon[644]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.66.
Jul  3 20:50:55 nick-OptiPlex-755 avahi-daemon[644]: New relevant interface wlan0.IPv4 for mDNS.
Jul  3 20:50:55 nick-OptiPlex-755 avahi-daemon[644]: Registering new address record for 192.168.1.66 on wlan0.IPv4.
Jul  3 20:50:56 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul  3 20:50:56 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul  3 20:50:56 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul  3 20:50:56 nick-OptiPlex-755 NetworkManager[667]: <info> Policy set 'PlusnetWirelessCA8D45' (wlan0) as default for IPv4 routing and DNS.
Jul  3 20:50:58 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) successful, device activated.
Jul  3 20:51:07 nick-OptiPlex-755 NetworkManager[667]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul  3 20:51:07 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul  3 20:51:07 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul  3 20:51:07 nick-OptiPlex-755 NetworkManager[667]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

---

### Post by nickyc on 2014-07-03
OK I think I may have resolved this for good now I changed my routers security to WEP from WPA2. I have then downloaded without a break in the connection. Thank you for your time on here Chili555 much appreciated.

---

