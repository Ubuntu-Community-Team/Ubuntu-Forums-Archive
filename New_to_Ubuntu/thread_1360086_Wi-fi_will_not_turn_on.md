---
title: "Wi-fi will not turn on"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by osizzle on 2009-12-20
When i boot into ubuntu, my wi-fi will not turn on. I have a dell inspiron 1545. It worked fine before, but suddenly it just does not work. The wi-fi does work when i am in Vista. I sense that it might be a driver problem, but that doesn't make sense b/c it was working well before without adding any specific driver stuff. What to do? what to do? :(

---

### Post by hugmenot on 2009-12-20
What do you mean when you say that it doesn&#8217;t turn on?

Give more details.

---

### Post by Unixp on 2009-12-20
What wifi card do you have?

/Alec

---

### Post by osizzle on 2009-12-20
I have a Intel (R) Wifi Link 5100 AGN and in Ubuntu the wifi will not enable. It is disabled. and when i try to enable it, it won't allow me to by deselecting or un highlighting the enable button.

---

### Post by hugmenot on 2009-12-20
Did you inadvertently engage the kill switch?

Can you run this:

```

sudo dmesg -c > /dev/null
sudo rmmod iwlagn && sudo modprobe iwlagn
dmesg

```

---

### Post by osizzle on 2009-12-21
no that didn't work i got this code :

 [FONT=&quot]ERROR: Module iwalgn does not exist in /proc/modules[/FONT]

---

### Post by hugmenot on 2009-12-21
iwlagn. Just copy and paste these lines into terminal.

---

### Post by osizzle on 2009-12-22
I did  what u said and got this strange output:

   [SIZE=1]8[  18.491183] iwlagn 0000:0c:00.0: PCI INT A disabled[/SIZE]
  [SIZE=1][  188.521932] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k[/SIZE]
  [SIZE=1][  188.521937] iwlagn: Copyright(c) 2003-2009 Intel Corporation[/SIZE]
  [SIZE=1][  188.522310] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17[/SIZE]
  [SIZE=1][  188.522344] iwlagn 0000:0c:00.0: setting latency timer to 64[/SIZE]
  [SIZE=1][  188.522415] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54[/SIZE]
  [SIZE=1][  188.563106] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels[/SIZE]
  [SIZE=1][  188.563186] iwlagn 0000:0c:00.0: irq 31 for MSI/MSI-X[/SIZE]
  [SIZE=1][  188.565417] phy1: Selected rate control algorithm 'iwl-agn-rs'[/SIZE]
  [SIZE=1][  188.582967] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-2.ucode[/SIZE]
  [SIZE=1][  188.590688] iwlagn 0000:0c:00.0: loaded firmware version 8.24.2.12[/SIZE]
  [SIZE=1][  188.734768] Registered led device: iwl-phy1::radio[/SIZE]
  [SIZE=1][  188.734798] Registered led device: iwl-phy1::assoc[/SIZE]
  [SIZE=1][  188.734827] Registered led device: iwl-phy1::RX[/SIZE]
  [SIZE=1][  188.734861] Registered led device: iwl-phy1::TX[/SIZE]
  [SIZE=1][  188.762140] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/SIZE]
  [SIZE=1][  209.507304] Registered led device: iwl-phy1::radio[/SIZE]
  [SIZE=1][  209.507334] Registered led device: iwl-phy1::assoc[/SIZE]
  [SIZE=1][  209.507362] Registered led device: iwl-phy1::RX[/SIZE]
  [SIZE=1][  209.507388] Registered led device: iwl-phy1::TX[/SIZE]
  [SIZE=1][  209.531240] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/SIZE]

---

### Post by hugmenot on 2009-12-22
Looking good. The problem must lie higher up in the networking stack.

Can you open two terminal windows and then start this command in one of them
```
tail -f /var/log/syslog
```

Then do this in the other terminal:
```
sudo restart network-manager
```

Post what is printed in the first terminal. 

When you click the wireless menu, what do you see?

---

### Post by osizzle on 2009-12-23
After : “~$ tail -f /var/log/syslog” I got this in terminal #1
  [INDENT][SIZE=2]
[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu NetworkManager: <info>  (eth0): bringing up device.[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu NetworkManager: <info>  (eth0): preparing device.[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/eth0[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu kernel: [  217.556534] sky2 eth0: enabling interface[/SIZE]
[SIZE=2]Dec 23 08:37:12 ubuntu kernel: [  217.557002] ADDRCONF(NETDEV_UP): eth0: link is not ready[/SIZE]
[SIZE=2]Dec 23 08:38:54 ubuntu anacron[1188]: Job `cron.daily' started[/SIZE]
[SIZE=2]Dec 23 08:38:54 ubuntu anacron[3853]: Updated timestamp for job `cron.daily' to 2009-12-23[/SIZE]
[SIZE=2]
[/SIZE]
[/INDENT]                    [SIZE=3]After “~$ sudo restart network-manager “ In terminal #2 I got [/SIZE]
  [INDENT][SIZE=2]
[/SIZE]
[SIZE=2]network-manager start/running, process 4017[/SIZE]
[/INDENT]  [SIZE=2]
[/SIZE]
[SIZE=3]And After “~$ sudo restart network-manager” this was what came up in terminal #1[/SIZE]
  [INDENT][SIZE=2]
[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): cleaning up...[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): taking down device.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  exiting (success)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu kernel: [  607.690152] sky2 eth0: disabling interface[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  starting...[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  modem-manager is now available[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: init![/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wmaster0, iface: wmaster0)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/eth0, iface: eth0)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  Found radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  Wireless now disabled by radio killswitch[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: (10307680) ... get_connections.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    SCPlugin-Ifupdown: (10307680) ... get_connections (managed=false): return empty list.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (wlan0): now managed[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (wlan0): bringing up device.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): carrier is OFF[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): now managed[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): bringing up device.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): preparing device.[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/eth0[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu kernel: [  607.923046] sky2 eth0: enabling interface[/SIZE]
[SIZE=2]Dec 23 08:43:42 ubuntu kernel: [  607.923502] ADDRCONF(NETDEV_UP): eth0: link is not ready [/SIZE]

[/INDENT]

Still doesn't work

---

### Post by hugmenot on 2009-12-24
As I suspected:
```
Dec 23 08:43:42 ubuntu NetworkManager: <info> Wireless now disabled by radio killswitch
```

Either a hardware switch or an Fn+function key combo that disabled your wireless.

---

### Post by osizzle on 2009-12-24
So what do I do? The wifi button works in Vista and originally was working in Ubuntu, but not anymore. That Fn button isn't really a Fn button b/c the commands are reversed on the inspiron 1545. I tried all Fn combinations with that top row above the numbers (e.g. F1-F12) nothing happened.

---

### Post by geek4unix on 2010-09-06
The mention of rfkill reminds me of a similar problem I had, perhaps installing the 'rfkill' package.

If it is, 'rfkill unblock all' should at least work around the problem and enable the card again (soft block only).

This is my problem / solution:

[http://winunixmac.com/tips-and-tricks/67-ubuntu-1041-lts-wireless-networki](http://winunixmac.com/tips-and-tricks/67-ubuntu-1041-lts-wireless-networki)

---

### Post by gauravj on 2010-09-07
try re-installing network-manager-gnome.

---

