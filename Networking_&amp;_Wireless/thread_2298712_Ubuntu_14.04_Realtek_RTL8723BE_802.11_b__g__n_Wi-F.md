---
title: "Ubuntu 14.04 Realtek RTL8723BE 802.11 b / g / n Wi-Fi Adapter constantly switched off"
date: 2015-10-13
forum: Networking &amp; Wireless
---

### Post by antares4 on 2015-10-13
Please, help.
On my laptop constantly switched off WiFi


os - ubuntu 14.04
Realtek RTL8723BE 802.11 b / g / n Wi-Fi Adapter

after failure
```



$ cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
12:Oct 13 12:16:45 maxim-HP NetworkManager[835]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
17:Oct 13 12:27:30 maxim-HP NetworkManager[835]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
19:Oct 13 12:27:34 maxim-HP NetworkManager[835]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
20:Oct 13 12:27:34 maxim-HP NetworkManager[835]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
21:Oct 13 12:27:34 maxim-HP NetworkManager[835]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1143
22:Oct 13 12:27:34 maxim-HP NetworkManager[835]: <info> Policy set 'DAP-1155' (wlan0) as default for IPv4 routing and DNS.
26:Oct 13 12:27:34 maxim-HP NetworkManager[835]: <info> Writing DNS information to /sbin/resolvconf




$ cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
98:Oct 13 12:37:56 maxim-HP NetworkManager[835]: <info> (eth0): IP6 addrconf timed out or failed.
99:Oct 13 12:37:56 maxim-HP NetworkManager[835]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
100:Oct 13 12:37:56 maxim-HP NetworkManager[835]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
101:Oct 13 12:37:56 maxim-HP NetworkManager[835]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
108:Oct 13 13:16:42 maxim-HP NetworkManager[835]: <info> (wlan0): roamed from BSSID 00:07:26:39:3F:31 (DAP-1155) to (none) ((none))
109:Oct 13 13:16:42 maxim-HP NetworkManager[835]: <warn> Connection disconnected (reason 15)
110:Oct 13 13:16:42 maxim-HP NetworkManager[835]: <info> (wlan0): supplicant interface state: completed -> disconnected
120:Oct 13 13:16:52 maxim-HP NetworkManager[835]: <info> (wlan0): supplicant interface state: disconnected -> scanning
124:Oct 13 13:16:58 maxim-HP NetworkManager[835]: <info> (wlan0): supplicant interface state: scanning -> authenticating
125:Oct 13 13:16:58 maxim-HP NetworkManager[835]: <warn> (wlan0): link timed out.
126:Oct 13 13:16:58 maxim-HP NetworkManager[835]: <info> (wlan0): device state change: activated -> failed (reason 'SSID not found') [100 120 53]
127:Oct 13 13:16:58 maxim-HP NetworkManager[835]: <warn> Activation (wlan0) failed for connection 'DAP-1155'
129:Oct 13 13:16:58 maxim-HP NetworkManager[835]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
130:Oct 13 13:16:58 maxim-HP NetworkManager[835]: <info> (wlan0): deactivating device (reason 'none') [0]
133:Oct 13 13:16:58 maxim-HP NetworkManager[835]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1178
137:Oct 13 13:17:03 maxim-HP NetworkManager[835]: <info> Policy set '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1' (eth0) as default for IPv4 routing and DNS.
141:Oct 13 13:17:03 maxim-HP NetworkManager[835]: <info> Writing DNS information to /sbin/resolvconf
145:Oct 13 13:17:03 maxim-HP NetworkManager[835]: <warn> Connection disconnected (reason -3)
146:Oct 13 13:17:03 maxim-HP NetworkManager[835]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
147:Oct 13 13:17:03 maxim-HP NetworkManager[835]: <warn> Connection disconnected (reason -3)

```

failure to
sudo iwlist wlan0 scan
working
after failure
```
sudo iwlist wlan0 scan
wlan0 Failed to read scan data: Resource temporarily unavailable
```

on a laptop is also installed in win8 it all work - no problem.

---

### Post by Hadaka on 2015-10-13
Hi try this..
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
then go to network configuration and set your IPv6 to IGNORE. (see screen shot attached)
[ATTACH=CONFIG]264931[/ATTACH]
reboot and test

---

### Post by antares4 on 2015-10-14
> **Hadaka said:**
> 
then go to network configuration and set your IPv6 to IGNORE. (see screen shot attached)
reboot and test

 
This is done for a long time did not help.

```
$ echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
options rtl8723be fwlps=N ips=N

```

Also, this is done 
[http://ubuntuforums.org/showthread.php?t=2239932&p=13100410#post13100410](http://ubuntuforums.org/showthread.php?t=2239932&p=13100410#post13100410)
It did not help

---

### Post by antares4 on 2015-10-15
Problem solved.
[http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem](http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem)
> 
[COLOR=#111111][FONT=Ubuntu]First of all remove the settings you made.[/FONT][/COLOR]
sudo rm /etc/modprobe.d/rtl8723be.conf
[COLOR=#111111][FONT=Ubuntu]If you do not have this file, nothing is wrong.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then install a good driver[/FONT][/COLOR]
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
[COLOR=#111111][FONT=Ubuntu]Reboot and enjoy[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is the same driver as [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new), but packed as dkms.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]You can see all that at [https://github.com/hanipouspilot/rtlwifi_new](https://github.com/hanipouspilot/rtlwifi_new)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If you also need bluetooth working run also[/FONT][/COLOR]
sudo apt-get install rtl8723au-bt-dkms linux-firmware

---

### Post by Hadaka on 2015-10-15
Glad you found a solution !
enjoy

---

### Post by jeremy31 on 2015-10-15
> **antares4 said:**
> Problem solved.
[http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem](http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem)

Can you post the result of ```
for p in /sys/module/rtl8723be/parameters/*; do echo $p; cat $p; done
```
Thanks

---

