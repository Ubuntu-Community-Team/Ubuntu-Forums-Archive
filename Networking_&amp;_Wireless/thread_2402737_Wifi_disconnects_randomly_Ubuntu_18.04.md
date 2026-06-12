---
title: "Wifi disconnects randomly Ubuntu 18.04"
date: 2018-10-03
forum: Networking &amp; Wireless
---

### Post by James_Creasy on 2018-10-03
I've read dozens of threads on wifi disconnecting on 18.04 and earlier, feeling stuck. Surface Laptop, 18.04 dual boot.  

lshw

           *-network
                description: Wireless interface
                product: 88W8897 [AVASTAR] 802.11ac Wireless
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 00
                serial: c4:9d:ed:a8:15:51
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=mwifiex_pcie ip=192.168.86.176 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:132 memory:a1500000-a15fffff memory:a1400000-a14fffff

And attached is journalctl --follow when the wifi dies.

$ journalctl --follow
-- Logs begin at Tue 2018-10-02 03:53:24 PDT. --
Oct 03 16:22:07 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162207.473782:ERROR:gles2_cmd_decoder.cc(18047)] [.BrowserCompositor-0x1b220b72dc00]GL ERROR :GL_INVALID_OPERATION : glCreateAndConsumeTextureCHROMIUM: invalid mailbox name
Oct 03 16:22:07 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162207.473886:ERROR:gles2_cmd_decoder.cc(18047)] [.BrowserCompositor-0x1b220b72dc00]GL ERROR :GL_INVALID_OPERATION : glCreateAndConsumeTextureCHROMIUM: invalid mailbox name
Oct 03 16:22:07 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162207.473962:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:22:07 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162207.474030:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:22:07 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162207.489961:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:22:07 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162207.490123:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:23:06 surface dbus-daemon[1775]: [session uid=1000 pid=1775] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.72' (uid=1000 pid=2793 comm="/usr/bin/gnome-terminal.real " label="unconfined")
Oct 03 16:23:06 surface systemd[1751]: Starting GNOME Terminal Server...
Oct 03 16:23:06 surface dbus-daemon[1775]: [session uid=1000 pid=1775] Successfully activated service 'org.gnome.Terminal'
Oct 03 16:23:06 surface systemd[1751]: Started GNOME Terminal Server.
Oct 03 16:23:19 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162319.388710:ERROR:gles2_cmd_decoder.cc(18047)] [.BrowserCompositor-0x1b220b72dc00]GL ERROR :GL_INVALID_OPERATION : glCreateAndConsumeTextureCHROMIUM: invalid mailbox name
Oct 03 16:23:19 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162319.388785:ERROR:gles2_cmd_decoder.cc(18047)] [.BrowserCompositor-0x1b220b72dc00]GL ERROR :GL_INVALID_OPERATION : glCreateAndConsumeTextureCHROMIUM: invalid mailbox name
Oct 03 16:23:19 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162319.388858:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:23:19 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162319.389867:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:23:19 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162319.399883:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:23:19 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162319.400041:ERROR:gles2_cmd_decoder.cc(10168)] [.BrowserCompositor-0x1b220b72dc00]RENDER WARNING: texture bound to texture unit 0 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
Oct 03 16:23:49 surface systemd[1]: Starting Cleanup of Temporary Directories...
Oct 03 16:23:49 surface systemd[1]: Started Cleanup of Temporary Directories.
Oct 03 16:24:00 surface org.gnome.Shell.desktop[1899]: [2386:2386:1003/162400.036041:ERROR:buffer_manager.cc(491)] [.BrowserCompositor-0x1b220b478c00]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
Oct 03 16:24:55 surface pulseaudio[1922]: [alsa-sink-ALC298 Analog] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write.
Oct 03 16:24:55 surface pulseaudio[1922]: [alsa-sink-ALC298 Analog] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Oct 03 16:24:55 surface pulseaudio[1922]: [alsa-sink-ALC298 Analog] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Oct 03 16:26:24 surface wpa_supplicant[807]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=e4:f0:42:e2:84:55 reason=0 locally_generated=1
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: Firmware wakeup failed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: failed to get signal information
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: FW in reset state
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: failed to get signal information
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: FW in reset state
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: info: shutdown mwifiex...
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface kernel: mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
Oct 03 16:26:24 surface dhclient[1466]: receive_packet failed on wlp2s0: Network is down
Oct 03 16:26:24 surface NetworkManager[817]: <info>  [1538609184.9043] manager: NetworkManager state is now CONNECTED_SITE
Oct 03 16:26:24 surface whoopsie[900]: [16:26:24] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Oct 03 16:26:24 surface whoopsie[900]: [16:26:24] offline
Oct 03 16:26:24 surface whoopsie[900]: [16:26:24] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Oct 03 16:26:24 surface avahi-daemon[767]: Interface wlp2s0.IPv6 no longer relevant for mDNS.
Oct 03 16:26:24 surface NetworkManager[817]: <info>  [1538609184.9056] device (wlp2s0): state change: activated -> unmanaged (reason 'removed', sys-iface-state: 'removed')
Oct 03 16:26:24 surface avahi-daemon[767]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::4728:bae9:3b1c:24f0.
Oct 03 16:26:24 surface systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 03 16:26:24 surface avahi-daemon[767]: Interface wlp2s0.IPv4 no longer relevant for mDNS.
Oct 03 16:26:24 surface systemd[1]: Starting Load/Save RF Kill Switch Status...
Oct 03 16:26:24 surface avahi-daemon[767]: Leaving mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.86.176.
Oct 03 16:26:24 surface NetworkManager[817]: <info>  [1538609184.9408] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 1466
Oct 03 16:26:24 surface avahi-daemon[767]: Withdrawing address record for fe80::4728:bae9:3b1c:24f0 on wlp2s0.
Oct 03 16:26:24 surface NetworkManager[817]: <info>  [1538609184.9409] dhcp4 (wlp2s0): state changed bound -> done
Oct 03 16:26:24 surface avahi-daemon[767]: Withdrawing address record for 192.168.86.176 on wlp2s0.
Oct 03 16:26:24 surface NetworkManager[817]: <info>  [1538609184.9429] manager: NetworkManager state is now CONNECTED_LOCAL
Oct 03 16:26:24 surface dbus-daemon[769]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.10' (uid=0 pid=817 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct 03 16:26:24 surface systemd-rfkill[2890]: Failed to open device rfkill0: No such device
Oct 03 16:26:24 surface systemd[1]: Started Load/Save RF Kill Switch Status.
Oct 03 16:26:24 surface NetworkManager[817]: <info>  [1538609184.9638] radio killswitch /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0/ieee80211/phy0/rfkill0 disappeared
Oct 03 16:26:24 surface NetworkManager[817]: <warn>  [1538609184.9644] dns-sd-resolved[0x7fcdf8004ec0]: Failed: GDBus.Error:org.freedesktop.resolve1.NoSuchLink: Link 3 not known
Oct 03 16:26:24 surface ModemManager[761]: <info>  (net/wlp2s0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0
Oct 03 16:26:24 surface NetworkManager[817]: <warn>  [1538609184.9645] dns-sd-resolved[0x7fcdf8004ec0]: Failed: GDBus.Error:org.freedesktop.resolve1.NoSuchLink: Link 3 not known
Oct 03 16:26:24 surface NetworkManager[817]: <info>  [1538609184.9653] devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0/net/wlp2s0, iface: wlp2s0)
Oct 03 16:26:24 surface dbus-daemon[769]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 03 16:26:24 surface systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 03 16:26:24 surface gsd-sharing[2026]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Oct 03 16:26:24 surface nm-dispatcher[2889]: req:1 'connectivity-change': new request (1 scripts)
Oct 03 16:26:24 surface gsd-sharing[2026]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Oct 03 16:26:24 surface nm-dispatcher[2889]: req:1 'connectivity-change': start running ordered scripts...
Oct 03 16:26:24 surface gsd-sharing[2026]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Oct 03 16:26:24 surface nm-dispatcher[2889]: req:2 'down' [wlp2s0]: new request (1 scripts)
Oct 03 16:26:24 surface nm-dispatcher[2889]: req:2 'down' [wlp2s0]: start running ordered scripts...
Oct 03 16:26:24 surface gnome-shell[1899]: JS WARNING: [resource:///org/gnome/shell/ui/status/network.js 1204]: reference to undefined property "_strengthChangedId"
Oct 03 16:26:25 surface wpa_supplicant[807]: nl80211: deinit ifname=wlp2s0 disabled_11b_rates=0
Oct 03 16:26:25 surface kernel: mwifiex_pcie 0000:02:00.0: WLAN FW already running! Skip FW dnld
Oct 03 16:26:25 surface kernel: mwifiex_pcie 0000:02:00.0: WLAN FW is active
Oct 03 16:26:26 surface kernel: mwifiex_pcie 0000:02:00.0: Unknown api_id: 4
Oct 03 16:26:26 surface kernel: mwifiex_pcie 0000:02:00.0: info: MWIFIEX VERSION: mwifiex 1.0 (15.68.7.p154) 
Oct 03 16:26:26 surface kernel: mwifiex_pcie 0000:02:00.0: driver_version = mwifiex 1.0 (15.68.7.p154) 
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.0413] wifi-nl80211: (mlan0): using nl80211 for WiFi device control
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.0419] device (mlan0): driver supports Access Point (AP) mode
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.0524] manager: (mlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/4)
Oct 03 16:26:26 surface systemd-udevd[2943]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.0696] rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0/ieee80211/phy1/rfkill2) (driver mwifiex_pcie)
Oct 03 16:26:26 surface kernel: mwifiex_pcie 0000:02:00.0 wlp2s0: renamed from mlan0
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.1354] devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0/net/wlp2s0, iface: wlp2s0)
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.1355] device added (path: /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0/net/wlp2s0, iface: wlp2s0): no ifupdown configuration found.
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.1366] device (wlp2s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Oct 03 16:26:26 surface kernel: IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Oct 03 16:26:26 surface kernel: IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Oct 03 16:26:26 surface wpa_supplicant[807]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
Oct 03 16:26:26 surface wpa_supplicant[807]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Oct 03 16:26:26 surface wpa_supplicant[807]: dbus: Failed to construct signal
Oct 03 16:26:26 surface wpa_supplicant[807]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.1979] device (wlp2s0): supplicant interface state: starting -> ready
Oct 03 16:26:26 surface NetworkManager[817]: <info>  [1538609186.1979] device (wlp2s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
Oct 03 16:26:26 surface kernel: IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Oct 03 16:26:28 surface ModemManager[761]: <info>  Couldn't check support for device at '/sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0': not supported by any plugin
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9315] policy: auto-activating connection 'jc'
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9366] device (wlp2s0): Activation: starting connection 'jc' (e0a6f399-7e45-40da-a43e-a48cd4e05dc4)
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9376] device (wlp2s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9384] manager: NetworkManager state is now CONNECTING
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9405] device (wlp2s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9415] device (wlp2s0): Activation: (wifi) access point 'jc' has security, but secrets are required.
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9416] device (wlp2s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9591] device (wlp2s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9610] device (wlp2s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9616] device (wlp2s0): Activation: (wifi) connection 'jc' has security, and secrets exist.  No new secrets needed.
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9617] Config: added 'ssid' value 'jc'
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9617] Config: added 'scan_ssid' value '1'
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9618] Config: added 'bgscan' value 'simple:30:-80:86400'
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9618] Config: added 'key_mgmt' value 'WPA-PSK'
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9618] Config: added 'auth_alg' value 'OPEN'
Oct 03 16:26:28 surface NetworkManager[817]: <info>  [1538609188.9619] Config: added 'psk' value '<hidden>'
Oct 03 16:26:28 surface wpa_supplicant[807]: wlp2s0: Trying to associate with e4:f0:42:e2:84:55 (SSID='jc' freq=5745 MHz)
Oct 03 16:26:28 surface kernel: mwifiex_pcie 0000:02:00.0: info: trying to associate to 'jc' bssid e4:f0:42:e2:84:55
Oct 03 16:26:29 surface wpa_supplicant[807]: wlp2s0: Associated with e4:f0:42:e2:84:55
Oct 03 16:26:29 surface wpa_supplicant[807]: WMM AC: Missing IEs
Oct 03 16:26:29 surface wpa_supplicant[807]: wlp2s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Oct 03 16:26:29 surface NetworkManager[817]: <info>  [1538609189.0697] device (wlp2s0): supplicant interface state: ready -> associating
Oct 03 16:26:29 surface kernel: mwifiex_pcie 0000:02:00.0: info: associated to bssid e4:f0:42:e2:84:55 successfully
Oct 03 16:26:29 surface NetworkManager[817]: <info>  [1538609189.0749] device (wlp2s0): supplicant interface state: associating -> associated
Oct 03 16:26:29 surface NetworkManager[817]: <info>  [1538609189.0966] device (wlp2s0): supplicant interface state: associated -> 4-way handshake
Oct 03 16:26:39 surface wpa_supplicant[807]: wlp2s0: Authentication with e4:f0:42:e2:84:55 timed out.
Oct 03 16:26:51 surface wpa_supplicant[807]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=e4:f0:42:e2:84:55 reason=3 locally_generated=1
Oct 03 16:26:51 surface wpa_supplicant[807]: wlp2s0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Oct 03 16:26:51 surface wpa_supplicant[807]: wlp2s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="jc" auth_failures=1 duration=10 reason=WRONG_KEY
Oct 03 16:26:51 surface NetworkManager[817]: <warn>  [1538609211.2302] sup-iface[0x55b55f30a830,wlp2s0]: connection disconnected (reason -3)
Oct 03 16:26:51 surface kernel: mwifiex_pcie 0000:02:00.0: cmd_wait_q terminated: -110
Oct 03 16:26:54 surface NetworkManager[817]: <warn>  [1538609214.2544] device (wlp2s0): Activation: (wifi) association took too long
Oct 03 16:26:54 surface NetworkManager[817]: <info>  [1538609214.2546] device (wlp2s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Oct 03 16:26:54 surface NetworkManager[817]: <warn>  [1538609214.2581] device (wlp2s0): Activation: (wifi) asking for new secrets
Oct 03 16:26:54 surface NetworkManager[817]: <info>  [1538609214.2602] device (wlp2s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 03 16:26:54 surface NetworkManager[817]: <info>  [1538609214.2605] device (wlp2s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 03 16:27:01 surface kernel: mwifiex_pcie 0000:02:00.0: info: successfully disconnected from e4:f0:42:e2:84:55: reason code 2
Oct 03 16:27:03 surface kernel: mwifiex_pcie 0000:02:00.0: cmd_wait_q terminated: -110
Oct 03 16:27:03 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:27:15 surface kernel: mwifiex_pcie 0000:02:00.0: cmd_wait_q terminated: -110
Oct 03 16:27:15 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys
Oct 03 16:27:27 surface kernel: mwifiex_pcie 0000:02:00.0: cmd_wait_q terminated: -110
Oct 03 16:27:27 surface kernel: mwifiex_pcie 0000:02:00.0: deleting the crypto keys

---

### Post by James_Creasy on 2018-10-05
Additional info: restarting network manager doesn't work.

Computer can't restart, hangs on the shutting down screen. Have to power off to reboot and restore wifi.

---

