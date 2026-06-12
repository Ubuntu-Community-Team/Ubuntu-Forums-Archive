---
title: "Choosing a USB adaptor for 15.10 and how to use them"
date: 2016-01-27
forum: Networking &amp; Wireless
---

### Post by mistcloud-misty on 2016-01-27
First off, the basics: ```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)

03:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter
```

I've had all I can take from the Mediatek's inability to complete a search without slow DNS lookups, random disconnects after logging in or resuming from suspend, and "failure to flush the queue" that forces me to reboot, only to do so immediately right after. The driver I used worked okay for a few days and then suddenly I logged in and there was no Internet because it 'failed to flush on queue 2" over and over in terminal, and rebooting didn't help because it was constantly failing to flush. After trying to use recovery mode, the wireless worked in that mode but naturally I was unable to login to 'low graphics mode' because Nvidia's proprietary drivers are installed (not sure why that prevents me from logging but it always does). Removing the drivers let me login to recovery mode's low graphics mode but when rebooting, I ended up having the 'cannot detect monitor, graphics card, or input mode' error, and no fix I could find on the internet made that go away, so long story short, I had to completely reinstall my system which was almost entirely unusable (even tty1 console would freeze after a couple of commands and keyboard logging was very slow, making it almost impossible to do anything). 

So I'm going to solve one problem by getting a USB network adapter. The problem is the Wiki page on network adapters is very out of date and I'm not sure which ones work with Ubuntu 15.10 out of the box. My preference is out of the box because the ethernet will not connect no matter what cables I use so going online that way to download the proper driver won't work. Basically I'm looking for something that automatically connects to the wireless without needing to download and install a driver.

Since I've never used a wireless adapter, I also want to know if I need to uninstall the mediatek driver before using the adapter. Is there any command necessary to 'turn on' the adapter or is it automatic once plugged in by USB? Any tips would be appreciated. If anyone can point me at a 15.10 compatible, out of the box adapter at amazon that would be the best site, because I have prime's 2-day shipping and I have no idea how many days I have before the wireless decides to stop working again. I saw some things that worked with earlier versions of Ubuntu (like 10.04) but I know software changes a lot since then so I don't want to order something that doesn't work on the newest version.

---

### Post by chili555 on 2016-01-27
Here you go: [http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG/ref=sr_1_1?ie=UTF8&qid=1453911945&sr=8-1&keywords=tplink+722](http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG/ref=sr_1_1?ie=UTF8&qid=1453911945&sr=8-1&keywords=tplink+722)

I have one and, in Ubuntu 15.10, I plug it in, it blinks twice and connects! I installed literally nothing (!!) to get it working.

You will need to blacklist the driver for the internal device. Find it here:```
lspci -nnk | grep 0280 -A2
```Here is a sample from my machine:> 03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 6b)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:c262]
	Kernel driver in use: [COLOR="#FF0000"]iwlwifi[/COLOR]Yours will be different; I assume mt76some_such.

Blacklist it:```
sudo -i
echo "blacklist mt76whatever"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r mt76whatever
exit
```My USB arrived from Amazon coded to use the wireless frequencies from China. I get slightly better performance using my own CRDA code.

Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

I suggest you undertake the CRDA change immediately.

I am sure that there are other choices. But I have first-hand experience with that one.

---

### Post by mistcloud-misty on 2016-01-27
Hey thanks for your response! I checked that out and found it could be delivered by this Friday so I ordered it. I've made sure to change the CRDA before (initially I couldn't connect to public wifi networks without disconnecting constantly without it). I hope this solves my problems and makes this computer a bit more reliable!

---

### Post by mistcloud-misty on 2016-01-29
The adapter came in today and it works, however I have a few issues. I have set the doman and blacklisted the old driver, however, it takes a very long time for the wireless to connect to the network, always taking quite a few minutes on this step: "connecting (getting IP configuration)"

The wireless worked for maybe 2 minutes after plugging it in and then I ended up with a DNS unable to resolve at all so couldn't look up anything. I decided maybe rebooting would help and after quite awhile of waiting for connection the wireless network is connected and functioning fine.

I had some system errors as a result with network manager crashing and a few other things. Got any ideas on what caused it? Got 5 bars and the speed is wonderful but taking 5 minutes or more to connect to the network is a little too much. I have IPv6 set to ignore as usual but I still get this in dmesg when connecting: 
```
[  186.221843] IPv6: ADDRCONF(NETDEV_UP): wlxf4f26d17b7ea: link is not ready
```

I'll attach the wireless script below. It wouldn't fit as a .txt so I had to upload the tar.gz file (sorry!). 

It has been working wonderfully since connected but I'm not an optimist when it comes to wireless as of lately.

---

### Post by chili555 on 2016-01-29
Bummer! My adapter works perfectly; of course, it's in my network, connecting to my 15-year-old router!

Your wireless script shows everything set the way I'd recommend, at least, so far. IPv6 to ignore, WPA2-AES, CRDA, etc. I do notice that the device is trying to negotiate 72 Mbps speeds. You might experiment in the router to change from B, G and N speeds to B and G only. Reboot the router and see if connectivity improves.

[http://i.stack.imgur.com/KBFbn.png](http://i.stack.imgur.com/KBFbn.png) This has G and N highlighted, but I suggest you experiment with B and G.

There are a few driver parameters available that we might try:```
sudo modprobe -r ath9k_htc
sudo modprobe ath9k_htc nohwcrypt=1
```If it helps, make it permanent:```
sudo -i
echo "options ath9k_htc nohwcrypt=1"  >  /etc/modprobe.d/ath9k_htc.conf
exit
```Any improvement?

If not, let's see:```
cat /var/log/syslog | grep -i network | tail -n20
```

---

### Post by mistcloud-misty on 2016-01-29
I don't have access to the router since I'm just using the family internet connection and the router itself belongs to my dad, so will have to wait on changing those settings.

I did try the driver parameters, and after the first command, lost all wireless connection, and nothing changed with the second command. After unplugging and replugging the usb, however, the wireless connected after about a minute - strangely the network is always 'out of range' for awhile before coming in range at full strength and randomly connecting. There are two outputs from before unplugging it and after unplugging it:
```
cat /var/log/syslog | grep -i network | tail -n20
Jan 29 18:28:07 arcane NetworkManager[686]: <info>  devices removed (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/net/wlxf4f26d17b7ea, iface: wlxf4f26d17b7ea)
Jan 29 18:28:07 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): supplicant interface state: completed -> disconnected
Jan 29 18:28:07 arcane NetworkManager[686]: <info>  radio killswitch /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/ieee80211/phy0/rfkill2 disappeared
Jan 29 18:28:23 arcane NetworkManager[686]: <warn>  (wlxf4f26d17b7ea): link timed out.
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): device state change: activated -> failed (reason 'ssid-not-found') [100 120 53]
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  NetworkManager state is now CONNECTED_LOCAL
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  NetworkManager state is now DISCONNECTED
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  Connection 'DDW365CB 1' failed to autoconnect; 4 tries left
Jan 29 18:28:23 arcane NetworkManager[686]: <warn>  (wlxf4f26d17b7ea): Activation: failed for connection 'DDW365CB 1'
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 29 18:28:23 arcane NetworkManager[686]: <error> [1454110103.409037] [platform/nm-linux-platform.c:2782] do_change_link(): platform-linux: do-change-link: failure changing link 3: No such device (31)
Jan 29 18:28:23 arcane NetworkManager[686]: <warn>  (wlxf4f26d17b7ea): failed to enable userspace IPv6LL address handling
Jan 29 18:28:23 arcane systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan 29 18:28:23 arcane systemd[1]: Started Network Manager Script Dispatcher Service.
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): canceled DHCP transaction, DHCP client pid 2750
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): DHCPv4 state changed bound -> done
Jan 29 18:28:23 arcane NetworkManager[686]: <error> [1454110103.442892] [platform/nm-linux-platform.c:2782] do_change_link(): platform-linux: do-change-link: failure changing link 3: No such device (31)
Jan 29 18:28:23 arcane NetworkManager[686]: <error> [1454110103.442927] [platform/nm-linux-platform.c:2782] do_change_link(): platform-linux: do-change-link: failure changing link 3: No such device (31)
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  Writing DNS information to /sbin/resolvconf
Jan 29 18:28:23 arcane NetworkManager[686]: <info>  Device 'wlxf4f26d17b7ea' has no connection; scheduling activate_check in 0 seconds.

```

after:
```
cat /var/log/syslog | grep -i network | tail -n20
Jan 29 18:30:24 arcane NetworkManager[686]: <info>  dhclient started with pid 7088
Jan 29 18:30:25 arcane NetworkManager[686]: <info>    address 192.168.0.11
Jan 29 18:30:25 arcane NetworkManager[686]: <info>    plen 24 (255.255.255.0)
Jan 29 18:30:25 arcane NetworkManager[686]: <info>    gateway 192.168.0.1
Jan 29 18:30:25 arcane NetworkManager[686]: <info>    server identifier 192.168.0.1
Jan 29 18:30:25 arcane NetworkManager[686]: <info>    lease time 3600
Jan 29 18:30:25 arcane NetworkManager[686]: <info>    nameserver '209.18.47.61'
Jan 29 18:30:25 arcane NetworkManager[686]: <info>    nameserver '209.18.47.62'
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): DHCPv4 state changed unknown -> bound
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  NetworkManager state is now CONNECTED_LOCAL
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  Policy set 'DDW365CB 1' (wlxf4f26d17b7ea) as default for IPv4 routing and DNS.
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  Writing DNS information to /sbin/resolvconf
Jan 29 18:30:25 arcane NetworkManager[686]: <info>  (wlxf4f26d17b7ea): Activation: successful, device activated.
Jan 29 18:30:27 arcane whoopsie[633]: [18:30:27] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/5
Jan 29 18:30:27 arcane whoopsie[633]: [18:30:27] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/5
Jan 29 18:30:27 arcane whoopsie[633]: [18:30:27] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/5

```


After several hours of using the internet (prior to checking the commands), there haven't been any disconnects, very few slow DNS lookups, and nothing loading slower than usual. It's just the initial connection to the network that seems to be slow.

---

### Post by chili555 on 2016-01-29
I still suggest the router change and look forward to your report.

---

### Post by mistcloud-misty on 2016-01-31
Unfortunately after checking our modem settings (it's a Time Warner Cable duo Modem+router), there was no setting that allowed us to change to B+G. There is only Wireless N or no Wireless N in the settings but there was a setting to increase the wireless N to a higher bandwidth with more support, which we tried. It is a relatively new modem, so maybe those settings aren't available anymore. 

After the third restart I did, the wireless connects almost instantly, so it seems that particular problem was fixed just from another reboot - maybe there were a few kinks there to work out. Unfortunately there is some slow DNS, and at times - after quite awhile of using the internet - the DNS stops altogether and nothing loads until I reset the wireless in settings. There is lag and various disconnecting phases when on an online game of some kind, which started after using this usb, but since I can't find much of a problem with the internet itself I can't be sure if it's because of the network adapter and something going wrong or coincidental server problems. 

Strangely, it seems to be ignoring my changes to the CRDA, often with dmesg saying the region is unset (when in the file it is set to the US), and usually changing it to CN or FCC - I'm not sure if that plays a problem or not.

This error occasionally appears in my dmesg and kernel logs, but also not sure if it's related to the connection:
```
ath: phy0: Could not kill baseband RX
```

---

### Post by chili555 on 2016-01-31
> There is only Wireless N or no Wireless N in the settingsI would certainly try both ways.

FCC is the same as USA. ```
chili@T440p:~$ iw reg get
country [COLOR="#FF0000"]US[/COLOR]: DFS-[COLOR="#FF0000"]FCC[/COLOR]
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)
```I believe you set a driver parameter in post #5. I suggest that we change it:```
sudo gedit /etc/modprobe.d/ath9k_htc.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. I believe the file now reads:```
options ath9k_htc nohwcrypt=1
```Change it to read:```
options ath9k_htc btcoex_enable=1
```Proofread carefully, save and close the text editor. Reboot.

Better? Worse? Same??

---

### Post by mistcloud-misty on 2016-01-31
That actually seemed to help quite a bit so far. Instant connection, and even websites that loaded slowly are loading almost instantly. Less lag on the games I play, minus an occasional spike here or there but I wouldn't say those are internet related since spikes tend to be server problems. No slow DNS problems yet and I won't know about a complete DNS 'crash' until I run the computer for almost a day straight without rebooting since it usually takes that long for that problem to happen.

I checked a few of the previously mentioned commands and found that dnsmasq failed to load, and the bit-rate of the card jumped up from around 16 (estimate, forgot already) to 90 MB/s. 

```
 cat /var/log/syslog | grep -i network | tail -n20
Jan 31 10:46:35 arcane NetworkManager[658]: <info>  (wlxf4f26d17b7ea): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 31 10:46:35 arcane NetworkManager[658]: <info>  NetworkManager state is now CONNECTED_LOCAL
Jan 31 10:46:35 arcane NetworkManager[658]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Jan 31 10:46:35 arcane NetworkManager[658]: <info>  Policy set 'DDW365CB 1' (wlxf4f26d17b7ea) as default for IPv4 routing and DNS.
Jan 31 10:46:35 arcane NetworkManager[658]: <info>  DNS: starting dnsmasq...
Jan 31 10:46:35 arcane NetworkManager[658]: <warn>  dnsmasq not available on the bus, can't update servers.
Jan 31 10:46:35 arcane NetworkManager[658]: <error> [1454255195.835221] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jan 31 10:46:35 arcane NetworkManager[658]: <warn>  DNS: plugin dnsmasq update failed
Jan 31 10:46:35 arcane NetworkManager[658]: <info>  Writing DNS information to /sbin/resolvconf
Jan 31 10:46:37 arcane NetworkManager[658]: <info>  (wlxf4f26d17b7ea): Activation: successful, device activated.
Jan 31 10:46:37 arcane NetworkManager[658]: <warn>  dnsmasq appeared on DBus: :1.34
Jan 31 10:46:37 arcane NetworkManager[658]: <info>  Writing DNS information to /sbin/resolvconf
Jan 31 10:46:37 arcane systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan 31 10:46:37 arcane systemd[1]: Started Network Manager Script Dispatcher Service.
Jan 31 10:46:37 arcane whoopsie[653]: [10:46:37] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Jan 31 10:46:37 arcane whoopsie[653]: [10:46:37] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Jan 31 10:46:37 arcane whoopsie[653]: [10:46:37] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Jan 31 10:46:41 arcane NetworkManager[658]: <info>  WiFi hardware radio set enabled
Jan 31 10:46:41 arcane NetworkManager[658]: <info>  WWAN hardware radio set enabled
Jan 31 10:46:43 arcane NetworkManager[658]: <info>  startup complete
arcane@arcane:~$ iwconfig
enp2s0    no wireless extensions.

wlxf4f26d17b7ea  IEEE 802.11bgn  ESSID:"DDW365CB"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 54:35:30:24:C5:EF   
          Bit Rate=90 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:98   Missed beacon:0

lo        no wireless extensions.

```

Is invalid misc anything to worry about? I had some value for that on my other card too.

---

### Post by chili555 on 2016-01-31
Invalid Misc is normal. Here is the reading from my machine, using the exact same device:```
wlx30b5c2120f20  IEEE 802.11bgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:2B:B0:DC:45:XX  
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:[COLOR="#FF0000"]76[/COLOR]   Missed beacon:0

```Moreover, the seeming error:> <error> [1454255195.835221] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name...appears in my syslog as well and it connects and passes traffic perfectly, so I am not worried about it.> I won't know about a complete DNS 'crash' until I run the computer for almost a day straight without rebooting since it usually takes that long for that problem to happen.I will be interested in your report.

If it does crash, try to capture the syslog:```
cat /var/log/syslog | grep -e ath -e dns | tail -n20
```

---

### Post by mistcloud-misty on 2016-02-01
Well instead of that a new problem occurred. The wireless disconnected and would not reconnect, repeatedly asking me for the network password and not accepting it when I put it in. Worked fine after restart. This is the last 100 messages with the network log command.
```
cat /var/log/syslog | grep -i network | tail -n100
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  SCPlugin-Ofono: (9427872) ... get_connections.
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  SCPlugin-Ofono: (9427872) connections count: 0
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  get unmanaged devices count: 0
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  monitoring kernel firmware directory '/lib/firmware'.
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  monitoring ifupdown state file '/run/network/ifstate'.
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/ieee80211/phy0/rfkill2) (driver ath9k_htc)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  rfkill0: found WiFi radio killswitch (at /sys/devices/platform/asus-nb-wmi/rfkill/rfkill0) (platform driver asus-nb-wmi)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMVxlanFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMVlanFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMVethFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMTunFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMMacvlanFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMInfinibandFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMGreFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMEthernetFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMBridgeFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMBondFactory (internal)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  WiFi enabled by radio killswitch; enabled by state file
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  WWAN enabled by radio killswitch; enabled by state file
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  WiMAX enabled by radio killswitch; enabled by state file
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  Networking is enabled by state file
Feb  1 11:43:15 arcane NetworkManager[699]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (lo): link connected
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (lo): new Generic device (carrier: ON, driver: 'unknown', ifindex: 1)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): using nl80211 for WiFi device control
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): driver supports Access Point (AP) mode
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): new 802.11 WiFi device (carrier: UNKNOWN, driver: 'ath9k_htc', ifindex: 3)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (enp2s0): new Ethernet device (carrier: OFF, driver: 'r8169', ifindex: 2)
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  (enp2s0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  urfkill disappeared from the bus
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  ofono is now available
Feb  1 11:43:15 arcane NetworkManager[699]: <warn>  failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Feb  1 11:43:15 arcane NetworkManager[699]: <info>  ModemManager available in the bus
Feb  1 11:43:16 arcane NetworkManager[699]: <info>  wpa_supplicant running
Feb  1 11:43:16 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): supplicant interface state: starting -> ready
Feb  1 11:43:16 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb  1 11:43:16 arcane NetworkManager[699]: <info>  Device 'wlxf4f26d17b7ea' has no connection; scheduling activate_check in 0 seconds.
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): supplicant interface state: ready -> inactive
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  Auto-activating connection 'DDW365CB 1'.
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): Activation: starting connection 'DDW365CB 1' (71468bed-5cf9-42ce-88ed-3254651d6ac3)
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  NetworkManager state is now CONNECTING
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: prepare -> config (reason 'none') [40 50 0]
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): Activation: (wifi) connection 'DDW365CB 1' has security, and secrets exist.  No new secrets needed.
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  Config: added 'ssid' value 'DDW365CB'
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  Config: added 'scan_ssid' value '1'
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  Config: added 'psk' value '<omitted>'
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  Config: set interface ap_scan to 1
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): supplicant interface state: inactive -> authenticating
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): supplicant interface state: authenticating -> associating
Feb  1 11:43:17 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): supplicant interface state: associating -> associated
Feb  1 11:43:18 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): supplicant interface state: associated -> 4-way handshake
Feb  1 11:43:18 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): supplicant interface state: 4-way handshake -> completed
Feb  1 11:43:18 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'DDW365CB'.
Feb  1 11:43:18 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb  1 11:43:18 arcane NetworkManager[699]: <info>  Activation (wlxf4f26d17b7ea) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb  1 11:43:18 arcane NetworkManager[699]: <info>  dhclient started with pid 880
Feb  1 11:43:19 arcane NetworkManager[699]: <info>    address 192.168.0.11
Feb  1 11:43:19 arcane NetworkManager[699]: <info>    plen 24 (255.255.255.0)
Feb  1 11:43:19 arcane NetworkManager[699]: <info>    gateway 192.168.0.1
Feb  1 11:43:19 arcane NetworkManager[699]: <info>    server identifier 192.168.0.1
Feb  1 11:43:19 arcane NetworkManager[699]: <info>    lease time 3600
Feb  1 11:43:19 arcane NetworkManager[699]: <info>    nameserver '209.18.47.61'
Feb  1 11:43:19 arcane NetworkManager[699]: <info>    nameserver '209.18.47.62'
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): DHCPv4 state changed unknown -> bound
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): device state change: secondaries -> activated (reason 'none') [90 100 0]
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  NetworkManager state is now CONNECTED_LOCAL
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  Policy set 'DDW365CB 1' (wlxf4f26d17b7ea) as default for IPv4 routing and DNS.
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  DNS: starting dnsmasq...
Feb  1 11:43:19 arcane NetworkManager[699]: <warn>  dnsmasq not available on the bus, can't update servers.
Feb  1 11:43:19 arcane NetworkManager[699]: <error> [1454344999.787276] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Feb  1 11:43:19 arcane NetworkManager[699]: <warn>  DNS: plugin dnsmasq update failed
Feb  1 11:43:19 arcane NetworkManager[699]: <info>  Writing DNS information to /sbin/resolvconf
Feb  1 11:43:21 arcane NetworkManager[699]: <info>  (wlxf4f26d17b7ea): Activation: successful, device activated.
Feb  1 11:43:21 arcane NetworkManager[699]: <info>  startup complete
Feb  1 11:43:21 arcane NetworkManager[699]: <warn>  dnsmasq appeared on DBus: :1.23
Feb  1 11:43:21 arcane NetworkManager[699]: <info>  Writing DNS information to /sbin/resolvconf
Feb  1 11:43:21 arcane systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  1 11:43:21 arcane systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  1 11:43:22 arcane whoopsie[695]: [11:43:22] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb  1 11:43:22 arcane whoopsie[695]: [11:43:22] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb  1 11:43:22 arcane whoopsie[695]: [11:43:22] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb  1 11:43:25 arcane NetworkManager[699]: <info>  WiFi hardware radio set enabled
Feb  1 11:43:25 arcane NetworkManager[699]: <info>  WWAN hardware radio set enabled
Feb  1 11:44:19 arcane ureadahead[219]: ureadahead:network: Ignored relative path
Feb  1 11:44:19 arcane ureadahead[219]: ureadahead:NetworkManager_new.934: Ignored relative path
Feb  1 11:44:19 arcane ureadahead[219]: ureadahead:NetworkManager: Ignored relative path
Feb  1 11:44:19 arcane ureadahead[219]: message repeated 3 times: [ ureadahead:NetworkManager: Ignored relative path]
Feb  1 11:44:19 arcane ureadahead[219]: ureadahead:NetworkManager_new.984: Ignored relative path
Feb  1 11:44:19 arcane ureadahead[219]: ureadahead:NetworkManager: Ignored relative path
Feb  1 11:44:19 arcane ureadahead[219]: message repeated 2 times: [ ureadahead:NetworkManager: Ignored relative path]

```

and repeated in kernel logs: ```

Feb  1 11:42:27 arcane kernel: [39704.507487] IPv6: ADDRCONF(NETDEV_CHANGE): wlxf4f26d17b7ea: link becomes ready
Feb  1 11:42:34 arcane kernel: [39711.678322] wlxf4f26d17b7ea: deauthenticated from 54:35:30:24:c5:ef (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
Feb  1 11:42:35 arcane kernel: [39711.856021] cfg80211: World regulatory domain updated:
Feb  1 11:42:35 arcane kernel: [39711.856024] cfg80211:  DFS Master region: unset
Feb  1 11:42:35 arcane kernel: [39711.856025] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb  1 11:42:35 arcane kernel: [39711.856027] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.856028] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.856029] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.856031] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.856032] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb  1 11:42:35 arcane kernel: [39711.856034] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Feb  1 11:42:35 arcane kernel: [39711.856035] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.856036] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.858889] cfg80211: Regulatory domain changed to country: US
Feb  1 11:42:35 arcane kernel: [39711.858892] cfg80211:  DFS Master region: FCC
Feb  1 11:42:35 arcane kernel: [39711.858894] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb  1 11:42:35 arcane kernel: [39711.858896] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.858897] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.858899] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
Feb  1 11:42:35 arcane kernel: [39711.858900] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
Feb  1 11:42:35 arcane kernel: [39711.858901] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Feb  1 11:42:38 arcane kernel: [39715.355393] wlxf4f26d17b7ea: authenticate with 54:35:30:24:c5:ef
Feb  1 11:42:38 arcane kernel: [39715.632860] wlxf4f26d17b7ea: send auth to 54:35:30:24:c5:ef (try 1/3)
Feb  1 11:42:38 arcane kernel: [39715.635127] wlxf4f26d17b7ea: authenticated
Feb  1 11:42:38 arcane kernel: [39715.639245] wlxf4f26d17b7ea: associate with 54:35:30:24:c5:ef (try 1/3)
Feb  1 11:42:38 arcane kernel: [39715.642924] wlxf4f26d17b7ea: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=5)
Feb  1 11:42:38 arcane kernel: [39715.652328] wlxf4f26d17b7ea: associated
Feb  1 11:42:45 arcane kernel: [39722.775342] wlxf4f26d17b7ea: deauthenticated from 54:35:30:24:c5:ef (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
Feb  1 11:42:46 arcane kernel: [39722.949063] cfg80211: World regulatory domain updated:
Feb  1 11:42:46 arcane kernel: [39722.949066] cfg80211:  DFS Master region: unset
Feb  1 11:42:46 arcane kernel: [39722.949068] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb  1 11:42:46 arcane kernel: [39722.949070] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.949072] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.949074] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.949076] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.949078] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb  1 11:42:46 arcane kernel: [39722.949080] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Feb  1 11:42:46 arcane kernel: [39722.949082] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.949083] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.955719] cfg80211: Regulatory domain changed to country: US
Feb  1 11:42:46 arcane kernel: [39722.955722] cfg80211:  DFS Master region: FCC
Feb  1 11:42:46 arcane kernel: [39722.955724] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb  1 11:42:46 arcane kernel: [39722.955727] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.955730] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.955732] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
Feb  1 11:42:46 arcane kernel: [39722.955734] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
Feb  1 11:42:46 arcane kernel: [39722.955736] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Feb  1 11:42:53 arcane kernel: [39730.327764] wlxf4f26d17b7ea: authenticate with 54:35:30:24:c5:ef
Feb  1 11:42:53 arcane kernel: [39730.608397] wlxf4f26d17b7ea: send auth to 54:35:30:24:c5:ef (try 1/3)
Feb  1 11:42:53 arcane kernel: [39730.610732] wlxf4f26d17b7ea: authenticated
Feb  1 11:42:53 arcane kernel: [39730.611036] wlxf4f26d17b7ea: associate with 54:35:30:24:c5:ef (try 1/3)
Feb  1 11:42:53 arcane kernel: [39730.614593] wlxf4f26d17b7ea: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=5)
Feb  1 11:42:53 arcane kernel: [39730.623846] wlxf4f26d17b7ea: associated
Feb  1 11:43:00 arcane kernel: [39737.771357] wlxf4f26d17b7ea: deauthenticated from 54:35:30:24:c5:ef (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
Feb  1 11:43:01 arcane kernel: [39737.961114] cfg80211: World regulatory domain updated:
Feb  1 11:43:01 arcane kernel: [39737.961117] cfg80211:  DFS Master region: unset
Feb  1 11:43:01 arcane kernel: [39737.961118] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb  1 11:43:01 arcane kernel: [39737.961120] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.961121] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.961122] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.961124] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.961126] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb  1 11:43:01 arcane kernel: [39737.961127] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Feb  1 11:43:01 arcane kernel: [39737.961128] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.961129] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.967600] cfg80211: Regulatory domain changed to country: US
Feb  1 11:43:01 arcane kernel: [39737.967603] cfg80211:  DFS Master region: FCC
Feb  1 11:43:01 arcane kernel: [39737.967605] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb  1 11:43:01 arcane kernel: [39737.967608] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.967611] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.967614] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
Feb  1 11:43:01 arcane kernel: [39737.967616] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
Feb  1 11:43:01 arcane kernel: [39737.967618] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Feb  1 11:43:02 arcane kernel: [39739.536478] IPv6: ADDRCONF(NETDEV_UP): wlxf4f26d17b7ea: link is not ready
```


**EDIT for extra info:**

Today I had class and I tested it out on the campus's wireless network which does not have a security protocol (just none under the dropdown). The lag I had previously experienced on the game was gone, speed was faster, no host resolve. It seems there is something about the home network and the adapter that aren't working right, so hopefully I can find out what that is. Network works perfectly and finds more network connections in the area than I had available with the mediatek card at campus.

---

### Post by chili555 on 2016-02-01
> It seems there is something about the home network and the adapter that aren't working right, so hopefully I can find out what that is.I concur.

As a coincidence, I received a new router and combined it with the latest DSL modem provided by my ISP during the duration of this thread. I set them up, as I usually recommend to all, as follows:> First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.I was then anxious to try my TL-WN722N. I temporarily blacklisted the driver for my internal device, rebooted and connected perfectly and at N speeds!

I urge you to check and adjust the router settings.

---

### Post by mistcloud-misty on 2016-02-02
Checked the settings and so far they are set as recommended. We have no WPA2-AES setting, only have WPA2-PSK and TKIP so will stick with the PSK right now. Channel is fixed, CRDA also set.

Now I've noticed the majority of 'crashes', DNS and the 4-way handshake time out only occur after having suspended the laptop at some point, both fixed by unplugging the device and replugging it. If on fresh reboot, no crash ever occurs until suspend, but doesn't always occur after a suspend for many hours. As a workaround to avoid those I'll just shut down at night and reboot as necessary after suspend. Wireless worked flawlessly on campus's public network after suspend (as comparison). Network manager crashed after one of the wireless crashes in which it didn't detect the device but works fine afterwards (it was after suspend when I switched from public wireless to home wireless). 

There was a kernel update today and after logging into that kernel there is a little less lag and a few less errors in kernel.

---

### Post by mistcloud-misty on 2016-02-14
Just an update.

I manually set the BSSID to the router address and immediately after, all lag has gone and I haven't had a network crash in over 5 hours. (after the last kernel update I was having network crashes much more often). It's all working a lot smoother now. 

Such a simple fix for such an annoying problem. 

Thanks for your help, the adapter works wonderfully now.

---

### Post by chili555 on 2016-02-14
Awesome! Glad it's working.

---

### Post by mistcloud-misty on 2016-02-14
Welp. It worked for quite a few hours until I had many repeated DNS crashes, and restarting network-manager, switching wireless off/on, and unplugging/replugging the usb only fixed it for 20 minutes or so. Finally I rebooted, and now everything is extremely slow. Full connectivity, 150 mb/s, but everything loads super slow and is really bogged down. 

I ran the wireless script again and now have unsupported characters where the Mac Address should be for the network. I'll add that as an attachment. 

As a side note, this is what I find in kernel logs when DNS goes down: 
```
Feb 14 22:20:57 arcane kernel: [97448.412171] usb 1-3: USB disconnect, device number 14
Feb 14 22:20:57 arcane kernel: [97448.425951] wlxf4f26d17b7ea: deauthenticating from 54:35:30:24:c5:ef by local choice (Reason: 3=DEAUTH_LEAVING)
Feb 14 22:20:58 arcane kernel: [97448.526180] ath: phy9: Chip reset failed
Feb 14 22:20:58 arcane kernel: [97448.526184] ath: phy9: Unable to reset channel (2462 Mhz) reset status -22
Feb 14 22:20:58 arcane kernel: [97448.526186] ath: phy9: Unable to set channel
Feb 14 22:20:58 arcane kernel: [97448.626450] ath: phy9: RX failed to go idle in 10 ms RXSM=0x0
Feb 14 22:20:58 arcane kernel: [97448.636501] ath: phy9: Failed to wakeup in 500us
Feb 14 22:20:58 arcane kernel: [97448.736992] ath: phy9: RX failed to go idle in 10 ms RXSM=0x4074e306
Feb 14 22:20:58 arcane kernel: [97448.747177] ath: phy9: Failed to wakeup in 500us
Feb 14 22:20:58 arcane kernel: [97448.757181] ath: phy9: Failed to wakeup in 500us
Feb 14 22:20:58 arcane kernel: [97449.058748] ath: phy9: RX failed to go idle in 10 ms RXSM=0x306ee306
```

Hopefully there will be a way to get this thing working perfect on my system.

---

### Post by chili555 on 2016-02-15
This may be helpful. I have encountered a couple of cases where continued dropping and reconnecting or repeated attempts to reconnect were solved by adding the BSSID in Network Manager. Please click the NM icon and select 'Edit Connections...' Under wifi, select your connection, DDW365CB 1. Click Edit. In the BSSID space, add the MAC address of your router.

Find it with:```
iwconfig
```Here is a redacted sample from my machine:```
wlp3s0    IEEE 802.11bgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: [COLOR="#FF0000"]xx:2B:B0:DC:45:xx [/COLOR]  
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:128   Missed beacon:0
```Copy the address as it appears exactly into the BSSID space. Save and close the Edit Connections dialog. It may help to restart NM:```
sudo service network-manager restart
```Any improvement?

[http://img.xrmb2.net/images/647404.png](http://img.xrmb2.net/images/647404.png)

---

### Post by mistcloud-misty on 2016-02-15
Hello. The BSSID was set the access point.

Following a guide I removed dns=dnsmasq from a config file and uninstalled resolveconf. Connection improved a lot with less lag and fast loading but DNS resolve continues to drop every 20-30 minutes, though I can easily get it back from reselecting my network from the drop-down list. 

Can't seem to find anything in logs, dmesg, or network logs about what is going on.

---

### Post by chili555 on 2016-02-15
> Can't seem to find anything in logs, dmesg, or network logs about what is going on. May we have a peek?```
cat /var/log/syslog | grep -e etwork -e wlp | tail -n20
```Paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Ideally, taken soon after a drop.

---

### Post by mistcloud-misty on 2016-02-15
[http://paste.ubuntu.com/15085590/](http://paste.ubuntu.com/15085590/)

That was taken immediately when the DNS went down.

And just as comparison, this is immediately after manually disconnecting and reconnecting the internet through the network manager icon.

[http://paste.ubuntu.com/15085637/](http://paste.ubuntu.com/15085637/)

---

### Post by chili555 on 2016-02-15
I see this in both:> Feb 15 16:29:26 arcane whoopsie[619]: [16:29:26] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Feb 15 16:29:26 arcane whoopsie[619]: [16:29:26] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Feb 15 16:29:26 arcane whoopsie[619]: [16:29:26] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
The explanation of *whoopsie* is here: [http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it](http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it)> What's whoopsie ?

    It's the "Ubuntu Error Reporting" daemon, and is installed by default in both desktop/server installations.

    When something crashes, whoopsie does two things:
        Collects the crash report generated by Apport and
        Can send them to Ubuntu/Canonical (specifically to [https://daisy.ubuntu.com](https://daisy.ubuntu.com) :)
OT: whoopsie > daisy! Hahahaha!!

So, it seems that something in Network Manager is not operating as expected and is, in fact, crashing.

We could uninstall and purge NM and all it's configuration files and then reinstall. Or, if this is a stay-at-home computer that doesn't need the ability to roam to the coffee shop, library, etc., we can remove NM and configure manually. I will be happy to assist in either case. What is your choice?

By the way, here is a ping test of your DNS nameserver:```
chili@T440p:~$ ping -c3 209.18.47.62
PING 209.18.47.62 (209.18.47.62) 56(84) bytes of data.
64 bytes from 209.18.47.62: icmp_seq=1 ttl=49 time=75.2 ms
64 bytes from 209.18.47.62: icmp_seq=2 ttl=49 time=50.6 ms
64 bytes from 209.18.47.62: icmp_seq=3 ttl=49 time=61.0 ms

--- 209.18.47.62 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 50.622/62.303/75.231/10.089 ms

```And mine:```
chili@T440p:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=55 time=20.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=55 time=19.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=55 time=22.7 ms
```In either case, you could certainly find faster DNS nameservers than you currently use.

---

### Post by mistcloud-misty on 2016-02-15
The first option would be best because I use this computer at campus to do work and I have a computing class where I need the wireless to work also. 

In regards to the nameserver I did try changing it to google's public server which sped things up but the crashes still occurred on it. 

I'd be happy to try and purge network manager and hope a reinstall fixes the problems.

---

### Post by chili555 on 2016-02-15
Please see if this package is installed on your system:

```
sudo dpkg -s network-manager-gnome

```
Now, download this package to your desktop: [http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_1.0.4-0ubuntu5_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_1.0.4-0ubuntu5_amd64.deb) If the package network-manager-gnome is found to be installed, then this one, too: [http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.10.1-0ubuntu7_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.10.1-0ubuntu7_amd64.deb)

Now purge the existing packages:

```
sudo apt-get purge network-manager
sudo apt-get purge network-manager-gnome  [COLOR="#FF0000"]<--Only if it was found to be installed[/COLOR]

```
Now, double-check for left-overs:

```
ls /etc/  | grep -i network

```
If you see a directory called NetworkManager, remove it:

```
sudo rm -rf /etc/NetworkManager
```

Be careful and proofread carefully. rm -rf is all-powerful, absolute and unforgiving. 

Next, I suggest you reboot. You will, of course, temporarily have no connectivity until we reinstall:

```
cd ~/Desktop
sudo dpkg -i network*.deb
```

You might get it to start with:

```
sudo service network-manager start

```
It may take a reboot.

Any improvement?

---

### Post by mistcloud-misty on 2016-02-15
I connected fast, however the problems still occur. Logs:
[http://paste.ubuntu.com/15087818/](http://paste.ubuntu.com/15087818/)

I needed both packages by the way.

---

### Post by chili555 on 2016-02-15
Interesting. May I see:```
cat /var/log/syslog | grep whoopsie | tail -n20
```Interesting that daisy doesn't appear to be on line now:```
chili@T440p:~$ ping -c3 daisy.ubuntu.com
PING daisy.ubuntu.com (91.189.92.57) 56(84) bytes of data.

--- daisy.ubuntu.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```The plot thickens.

Is the connectivity better, worse or the same?

---

### Post by mistcloud-misty on 2016-02-15
[http://paste.ubuntu.com/15087912/](http://paste.ubuntu.com/15087912/)

As for the connectivity speed, it was great until I rebooted (wanted the network icon in the top tray) and now it's much slower. BUT it hasn't crashed so far on this reboot despite the bad speed.

EDIT: About as soon as I posted this the DNS crashed.

---

### Post by chili555 on 2016-02-16
I am starting to believe that the whoopsie is simply that daisy is not available at the moment and that NM is trying and failing to get through.>     EDIT: About as soon as I posted this the DNS crashed.I am still not quite sure what is actually going wrong here. What do you mean by DNS crash? That you try to load a web page and it tries and tries and never quite gets there? Or do you get a 404 server not found? Or a 'check your connection'? Or...what?

When such things happen, can you ping your router?```
ping -c3 192.168.0.1
```If you get ping returns, you are still connected wirelessly to the router and the trouble is upstream.

Can you, at the time of a "DNS crash", ping your DNS nameserver?```
ping -c3 8.8.8.8
```If you get ping returns, you are still connected to the internet and the trouble is still further upstream.

Can you ping a known working website by name, requiring the use of DNS name resolution?```
ping -c3 www.ubuntu.com
```Where is the actual break in the chain?> Following a guide I removed dns=dnsmasq from a config file and uninstalled resolveconf. I doubt this will be helpful in the long run. In most cases, dnsmasq is faster once a cache is built.

---

### Post by mistcloud-misty on 2016-02-16
When it goes down, Firefox is stuck on 'looking up' the website until it times out and gives a server not found error. Chrome is stuck on 'resolving host' until it times out and gives me a name error. Both are only resolvable by refreshing the internet connection in one way or the other for a short time.

Pinging the router and m DNS server both worked at the time it was down. 

I was unable to ping an actual web address such as ubuntu.com, however. 
ping: unknown host [www.ubuntu.com](www.ubuntu.com)

I am getting weird notifications about being connected to the ethernet when there isn't a single ethernet cable around.

---

### Post by chili555 on 2016-02-16
> Pinging the router and m DNS server both worked at the time it was down.

I was unable to ping an actual web address such as ubuntu.com, however.
ping: unknown host [www.ubuntu.com](www.ubuntu.com)Weird! 

Since you removed dnsmasq, I assume that the DNS nameservers are declared in /etc/resolv.conf. May we have a look?```
cat /etc/resolv.conf
ls -al /etc/resolv.conf
```When it is working and again when it is "crashed," may we see:```
dig www.ubuntu.com

```The guys in the back room are so mean, they always refer me to the hardest cases.

---

### Post by mistcloud-misty on 2016-02-16
Working:
```
dig www.ubuntu.com

; <<>> DiG 9.9.5-11ubuntu1.2-Ubuntu <<>> www.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3491
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;www.ubuntu.com.            IN    A

;; ANSWER SECTION:
www.ubuntu.com.        195    IN    A    91.189.89.103

;; Query time: 47 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Feb 16 16:23:07 EST 2016
;; MSG SIZE  rcvd: 59


```

Down:
```
dig www.ubuntu.com

; <<>> DiG 9.9.5-11ubuntu1.2-Ubuntu <<>> www.ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```

And the other two commands.

```
arcane@arcane:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.1.1
arcane@arcane:~$ ls -al /etc/resolv.conf
-rw-r--r-- 1 root root 51 Feb 16 16:38 /etc/resolv.conf

```

---

### Post by chili555 on 2016-02-16
> ;; Query time: 47 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Feb 16 16:23:07 EST 2016and.....> arcane@arcane:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.1.1These settings are typical of a system running and using dnsmasq, some of which you have removed; evidently not all.

Please do:```
sudo gedit /etc/resolv.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the file to read:```
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 192.168.0.1
```Proofread carefully, save and close the text editor.

Test for a while. If the problem persists, again let us see:```
dig www.ubuntu.com
```

---

### Post by mistcloud-misty on 2016-02-16
Same problem but seems to take longer before the DNS occurs.

Connection in general has greatly improved. 

```

; <<>> DiG 9.9.5-11ubuntu1.2-Ubuntu <<>> www.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62951
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 8192
;; QUESTION SECTION:
;www.ubuntu.com.            IN    A

;; ANSWER SECTION:
www.ubuntu.com.        60    IN    A    91.189.89.115

;; Query time: 67 msec
;; SERVER: 209.18.47.62#53(209.18.47.62)
;; WHEN: Tue Feb 16 17:20:41 EST 2016
;; MSG SIZE  rcvd: 59

```

---

### Post by mistcloud-misty on 2016-02-17
I was reading around a bit on DNS in Ubuntu and I came across some configurations for a certain file- network interfaces. I do not know much about how important the file is for my specific connections, but I've noticed a few people add their nameservers and other network information to the file, yet when I check what is already in the file on my computer it only contains this information:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

Does that matter at all or is it only used for 'servers'?

---

### Post by chili555 on 2016-02-17
It is typically only used for servers, however, it may be used anywhere. Usually, either Network Manager does the work for us, automatically, or /etc/network/interfaces, manually, but not both.

One of my desktop machines has NM removed and all details included in /etc/network/interfaces. I am not dragging my NUC and 24" monitor down to the coffee shop to connect. It will only be connected at my home, so I removed NM and its overhead.

There is no reason for you to disturb the file.

I still know no reason for what is going wrong here or what to do about it.

---

### Post by mistcloud-misty on 2016-02-17
Thanks for explaining that file. 

I checked my logs again, and I finally found something, in the syslogs. I thought I checked them but either I checked the wrong one (there are older versions) or missed it altogether, I'm not sure. There is a massive amount of spam in that from zeitgeist and others but the thing I found most interesting/related, or just confusing really, is the far bottom. I posted it on the pastebin, and included the time from when I last connected to the internet after a crash to the next crash. 

[http://paste.ubuntu.com/15103904/](http://paste.ubuntu.com/15103904/)

Might also explain why I keep getting notifications for ethernet being connected when I'm not connected to an ethernet network. Hopefully this is something that can be resolvable. Since this is a fresh install I haven't changed anything other than what was mentioned in this thread for internet settings, so I'm note quite sure why these errors are occurring and what to do with them.

---

### Post by chili555 on 2016-02-17
You have a whole array of things going on here:> Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Feb 17 18:52:33 arcane gnome-session[1362]: Please ask your system administrator to enable user sharing.And this:> (nautilus:1502): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/arcane/.local/share/recently-used.xbel', but the parser failed: Failed to open fileAnd this:> org.gnome.zeitgeist.Engine[1228]: #033[31m[23:52:46.401805 WARNING]#033[0m sql.vala:350: sql.vala:293: Can't commit transaction: 5, cannot commit transaction - SQL statements in prAnd, most importantly to networking, this:> Feb 17 18:54:49 arcane dhclient: DHCPDISCOVER on wlxf4f26d17b7ea to 255.255.255.255 port 67 interval 15 (xid=0x9773c564)
Feb 17 18:54:49 arcane dhclient: send_packet: No such device or address
Feb 17 18:54:49 arcane dhclient: dhclient.c:2094: Failed to send 300 byte long packet over wlxf4f26d17b7ea interface.
Feb 17 18:54:53 arcane dhclient: DHCPDISCOVER on enp2s0 to 255.255.255.255 port 67 interval 3 (xid=0x7b638069)
Feb 17 18:54:56 arcane dhclient: DHCPDISCOVER on enp2s0 to 255.255.255.255 port 67 interval 8 (xid=0x7b638069)
Feb 17 18:55:04 arcane dhclient: DHCPDISCOVER on enp2s0 to 255.255.255.255 port 67 interval 16 (xid=0x7b638069)
Feb 17 18:55:04 arcane dhclient: DHCPDISCOVER on wlxf4f26d17b7ea to 255.255.255.255 port 67 interval 16 (xid=0x9773c564)
Feb 17 18:55:04 arcane dhclient: send_packet: No such device or address
Feb 17 18:55:04 arcane dhclient: dhclient.c:2094: Failed to send 300 byte long packet over wlxf4f26d17b7ea interface.Frankly, I'd seriously consider a reinstall. You could certainly try the live DVD or USB and see if everything works as expected. If so, I'd back up and reinstall. My last clean install, about a month ago, took about 15 minutes.

Yes, I know; I'm a compulsive tinkerer and I *like* to reinstall once in a while!

---

### Post by mistcloud-misty on 2016-02-17
Tested out on USB for an hour before reinstalling, no DNS issues (the  shared file error still appears in logs but doesn't seem to do anything  but complain). 

Unfortunately I've had some DNS problems after  installing, after doing some of the updates. Only once so far, but there  was no error from dhclient like before in syslogs. 

Instead, I get this in kernel logs between the downfall: ```

Feb  18 03:13:09 arcane-X555LB kernel: [   11.838414] audit: type=1400  audit(1455783187.649:2): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session"  pid=581 comm="apparmor_parser"
Feb 18 03:13:09 arcane-X555LB kernel:  [   11.838425] audit: type=1400 audit(1455783187.649:3):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="chromium" pid=581 comm="apparmor_parser"
Feb 18 03:13:09  arcane-X555LB kernel: [   11.850816] audit: type=1400  audit(1455783187.661:4): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/sbin/dhclient" pid=581  comm="apparmor_parser"
Feb 18 03:13:09 arcane-X555LB kernel: [    11.850833] audit: type=1400 audit(1455783187.661:5): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581  comm="apparmor_parser"
Feb 18 03:13:09 arcane-X555LB kernel: [    11.850837] audit: type=1400 audit(1455783187.661:6): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=581  comm="apparmor_parser"
Feb 18 03:13:09 arcane-X555LB kernel: [    11.850841] audit: type=1400 audit(1455783187.661:7): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="/usr/lib/connman/scripts/dhclient-script" pid=581  comm="apparmor_parser"
Feb 18 03:13:09 arcane-X555LB kernel: [    12.007886] audit: type=1400 audit(1455783187.817:8): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="/usr/bin/evince"  pid=581 comm="apparmor_parser"
Feb 18 03:13:09 arcane-X555LB kernel:  [   12.007903] audit: type=1400 audit(1455783187.817:9):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="sanitized_helper" pid=581 comm="apparmor_parser"
Feb 18  03:13:09 arcane-X555LB kernel: [   12.007908] audit: type=1400  audit(1455783187.817:10): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/bin/evince-previewer" pid=581  comm="apparmor_parser"
Feb 18 03:13:09 arcane-X555LB kernel: [    12.007911] audit: type=1400 audit(1455783187.817:11): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="sanitized_helper"  pid=581 comm="apparmor_parser"

```

Not sure if that's actually an error or not of course. 

This  is in dmesg at the time of the problem: perf interrupt took too long  (2507 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

Also not sure if related because I used to get those before without any seeming problems...

And the dns tail of syslogs: 
```
 cat /var/log/syslog | grep -e ath -e dns | tail -n20
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:.: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: message repeated 18 times: [ ureadahead:.: Ignored relative path]
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:NetworkManager: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: message repeated 3 times: [ ureadahead:NetworkManager: Ignored relative path]
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:NetworkManager_new.978: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:.: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: message repeated 18 times: [ ureadahead:.: Ignored relative path]
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:NetworkManager: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: message repeated 2 times: [ ureadahead:NetworkManager: Ignored relative path]
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:.xsession-errors: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:.: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:tracing_on: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:events/fs/open_exec/enable: Ignored relative path
Feb 17 22:14:01 arcane-X555LB ureadahead[228]: ureadahead:events/fs/do_sys_open/enable: Ignored relative path
Feb 17 22:15:16 arcane-X555LB systemd[817]: Stopped target Paths.
Feb  17 22:28:01 arcane-X555LB systemd-tmpfiles[6483]:  [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log",  ignoring.
Feb 17 22:37:59 arcane-X555LB dnsmasq[933]: setting upstream servers from DBus
Feb 17 22:38:03 arcane-X555LB dnsmasq[933]: setting upstream servers from DBus
Feb 17 22:38:03 arcane-X555LB dnsmasq[933]: using nameserver 209.18.47.62#53
Feb 17 22:38:03 arcane-X555LB dnsmasq[933]: using nameserver 209.18.47.61#53

```

I'm hoping that's just a one time problem as opposed to a recurrence of all the problems as before.

---

### Post by mistcloud-misty on 2016-02-19
I believe the problem is solved now.

After the printer went 'missing' while still connected to the wifi (via DNSSD or something), and my mother's laptop began having problems, I decided a hard reboot was in order for the modem. The "reboot" in the config settings doesn't seem to do anything at all, since I used that a few times to no avail, so I did what people said worked best for the Time Warner Cable modem and unplugged it for 5 minutes before plugging it back in. All lag, connection issues, and DNS failures are resolved. The printer immediately printed what was sitting in the queue for the past few days when no one could find it. My ping results are much faster now as well. 
```
arcane@arcane-X555LB:~$ ping -c5 209.18.47.62
PING 209.18.47.62 (209.18.47.62) 56(84) bytes of data.
64 bytes from 209.18.47.62: icmp_seq=1 ttl=57 time=27.1 ms
64 bytes from 209.18.47.62: icmp_seq=2 ttl=57 time=27.1 ms
64 bytes from 209.18.47.62: icmp_seq=4 ttl=57 time=29.6 ms
64 bytes from 209.18.47.62: icmp_seq=5 ttl=57 time=27.3 ms

--- 209.18.47.62 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4012ms
rtt min/avg/max/mdev = 27.127/27.823/29.672/1.070 ms

```

and

```
ping -c5 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=53 time=172 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=53 time=33.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=53 time=33.4 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=53 time=33.1 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=53 time=33.8 ms

--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 33.104/61.223/172.345/55.561 ms

```

Much faster than my 200-400 ms for both servers that it was before. 

Downloads speeds and upload speeds which were randomly around 1.7 and 0.8 after reinstall are now back to normal (30 and 6) respectively. 

It seems a very odd coincidence that the modem caused problems as soon as I plugged in a new adapter. Ah well.

Thanks so much for your help!

---

### Post by chili555 on 2016-02-19
I'm very glad it's working.> It seems a very odd coincidence that the modem caused problems as soon as I plugged in a new adapter.If the issues return, I suggest that you call TWC and report that their cable modem is defective and that you'd appreciate a new one, at their expense, of course.

---

