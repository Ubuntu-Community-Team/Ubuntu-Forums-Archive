---
title: "dhcp only launches correctly after booting from windows"
date: 2021-01-11
forum: Networking &amp; Wireless
---

### Post by mravox on 2021-01-11
[SIZE=2]Apologies in advance as I know next to nothing about networking. 

As implied in title, I am dual booting Windows 10 and Ubuntu 20.04. [COLOR=#242729][FONT=Arial]Yesterday I installed a new printer on my network, plugged via ethernet into my router. I believe the ethernet connection on my PC was still working, but I had not restarted my computer, which is where the issue first occurred, so I can't be sure. I also ran apt update, apt upgrade, and apt autoremove. It was rebooting after this that I noticed my ethernet connection was throwing the error "Activation of network connection failed".

I dug into the logs a little bit and have narrowed the issue down to dhcp (I think -- again I know very little). 

Running [/FONT][/COLOR]```
sudo journalctl  -b 0 -u NetworkManager
```[COLOR=#242729][FONT=Arial] led me to the line [/FONT][/COLOR]```
[FONT=Consolas]<warn>  [1610410697.1389] dhcp4 (enp4s0): request timed out[/FONT]
```

However, looking at the logs the same way after booting from Windows shows that dhcp4 succeeds in fetching DNS data.

If anyone could help me I would be very grateful. I have spent all day with this headache and I am about ready to back up my data and reinstall ubuntu. [/SIZE]

---

### Post by mravox on 2021-01-12
I have wiped my ubuntu install and reinstalled ubuntu 20.04. I am still getting the same issue. Can anyone please help me?

---

### Post by SeijiSensei on 2021-01-13
I'd start by running
```
sudo dhclient -v 
```
and see if it reports any errors.  If you have multiple network interfaces, add the interface name that points to the DHCP server (e.g., enp4s0, wlp2s0, etc.) to the end of the command. 

A successful connection looks like this:
```

$ sudo dhclient -v wlp2s0
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/74:e5:0b:f0:63:36
Sending on   LPF/wlp2s0/74:e5:0b:f0:63:36
Sending on   Socket/fallback
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0x99536531)
DHCPOFFER of 192.168.100.63 from 192.168.100.1
DHCPREQUEST for 192.168.100.63 on wlp2s0 to 255.255.255.255 port 67 (xid=0x31655399)
DHCPACK of 192.168.100.63 from 192.168.100.1 (xid=0x99536531)
bound to 192.168.100.63 -- renewal in 2778 seconds.

```
192.168.100.1 is my router where the DHCP server is located.

---

### Post by mravox on 2021-01-13
Hey, thank you very much for your help.

Here is the output of the dhclient -v command:

```

Listening on LPF/enp4s0/18:c0:4d:32:11:16
Sending on   LPF/enp4s0/18:c0:4d:32:11:16
Sending on   Socket/fallback
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 3 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 3 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 7 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 15 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 14 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 15 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 21 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 20 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 20 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 18 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 10 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 10 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 20 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 8 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 10 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 15 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 12 (xid=0x55aea74a)
DHCPDISCOVER on enp4s0 to 255.255.255.255 port 67 interval 18 (xid=0x55aea74a)

```

It seems to get stuck on DHCPDISCOVER and loop there forever

And here is the output of "sudo journalctl -b 0 -u NetworkManger", just in case I wasn't reading it correctly (I have no idea what I am doing, so I probably was not.)

```

Jan 13 10:47:23 henry-ubuntu systemd[1]: Starting Network Manager...
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.5999] NetworkManager (version 1.22.10) is starting... (for the first time)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6000] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.c>
Jan 13 10:47:23 henry-ubuntu systemd[1]: Started Network Manager.
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6019] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6072] manager[0x558288580030]: monitoring kernel firmware directory '/lib/firmware'.
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6072] monitoring ifupdown state file '/run/network/ifstate'.
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6784] hostname: hostname: using hostnamed
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6784] hostname: hostname changed from (none) to "henry-ubuntu"
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6786] dns-mgr[0x558288568290]: init: dns=systemd-resolved rc-manager=symlink, plugin=systemd-resolved
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6787] manager[0x558288580030]: rfkill: Wi-Fi hardware radio set enabled
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6787] manager[0x558288580030]: rfkill: WWAN hardware radio set enabled
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6817] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-adsl.so)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6830] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wifi.so)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6847] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-team.so)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6876] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-bluetooth.so)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6882] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wwan.so)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6884] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6885] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6886] manager: Networking is enabled by state file
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6887] dhcp-init: Using DHCP client 'internal'
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6896] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-settings-plugin-ifupdown.so")
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6896] settings: Loaded settings plugin: keyfile (internal)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6896] ifupdown: management mode: managed
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <warn>  [1610563643.6897] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6928] device (lo): carrier: link connected
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6930] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6942] manager: (enp4s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.6953] device (enp4s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <warn>  [1610563643.8916] Error: failed to open /run/network/ifstate
Jan 13 10:47:23 henry-ubuntu NetworkManager[791]: <info>  [1610563643.8956] modem-manager: ModemManager available
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7306] device (enp4s0): carrier: link connected
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7308] device (enp4s0): state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7314] policy: auto-activating connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7318] device (enp4s0): Activation: starting connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7319] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7321] manager: NetworkManager state is now CONNECTING
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7323] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7326] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:47:26 henry-ubuntu NetworkManager[791]: <info>  [1610563646.7328] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
Jan 13 10:47:42 henry-ubuntu NetworkManager[791]: <info>  [1610563662.3694] agent-manager: agent[e5bc6454c8943012,:1.75/org.gnome.Shell.NetworkAgent/1000]: agent registered
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <warn>  [1610563692.0629] dhcp4 (enp4s0): request timed out
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0629] dhcp4 (enp4s0): state changed unknown -> timeout
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0630] device (enp4s0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0636] manager: NetworkManager state is now DISCONNECTED
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <warn>  [1610563692.0644] device (enp4s0): Activation: failed for connection 'Wired connection 1'
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0646] device (enp4s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0652] dhcp4 (enp4s0): canceled DHCP transaction
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0652] dhcp4 (enp4s0): state changed timeout -> done
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0662] policy: auto-activating connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0670] device (enp4s0): Activation: starting connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0673] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0677] manager: NetworkManager state is now CONNECTING
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0679] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0684] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:12 henry-ubuntu NetworkManager[791]: <info>  [1610563692.0687] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <warn>  [1610563737.0687] dhcp4 (enp4s0): request timed out
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0687] dhcp4 (enp4s0): state changed unknown -> timeout
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0688] device (enp4s0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0693] manager: NetworkManager state is now DISCONNECTED
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <warn>  [1610563737.0702] device (enp4s0): Activation: failed for connection 'Wired connection 1'
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0705] device (enp4s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0711] dhcp4 (enp4s0): canceled DHCP transaction
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0711] dhcp4 (enp4s0): state changed timeout -> done
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0721] policy: auto-activating connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0731] device (enp4s0): Activation: starting connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0732] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0737] manager: NetworkManager state is now CONNECTING
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0740] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0745] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:48:57 henry-ubuntu NetworkManager[791]: <info>  [1610563737.0749] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <warn>  [1610563782.0704] dhcp4 (enp4s0): request timed out
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.0704] dhcp4 (enp4s0): state changed unknown -> timeout
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.0705] device (enp4s0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.0709] manager: NetworkManager state is now DISCONNECTED
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <warn>  [1610563782.0718] device (enp4s0): Activation: failed for connection 'Wired connection 1'
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.0720] device (enp4s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.0973] dhcp4 (enp4s0): canceled DHCP transaction
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.0974] dhcp4 (enp4s0): state changed timeout -> done
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.1001] policy: auto-activating connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.1008] device (enp4s0): Activation: starting connection 'Wired connection 1' (37d5eeae-7269-362c-a383-e19481532370)
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.1009] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.1012] manager: NetworkManager state is now CONNECTING
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.1014] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.1018] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jan 13 10:49:42 henry-ubuntu NetworkManager[791]: <info>  [1610563782.1020] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <warn>  [1610563827.0694] dhcp4 (enp4s0): request timed out
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <info>  [1610563827.0694] dhcp4 (enp4s0): state changed unknown -> timeout
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <info>  [1610563827.0695] device (enp4s0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <info>  [1610563827.0699] manager: NetworkManager state is now DISCONNECTED
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <warn>  [1610563827.0708] device (enp4s0): Activation: failed for connection 'Wired connection 1'
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <info>  [1610563827.0710] device (enp4s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <info>  [1610563827.1054] dhcp4 (enp4s0): canceled DHCP transaction
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <info>  [1610563827.1055] dhcp4 (enp4s0): state changed timeout -> done
Jan 13 10:50:27 henry-ubuntu NetworkManager[791]: <info>  [1610563827.1092] manager: startup complete

```

---

### Post by mravox on 2021-01-14
So I think I am making some progress (maybe) in at least finding more ways to troubleshoot. I tried to set up networkd (unsuccessfully, but I will keep trying) and I was able to successfully switch to static IP by editing the netplan yaml configuration file. That resulted in a status of "Wired Connected" but a "?" over the LAN icon. Websites were loading really really slowly, and mostly not at all. But still, maybe, progress? Interestingly, I keep my IP newly set static IP and have full internet connection when booting from windows into ubuntu, which is consistent with this being an ubuntu -> ubuntu reboot issue. Next I will double check that my BIOS clock is set correctly. If I don't post here again immediately, it is and that was not the issue.

---

### Post by SeijiSensei on 2021-01-15
All I can think of is that you're running some kind of firewall on the Ubuntu side which keeps packets from being sent to 255.255.255.255.

Is this a vanilla installation, or did you add some rules with iptables? If so, flush them all with
```

sudo iptables -F INPUT
sudo iptables -F FORWARD
sudo iptables -F OUTPUT

```
and try again.

---

### Post by mravox on 2021-01-15
Thanks, I appreciate your help. It is a vanilla installation, and I have not added any iptables rules. I ran those commands anyway but of course it didn't help. I appreciate the effort though, thank you. I may just have to switch back to windows and see if I can get my python scripts running with task scheduler. I hate to do it but I need a consistent internet connection

---

### Post by SeijiSensei on 2021-01-16
You could try running Xubuntu in a VirtualBox virtual machine. See [https://ubuntuforums.org/showthread.php?t=2456645&p=14014685#post14014685](https://ubuntuforums.org/showthread.php?t=2456645&p=14014685#post14014685) for details.

---

