---
title: "Mobile Broadband no internet access(sometimes)"
date: 2015-11-20
forum: Networking &amp; Wireless
---

### Post by aegir2 on 2015-11-20
I just installed ubuntu 15.10 and I have pretty big problem. Mobile broadband  connects but there is no internet  access some times, i have no idea, it doesnt work most of times but  sometimes it works, for e.g now. This usb internet thingie worked on all  other distros I checked so its not hardware but some weird modemmanager  or nm thing? How to even approach in fixing this? Please help!  Thanks!
Clarification: it always connects but most of times there is no internet access

---

### Post by aegir2 on 2015-11-20
Guys please help i can't use ubuntu without internet. I can't connect atm so here is result of
```

tail -f /var/log/syslog

```
```

Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  NetworkManager state is now CONNECTING
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Simple connect started...
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Simple connect state (4/8): Wait to get fully enabled
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Simple connect state (5/8): Register
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Simple connect state (6/8): Bearer
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Simple connect state (7/8): Connect
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (registered -> connecting)
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): modem state changed, 'registered' --> 'connecting' (reason: user-requested)
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connecting -> connected)
Nov 20 17:44:14 ubuntu ModemManager[2354]: <info>  Simple connect state (8/8): All done
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): modem state changed, 'connecting' --> 'connected' (reason: user-requested)
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <warn>  (ttyUSB0): failed to look up interface index
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <warn>  (ttyUSB0): interface ttyUSB0 not up for IP configuration
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): using modem-specified IP timeout: 20 seconds
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  starting PPP connection
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  pppd started with pid 3690
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): IPv6 configuration disabled
Nov 20 17:44:14 ubuntu pppd[3690]: Plugin /usr/lib/pppd/2.4.6/nm-pppd-plugin.so loaded.
Nov 20 17:44:14 ubuntu NetworkManager[2574]: Plugin /usr/lib/pppd/2.4.6/nm-pppd-plugin.so loaded.
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (plugin_init): initializing
Nov 20 17:44:14 ubuntu pppd[3690]: pppd 2.4.6 started by root, uid 0
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  (ppp0): new Generic device (carrier: UNKNOWN, driver: 'unknown', ifindex: 10)
Nov 20 17:44:14 ubuntu pppd[3690]: Using interface ppp0
Nov 20 17:44:14 ubuntu pppd[3690]: Connect: ppp0 <--> /dev/ttyUSB0
Nov 20 17:44:14 ubuntu NetworkManager[2574]: Using interface ppp0
Nov 20 17:44:14 ubuntu NetworkManager[2574]: Connect: ppp0 <--> /dev/ttyUSB0
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (get_credentials): got credentials from NetworkManager
Nov 20 17:44:14 ubuntu pppd[3690]: CHAP authentication succeeded: Welcome!!
Nov 20 17:44:14 ubuntu pppd[3690]: CHAP authentication succeeded
Nov 20 17:44:14 ubuntu NetworkManager[2574]: CHAP authentication succeeded: Welcome!!
Nov 20 17:44:14 ubuntu NetworkManager[2574]: CHAP authentication succeeded
Nov 20 17:44:14 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 20 17:44:14 ubuntu NetworkManager[2574]: <info>  device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 20 17:44:16 ubuntu pppd[3690]: Could not determine remote IP address: defaulting to 10.64.64.64
Nov 20 17:44:16 ubuntu pppd[3690]: local  IP address 10.216.195.46
Nov 20 17:44:16 ubuntu pppd[3690]: remote IP address 10.64.64.64
Nov 20 17:44:16 ubuntu pppd[3690]: primary   DNS address 195.29.166.120
Nov 20 17:44:16 ubuntu pppd[3690]: secondary DNS address 195.29.166.121
Nov 20 17:44:16 ubuntu NetworkManager[2574]: Could not determine remote IP address: defaulting to 10.64.64.64
Nov 20 17:44:16 ubuntu NetworkManager[2574]: local  IP address 10.216.195.46
Nov 20 17:44:16 ubuntu NetworkManager[2574]: remote IP address 10.64.64.64
Nov 20 17:44:16 ubuntu NetworkManager[2574]: primary   DNS address 195.29.166.120
Nov 20 17:44:16 ubuntu NetworkManager[2574]: secondary DNS address 195.29.166.121
Nov 20 17:44:16 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 9 / phase 'running'
Nov 20 17:44:16 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_ip_up): ip-up event
Nov 20 17:44:16 ubuntu NetworkManager[2574]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_ip_up): sending IPv4 config to NetworkManager...
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  keyfile: add connection in-memory (26f59bac-1da6-42a3-8287-2d77542fde76,"ppp0")
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): device state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  Device 'ppp0' has no connection; scheduling activate_check in 0 seconds.
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): Activation: starting connection 'ppp0' (26f59bac-1da6-42a3-8287-2d77542fde76)
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  PPP manager (IPv4 Config Get) reply received.
Nov 20 17:44:16 ubuntu whoopsie[736]: [17:44:16] Cannot reach: https://daisy.ubuntu.com
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Nov 20 17:44:16 ubuntu org.freedesktop.Telepathy.AccountManager[1477]: (process:1898): libnm-glib-WARNING **: async_got_type: could not read properties for /org/freedesktop/NetworkManager/Devices/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  NetworkManager state is now CONNECTED_LOCAL
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  Policy set 'T-Mobile Default 1' (ppp0) as default for IPv4 routing and DNS.
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  Writing DNS information to /sbin/resolvconf
Nov 20 17:44:16 ubuntu dnsmasq[1226]: setting upstream servers from DBus
Nov 20 17:44:16 ubuntu dnsmasq[1226]: using nameserver 195.29.166.120#53
Nov 20 17:44:16 ubuntu dnsmasq[1226]: using nameserver 195.29.166.121#53
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ttyUSB0): Activation: successful, device activated.
Nov 20 17:44:16 ubuntu dbus[658]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Nov 20 17:44:16 ubuntu systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov 20 17:44:16 ubuntu whoopsie[736]: [17:44:16] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/8
Nov 20 17:44:16 ubuntu whoopsie[736]: [17:44:16] Network connection may be a paid data plan: /org/freedesktop/NetworkManager/Devices/3
Nov 20 17:44:16 ubuntu NetworkManager[2574]: <info>  (ppp0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Nov 20 17:44:16 ubuntu dbus[658]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 20 17:44:16 ubuntu systemd[1]: Started Network Manager Script Dispatcher Service.
Nov 20 17:44:16 ubuntu nm-dispatcher: Dispatching action 'up' for ppp0
Nov 20 17:44:16 ubuntu gnome-session[1562]: (deja-dup-monitor:2359): GLib-CRITICAL **: Source ID 257 was not found when attempting to remove it
Nov 20 17:44:16 ubuntu gnome-session[1562]: (nm-applet:1738): libnm-glib-WARNING **: async_got_type: could not read properties for /org/freedesktop/NetworkManager/Devices/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
Nov 20 17:44:21 ubuntu whoopsie[736]: [17:44:21] Cannot reach: https://daisy.ubuntu.com

```

and if i go after reboot to edit network properties i get following error:
```

settings/nm-settings-connection.c.955 - Connection didn't have requested setting 'ppp

```

Please help!

---

### Post by praseodym on 2015-11-20
Please show the outputs of:

```
lsusb
usb-devices
lsmod
mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
```

---

### Post by aegir2 on 2015-11-20
Thank you for reply here are outputs:
lsusb
```

lsusb
Bus 002 Device 011: ID 12d1:1c05 Huawei Technologies Co., Ltd. Broadband stick (modem on)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1008 Silicon Motion 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
usb-devices
```

usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=2232 ProdID=1008 Rev=00.19
S:  Manufacturer=123
S:  Product=WebCam SCB-1100N
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 11 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```
lsmod
```

lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  0
ccm                    20480  0
nls_iso8859_1          16384  0
ppp_deflate            16384  0
bsd_comp               16384  0
ppp_async              20480  1
crc_ccitt              16384  1 ppp_async
rfcomm                 69632  0
nvram                  16384  0
msr                    16384  0
bnep                   20480  2
bbswitch               16384  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
option                 49152  2
videobuf2_core         49152  1 uvcvideo
usb_wwan               20480  1 option
v4l2_common            16384  1 videobuf2_core
usbserial              53248  7 option,usb_wwan
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             516096  12 bnep,btbcm,btrtl,btusb,rfcomm,btintel
arc4                   16384  2
iwldvm                233472  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
mac80211              733184  1 iwldvm
snd_hda_intel          36864  3
samsung_laptop         20480  0
intel_rapl             20480  0
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
iwlwifi               200704  1 iwldvm
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
kvm_intel             167936  0
kvm                   512000  1 kvm_intel
cfg80211              548864  3 iwlwifi,mac80211,iwldvm
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 32768  0
crct10dif_pclmul       16384  0
soundcore              16384  1 snd
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
input_leds             16384  0
cryptd                 20480  1 ghash_clmulni_intel
joydev                 20480  0
mei                    98304  1 mei_me
lpc_ich                24576  0
serio_raw              16384  0
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
uas                    24576  0
usb_storage            69632  1 uas
i915                 1130496  4
psmouse               126976  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  2
r8169                  81920  0
drm                   356352  6 i915,drm_kms_helper
libahci                32768  1 ahci
mii                    16384  1 r8169
video                  36864  2 i915,samsung_laptop

```
mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
```

mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/0'

```

tho there is output for -m 3 if it helps

```


/org/freedesktop/ModemManager1/Modem/3 (device id '1828bf7627506504a0f999738aa165e1e2b79ab2')
  -------------------------
  Hardware |   manufacturer: 'huawei'
           |          model: 'E173'
           |       revision: '21.015.03.05.55'
           |      supported: 'gsm-umts'
           |        current: 'gsm-umts'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1'
           |        drivers: 'option1'
           |         plugin: 'Generic'
           |   primary port: 'ttyUSB0'
           |          ports: 'ttyUSB0 (at), ttyUSB2 (at)'
  -------------------------
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'unknown'
           |          state: 'connected'
           |    power state: 'on'
           |    access tech: 'unknown'
           | signal quality: '58' (cached)
  -------------------------
  Modes    |      supported: 'allowed: any; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4'
  -------------------------
           |  enabled locks: 'none'
           |    operator id: '21901'
           |  operator name: 'T-Mobile HR'
           |   subscription: 'unknown'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/3'

  -------------------------
  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/3'

```

---

### Post by praseodym on 2015-11-21
Is there a web-interface if you open the browser?

```
Nov 20 17:44:16 ubuntu whoopsie[736]: [17:44:16] Network connection may be a [COLOR="#FF0000"]paid[/COLOR] data plan: /org/freedesktop/NetworkManager/Devices/3
```
Enough money available? The "mmcli" output shows no SIM-lock.

---

### Post by aegir2 on 2015-11-21
What do you mean with is there web interfece? It just says server not found like when you are offline and try using broweser.
And mobile broadband works with other distro and on windows so i doubt it hardware or money problem. I even managed to connect 2 times on ubuntu. I cant connect anymore tho... Help please i want to use ubuntu.

---

### Post by aegir2 on 2015-11-21
So i managed to connect by disabling ModemManager and using sakis3g but im not sure if it will work in future and this is not solution. Does this mean modemmanager problem?

---

### Post by praseodym on 2015-11-21
That is possible. You may try installing an earlier modemmanager version and block its upgrade.

---

### Post by aegir2 on 2015-11-21
How do i do that, i mean how do you find previous version? syntax is apt-get install modemmanager=version but what version, apt get only shows this current one  1.4.10-1ubuntu2 
in repo?

---

### Post by praseodym on 2015-11-21
Uninstall it and install the vivid version:

[http://packages.ubuntu.com/vivid/modemmanager](http://packages.ubuntu.com/vivid/modemmanager)

Search for "apt-pinning" to protect it from upgrades

---

### Post by aegir2 on 2015-11-21
Thank you for helping :D
Downgraded ModemManager and it doesn't connect at all, just says disconnected when i click on connect no errors whatsoever... Only good thing is that it seems sakis3g works well so i have internet at least. I hate these types of problems, where are my errors?!

---

### Post by praseodym on 2015-11-21
Maybe a NM problem. Please check for bug reports on that for 15.10.

---

