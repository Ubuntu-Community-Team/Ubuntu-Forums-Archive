---
title: "Intel Wireless 3945ABG Does Not Work On Upgrade."
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by emma3 on 2014-01-02
Hello all,

I've been using Ubuntu 10 and upgraded to 12 yesterday. I liked the look, and expected a few teething problems. I'll come to those later - my major problem is that on starting my computer yesterday evening it wouldn't connect to my wireless modem. 

Wneh using 10 it always said it needed me to unlock the keyring (or whatever it was). I'm not computer gifted, so changing this would be more hassle than accepting this small task. My point is that with 12 it demanded this too - only it didn't when started yesterday evening. 

What it did do was demand the password for my modem. This I duly found in the pens and pencils box in my stationery drawer where these things are kept. I inserted the required code and the wireless icon got about doing its bit. 

And then after a few minutes the dialogue screen popped back up asking me to authenticate the password. Again. 

One point of note is that when starting the computer the cursor on the authentication popup/panel is blinking but you can't enter anything as the popup isn't "live" (its headline is in a muted colour which means it needs clicking on to enable it - like a document you're referring to but not working on).

What am I doing wrong, and how can I get my laptop back online? I'd rather not use the wires as it's a long way from the modem and telephone socket.

---

### Post by emma3 on 2014-01-02
I would very much appreciate a response to this as not being able to use the internet with my laptop means I can't use it for my work. 

If you have any queries, please post them and I will respond as best I can.

---

### Post by emma3 on 2014-01-02
Just to say that I dug around a bit, and added the password into the appropriate place in the wireless setup box. 

It then asked me to enable wireless through the keyring using my password.

After a few minutes the wireless network popup returned asking me for the appropriate password for my wireless modem. Back to square one. 

I cannot do anything about this; it is a problem with the upgrade in some way. It worked pretty well using Ubuntu 10, and much as when upgrading from Ubuntu 9 - I have come to bitterly regret my actions!

---

### Post by steeldriver on 2014-01-02
Please be patient - we are all volunteers!

There are a couple of known issues that can cause repeated re-authentication requests - if you are comfortable using the terminal there are some commands to help with diagnosis - first to find exactly what wireless device you have

```

lspci -nnv | grep '\[02.0\]'

lshw -C network -sanitize

```

---

### Post by emma3 on 2014-01-02
Steeldriver, thankyou for your thoughts, I didn't get a message telling me you'd responded or I'd have tried it earlier. 

BTW I post as an expert on several forums which takes me around 1 -2 hours per day. I don't complain about it.

---

### Post by emma3 on 2014-01-03
Thanks - I've just tried to find my terminal. Only ... what with everything having changed and the bar at the top no longer has the link to the terminal, I simply have no idea where it is! 

Everything I liked about Ubuntu seems to be disappearing ... and the things I relied on too :-(

---

### Post by steeldriver on 2014-01-03
you  can type 'terminal' in the dash search box or just use the Ctrl-Alt-t key combo

---

### Post by emma3 on 2014-01-03
Okay! Found it - it's an 82566MM Gigabit Network Connection.

After a lot of technical stuff that you'd understand, it says "network DISABLED"

Never mind the "why"; we're dealing with computers, and anything less logical I have yet to meet ... what do I do now?

BTW it says that I should run this program as a "super user" (I don't feel that this is appropriate, do you?)

---

### Post by steeldriver on 2014-01-03
82566MM would be your wired ethernet connection I think

It would be helpful if you could post the whole output of the commands - you can copy from the terminal by highlighting text with the mouse (left click + drag) and then Ctrl-**Shift**-C (not Ctrl-C like regular windows)

Running lshw as super-user sometimes gives a bit more information but is not necessary in this case

---

### Post by emma3 on 2014-01-03
Thankyou. I did see that there was an "edit" function in the top bar. As to ejecting my USB stick ... that was another learning process. The guys who decided what became what didn't spend much time thinking about the user!

This is what it came back with ... 

Version:1.0 StartHTML:0000000167 EndHTML:0000003461 StartFragment:0000000454 EndFragment:0000003445    	 	 	 	   00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)  
 03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)  
 emma@emma-laptop:~$  
 emma@emma-laptop:~$ lshw -C network -sanitize  
 WARNING: you should run this program as super-user.  
   *-network                
        description: Ethernet interface  
        product: 82566MM Gigabit Network Connection  
        vendor: Intel Corporation  
        physical id: 19  
        bus info: pci@0000:00:19.0  
        logical name: eth0  
        version: 03  
        serial: [REMOVED]  
        capacity: 1Gbit/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.3-0 latency=0 multicast=yes port=twisted pair  
        resources: irq:46 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)  
   *-network DISABLED  
        description: Wireless interface  
        product: PRO/Wireless 3945ABG [Golan] Network Connection  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: wlan0  
        version: 02  
        serial: [REMOVED]  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-57-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11abg  
        resources: irq:48 memory:df2ff000-df2fffff  
 WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by steeldriver on 2014-01-03
I don't have direct experience with that device but there are some recent threads that may help you

[http://ubuntuforums.org/showthread.php?t=2164433](http://ubuntuforums.org/showthread.php?t=2164433)

[http://ubuntuforums.org/showthread.php?t=2173990](http://ubuntuforums.org/showthread.php?t=2173990)

---

### Post by emma3 on 2014-01-03
I'm afraid those are getting a little scary for me! Sorry.

---

### Post by chili555 on 2014-01-03
> *-network DISABLED
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0 Usually DISABLED means that the hardware switch on the laptop is set to disable the wireless or, rarely, that the laptop mode module that is supposed to recognize key presses is not working correctly. Please check around your laptop and see if the switch is on or off. If everything looks to be set correctly, please open a terminal Ctrl+Alt+t and run and post:```
rfkill list all
```

---

### Post by emma3 on 2014-01-03
Chili 555 - you could be right on that one; I disabled it when I put the wire in so as to stop the annoying popup wanting the password every time I switched the machine on.

However, the thing wasn't working before that, wanting the router's password and all that kind of thing.

I'm hoping that it'll work if I do a clean install of Windows 7? I'm hoping my upgrade hasn't damaged my wireless card permanently or permanently switched it off.

---

### Post by chili555 on 2014-01-03
We won't be able to troubleshoot why it won't connect as expected if it is switched off.

---

### Post by emma3 on 2014-01-04
Chili,

I get the impression someone forgot to mention that I'd need to do something. 

Would the device run properly with a clean install?

---

### Post by emma3 on 2014-01-04
Okay, here it is, wireless plugging away trying to establish contact with my router. 

Version:1.0 StartHTML:0000000167 EndHTML:0000002802 StartFragment:0000000454 EndFragment:0000002786    	 	 	 	     *-network                
        description: Ethernet interface  
        product: 82566MM Gigabit Network Connection  
        vendor: Intel Corporation  
        physical id: 19  
        bus info: pci@0000:00:19.0  
        logical name: eth0  
        version: 03  
        serial: [REMOVED]  
        capacity: 1Gbit/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.3-0 latency=0 multicast=yes port=twisted pair  
        resources: irq:46 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)  
   *-network  
        description: Wireless interface  
        product: PRO/Wireless 3945ABG [Golan] Network Connection  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: wlan0  
        version: 02  
        serial: [REMOVED]  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-57-generic firmware=15.32.2.9 latency=0 multicast=yes wireless=IEEE 802.11abg  
        resources: irq:48 memory:df2ff000-df2fffff  

What can you suggest?

---

### Post by chili555 on 2014-01-04
As it is trying to connect, let's look for clues as to why it isn't:```
dmesg | grep iwl
cat /var/log/syslog | grep -e wlan -e etwork
```

---

### Post by emma3 on 2014-01-04
OK - you asked for it! There's eight pages to play with!

```
Version:1.0 StartHTML:0000000167 EndHTML:0000034517 StartFragment:0000000454 EndFragment:0000034501    	 	 	 	   emma@emma-laptop:~$ dmesg | grep iwl  
 [   24.178422] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s  
 [   24.178523] iwl3945: Copyright(c) 2003-2011 Intel Corporation  
 [   24.178595] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   24.178611] iwl3945 0000:03:00.0: setting latency timer to 64  
 [   24.234485] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels  
 [   24.234490] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG  
 [   24.234648] iwl3945 0000:03:00.0: irq 48 for MSI/MSI-X  
 [   24.263453] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'  
 [  123.427026] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9 
``` 

```
 emma@emma-laptop:~$ cat /var/log/syslog | grep -e wlan -e etwork  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Auto-activating connection 'Auto Zy_private_KKUWJW_nomap'.  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0) starting connection 'Auto Zy_private_KKUWJW_nomap'  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0/wireless): access point 'Auto Zy_private_KKUWJW_nomap' has security, but secrets are required.  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]  
 Jan  4 11:28:15 emma-laptop NetworkManager[912]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.  
 Jan  4 11:30:02 emma-laptop NetworkManager[912]: <info> WiFi now disabled by radio killswitch  
 Jan  4 11:30:02 emma-laptop NetworkManager[912]: <info> (wlan0): device state change: need-auth -> unavailable (reason 'none') [60 20 0]  
 Jan  4 11:30:02 emma-laptop NetworkManager[912]: <info> (wlan0): deactivating device (reason 'none') [0]  
 Jan  4 11:30:02 emma-laptop NetworkManager[912]: <info> WWAN now disabled by radio killswitch  
 Jan  4 11:30:03 emma-laptop NetworkManager[912]: <info> (ttyUSB0): now unmanaged  
 Jan  4 11:30:03 emma-laptop NetworkManager[912]: <info> (ttyUSB0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]  
 Jan  4 11:30:03 emma-laptop NetworkManager[912]: <info> (ttyUSB0): cleaning up...  
 Jan  4 11:30:03 emma-laptop NetworkManager[912]: <info> (ttyUSB0): taking down device.  
 Jan  4 11:30:03 emma-laptop NetworkManager[912]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))  
 Jan  4 11:30:03 emma-laptop NetworkManager[912]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> DNS: loaded plugin dnsmasq  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: init!  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: update_system_hostname  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPluginIfupdown: management mode: unmanaged  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: end _init.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    Ifupdown: get unmanaged devices count: 0  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: (148707528) ... get_connections.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    SCPlugin-Ifupdown: (148707528) ... get_connections (managed=false): return empty list.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile: parsing Auto Internet-Gast ...  
 Jan  4 18:31:10 emma-laptop kernel: [    1.355770] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k  
 Jan  4 18:31:10 emma-laptop kernel: [    1.690539] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection  
 Jan  4 18:31:10 emma-laptop kernel: [   24.135897] type=1400 audit(1388856668.575:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"  
 Jan  4 18:31:10 emma-laptop kernel: [   24.178422] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s  
 Jan  4 18:31:10 emma-laptop kernel: [   25.588623] type=1400 audit(1388856670.031:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=929 comm="apparmor_parser"  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile:     read connection 'Auto Internet-Gast'  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile: parsing Auto Zy_private_KKUWJW_nomap ...  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile:     read connection 'Auto Zy_private_KKUWJW_nomap'  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile: parsing Auto FRITZ!Box Fon WLAN 7170 ...  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile:     read connection 'Auto FRITZ!Box Fon WLAN 7170'  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile: parsing Auto FRITZ!Box 6360 Cable ...  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile:     read connection 'Auto FRITZ!Box 6360 Cable'  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile: parsing Auto DCC-Public ...  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    keyfile:     read connection 'Auto DCC-Public'  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]:    Ifupdown: get unmanaged devices count: 0  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> modem-manager is now available  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> monitoring kernel firmware directory '/lib/firmware'.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver (unknown))  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> found WWAN radio killswitch rfkill2 (at /sys/devices/platform/thinkpad_acpi/rfkill/rfkill2) (driver thinkpad_acpi)  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> WiFi disabled by radio killswitch; enabled by state file  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> WWAN disabled by radio killswitch; disabled by state file  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> WiMAX enabled by radio killswitch; enabled by state file  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> Networking is enabled by state file 
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <warn> failed to allocate link cache: (-10) Operation not supported  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): carrier is OFF  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): now managed  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): bringing up device.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): preparing device.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (eth0): deactivating device (reason 'managed') [2]  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:19.0/net/eth0  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (wlan0): using nl80211 for WiFi device control  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (wlan0): now managed  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (wlan0): bringing up device.  
 Jan  4 18:31:10 emma-laptop NetworkManager[887]: <info> (wlan0): deactivating device (reason 'managed') [2]  
 Jan  4 18:31:10 emma-laptop kernel: [   26.411133] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Jan  4 18:31:24 emma-laptop NetworkManager[887]: dbus_g_error_get_name: assertion `error->code == DBUS_GERROR_REMOTE_EXCEPTION' failed  
 Jan  4 18:31:24 emma-laptop NetworkManager[887]: <warn> could not get modem properties: (null) Method "GetAll" with signature "s" on interface "org.freedesktop.DBus.Properties" doesn't exist  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> disable requested (sleeping: no  enabled: yes)  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> sleeping or disabling...  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> (eth0): now unmanaged  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> (eth0): cleaning up...  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> (eth0): taking down device.  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> (wlan0): now unmanaged  
 Jan  4 18:32:09 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> enable requested (sleeping: no  enabled: no)  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> waking up and re-enabling...  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> WWAN now enabled by management service  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (eth0): now managed  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (eth0): bringing up device.  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (eth0): preparing device.  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (eth0): deactivating device (reason 'managed') [2]  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (wlan0): now managed  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (wlan0): bringing up device.  
 Jan  4 18:32:13 emma-laptop NetworkManager[887]: <info> (wlan0): deactivating device (reason 'managed') [2]  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> (wlan0): bringing up device.  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> WiFi hardware radio set enabled  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> WiFi now enabled by radio killswitch  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> (wlan0): bringing up device.  
 Jan  4 18:32:47 emma-laptop kernel: [  123.498925] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> wpa_supplicant started  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: starting -> ready  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: ready -> inactive  
 Jan  4 18:32:47 emma-laptop NetworkManager[887]: <warn> Trying to remove a non-existant call id.  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Auto-activating connection 'Auto Zy_private_KKUWJW_nomap'.  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0) starting connection 'Auto Zy_private_KKUWJW_nomap'  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> (wlan0): preparing device.  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0/wireless): access point 'Auto Zy_private_KKUWJW_nomap' has security, but secrets are required.  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]  
 Jan  4 18:32:52 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Activation (wlan0/wireless): connection 'Auto Zy_private_KKUWJW_nomap' has security, and secrets exist.  No new secrets needed.  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Config: added 'ssid' value 'Zy_private_KKUWJW_nomap'  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Config: added 'scan_ssid' value '1' 
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Config: added 'key_mgmt' value 'WPA-PSK'  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Config: added 'psk' value '<omitted>'  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> Config: set interface ap_scan to 1  
 Jan  4 18:34:07 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: inactive -> scanning  
 Jan  4 18:34:11 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: scanning -> authenticating  
 Jan  4 18:34:11 emma-laptop kernel: [  206.908280] wlan0: authenticate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:11 emma-laptop kernel: [  206.910031] wlan0: authenticated  
 Jan  4 18:34:11 emma-laptop kernel: [  206.910198] wlan0: associate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:11 emma-laptop kernel: [  206.912983] wlan0: RX AssocResp from cc:5d:4e:8b:26:94 (capab=0xc11 status=0 aid=2)  
 Jan  4 18:34:11 emma-laptop kernel: [  206.912988] wlan0: associated  
 Jan  4 18:34:11 emma-laptop kernel: [  206.914658] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Jan  4 18:34:11 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: authenticating -> associating  
 Jan  4 18:34:11 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associating -> associated  
 Jan  4 18:34:11 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake  
 Jan  4 18:34:17 emma-laptop kernel: [  213.144254] wlan0: deauthenticated from cc:5d:4e:8b:26:94 (Reason: 15)  
 Jan  4 18:34:17 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected  
 Jan  4 18:34:17 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: disconnected -> scanning  
 Jan  4 18:34:21 emma-laptop kernel: [  216.715043] wlan0: authenticate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:21 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: scanning -> associating  
 Jan  4 18:34:21 emma-laptop kernel: [  216.716851] wlan0: authenticated  
 Jan  4 18:34:21 emma-laptop kernel: [  216.717161] wlan0: associate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:21 emma-laptop kernel: [  216.719984] wlan0: RX ReassocResp from cc:5d:4e:8b:26:94 (capab=0xc11 status=0 aid=2)  
 Jan  4 18:34:21 emma-laptop kernel: [  216.719993] wlan0: associated  
 Jan  4 18:34:21 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associating -> associated  
 Jan  4 18:34:21 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake  
 Jan  4 18:34:27 emma-laptop kernel: [  222.944727] wlan0: deauthenticated from cc:5d:4e:8b:26:94 (Reason: 15)  
 Jan  4 18:34:27 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected  
 Jan  4 18:34:27 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: disconnected -> scanning  
 Jan  4 18:34:30 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: scanning -> authenticating  
 Jan  4 18:34:30 emma-laptop kernel: [  226.528740] wlan0: authenticate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:30 emma-laptop kernel: [  226.530586] wlan0: authenticated  
 Jan  4 18:34:30 emma-laptop kernel: [  226.531599] wlan0: associate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:30 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: authenticating -> associating  
 Jan  4 18:34:30 emma-laptop kernel: [  226.539122] wlan0: RX ReassocResp from cc:5d:4e:8b:26:94 (capab=0xc11 status=0 aid=2)  
 Jan  4 18:34:30 emma-laptop kernel: [  226.539127] wlan0: associated  
 Jan  4 18:34:30 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associating -> associated  
 Jan  4 18:34:31 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake  
 Jan  4 18:34:37 emma-laptop kernel: [  232.775231] wlan0: deauthenticated from cc:5d:4e:8b:26:94 (Reason: 15)  
 Jan  4 18:34:37 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected  
 Jan  4 18:34:37 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: disconnected -> scanning  
 Jan  4 18:34:40 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: scanning -> authenticating  
 Jan  4 18:34:40 emma-laptop kernel: [  236.348955] wlan0: authenticate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:40 emma-laptop kernel: [  236.351076] wlan0: authenticated  
 Jan  4 18:34:40 emma-laptop kernel: [  236.351504] wlan0: associate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:40 emma-laptop kernel: [  236.354384] wlan0: RX ReassocResp from cc:5d:4e:8b:26:94 (capab=0xc11 status=0 aid=2)  
 Jan  4 18:34:40 emma-laptop kernel: [  236.354393] wlan0: associated  
 Jan  4 18:34:40 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: authenticating -> associating  
 Jan  4 18:34:40 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associating -> associated  
 Jan  4 18:34:41 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake  
 Jan  4 18:34:47 emma-laptop kernel: [  242.565749] wlan0: deauthenticated from cc:5d:4e:8b:26:94 (Reason: 15)  
 Jan  4 18:34:47 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected  
 Jan  4 18:34:47 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: disconnected -> scanning  
 Jan  4 18:34:50 emma-laptop kernel: [  246.134966] wlan0: authenticate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:50 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: scanning -> associating  
 Jan  4 18:34:50 emma-laptop kernel: [  246.136860] wlan0: authenticated  
 Jan  4 18:34:50 emma-laptop kernel: [  246.137174] wlan0: associate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:34:50 emma-laptop kernel: [  246.140693] wlan0: RX ReassocResp from cc:5d:4e:8b:26:94 (capab=0xc11 status=0 aid=2)  
 Jan  4 18:34:50 emma-laptop kernel: [  246.140703] wlan0: associated  
 Jan  4 18:34:50 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associating -> associated  
 Jan  4 18:34:50 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake  
 Jan  4 18:34:56 emma-laptop kernel: [  252.336246] wlan0: deauthenticated from cc:5d:4e:8b:26:94 (Reason: 15)  
 Jan  4 18:34:56 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected  
 Jan  4 18:34:56 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: disconnected -> scanning  
 Jan  4 18:35:00 emma-laptop kernel: [  255.902855] wlan0: authenticate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:35:00 emma-laptop kernel: [  255.904674] wlan0: authenticated  
 Jan  4 18:35:00 emma-laptop kernel: [  255.905230] wlan0: associate with cc:5d:4e:8b:26:94 (try 1)  
 Jan  4 18:35:00 emma-laptop kernel: [  255.908169] wlan0: RX ReassocResp from cc:5d:4e:8b:26:94 (capab=0xc11 status=0 aid=2)  
 Jan  4 18:35:00 emma-laptop kernel: [  255.908180] wlan0: associated  
 Jan  4 18:35:00 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: scanning -> associating  
 Jan  4 18:35:00 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associating -> associated  
 Jan  4 18:35:00 emma-laptop NetworkManager[887]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake  

 emma@emma-laptop:~$  
```

It did have something about "killswitch" in there - the switch was switched to let the wireless work.

---

### Post by chili555 on 2014-01-04
> wlan0: deauthenticated from cc:5d:4e:8b:26:94 (Reason: 15) ....at which point the popup comes back to tell you thhat you are disconnected and to ask you for your password...*again*! According to many sources, here, for example, [http://forums.gentoo.org/viewtopic-t-880813-start-0.html](http://forums.gentoo.org/viewtopic-t-880813-start-0.html),  reason 15 is is a "4-way handshake timeout" meaning that the router didn't like the password that you provided. I suggest you retrace your steps and be sure the password is correct. I myself struggled for a couple of days until I remembered that I had changed the password after my beloved brother-in-law left town and forgot that the password was no longer ilovecoldbeer but was now Ilovecoldbeer. Way to be professional, Chili!

Second, I'd change the encryption method in the router from mixed mode WPA and WPA2 to WPA2-AES only. Finally, I suggest that you experimentally declare your regulatory domain from here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)  For example:```
sudo iw reg set US
```Now can you connect and stay connected?

---

### Post by emma3 on 2014-01-05
Okay. the password is good. I tried with my little laptop (works on XP - so it's not usually on the internet) - and it connected happily enough. However for some reason it couldn't connect to google.nl. I guess this is the problem I'm having with my Ubuntu laptop - only if the problem's with the router, why should it only occur when I've run an upgrade? 

I am thoroughly fed up! It baffles me, and it's probably one box that's not been ticked - but which box and where to find it is the real problem. I feel like Theseus in the minotaur's lair, only without breadcrumbs.

---

### Post by emma3 on 2014-01-06
Okay, I'm outta here. As ever with Linux, if it doesn't work, it's not going to. I'll get my coat and lock the door as I leave. I'll pop the key through the letterbox, okay?

---

### Post by chili555 on 2014-01-06
I won't try to talk you out of leaving; Ubuntu in particular and Linux in general aren't for everyone. Neither are Windows nor Mac OS, for that matter. Only you know what your needs and wants are.

I can tell you that many of the posts I answered in this thread were from a Lenovo T60 running 12.04 LTS and an Intel 3945. I know it works. At least in my case, it works seamlessly and perfectly.

Did you try all of the suggestions I offered? What was the outcome? We can try several other things as well.

---

### Post by emma3 on 2014-01-06
I found Ubuntu 10 acceptable apart from the bits I couldn't get to work - like printers. Sadly most of the things I liked about 10 have been wiped - which means it's more like a mac now (which I'm using now but find harder to use - but the printers work seamlessly).

I'll lay a cable to the kitchen and plug it in. It's a lot less hassle. I struggled for days and days with the printers - and no matter what I did, they'd print once and that was and end of it. I learned my lesson. 

I appreciate the time you've taken - I simply feel overwhelmed by the complexity of Linux. Whenever there's a problem you've got to insert difficult to follow code. Earlier on in the thread it suggested looking at two other threads both of which popped code into the terminal. That terrified me, I have enough problems without adding to them by messing up a command or finding that my system wasn't quite like the others and my computer turns into a pancake. I'll keep it as it is and accept that if I continue using Linux, it's without wireless networking.

---

### Post by emma3 on 2014-01-21
A final note: it was as you suspected the router at fault. 

In mitigation, I plead insanity. My iMac was working with the router in wireless mode. Yet I couldn't connect my laptop because the wireless on my router was switched off. I didn't go looking for this because it was obviously switched on (ie other equipment could use it). It was only a fit of desperation that led me to discover this fact.

There was no way I could understand someone telling me to switch the router on ... when it was working "properly" - which in computer terms seems to be "it might be working - or not, depending on the circumstances". Now that really is logical. 

And I really am mad.

---

### Post by chili555 on 2014-01-21
No worries! We all have made a tiny mis-step at times; even me and even Linus! What's important is that it's working and now, hopefully, you have restored a bit of faith and confidence in Ubuntu.

---

