---
title: "Strange unable to connect with Intel 3945ABG"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Simimi on 2008-05-31
I recently installed Hardy on a friend's laptop only to see that the wireless isn't working. This is odd for me because the drivers and everything seem to be there and working and what not. Basically, we can not connect to anything, not even an open network with no security on it. I have tried 4 other threads in the forums and nothing seems to resolve the problem. We have a fresh, fully updated install of Hardy and are coming here fresh for help and ideas as to what this issue could be.

Here is some of the relevant information that I think will help with the issue at hand: We can not connect/use the wireless connection.

```

lshw:

*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:54:ed:f9
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```
```

ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:54:ed:f9  
          inet6 addr: fe80::21c:bfff:fe54:edf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:13977 (13.6 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:bf:54:ed:f9  
          inet addr:169.254.11.40  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-54-ED-F9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```

iwconfig

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"OurPlace"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0B:B4:EE:11:4D   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:3939-3939-3936-3636-3636
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

lspci -v

07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 135d
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at f4300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

```

Basically, everything shows up in network manager and such, (though on my machine I can detect networks, but this machine does not seem to do that, even when in roaming mode). We are using WEP for our security, though even testing on an open network didn't work. I know the network is ok because we can connect with anything else (psp, ps3, my gentoo notebook, etc).

Let me know if you would like anything else, here is a quick bit of information I grabbed from  /var/log/messages | grep iwl

```

 /var/log/messages | grep iwl

May 31 07:57:16 ubuntu kernel: [   30.052423] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 07:57:16 ubuntu kernel: [   30.052426] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 07:57:16 ubuntu kernel: [   30.052618] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 07:57:16 ubuntu kernel: [   30.995270] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 01:04:37 ubuntu kernel: [   29.579868] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 01:04:37 ubuntu kernel: [   29.579872] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 01:04:37 ubuntu kernel: [   29.580011] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 01:04:37 ubuntu kernel: [   30.784480] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 01:29:30 ubuntu kernel: [   31.993087] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 01:29:30 ubuntu kernel: [   31.993091] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 01:29:30 ubuntu kernel: [   31.993224] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 01:29:30 ubuntu kernel: [   32.894372] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 10:02:20 ubuntu kernel: [   30.458874] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 10:02:20 ubuntu kernel: [   30.458876] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 10:02:20 ubuntu kernel: [   30.459024] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 10:02:20 ubuntu kernel: [   31.117202] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 10:54:35 ubuntu kernel: [  146.791841] iwl3945: Radio Frequency Kill Switch is On:
May 31 10:54:58 ubuntu kernel: [  151.445324] iwl3945: Radio Frequency Kill Switch is On:
May 31 10:57:48 ubuntu kernel: [  190.652499] iwl3945: Radio Frequency Kill Switch is On:
May 31 11:50:39 ubuntu kernel: [ 3066.115583] iwl3945: Radio Frequency Kill Switch is On:
May 31 12:18:05 ubuntu kernel: [   30.973712] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 12:18:05 ubuntu kernel: [   30.973716] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 12:18:05 ubuntu kernel: [   30.973852] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 12:18:05 ubuntu kernel: [   31.757780] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 12:18:53 ubuntu kernel: [   56.045089] iwl3945: Radio Frequency Kill Switch is On:
May 31 14:41:35 ubuntu kernel: [   31.757490] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 14:41:35 ubuntu kernel: [   31.757494] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 14:41:35 ubuntu kernel: [   31.757650] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 14:41:35 ubuntu kernel: [   32.905906] iwl3945: Radio Frequency Kill Switch is On:
May 31 14:41:35 ubuntu kernel: [   32.911055] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 14:41:35 ubuntu kernel: [   32.921060] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 14:41:35 ubuntu kernel: [   32.940985] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 14:41:35 ubuntu kernel: [   32.968233] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 14:41:35 ubuntu kernel: [   32.988171] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 16:24:24 ubuntu kernel: [  354.377805] iwl3945: Radio Frequency Kill Switch is On:
May 31 20:40:07 ubuntu kernel: [   39.340542] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 20:40:07 ubuntu kernel: [   39.340545] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 20:40:07 ubuntu kernel: [   39.340675] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 20:40:07 ubuntu kernel: [   40.023935] iwl3945: Radio Frequency Kill Switch is On:
May 31 20:40:07 ubuntu kernel: [   40.029119] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:40:07 ubuntu kernel: [   40.039139] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:40:07 ubuntu kernel: [   40.059080] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:40:07 ubuntu kernel: [   40.086354] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:40:07 ubuntu kernel: [   40.106276] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 21:16:12 ubuntu kernel: [  186.964934] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
May 31 21:16:12 ubuntu kernel: [  186.964950] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 21:16:12 ubuntu kernel: [  186.965110] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 21:16:12 ubuntu kernel: [  187.053332] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
May 31 21:16:12 ubuntu kernel: [  187.054325] Registered led device: iwl-phy1:RX
May 31 21:16:12 ubuntu kernel: [  187.054344] Registered led device: iwl-phy1:TX
May 31 21:16:15 ubuntu kernel: [  188.363991] Registered led device: iwl-phy1:RX
May 31 21:16:15 ubuntu kernel: [  188.364036] Registered led device: iwl-phy1:TX
May 31 21:16:17 ubuntu kernel: [  189.638366] Registered led device: iwl-phy1:RX
May 31 21:16:17 ubuntu kernel: [  189.638394] Registered led device: iwl-phy1:TX
May 31 21:16:51 ubuntu kernel: [  195.880313] Registered led device: iwl-phy1:RX
May 31 21:16:51 ubuntu kernel: [  195.880342] Registered led device: iwl-phy1:TX
May 31 21:16:54 ubuntu kernel: [  197.625701] Registered led device: iwl-phy1:RX
May 31 21:16:54 ubuntu kernel: [  197.625720] Registered led device: iwl-phy1:TX
May 31 21:16:56 ubuntu kernel: [  198.853148] Registered led device: iwl-phy1:RX
May 31 21:16:56 ubuntu kernel: [  198.853166] Registered led device: iwl-phy1:TX
May 31 21:17:20 ubuntu kernel: [  202.412216] Registered led device: iwl-phy1:RX
May 31 21:17:20 ubuntu kernel: [  202.412246] Registered led device: iwl-phy1:TX
May 31 21:17:22 ubuntu kernel: [  203.547342] Registered led device: iwl-phy1:RX
May 31 21:17:22 ubuntu kernel: [  203.547360] Registered led device: iwl-phy1:TX

```

I am not sure if the problem lies in the messages log, I do see those big WARNING signs though... If any more information is needed, please do ask, we would both love to see this one resolved.

Thanks in advance!:popcorn:

---

### Post by chili555 on 2008-05-31
I see a few issues here. First is:> Radio Frequency Kill Switch is OnIs there a switch or key combination that turns the wireless on and off on your laptop (he asks, retoricaly)? Open a terminal and do:```
sudo tail -f /var/log/messages
```Move the switch or manipulate the keys until *messages* reports the kill switch is off.

Next, I see:> Encryption key:3939-3939-3936-3636-3636I trust this is not your real key and, especially, not its length. 
# 40-or 64-bit ASCII WEP code has 5 characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters
As you can see, no WEP key has 20 characters.

Finally, what does this command tell us?```
sudo iwlist wlan0 scan
```

---

### Post by ugm6hr on 2008-05-31
Consider the Windows power saving factor too:
Point 8 from [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

---

### Post by Simimi on 2008-05-31
Here is the messages output with my own comments:
```

/var/log/messages

Jun  1 11:32:29 ubuntu kernel: [  122.031000] Registered led device: iwl-phy0:RX
Jun  1 11:32:29 ubuntu kernel: [  122.031045] Registered led device: iwl-phy0:TX
Jun  1 11:33:07 ubuntu kernel: [  126.525344] iwl3945: Radio Frequency Kill Switch is On:
Jun  1 11:33:07 ubuntu kernel: [  126.525350] Kill switch must be turned off for wireless networking to work.
Jun  1 11:33:11 ubuntu kernel: [  127.033505] Registered led device: iwl-phy0:RX
Jun  1 11:33:11 ubuntu kernel: [  127.033535] Registered led device: iwl-phy0:TX
Jun  1 11:33:15 ubuntu kernel: [  127.450036] iwl3945: Radio Frequency Kill Switch is On:
Jun  1 11:33:15 ubuntu kernel: [  127.450041] Kill switch must be turned off for wireless networking to work.
Jun  1 11:33:19 ubuntu kernel: [  127.840642] Registered led device: iwl-phy0:RX
Jun  1 11:33:19 ubuntu kernel: [  127.840687] Registered led device: iwl-phy0:TX
Jun  1 11:37:12 ubuntu kernel: [  150.502317] ACPI: PCI interrupt for device 0000:07:00.0 disabled
Jun  1 11:37:12 ubuntu kernel: [  150.572213] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 19 (level, low) -> IRQ 19
Jun  1 11:37:12 ubuntu kernel: [  150.595881] Registered led device: iwl-phy0:RX
Jun  1 11:37:12 ubuntu kernel: [  150.595900] Registered led device: iwl-phy0:TX
Jun  1 11:37:12 ubuntu kernel: [  150.599925] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  1 11:37:12 ubuntu kernel: [  150.608879] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  1 11:37:15 ubuntu kernel: [  153.616123] sky2 eth0: disabling interface
Jun  1 11:37:15 ubuntu kernel: [  153.639313] sky2 eth0: enabling interface
Jun  1 11:37:16 ubuntu kernel: [  153.643547] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  1 11:37:17 ubuntu kernel: [  155.311805] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jun  1 11:37:17 ubuntu kernel: [  155.314040] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  1 11:37:22 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun  1 11:37:22 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun  1 11:37:22 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  1 11:37:22 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  1 11:37:22 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun  1 11:37:34 ubuntu kernel: [  158.895037] sky2 eth0: Link is down.

```

As you can see messages never reports the kill switch as off, only that it says it needs to be off. In the left position I get that it is on, but on the other position I get that kill switch must be off, and then registering led device.

Our Wireless is WEP with a 10 digit numerical key. I changed to the hex setting and I... just noticed it is working for the moment... I hope it stays up after a reboot. Let me try!

EDIT: After reboot the wireless light is blue and I do not have the killswtich error in the messages log, but it does not work now... everything appears the same, the manual network config is the same as well.

Even now when it is not working the iwlist scan gives what appears to be the same information:
```

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:B4:EE:11:4D
                    ESSID:"OurPlace"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=88/100  Signal level=-45 dBm  Noise level=-71 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000011fdc1a991

```
I wonder if I have to do something odd, like retype the password into the manual config settings so it restarts the interface? No auto-connect? ifup says the card is configured...

EDIT2: Ok, retyping the password does nothing, dhclient wlan0 does nothing, when I restart iwconfig does not show an ESSID in the information but Manual Config for Network Manager does... if I do sudo iwconfig wlan0 essid "blah" then the light turns blue again, but I still have no connection... more ideas? It was working so the problem was fixed somewhere...

---

### Post by chili555 on 2008-06-01
Please try:```
sudo iwconfig wlan0 essid OurPlace
sudo iwconfig wlan0 key <ur_10_character_key>
sudo dhclient wlan0
```Did you connect?

In Network Manager, you should be able to see your ESSID, OurPlace, click on it, put in your 10-character key in WEP/hex and connect.

If this is a stay-at-home computer, you might consider disabling or uninstalling NM and hard-coding these details in */etc/network/interfaces.*

---

### Post by Simimi on 2008-06-01
Doing that produces the following:
```

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:bf:54:ed:f9
Sending on   LPF/wlan0/00:1c:bf:54:ed:f9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
It is as if the request is falling on deaf ears! But we have:
```

iwconfig

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"OurPlace"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Ideas? It worked once before so we know it works, but that working state didn't persist after the reboot.

EDIT: On my machine I see networks when I click the NM applet, this one does not see anything... at least not the bright orange displays mine has. I seem to recall when another person was working on it they did something like modprobe  <driver name> hardware_scan=1 or somesuch... but this machine never did have the networks shown in the NM applet.

EDIT2: We know the router is working because we are using it for the eth0 connection we are on now, and the psp and can still use the same wireless connection.

---

### Post by chili555 on 2008-06-01
> we are using it for the eth0 connection we are on nowPlease see here: [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager) especially this: > The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themIt seems that the reason your wireless may not be working is that you are being "managed." Please detach the wire, do:```
sudo /etc/init.d/networking restart
```Now can you see and click on OurPlace? If not, does this sequence produce a different result?```
sudo iwconfig wlan0 essid OurPlace
sudo iwconfig wlan0 key <ur_10_character_key>
sudo dhclient wlan0
```

---

### Post by Simimi on 2008-06-01
Ok That worked great, wireless is a go-go again! Now, what can we do such that this persists between shutdowns and restarts, and allows us to manually change to other wireless networks? I would hate to have to throw those 4 commands at the command line every time we want to turn it on. I wouldn't mind but this is for a brand new user coming over from Vista and I insured a smooth experience.

---

### Post by chili555 on 2008-06-01
> Now, what can we do such that this persists between shutdowns and restarts, and allows us to manually change to other wireless networks?That's a trick, isn't it? This is what I do, and I'm sure it's not the most elegant solution.

As my laptop is a stay-at-home computer 95% of the time, I have uninstalled Network Manager and installed Wicd. I amended */etc/network/interfaces* to look like:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid mylilrouter
wireless-key 0987654321
```I connect automagically at home.

If I am travelling to another location, before I pack up my laptop, I comment out the essid and key lines, like this:```
auto eth1
iface eth1 inet dhcp
#wireless-essid mylilrouter
#wireless-key 0987654321
```Then, when I get to the hotel, university or coffee shop, I click on Wicd, select a network and connect.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Simimi on 2008-06-01
The problem is that as soon as I restarted... following those same steps does not get my a DHCP Answer or an IP. From a cold boot up, restarting the init.d/network daemon, and doing the same steps for iwconfig do not produce the same results as before...

What now? Something is seriously off here.

EDIT: After fooling with it it turns out we have to...
```

sudo /etc/init.d/networking restart
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid OurPlace
sudo iwconfig wlan0 key 9999966666
sudo dhclient wlan0

```

This is really odd but I'm not going to argue with results... Can we automate this? This computer mostly stays at home on this network, but it won't be that way for long. Soon it will be traveling around and moving someplace else where it will have a new network to live on and this is a newbies' newbie's computer here. If it were mine I wouldn't care, but I am hoping to find an elegant, non-intrusive solution.

---

