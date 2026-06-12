---
title: "TL-WN723N v.3-RTL8188EU"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by ANSELM_KEREM on 2014-05-07
Hello,
[FONT=verdana]&#8203;[/FONT]
I have tried vary of solutions to run tl-wn723 v.3 in lubuntu14.04lts.
Downloaded rtl8188eu-master.zip and completed installation steps by

make
sudo make install

Then when I enterred, 

sudo modprobe 8188eu
 
here is the result:

"modprobe:error:could not insert '8188eu':device or resource busy"

Can anybody help me?

---

### Post by chili555 on 2014-05-07
That probably means that the native default driver rtl8188eu was already loaded and running:```
lsmod | grep 8188
```What trouble are you having that caused you to try a different driver?

---

### Post by ANSELM_KEREM on 2014-05-07
Hi,

Thanks for reply.

Output for that code is
"r8188eu   755586   0"

Probably as you said it is running right now. But I can't still use the usb modem.

Well, I've searched for some solutions to run usb wireless modem.
And most of them were pointing rtl8188eu. 
Doesn't it fix with TL-WN723v3 modem?
Should I use different one?

---

### Post by ANSELM_KEREM on 2014-05-07
To give expand information about my operating system:

> Kernel-Linux 3.13.0-24-generic(i686)
Default C Compiler-GNU C Compiler Version 4.8.2(Ubuntu 4.8.2-19Ubuntu1)
Distribution-Ubuntu 14.04LTS

---

### Post by chili555 on 2014-05-07
With the modem inserted, please run and post:```
lsusb
```

---

### Post by ANSELM_KEREM on 2014-05-07
Here is the output;

> Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
kerem@hp:~$ 


Thanks.

---

### Post by chili555 on 2014-05-07
> 0bda:8179 Realtek Semiconductor Corp. It turns out that the loaded driver, r8188eu, is correct for your device; from modinfo:```
$ modinfo r8188eu | grep 8179
alias:          usb:v07B8p8179d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]8179[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```If you have the device, the driver and it loads automatically but doesn't work as expected, something else is wrong. Compiling a different driver is unlikely to fix the real, underlying problem. Let's see if the logs hold any clues:```
dmesg | grep 8188
rfkill list all
iwconfig
```

---

### Post by ANSELM_KEREM on 2014-05-07
Yes, I have that device. And here are the other outputs:


> $ dmesg | grep 8188

[    0.338188] pci 0000:00:1f.1: reg 0x20: [io  0x4c40-0x4c4f]

[   21.235435] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.

[   21.264032] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)

[   21.477395] usbcore: registered new interface driver r8188eu

[   21.690338] 8188eu: module verification failed: signature and/or  required key missing - tainting kernel

[   21.698402] Error: Driver 'r8188eu' is already registered, aborting...


While making a copy of editor outputs to notepad there could be some mistakes. Because I am texting from a windows. Sorry for that.

---

### Post by ANSELM_KEREM on 2014-05-07
Second Code:

> $ rfkill list all


0: phy
0: Wireless LAN
	
Soft blocked: no
	
Hard blocked: yes




---

### Post by ANSELM_KEREM on 2014-05-07
> 
irda0     no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.


eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"


          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate: 0 kb/s   Tx-Power: off  


          Retry short limit:7   RTS thr: off   Fragment thr:off


          Power Management: off


          Link Quality: 0  Signal level: 0  Noise level: 0


          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0


          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


wlan1     unassociated  Nickname:"<WIFI@REALTEK>"


          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated


          Sensitivity: 0/0
  
          Retry:off   RTS thr: off   Fragment thr:off


          Power Management: off


          Link Quality:0  Signal level: 0  Noise level: 0


          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag: 0


          Tx excessive retries:0  Invalid misc:0   Missed beacon: 0

While making a copy of editor outputs to notepad there could be some mistakes. Because I am texting from a windows. Sorry for that.

---

### Post by chili555 on 2014-05-07
> Hard blocked: yesOften, including my Lenovos, flipping the wireless switch or key combination will also disable any USB wireless. Crazy, I know, but true. Please find and move the wireless switch or key combination to enable the wireless.

---

### Post by ANSELM_KEREM on 2014-05-07
Sorry for late response,
I noticed that I left the wireless button off. After switching that on the usb device started to light but result is same no connection.
Also the outputs are below;

> [FONT=georgia][COLOR=#000000]$dmesg | grep 8188[/COLOR][/FONT][LEFT][FONT=georgia][COLOR=#000000][  20.149209] r8188eu: module is from the staging directory, thequality is unknown, you have been warned.[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000][  20.186010] Chip Version Info :CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000][  20.239992] usbcore: registered new interface driver r8188eu[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000][  20.415987] 8188eu: module verification failed: signature and/or required key missing - tainting kernel[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000][  20.553746] Error: Driver 'r8188eu' is already registered,aborting...[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000][  24.992217] R8188EU: Firmware Version 11, SubVersion 1, Signature0x88e1[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000][  25.396966] R8188EU: ERROR indicate disassoc[/COLOR][/FONT]


[FONT=georgia][COLOR=#000000]$rfkill list all[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]0 :hci0 : Bluetooth[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]    Softblocked: no[/COLOR][/FONT]
[FONT=georgia]**[COLOR=#000000]    Hardblocked: [/COLOR][COLOR=#ff0000]no[/COLOR]**[/FONT]
[FONT=georgia][COLOR=#000000]1:phy0 : Wireless LAN[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]    Softblocked: no[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]    Hardblocked: no[/COLOR][/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia][COLOR=#000000]$iwconfig[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]irda0    no wireless extensions.[/COLOR][/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia][COLOR=#000000]lo       no wireless extensions.[/COLOR][/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia][COLOR=#000000]eth0     no wireless extensions.[/COLOR][/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia][COLOR=#000000]eth1     unassociated  ESSID: off/any  Nickname:"ipw2100"[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Mode:Managed Channel=0  Access Point: Not-Associated   [/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        BitRate: 0 kb/s   Tx-Power:16 dBm   [/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Retryshort limit:7   RTS thr: off   Fragment thr:off[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        PowerManagement:off[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        LinkQuality: 0  Signal level: 0  Noise level: 0[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Rxinvalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Txexcessive retries: 0  Invalid misc: 0   Missed beacon: 0[/COLOR][/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia][COLOR=#000000]wlan1    unassociated  Nickname:"<WIFI@REALTEK>"[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Mode:Managed Frequency=2.412 GHz  Access Point: Not-Associated   [/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Sensitivity : 0/0 [/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Retry : off  RTS thr:off   Fragment thr: off[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        PowerManagement:off[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        LinkQuality: 0  Signal level: 0  Noise level: 0[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Rxinvalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0[/COLOR][/FONT]
[FONT=georgia][COLOR=#000000]        Txexcessive retries: 0  Invalid misc: 0   Missed beacon: 0[/COLOR][/FONT]
[/LEFT]


---

### Post by chili555 on 2014-05-07
I suspect the internal device, the USB and Network Manager are a bit confused. I suggest we blacklist the internal and see if there is improvement:```
sudo -i
echo "blacklist ipw2100"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r ipw2100
exit
```Any change?

It may take a reboot.

---

### Post by ANSELM_KEREM on 2014-05-08
I tired the code but gave error at 56th line.
> [FONT=verdana][COLOR=#000000]$sudo -i[/COLOR][/FONT][LEFT][FONT=verdana][COLOR=#000000]root@hp:~#echo "echo blacklist ipw2100"  >> /etc/modprobe.d/blacklist.conf
[/COLOR][COLOR=#000000]root@hp:~#modprobe -r ipw2100[/COLOR][/FONT][/LEFT]
[COLOR=#000000][FONT=Times New Roman][FONT=verdana]libkmod:ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse:/etc/modprobe.d/blacklist.conf line 56: ignoring bad line startingwith 'echo[/FONT]'[/FONT][/COLOR]

So didn't try to reboot. Or should I?

---

### Post by chili555 on 2014-05-08
I wrote:> sudo -i
echo "blacklist ipw2100"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r ipw2100
exitAnd then you wrote:> sudo -i
root@hp:~#[COLOR="#FF0000"]echo[/COLOR] "[COLOR="#FF0000"]**echo**[/COLOR] blacklist ipw2100" >> /etc/modprobe.d/blacklist.conf
root@hp:~#modprobe -r ipw2100A simple typo. It's easy enough to fix:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```The last line now reads:```
echo blacklist ipw2100
```Change it so it reads:```
blacklist ipw2100
```Proofread carefully, save and close gedit. Reboot.

Any improvement?

---

### Post by ANSELM_KEREM on 2014-05-08
Sorry for my mistake.

I enterred 

[COLOR=#000000]Code:[/COLOR]
gksudo gedit /etc/modprobe.d/blacklist.conf
then

[COLOR=#000000]Code:[/COLOR]
echo blacklist ipw2100
as a result I saw 

[COLOR=#000000]Code:[/COLOR]
blacklist ipw2100[COLOR=#000000]
[/COLOR]

But I don't have any idea about "save and close gedit". I am a new user on it.

---

### Post by chili555 on 2014-05-08
Up at the top of the gedit text editor window, there is a button to click; 'Save.' Then Select File > Quit.

---

### Post by ANSELM_KEREM on 2014-05-08
gedit wasn't installed so that's why I couldn't open the editor. Now it is ok. I changed the file and saved but there is still no connection.

---

### Post by chili555 on 2014-05-08
After a reboot, let's see:```
dmesg | grep -e wlan -e 8188
cat /var/log/syslog | grep -e etwork -e wlan
```

---

### Post by ANSELM_KEREM on 2014-05-10
Hi there and sorry for my late response again;

> $ dmesg | grep -e wlan -e 8188[    1.098188] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.894035] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[   21.941522] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[   22.016270] usbcore: registered new interface driver r8188eu
[   22.268871] 8188eu: module verification failed: signature and/or  required key missing - tainting kernel
[   22.314405] Error: Driver 'r8188eu' is already registered, aborting...
[   22.404758] systemd-udevd[281]: renamed network interface wlan0 to wlan1
[   27.367244] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
[   27.772612] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   27.773291] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   27.782414] R8188EU: ERROR indicate disassoc
[   27.784248] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready 

> $ cat /var/log/syslog | grep -e etwork -e wlanMay 10 18:58:18 hp NetworkManager[732]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
May 10 18:58:21 hp NetworkManager[732]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
May 10 18:58:21 hp NetworkManager[732]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
May 10 18:58:21 hp NetworkManager[732]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1754
May 10 18:58:21 hp NetworkManager[732]: <warn> DNS: plugin dnsmasq update failed
May 10 18:58:21 hp NetworkManager[732]: <info> Removing DNS information from /sbin/resolvconf
May 10 18:58:21 hp NetworkManager[732]: <info> NetworkManager state is now DISCONNECTED
May 10 19:00:34 hp kernel: [   20.538316] type=1400 audit(1399737630.315:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=321 comm="apparmor_parser"
May 10 19:00:34 hp kernel: [   20.539310] type=1400 audit(1399737630.315:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=321 comm="apparmor_parser"
May 10 19:00:36 hp NetworkManager[746]: <info> NetworkManager (version 0.9.8.8) is starting...
May 10 19:00:36 hp NetworkManager[746]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
May 10 19:00:36 hp NetworkManager[746]: <info> WEXT support is enabled
May 10 19:00:36 hp NetworkManager[746]: <info> DNS: loaded plugin dnsmasq
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: init!
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: update_system_hostname
May 10 19:00:36 hp NetworkManager[746]:       interface-parser: parsing file /etc/network/interfaces
May 10 19:00:36 hp NetworkManager[746]:       interface-parser: finished parsing file /etc/network/interfaces
May 10 19:00:36 hp NetworkManager[746]:    SCPluginIfupdown: management mode: unmanaged
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan1, iface: wlan1)
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: end _init.
May 10 19:00:36 hp NetworkManager[746]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May 10 19:00:36 hp NetworkManager[746]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ofono: init!
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ofono: end _init.
May 10 19:00:36 hp NetworkManager[746]: <info> Loaded plugin (null): (null)
May 10 19:00:36 hp NetworkManager[746]:    Ifupdown: get unmanaged devices count: 0
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: (160215904) ... get_connections.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ifupdown: (160215904) ... get_connections (managed=false): return empty list.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ofono: (160083480) ... get_connections.
May 10 19:00:36 hp NetworkManager[746]:    SCPlugin-Ofono: (160083480) connections count: 0
May 10 19:00:36 hp NetworkManager[746]:    Ifupdown: get unmanaged devices count: 0
May 10 19:00:36 hp NetworkManager[746]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 10 19:00:36 hp NetworkManager[746]: <info> WiFi enabled by radio killswitch; enabled by state file
May 10 19:00:36 hp NetworkManager[746]: <info> WWAN enabled by radio killswitch; enabled by state file
May 10 19:00:36 hp NetworkManager[746]: <info> WiMAX enabled by radio killswitch; enabled by state file
May 10 19:00:36 hp NetworkManager[746]: <info> Networking is enabled by state file
May 10 19:00:36 hp NetworkManager[746]: <info> (wlan1): driver supports SSID scans (scan_capa 0x3F).
May 10 19:00:36 hp NetworkManager[746]: <info> (wlan1): using WEXT for WiFi device control
May 10 19:00:36 hp NetworkManager[746]: <info> (wlan1): new 802.11 WiFi device (driver: 'r8188eu' ifindex: 4)
May 10 19:00:36 hp NetworkManager[746]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/0
May 10 19:00:36 hp NetworkManager[746]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 19:00:36 hp NetworkManager[746]: <info> (wlan1): bringing up device.
May 10 19:00:37 hp NetworkManager[746]: <info> (wlan1): preparing device.
May 10 19:00:37 hp NetworkManager[746]: <info> (wlan1): deactivating device (reason 'managed') [2]
May 10 19:00:37 hp NetworkManager[746]: <info> (wlan1): taking down device.
May 10 19:00:37 hp kernel: [   27.772612] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
May 10 19:00:37 hp kernel: [   27.773291] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
May 10 19:00:37 hp kernel: [   27.784248] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
May 10 19:00:37 hp NetworkManager[746]: <info> (wlan1): bringing up device.
May 10 19:00:37 hp NetworkManager[746]: <warn> failed to allocate link cache: (-12) Object not found
May 10 19:00:37 hp NetworkManager[746]: <info> (eth0): carrier is OFF
May 10 19:00:37 hp NetworkManager[746]: <info> (eth0): new Ethernet device (driver: '8139cp' ifindex: 2)
May 10 19:00:37 hp NetworkManager[746]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May 10 19:00:37 hp NetworkManager[746]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 19:00:37 hp NetworkManager[746]: <info> (eth0): bringing up device.
May 10 19:00:37 hp NetworkManager[746]: <info> (eth0): preparing device.
May 10 19:00:37 hp NetworkManager[746]: <info> (eth0): deactivating device (reason 'managed') [2]
May 10 19:00:37 hp NetworkManager[746]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0
May 10 19:00:37 hp NetworkManager[746]: <warn> /sys/devices/virtual/net/irda0: couldn't determine device driver; ignoring...
May 10 19:00:37 hp NetworkManager[746]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
May 10 19:00:37 hp NetworkManager[746]: <warn> /sys/devices/virtual/net/irda0: couldn't determine device driver; ignoring...
May 10 19:00:37 hp NetworkManager[746]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
May 10 19:00:37 hp NetworkManager[746]: <info> urfkill disappeared from the bus
May 10 19:00:37 hp NetworkManager[746]: <info> ModemManager available in the bus
May 10 19:00:38 hp NetworkManager[746]: <info> wpa_supplicant started
May 10 19:00:38 hp NetworkManager[746]: <info> (wlan1) supports 1 scan SSIDs
May 10 19:00:38 hp NetworkManager[746]: <warn> Trying to remove a non-existant call id.
May 10 19:00:38 hp NetworkManager[746]: <info> (wlan1): supplicant interface state: starting -> ready
May 10 19:00:38 hp NetworkManager[746]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 10 19:00:38 hp NetworkManager[746]: <info> (wlan1): supplicant interface state: ready -> disconnected
May 10 19:00:38 hp NetworkManager[746]: <info> (wlan1) supports 1 scan SSIDs
May 10 19:00:40 hp kernel: [   30.417290] type=1400 audit(1399737640.195:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=814 comm="apparmor_parser"
May 10 19:00:40 hp kernel: [   30.418265] type=1400 audit(1399737640.195:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=814 comm="apparmor_parser"
May 10 19:00:40 hp NetworkManager[746]: <info> (wlan1): supplicant interface state: disconnected -> inactive
May 10 19:00:46 hp NetworkManager[746]: <info> WiFi hardware radio set enabled

---

### Post by chili555 on 2014-05-11
I am a bit troubled by this:> Error: Driver 'r8188eu' is already registered, aborting...Please do:```
gksudo gedit /etc/modules
```Use nano or kate if you do not have gedit. If there is any directive there related to 8188eu, please remove it. Proofread, save and close gedit or your preferred text editor.

I am also puzzled by:> <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]Please do:```
gksudo gedit /etc/network/interfaces
```If the file contains anything more than this, remove it:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```Proofread, save and close gedit or your preferred text editor.

Does your wireless scan and see networks?```
sudo iwlist wlan1 scan
```Just tell us if it sees your network, or if not, what is the error message; we don't need to see the entire list.

---

### Post by ANSELM_KEREM on 2014-05-11
There was nothing related to 8188eu in the file.

Interfaces file was also fine.

Yes it sees my network;
>          Cell 02 - Address: 94:0C:6D:A3:C5:98 
                  ESSID:"nil"
                   Protocol:IEEE 802.11bg
                   Mode:Master
                   Frequency:2.462 GHz (Channel 11)
                   Encryption key:on
                   Bit Rates:54 Mb/s
                   Extra:wpa_ie =dd160050f20101000050f20401000050f20401000050f202
                   IE: WPA Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
                   Quality:0  Signal level:0  Noise level:0

Thank you for your patience :)

---

### Post by chili555 on 2014-05-11
Please reboot and post again:```
cat /var/log/syslog | grep -e wlan -e etwork -e 8188 | tail -n20
```The clue has to be there!

---

### Post by ANSELM_KEREM on 2014-05-11
After reboot here it is;
> $ cat /var/log/syslog | grep -e wlan -e etwork -e 8188 | tail -n20May 11 21:32:11 hp NetworkManager[737]: <info> (eth0): preparing device.
May 11 21:32:11 hp NetworkManager[737]: <info> (eth0): deactivating device (reason 'managed') [2]
May 11 21:32:11 hp NetworkManager[737]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0
May 11 21:32:11 hp NetworkManager[737]: <warn> /sys/devices/virtual/net/irda0: couldn't determine device driver; ignoring...
May 11 21:32:11 hp NetworkManager[737]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
May 11 21:32:11 hp NetworkManager[737]: <warn> /sys/devices/virtual/net/irda0: couldn't determine device driver; ignoring...
May 11 21:32:11 hp NetworkManager[737]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
May 11 21:32:11 hp NetworkManager[737]: <info> urfkill disappeared from the bus
May 11 21:32:11 hp NetworkManager[737]: <info> ModemManager available in the bus
May 11 21:32:12 hp NetworkManager[737]: <info> wpa_supplicant started
May 11 21:32:12 hp NetworkManager[737]: <info> (wlan1) supports 1 scan SSIDs
May 11 21:32:12 hp NetworkManager[737]: <warn> Trying to remove a non-existant call id.
May 11 21:32:12 hp NetworkManager[737]: <info> (wlan1): supplicant interface state: starting -> ready
May 11 21:32:12 hp NetworkManager[737]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 11 21:32:12 hp NetworkManager[737]: <info> (wlan1): supplicant interface state: ready -> disconnected
May 11 21:32:12 hp NetworkManager[737]: <info> (wlan1) supports 1 scan SSIDs
May 11 21:32:14 hp NetworkManager[737]: <info> (wlan1): supplicant interface state: disconnected -> inactive
May 11 21:32:14 hp kernel: [   30.510897] type=1400 audit(1399833134.287:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=805 comm="apparmor_parser"
May 11 21:32:14 hp kernel: [   30.511873] type=1400 audit(1399833134.287:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=805 comm="apparmor_parser"
May 11 21:32:20 hp NetworkManager[737]: <info> WiFi hardware radio set enabled

---

### Post by chili555 on 2014-05-11
I just do not understand why your device doesn't start and run as expected. Have you specified any settings in Network Manager? You shouldn't need any and should remove them, if any. May I see, with the ethernet detached:```
nm-tool
```

---

### Post by ANSELM_KEREM on 2014-05-12
No, I didn't change anything but when I tried to run software updater it failed all the installations.
I am not familiar with computer but I guess my laptop may have a hardware problem?
What do you think?

> 
$ nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
 Type:              Wired
 Driver:            8139cp
 State:             unavailable
 Default:           no
 HW Address:        00:0F:B0:4C:FB:22


 Capabilities:
   Carrier Detect:  yes


 Wired Properties
   Carrier:         off




- Device: wlan1 ----------------------------------------------------------------
 Type:              802.11 WiFi
 Driver:            r8188eu
 State:             disconnected
 Default:           no
 HW Address:        10:FE:ED:23:BE:F9


 Capabilities:


 Wireless Properties
   WEP Encryption:  yes
   WPA Encryption:  yes
   WPA2 Encryption: yes


 Wireless Access Points 
   TTNET_TPLINK_A2B8: Infra, F8:1A:67:D5:A2:B8, Freq 2417 MHz, Rate 44 Mb/s, Strength 0 WPA WPA2
   dincer:          Infra, FA:1A:67:B8:74:76, Freq 2412 MHz, Rate 44 Mb/s, Strength 0 WPA WPA2
   nil:             Infra, 94:0C:6D:A3:C5:98, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA
   sinem:           Infra, F8:1A:67:C7:6D:CE, Freq 2437 MHz, Rate 44 Mb/s, Strength 0 WPA WPA2
   NetMASTER Uydunet-CE46: Infra, 00:1A:2B:93:7F:F6, Freq 2462 MHz, Rate 44 Mb/s, Strength 0 WPA
   AirTies_Air5343: Infra, 18:28:61:B6:F7:09, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WEP




---

### Post by chili555 on 2014-05-13
Please run the command:```
nm-applet &
```Does the Network Manager icon appear? If so, let's get it to appear automatically: [http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599)

Once you've logged out and back in and the icon is present, can you click the icon, enable wifi, enable networking, select your network and connect?

---

### Post by George-Gate on 2014-06-25
You can try :

sudo rmmod r8188eu
sudo modprobe 8188eu

---

