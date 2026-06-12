---
title: "Unity becomes unresponsive after about 30 minutes of idle time"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-04-30
Hi! If I leave Unity alone for about half an hour, it becomes totally unresponsive. I can move the mouse, that is all. I can't click on anything in any window, keyboard shortcuts don't work either, but I can ctrl+alt+F1 to drop to a console. The seconds don't even change on the clock. Only a restart gets it working again. I've tried disabling the screensaver and screen blanking, to no avail. Does anyone else have this issue? I can't find a bug on Launchpad. Here's lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

---

### Post by corncob on 2011-04-30
I had the same problem with the beta.  Maybe it got fixed in the stable release.  I can't say since I'm using the classic desktop.

---

### Post by pi.boy.travis on 2011-04-30
> **corncob said:**
> I had the same problem with the beta.  Maybe it got fixed in the stable release.  I can't say since I'm using the classic desktop.

I'm using the stable release. :/

---

### Post by TeoBigusGeekus on 2011-04-30
Does tty1 give you any error message?

---

### Post by pi.boy.travis on 2011-04-30
> **TeoBigusGeekus said:**
> Does tty1 give you any error message?

Nope, just a login prompt.

And, actually, I AM using the beta2! I checked /etc/issue, and it said I was using the development branch. I must have accidentally used the wrong ISO. I'll reinstall the stable release and see if that fixes it. . .

---

### Post by pi.boy.travis on 2011-04-30
Just reinstalled the ACTUAL 11.04, and it still happens. . .

---

### Post by pi.boy.travis on 2011-05-01
Looks like this one isn't going down without a fight. . . Here's syslog minutes after the freeze:

```

Apr 30 22:59:37 travis-laptop kernel: [ 9893.510146] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510152] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510157] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510163] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510168] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510173] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510179] cfg80211: World regulatory domain updated:
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510183] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510189] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510195] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510200] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510206] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop kernel: [ 9893.510211] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 30 22:59:37 travis-laptop NetworkManager[845]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 30 22:59:45 travis-laptop wpa_supplicant[991]: Trying to associate with 68:7f:74:51:d5:5b (SSID='whitaker' freq=2437 MHz)
Apr 30 22:59:45 travis-laptop NetworkManager[845]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 30 22:59:45 travis-laptop kernel: [ 9901.180577] wlan0: authenticate with 68:7f:74:51:d5:5b (try 1)
Apr 30 22:59:45 travis-laptop kernel: [ 9901.182089] wlan0: authenticated
Apr 30 22:59:45 travis-laptop kernel: [ 9901.182122] wlan0: associate with 68:7f:74:51:d5:5b (try 1)
Apr 30 22:59:45 travis-laptop wpa_supplicant[991]: Associated with 68:7f:74:51:d5:5b
Apr 30 22:59:45 travis-laptop wpa_supplicant[991]: CTRL-EVENT-CONNECTED - Connection to 68:7f:74:51:d5:5b completed (reauth) [id=0 id_str=]
Apr 30 22:59:45 travis-laptop NetworkManager[845]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 30 22:59:45 travis-laptop NetworkManager[845]: <info> (wlan0): supplicant connection state:  associated -> completed
Apr 30 22:59:45 travis-laptop kernel: [ 9901.184419] wlan0: RX AssocResp from 68:7f:74:51:d5:5b (capab=0x401 status=0 aid=5)
Apr 30 22:59:45 travis-laptop kernel: [ 9901.184426] wlan0: associated
Apr 30 23:01:46 travis-laptop kernel: [10022.084412] usb 2-4.3: USB disconnect, address 10
Apr 30 23:01:46 travis-laptop kernel: [10022.300600] sd 7:0:0:0: [sdd] Synchronizing SCSI cache
Apr 30 23:01:46 travis-laptop kernel: [10022.302106] sd 7:0:0:0: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 30 23:01:46 travis-laptop kernel: [10022.376643] JBD2: I/O error detected when updating journal superblock for sdd1-8.
Apr 30 23:01:58 travis-laptop kernel: [10034.076453] usb 2-4.3: new high speed USB device using ehci_hcd and address 11
Apr 30 23:01:58 travis-laptop kernel: [10034.188092] scsi8 : usb-storage 2-4.3:1.0
Apr 30 23:01:59 travis-laptop kernel: [10035.189933] scsi 8:0:0:0: Direct-Access     Seagate  FreeAgent        0138 PQ: 0 ANSI: 4
Apr 30 23:01:59 travis-laptop kernel: [10035.191443] sd 8:0:0:0: Attached scsi generic sg4 type 0
Apr 30 23:01:59 travis-laptop kernel: [10035.193330] sd 8:0:0:0: [sdd] 3907029166 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr 30 23:01:59 travis-laptop kernel: [10035.193816] sd 8:0:0:0: [sdd] Write Protect is off
Apr 30 23:01:59 travis-laptop kernel: [10035.193823] sd 8:0:0:0: [sdd] Mode Sense: 1c 00 00 00
Apr 30 23:01:59 travis-laptop kernel: [10035.196447] sd 8:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 23:01:59 travis-laptop kernel: [10035.228098]  sdd: sdd1
Apr 30 23:01:59 travis-laptop kernel: [10035.230453] sd 8:0:0:0: [sdd] Attached SCSI disk
Apr 30 23:02:01 travis-laptop kernel: [10036.893179] EXT4-fs (sdd1): warning: maximal mount count reached, running e2fsck is recommended
Apr 30 23:02:01 travis-laptop kernel: [10036.987906] EXT4-fs (sdd1): recovery complete
Apr 30 23:02:01 travis-laptop kernel: [10036.988484] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
Apr 30 23:17:02 travis-laptop CRON[6482]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 23:26:43 travis-laptop AptDaemon: INFO: Initializing daemon
Apr 30 23:31:43 travis-laptop AptDaemon: INFO: Quitting due to inactivity
Apr 30 23:31:43 travis-laptop AptDaemon: INFO: Shutdown was requested
Apr 30 23:41:58 travis-laptop kernel: [12434.628769] usb 2-4.3: USB disconnect, address 11
Apr 30 23:41:58 travis-laptop kernel: [12434.652426] JBD2: I/O error detected when updating journal superblock for sdd1-8.
Apr 30 23:41:58 travis-laptop kernel: [12434.661663] sd 8:0:0:0: [sdd] Synchronizing SCSI cache
Apr 30 23:41:58 travis-laptop kernel: [12434.661999] sd 8:0:0:0: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 30 23:42:10 travis-laptop kernel: [12446.620313] usb 2-4.3: new high speed USB device using ehci_hcd and address 12
Apr 30 23:42:11 travis-laptop kernel: [12446.734201] scsi9 : usb-storage 2-4.3:1.0
Apr 30 23:42:12 travis-laptop kernel: [12447.733441] scsi 9:0:0:0: Direct-Access     Seagate  FreeAgent        0138 PQ: 0 ANSI: 4
Apr 30 23:42:12 travis-laptop kernel: [12447.734131] sd 9:0:0:0: Attached scsi generic sg4 type 0
Apr 30 23:42:12 travis-laptop kernel: [12447.737298] sd 9:0:0:0: [sdd] 3907029166 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr 30 23:42:12 travis-laptop kernel: [12447.738924] sd 9:0:0:0: [sdd] Write Protect is off
Apr 30 23:42:12 travis-laptop kernel: [12447.738930] sd 9:0:0:0: [sdd] Mode Sense: 1c 00 00 00
Apr 30 23:42:12 travis-laptop kernel: [12447.740536] sd 9:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 23:42:12 travis-laptop kernel: [12447.775654]  sdd: sdd1
Apr 30 23:42:12 travis-laptop kernel: [12447.779534] sd 9:0:0:0: [sdd] Attached SCSI disk
Apr 30 23:42:13 travis-laptop kernel: [12449.189640] EXT4-fs (sdd1): warning: maximal mount count reached, running e2fsck is recommended
Apr 30 23:42:13 travis-laptop kernel: [12449.305114] EXT4-fs (sdd1): recovery complete
Apr 30 23:42:13 travis-laptop kernel: [12449.305678] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
Apr 30 23:50:33 travis-laptop kernel: [12948.676870] usb 2-4.2: USB disconnect, address 4
Apr 30 23:50:33 travis-laptop kernel: [12948.676875] usb 2-4.2.1: USB disconnect, address 8
Apr 30 23:50:59 travis-laptop AptDaemon: INFO: Initializing daemon
Apr 30 23:52:33 travis-laptop kernel: [13068.872265] sd 9:0:0:0: [sdd] Synchronizing SCSI cache
Apr 30 23:52:33 travis-laptop kernel: [13068.874430] WARNING! power/level is deprecated; use power/control instead
Apr 30 23:52:35 travis-laptop kernel: [13070.772684] usb 2-4.3: USB disconnect, address 12
Apr 30 23:52:42 travis-laptop kernel: [13077.913080] composite sync not supported
Apr 30 23:55:59 travis-laptop AptDaemon: INFO: Quitting due to inactivity
Apr 30 23:55:59 travis-laptop AptDaemon: INFO: Shutdown was requested
May  1 00:17:01 travis-laptop CRON[7921]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 00:21:58 travis-laptop kernel: [14833.729091] composite sync not supported
May  1 00:22:11 travis-laptop kernel: [14847.490556] composite sync not supported
May  1 00:22:12 travis-laptop kernel: [14847.763811] composite sync not supported
May  1 00:22:16 travis-laptop acpid: client connected from 968[0:0]
May  1 00:22:16 travis-laptop acpid: 1 client rule loaded
May  1 00:22:16 travis-laptop kernel: [14851.748158] composite sync not supported
```

And here's .xsession-errors:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-UlxNpS
SSH_AUTH_SOCK=/tmp/keyring-UlxNpS/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-UlxNpS
SSH_AUTH_SOCK=/tmp/keyring-UlxNpS/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-UlxNpS
SSH_AUTH_SOCK=/tmp/keyring-UlxNpS/ssh
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
** Message: adding killswitch idx 1 state KILLSWITCH_STATE_UNBLOCKED
** Message: adding killswitch idx 2 state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
Initializing vpswitch options...done
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 2 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
Initializing animation options...done
Initializing snap options...done
30/04/2011 08:15:27 PM Autoprobing TCP port in (all) network interface
30/04/2011 08:15:27 PM Listening IPv6://[::]:5900
30/04/2011 08:15:27 PM Listening IPv4://0.0.0.0:5900
30/04/2011 08:15:27 PM Autoprobing selected port 5900
30/04/2011 08:15:27 PM Advertising security type: 'TLS' (18)
30/04/2011 08:15:27 PM Advertising authentication type: 'VNC Authentication' (2)
30/04/2011 08:15:27 PM Advertising security type: 'VNC Authentication' (2)
Initializing expo options...done
** (nm-applet:1503): DEBUG: old state indicates that this was not a disconnect 0
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
** (nm-applet:1503): DEBUG: foo_client_state_changed_cb
Initializing unitymtgrabhandles options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/travis/.compiz/session/10d1ca0e1c25dc1848130420892262677600000014170029"
Initializing session options...done

** (gnome-screensaver:1552): WARNING **: screensaver already running in this session
Initializing nautilus-gdu extension
** (<unknown>:1482): DEBUG: Unity accessibility initialization
** (nm-applet:1503): DEBUG: foo_client_state_changed_cb
** (<unknown>:1482): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

unity-panel-service: no process found
** (<unknown>:1482): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
Starting unity-window-decorator
** (<unknown>:1482): DEBUG: PlaceEntry: Applications
** (<unknown>:1482): DEBUG: PlaceEntry: Commands
** (<unknown>:1482): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:1482): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:1482): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:1482): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:1482): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:1482): DEBUG: TrayChild Rejected: gnome-power-manager gnome-power-manager Gnome-power-manager
** (<unknown>:1482): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet
** (<unknown>:1482): DEBUG: TrayChild Rejected: bluetooth-manager bluetooth-applet Bluetooth-applet

(<unknown>:1482): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:1482): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:1482): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:1482): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:1482): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:1482): DEBUG: IndicatorAdded: libme.so
** (<unknown>:1482): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:1482): DEBUG: Connected to proxy
** (<unknown>:1482): DEBUG: Connected to proxy
** (<unknown>:1482): DEBUG: Connected to proxy

(<unknown>:1482): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1482): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1482): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1482): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1482): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1482): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1482): dee-WARNING **: Transaction from com.canonical.Unity.ApplicationsPlace.RunnerGroupsModel is in the past. Ignoring transaction.
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:1728): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:1779): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1482): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1482): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1482): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** Message: init gpgme version 1.2.0
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Seahorse window size doesn't fit

** (seahorse:2446): WARNING **: SSH command failed: (255)

** (seahorse:2446): WARNING **: SSH error output: 
** (process:2468): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2469): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2470): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied (publickey,password).



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (seahorse:2446): WARNING **: SSH command failed: (255)

** (seahorse:2446): WARNING **: SSH error output: 
** (process:2475): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2476): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2477): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied (publickey,password).


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:2482): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** Message: could not grab keyboard
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Seahorse window size doesn't fit

(seahorse:2446): Gtk-CRITICAL **: IA__gtk_widget_grab_default: assertion `gtk_widget_get_can_default (widget)' failed

(unity-window-decorator:1641): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (seahorse:2446): WARNING **: SSH command failed: (255)

** (seahorse:2446): WARNING **: SSH error output: 
** (process:2542): WARNING **: couldn't open fd 26: Bad file descriptor
Permission denied, please try again.


** (process:2543): WARNING **: couldn't open fd 26: Bad file descriptor
Permission denied, please try again.


** (process:2544): WARNING **: couldn't open fd 26: Bad file descriptor
Permission denied (publickey,password).


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:2548): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (seahorse:2446): WARNING **: SSH command failed: (255)

** (seahorse:2446): WARNING **: SSH error output: 
** (process:2583): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2584): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2585): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied (publickey,password).



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (seahorse:2446): WARNING **: SSH command failed: (255)

** (seahorse:2446): WARNING **: SSH error output: 
** (process:2590): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2591): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied, please try again.


** (process:2592): WARNING **: couldn't open fd 23: Bad file descriptor
Permission denied (publickey,password).



** (seahorse:2446): CRITICAL **: fire_selection_changed: assertion `SEAHORSE_IS_KEY_MANAGER (self)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (nautilus:1491): WARNING **: bookmark uri is sftp://ubuntu-server.local/home/travis/.ssh, but expected sftp://ubuntu-server.local/home/travis

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1497): DEBUG: desktop-launch-listener.vala:118: ran with uri: sftp://ubuntu-server.local/home/travis/.ssh/authorized_keys
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1497): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/travis/.ssh/id_rsa.pub
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: desktop-launch-listener.vala:118: ran with uri: sftp://ubuntu-server.local/home/travis/.ssh/authorized_keys
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported

** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported

** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:3101): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** Message: init gpgme version 1.2.0
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Seahorse window size doesn't fit

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** Message: could not grab keyboard
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Seahorse window size doesn't fit

(seahorse:3193): Gtk-CRITICAL **: IA__gtk_widget_grab_default: assertion `gtk_widget_get_can_default (widget)' failed

** (<unknown>:1482): WARNING **: Failed to fetch type: Method "WindowType" with signature "" on interface "org.ayatana.bamf.window" doesn't exist


(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** Message: init gpgme version 1.2.0
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Seahorse window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:3654): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


NOTE: child process received `Goodbye', closing down
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-keyring-prompt window size doesn't fit

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1491): GStreamer-CRITICAL **: gst_debug_add_log_function: assertion `func != NULL' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:4857): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `gchar'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
NOTE: child process received `Goodbye', closing down
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:5092): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1497): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///media/Seagate/Backup/applist
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///media/Seagate/Backup/applist
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(<unknown>:1482): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported

** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: incorrect total size of bitmap (48328 specified; 9640 real)
/tmp/tmp.U4Uy7o61TS: skipping 38688 bytes of garbage at 17110
/tmp/tmp.U4Uy7o61TS: premature end
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
/tmp/tmp.U4Uy7o61TS: clr_important field in bitmap should be zero
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: System-config-printer.py window size doesn't fit
params.c:OpenConfFile() - Unable to open configuration file "/home/travis/.smb/smb.conf":
	No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/travis/.smb/smb.conf.append":
	No such file or directory

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: System-config-printer.py window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: System-config-printer.py window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
/tmp/tmp.ewlkfSvIO4: clr_important field in bitmap should be zero
/tmp/tmp.ewlkfSvIO4: clr_important field in bitmap should be zero
/tmp/tmp.ewlkfSvIO4: clr_important field in bitmap should be zero
/tmp/tmp.ewlkfSvIO4: clr_important field in bitmap should be zero
/tmp/tmp.ewlkfSvIO4: clr_important field in bitmap should be zero
/tmp/tmp.ewlkfSvIO4: clr_important field in bitmap should be zero

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
2011-04-30 23:07:07,516 INFO     Starting up Miro
2011-04-30 23:07:07,517 INFO     Version:    3.5.1
2011-04-30 23:07:07,518 INFO     Revision:   ssh://ben@git.participatoryculture.org:2191/var/git/miro - e5e3cabb
2011-04-30 23:07:07,518 INFO     Builder:    buildd@rothera
2011-04-30 23:07:07,519 INFO     Build Time: 1295694488.06
2011-04-30 23:07:07,519 INFO     Reading HTTP Password list
2011-04-30 23:07:07,520 INFO     Starting libCURL thread
2011-04-30 23:07:07,526 INFO     Starting event loop thread
2011-04-30 23:07:07,528 INFO     Restoring database...
2011-04-30 23:07:07,535 INFO     Sqlite3 version:   3.7.4
2011-04-30 23:07:07,535 INFO     Pysqlite version:  2.6.0
2011-04-30 23:07:07,536 INFO     opening database /home/travis/.miro/sqlitedb
2011-04-30 23:07:07,581 INFO     path of database: /home/travis/.miro/sqlitedb
2011-04-30 23:07:07,581 INFO     closing database
2011-04-30 23:07:07,582 INFO     Vacuuming the db before shutting down.
2011-04-30 23:07:07,626 INFO     Linux version:     Linux 2.6.38-8-generic i686
2011-04-30 23:07:07,627 INFO     Python version:    2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
[GCC 4.5.2]
2011-04-30 23:07:07,627 INFO     Gtk+ version:      (2, 24, 4)
2011-04-30 23:07:07,627 INFO     PyGObject version: (2, 28, 3)
2011-04-30 23:07:07,627 INFO     PyGtk version:     (2, 22, 0)
2011-04-30 23:07:07,628 INFO     Language:          [('LANGUAGE', 'en_US:en'), ('LANG', 'en_US.UTF-8')]
2011-04-30 23:07:08,725 INFO     libtorrent:        0.15.5.0
2011-04-30 23:07:08,725 INFO     pycurl:            libcurl/7.21.3 GnuTLS/2.8.6 zlib/1.2.3.4 libidn/1.18
2011-04-30 23:07:08,726 INFO     set_renderer: trying to add gstreamerrenderer
2011-04-30 23:07:09,267 INFO     GStreamer version: GStreamer 0.10.32
2011-04-30 23:07:09,297 INFO     GStreamer audiosink: gconfaudiosink
2011-04-30 23:07:09,299 INFO     opening database /home/travis/.miro/upgrading_database_110
2011-04-30 23:07:09,300 INFO     upgrading database to version 111
2011-04-30 23:07:09,305 INFO     GStreamer videosink: gconfvideosink
2011-04-30 23:07:09,306 INFO     GStreamer version: GStreamer 0.10.32
2011-04-30 23:07:09,307 INFO     GStreamer audiosink: gconfaudiosink
2011-04-30 23:07:09,307 INFO     set_renderer: successfully loaded gstreamerrenderer
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/base.py:160: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  return self._widget.size_request()
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/window.py:676: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.packing_vbox.pack_start(widget._widget)
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/window.py:659: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self._window.show_all()
2011-04-30 23:07:09,650 INFO     upgrading database to version 112
2011-04-30 23:07:09,884 INFO     upgrading database to version 113
2011-04-30 23:07:09,887 INFO     upgrading database to version 114
2011-04-30 23:07:10,779 INFO     upgrading database to version 115
2011-04-30 23:07:12,245 INFO     upgrading database to version 116
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(evolution:5981): GLib-GObject-WARNING **: g_object_get_property: object class `EShellSettings' has no property named `cal-primary-calendar'
Migrating cached data
  mv /home/travis/.evolution/cache/http /home/travis/.cache/evolution/http
  mv /home/travis/.evolution/cache/tmp /home/travis/.cache/evolution/tmp
  rmdir /home/travis/.evolution/cache
  FAILED: Directory not empty (contents follows)
          addressbook
Migrating config data
  mv /home/travis/.evolution/addressbook/views/current_view-couchdb:__127.0.0.1.xml /home/travis/.config/evolution/addressbook/views/current_view-couchdb:__127.0.0.1.xml
  mv /home/travis/.evolution/addressbook/views/custom_view-couchdb:__127.0.0.1.xml /home/travis/.config/evolution/addressbook/views/custom_view-couchdb:__127.0.0.1.xml
  mv /home/travis/.evolution/addressbook/searches.xml /home/travis/.config/evolution/addressbook/searches.xml
  mv /home/travis/.evolution/addressbook/config/state /home/travis/.config/evolution/addressbook/state.ini
  mv /home/travis/.evolution/mail/views/custom_view-imap:__pi.boy.travis@imap.gmail.com_INBOX.xml /home/travis/.config/evolution/mail/views/custom_view-imap:__pi.boy.travis@imap.gmail.com_INBOX.xml
  mv /home/travis/.evolution/mail/views/current_view-imap:__pi.boy.travis@imap.gmail.com_INBOX.xml /home/travis/.config/evolution/mail/views/current_view-imap:__pi.boy.travis@imap.gmail.com_INBOX.xml
  mv /home/travis/.evolution/mail/views/custom_view-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_All_20Mail.xml /home/travis/.config/evolution/mail/views/custom_view-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_All_20Mail.xml
  mv /home/travis/.evolution/mail/views/current_view-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_All_20Mail.xml /home/travis/.config/evolution/mail/views/current_view-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_All_20Mail.xml
  mv /home/travis/.evolution/mail/searches.xml /home/travis/.config/evolution/mail/searches.xml
  mv /home/travis/.evolution/mail/config/state /home/travis/.config/evolution/mail/state.ini
  mv /home/travis/.evolution/memos/searches.xml /home/travis/.config/evolution/memos/searches.xml
  mv /home/travis/.evolution/mail/config/gtkrc-mail-fonts /home/travis/.config/evolution/mail/gtkrc-mail-fonts
  mv /home/travis/.evolution/mail/config/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Sent_20Mail /home/travis/.config/evolution/mail/folders/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Sent_20Mail
  mv /home/travis/.evolution/mail/config/et-expanded-mbox:_home_travis_.evolution_mail_local_Drafts /home/travis/.config/evolution/mail/folders/et-expanded-mbox:_home_travis_.local_share_evolution_mail_local_Drafts
  mv /home/travis/.evolution/mail/config/et-expanded-mbox:_home_travis_.evolution_mail_local_Outbox /home/travis/.config/evolution/mail/folders/et-expanded-mbox:_home_travis_.local_share_evolution_mail_local_Outbox
  mv /home/travis/.evolution/mail/config/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_All_20Mail /home/travis/.config/evolution/mail/folders/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_All_20Mail
  mv /home/travis/.evolution/mail/config/et-expanded-mbox:_home_travis_.evolution_mail_local_Sent /home/travis/.config/evolution/mail/folders/et-expanded-mbox:_home_travis_.local_share_evolution_mail_local_Sent
  mv /home/travis/.evolution/mail/config/et-expanded-mbox:_home_travis_.evolution_mail_local_Inbox /home/travis/.config/evolution/mail/folders/et-expanded-mbox:_home_travis_.local_share_evolution_mail_local_Inbox
  mv /home/travis/.evolution/mail/config/et-expanded-mbox:_home_travis_.evolution_mail_local_._23evolution_Trash /home/travis/.config/evolution/mail/folders/et-expanded-mbox:_home_travis_.local_share_evolution_mail_local_._23evolution_Trash
  mv /home/travis/.evolution/mail/config/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Spam /home/travis/.config/evolution/mail/folders/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Spam
  mv /home/travis/.evolution/mail/config/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Trash /home/travis/.config/evolution/mail/folders/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Trash
  mv /home/travis/.evolution/mail/config/et-expanded-mbox:_home_travis_.evolution_mail_local_Templates /home/travis/.config/evolution/mail/folders/et-expanded-mbox:_home_travis_.local_share_evolution_mail_local_Templates
  mv /home/travis/.evolution/mail/config/et-expanded-imap:__pi.boy.travis@imap.gmail.com_INBOX /home/travis/.config/evolution/mail/folders/et-expanded-imap:__pi.boy.travis@imap.gmail.com_INBOX
  mv /home/travis/.evolution/mail/config/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Starred /home/travis/.config/evolution/mail/folders/et-expanded-imap:__pi.boy.travis@imap.gmail.com__5bGmail_5d_Starred
  mv /home/travis/.evolution/mail/config/et-expanded-mbox:_home_travis_.evolution_mail_local_._23evolution_Junk /home/travis/.config/evolution/mail/folders/et-expanded-mbox:_home_travis_.local_share_evolution_mail_local_._23evolution_Junk
  rmdir /home/travis/.evolution/addressbook/config
  rmdir /home/travis/.evolution/addressbook/views
  rmdir /home/travis/.evolution/calendar/config
  rmdir /home/travis/.evolution/mail/config
  rmdir /home/travis/.evolution/mail/views
  rmdir /home/travis/.evolution/memos/config
  rmdir /home/travis/.evolution/memos/views
  rmdir /home/travis/.evolution/tasks/config
  mv /home/travis/.evolution/printing /home/travis/.config/evolution/printing.ini
Migrating local user data
  mv /home/travis/.evolution/mail/imap/pi.boy.travis@imap.gmail.com /home/travis/.local/share/evolution/mail/imap/pi.boy.travis@imap.gmail.com
  mv /home/travis/.evolution/mail/vfolder/folders.db /home/travis/.local/share/evolution/mail/vfolder/folders.db
  mv /home/travis/.evolution/mail/local/Drafts.cmeta /home/travis/.local/share/evolution/mail/local/Drafts.cmeta
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Templates.ibex.index /home/travis/.local/share/evolution/mail/local/Templates.ibex.index
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Inbox.ibex.index /home/travis/.local/share/evolution/mail/local/Inbox.ibex.index
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Sent /home/travis/.local/share/evolution/mail/local/Sent
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Templates.cmeta /home/travis/.local/share/evolution/mail/local/Templates.cmeta
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Templates /home/travis/.local/share/evolution/mail/local/Templates
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Drafts /home/travis/.local/share/evolution/mail/local/Drafts
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/folders.db /home/travis/.local/share/evolution/mail/local/folders.db
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Outbox.ibex.index /home/travis/.local/share/evolution/mail/local/Outbox.ibex.index
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Outbox /home/travis/.local/share/evolution/mail/local/Outbox
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Inbox.ibex.index.data /home/travis/.local/share/evolution/mail/local/Inbox.ibex.index.data
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Outbox.ibex.index.data /home/travis/.local/share/evolution/mail/local/Outbox.ibex.index.data
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Inbox.cmeta /home/travis/.local/share/evolution/mail/local/Inbox.cmeta
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/.#evolution.sbd /home/travis/.local/share/evolution/mail/local/.#evolution.sbd
  mv /home/travis/.evolution/mail/local/Outbox.cmeta /home/travis/.local/share/evolution/mail/local/Outbox.cmeta
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Sent.ibex.index.data /home/travis/.local/share/evolution/mail/local/Sent.ibex.index.data
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Drafts.ibex.index.data /home/travis/.local/share/evolution/mail/local/Drafts.ibex.index.data
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Sent.ibex.index /home/travis/.local/share/evolution/mail/local/Sent.ibex.index
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Drafts.ibex.index /home/travis/.local/share/evolution/mail/local/Drafts.ibex.index
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Templates.ibex.index.data /home/travis/.local/share/evolution/mail/local/Templates.ibex.index.data
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Inbox /home/travis/.local/share/evolution/mail/local/Inbox
  FAILED: Destination file already exists
  mv /home/travis/.evolution/mail/local/Sent.cmeta /home/travis/.local/share/evolution/mail/local/Sent.cmeta
  FAILED: Destination file already exists
  rmdir /home/travis/.evolution/mail/local
  FAILED: Directory not empty (contents follows)
          Inbox
          Sent.cmeta
          Templates.cmeta
          Outbox.cmeta
          Templates.ibex.index.data
          Inbox.cmeta
          Templates.ibex.index
          Drafts.cmeta
          Sent
          Sent.ibex.index.data
          Templates
          Outbox
          Outbox.ibex.index
          Drafts
          folders.db
          Sent.ibex.index
          Inbox.ibex.index.data
          Drafts.ibex.index
          Outbox.ibex.index.data
          Inbox.ibex.index
          Drafts.ibex.index.data
  rmdir /home/travis/.evolution/mail/imap
  rmdir /home/travis/.evolution/mail/vfolder
  rmdir /home/travis/.evolution/tasks
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/travis/.evolution/mail
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/travis/.evolution/calendar
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/travis/.evolution/memos
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/travis/.evolution/addressbook
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/travis/.evolution/cache
  FAILED: Directory not empty (contents follows)
          addressbook
  mv /home/travis/.evolution/categories.xml /home/travis/.local/share/evolution/categories.xml
  FAILED: Destination file already exists
  mv /home/travis/.evolution/key3.db /home/travis/.local/share/evolution/key3.db
  mv /home/travis/.evolution/cert8.db /home/travis/.local/share/evolution/cert8.db
  mv /home/travis/.evolution/camel-cert.db /home/travis/.local/share/evolution/camel-cert.db
  mv /home/travis/.evolution/secmod.db /home/travis/.local/share/evolution/secmod.db

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution:5981): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:5981): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
Can't open file 'wordlist.db' in directory '/home/travis/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
2011-04-30 23:11:59,702 INFO     upgrading database to version 117
2011-04-30 23:11:59,900 INFO     upgrading database to version 118
2011-04-30 23:12:01,957 INFO     upgrading database to version 119
2011-04-30 23:12:02,191 INFO     closing database
2011-04-30 23:12:02,191 INFO     Vacuuming the db before shutting down.
2011-04-30 23:12:03,092 INFO     opening database /home/travis/.miro/sqlitedb
2011-04-30 23:12:03,100 TIMING   Database upgrade time: 295.567
2011-04-30 23:12:03,101 DBLOG    Upgraded database from version 110 to 119
2011-04-30 23:12:03,102 DBLOG    start database log entries
2011-04-30 23:12:03,105 DBLOG    * Sun May  2 13:37:00 2010: Upgraded database from version 104 to 110
2011-04-30 23:12:03,112 DBLOG    * Sat Apr 30 23:12:03 2011: Upgraded database from version 110 to 119
2011-04-30 23:12:03,112 DBLOG    end database log entries
2011-04-30 23:12:03,113 INFO     Loading video converters...

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


2011-04-30 23:12:03,286 INFO     setup tabs...
2011-04-30 23:12:03,292 INFO     setup theme...

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


2011-04-30 23:12:03,931 INFO     First time -- calling handler.

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/window.py:396: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self._window.add(widget._widget)
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/layout.py:44: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  padding=padding)
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/window.py:368: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self._window.show()
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Miro.real window size doesn't fit
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/layout.py:45: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  widget._widget.show()
2011-04-30 23:12:20,794 INFO     Checking movies directory '/home/travis/.miro/Movies/'...

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/window.py:589: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.vbox.pack_start(widget._widget, expand=True)

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/drawing.py:192: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  child_width, child_height = self.get_child().size_request()
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Miro.real window size doesn't fit
** (<unknown>:1482): DEBUG: TrayChild Accepted: Miro miro.real Miro.real

** (<unknown>:1482): WARNING **: Attempted to register a quicklist that was previously registered
2011-04-30 23:12:23,425 TIMING   idle (handling backend message: <miro.messages.TrackNewVideoCount object at 0xaa31ca0c>) too slow (1.012 secs)
** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/css/style.css?nonce=.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/css/rating.css?nonce=.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.min.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.form.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.corners.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/rating.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/miroguide.js?nonce=.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.preload-min.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/feature_rotate.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/hover.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.min.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.form.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.corners.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/rating.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/miroguide.js?nonce=.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/jquery.preload-min.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/popup/bottom.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/small_add_feed.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/feature_rotate.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ ran insecure content from http://s3.miroguide.com/static/js/hover.js.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/hills.jpg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/feedback.gif.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/top_bar_menu_bg.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/logo.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/logo.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/top_bar_search.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/audio_badge.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/load-indicator.gif.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/small_submit_search.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/lower_top_bar_bg.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/lower_top_bar_bg.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/genres_popdown_bottom.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/lower_top_bar_separator.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/lower_top_bar_separator.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/hover_menu.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/hover_menu.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/hover_menu_bg.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/menu_check.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/hover_menu_top.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/hover_menu_bottom.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/welcome_bottom.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/audio_badge.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/buttons/featured_left_button.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/buttons/featured_items_bg.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/featured_separator.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/195x130/14086.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/featured_img_bg.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/large_add_feed.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/195x130/112.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/195x130/9792.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/195x130/6765.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/195x130/2503.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/buttons/featured_right_button.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/big_search.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/big_search.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/item_bar_left_xl.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14152.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14141.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14140.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14596.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14137.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14115.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/12918.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/12905.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/12855.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/12781.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/9758.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/4170.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/4149.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/9965.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/9768.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/2031.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14122.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14135.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14059.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/media/thumbnails/97x65/14120.jpeg.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/ico_hd_tag_tiny.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/load-indicator.gif.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/load-indicator-bg.png.


2011-04-30 23:12:25,962 INFO     Starting auto downloader...
2011-04-30 23:12:26,150 WARNING  asked to delete '/media/Seagate/Miro/Apple-Keynotes/ipad.m4v' but it's not there.
2011-04-30 23:12:26,159 WARNING  asked to delete '/media/Seagate/Miro/Apple-Keynotes/apr2010_evt.m4v' but it's not there.
2011-04-30 23:12:26,168 WARNING  asked to delete '/media/Seagate/Miro/Apple-Keynotes/wwdc10_keynote.m4v' but it's not there.
2011-04-30 23:12:26,191 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST043_nmm_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,199 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST042_chameleon_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,213 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST041_catalytic_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,222 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST040_futureofnews_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,263 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST039_bokode_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,271 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST038_robots-rescue_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,279 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST037_roadie_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,287 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST036_extract_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,295 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST035_graspables_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,303 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST034_neurobio_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,311 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST033_scratch-mit_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,320 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST032_selectricity_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,330 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST031_wii-guitar_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,341 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST030_urban-pixels_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,350 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST029_urop-ml_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,358 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST028_physical-heart_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,366 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST027_civic-media_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,373 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST026_storied-navigation_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,381 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST025_roboscooter_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,389 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST024_design-elastic-mind_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,398 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST044_community_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,406 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST045_facesense_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,414 WARNING  asked to delete '/media/Seagate/Miro/LabCAST-HD/LabCAST046_icalm_AppleTV-1280x720.m4v' but it's not there.
2011-04-30 23:12:26,437 WARNING  asked to delete '/media/Seagate/Miro/Uploads-by-ubuntudevelopers/video.mp4' but it's not there.
2011-04-30 23:12:26,452 WARNING  asked to delete '/media/Seagate/Miro/Uploads-by-ubuntudevelopers/video.3.mp4' but it's not there.
2011-04-30 23:12:26,475 WARNING  asked to delete '/media/Seagate/Miro/Uploads-by-ubuntudevelopers/videoplayback-ip=24.0.0.0_sparams=id,expire,ip,ipbits,itag,algorithm,burst,fa.25_id=d598fe4113886f10.mp4' but it's not there.
2011-04-30 23:12:26,488 WARNING  asked to delete '/media/Seagate/Miro/Uploads-by-ubuntudevelopers/videoplayback-ip=24.0.0.0_sparams=id,expire,ip,ipbits,itag,algorithm,burst,fa.25_id=a5c594c4b5e8ff30.mp4' but it's not there.
2011-04-30 23:12:26,511 WARNING  asked to delete '/media/Seagate/Miro/Uploads-by-ubuntudevelopers/videoplayback-ip=24.0.0.0_sparams=id,expire,ip,ipbits,itag,algorithm,burst,fa.25_id=439632738447e8c3.mp4' but it's not there.
2011-04-30 23:12:26,522 WARNING  asked to delete '/media/Seagate/Miro/Uploads-by-ubuntudevelopers/videoplayback-ip=24.0.0.0_sparams=id,expire,ip,ipbits,itag,algorithm,burst,fa.25_id=5c7de62b5efab3cf.mp4' but it's not there.
2011-04-30 23:12:26,531 WARNING  asked to delete '/media/Seagate/Miro/Uploads-by-ubuntudevelopers/videoplayback-ip=24.0.0.0_sparams=id,expire,ip,ipbits,itag,algorithm,burst,fa.25_id=ca1775776b403ce8.mp4' but it's not there.
2011-04-30 23:12:26,545 WARNING  asked to delete '/media/Seagate/Miro/Macworld-Video/mwvodcast143.mp4' but it's not there.
2011-04-30 23:12:26,554 WARNING  asked to delete '/media/Seagate/Miro/Macworld-Video/mwvodcast144.mp4' but it's not there.
2011-04-30 23:12:26,563 WARNING  asked to delete '/media/Seagate/Miro/Macworld-Video/mwvodcast145.mp4' but it's not there.
2011-04-30 23:12:26,573 WARNING  asked to delete '/media/Seagate/Miro/Macworld-Video/mwvodcast148.mp4' but it's not there.
2011-04-30 23:12:26,619 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/LOST_FRIENDSTER_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,628 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/CHILDRENS_BOOK_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,635 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/LIL_WAYNE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,644 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/SHITTY_FORD_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,652 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/STOKED_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,660 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/ZOMBIE_REAGAN_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,668 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/ET_ALIEN_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,676 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/OBAMA_TELEPROMPTER_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,685 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/MODERN_WARFARE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,693 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/GLENN_BECK_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,713 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/ROOF_COLLAPSE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,720 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/MASCULINE_COSTUMES_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,728 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/BIDEN_SNEEZE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,737 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/STALKER_REPORTER_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,745 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/OBAMA_WILDFIRES_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,753 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/TEEN_SMOKING_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,762 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/OBAMA_FAMILY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,770 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/SEXUAL_ARSON_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,779 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/DADDYS_GUN_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,787 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/BAT_LOOSE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,795 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/NOUVEAU_POOR_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,804 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/PREEMPTIVE_CLINTON_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,812 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/9_11_MASTURBATION_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,820 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/LIONS_MENTORS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,828 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/****_SPILL_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,836 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/CONGO_STIMULUS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,845 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/BIDEN_HENNESSY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,853 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/ABORTION_LAW_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,861 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/LOST_FANS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,870 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/CAT_LOVE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,877 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/RETURN_TO_DRINKING_ITUNES2.mp4' but it's not there.
2011-04-30 23:12:26,886 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/RETROACTIVE_IMMUNITY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,895 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/SEX_WITH_WIFE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,903 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/DRUNK_WORM_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,913 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/LOVELESS_MARRIAGE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,922 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/BABY_SKULLS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,931 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/DENMARK_TOURISM_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,940 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/REALITY_SHOW_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,949 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/OBAMA_LIP_SYNC_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,958 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/DEATH_OF_NEWSPAPERS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,968 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/********_STORY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,979 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/SNAKE_ATTACK_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,989 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network--Video-/AIRBUD_ITUNES.mp4' but it's not there.
2011-04-30 23:12:26,998 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/SHAPESHIFTER_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,007 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/AIRBUD_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,016 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/SNAKE_ATTACK_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,026 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/********_STORY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,035 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/DEATH_OF_NEWSPAPERS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,045 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/OBAMA_LIP_SYNC_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,055 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/REALITY_SHOW_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,065 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/DENMARK_TOURISM_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,078 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/BABY_SKULLS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,088 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/LOVELESS_MARRIAGE_ITUNES.mp4' but it's not there.
** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/small_add_button.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/buttons/preview-cap.png.


2011-04-30 23:12:27,098 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/DRUNK_WORM_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,107 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/CAT_LOVE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,116 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/RETURN_TO_DRINKING_ITUNES2.mp4' but it's not there.
2011-04-30 23:12:27,125 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/RETROACTIVE_IMMUNITY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,133 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/SEX_WITH_WIFE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,143 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/LOST_FANS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,153 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/ABORTION_LAW_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,163 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/BIDEN_HENNESSY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,173 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/CONGO_STIMULUS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,183 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/****_SPILL_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,199 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/LOST_FRIENDSTER_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,210 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/CHILDRENS_BOOK_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,220 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/LIL_WAYNE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,231 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/STOKED_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,240 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/STOUFFERS_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,248 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/GORILLA_MORTALITY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,258 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/FENWAY_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,267 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/RACIST_ASSASSINATION_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,277 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/DEA_SON_BUST_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,287 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/JUICE_INFOMERCIAL_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,297 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/HIDING_PORN_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,306 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/IRON_MAN_2_IPHONE_AD.mp4' but it's not there.
2011-04-30 23:12:27,315 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/IRON_MAN_2_IPHONE_AD.1.mp4' but it's not there.
2011-04-30 23:12:27,324 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/IRON_MAN_2_IPHONE_AD.2.mp4' but it's not there.
2011-04-30 23:12:27,333 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/star-jockey-expected-to-brutally-whip-horse-to-ken-podcast.mp4' but it's not there.
2011-04-30 23:12:27,344 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/live-feed-obama-attends-the-white-house-maintenanc-podcast.mp4' but it's not there.
2011-04-30 23:12:27,354 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/BARRYMORE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,364 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/advocacy-group-mothers-have-a-right-to-expose-milk-podcast.mp4' but it's not there.
2011-04-30 23:12:27,372 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/joad-show-promo-podcast.mp4' but it's not there.
2011-04-30 23:12:27,381 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/GOOGLE_PHONE_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,392 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/christian-groups-biblical-armageddon-must-be-taugh-podcast.mp4' but it's not there.
2011-04-30 23:12:27,402 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/IHOP_ITUNES2.mp4' but it's not there.
2011-04-30 23:12:27,411 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/FIREFIGHTER_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,421 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/boston-globe-tailors-print-edition-for-three-remai-podcast.mp4' but it's not there.
2011-04-30 23:12:27,431 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/shaman_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,441 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/soccer-officially-announces-it-is-gay-podcast.mp4' but it's not there.
2011-04-30 23:12:27,450 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/ANTHEM_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,460 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/BLITZER_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,470 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/ANISTON_AFRICA_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,482 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/INT_PARROT_ITUNES.mp4' but it's not there.
2011-04-30 23:12:27,492 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/overcome-money-worries-by-visualizing-them-as-a-gr-podcast.mp4' but it's not there.
2011-04-30 23:12:27,502 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/TIME_FOR_ADULTS_ITUNES_new.mp4' but it's not there.
2011-04-30 23:12:27,511 WARNING  asked to delete '/media/Seagate/Miro/Onion-News-Network/TESTS_BIASED_ITUNES_new.mp4' but it's not there.
2011-04-30 23:12:27,526 WARNING  asked to delete '/media/Seagate/Miro/TEDTalks--hd-/CraigVenter_2010P_480.mp4' but it's not there.
2011-04-30 23:12:27,540 TIMING   idle (on_frontend_started() (using idle_iterator)) too slow (1.407 secs)
** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/buttons/preview-bg.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/popup/right_arrow.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/popup/border.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/popup/top.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/popup/left_arrow.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/popup/right_shadow.png.


2011-04-30 23:12:27,849 INFO     Starting movie data updates
2011-04-30 23:12:27,892 INFO     this platform has autoupdate disabled.  skipping.
2011-04-30 23:12:27,894 INFO     Running movie data process: ('/usr/bin/python2.7', '/usr/lib/pymodules/python2.7/miro/plat/renderers/gst_extractor.py', '/media/Seagate/Miro/Apple-Keynotes/unknown', '/home/travis/.miro/icon-cache/extracted/unknown.HbqTx.png')
** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/misc_button_med_cap.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/misc_button_med.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/big_no-nos.png.


** Message: console message:  @1: The page at https://www.miroguide.com/ displayed insecure content from http://s3.miroguide.com/static/images/big_stars.png.


2011-04-30 23:12:28,166 INFO     checking https://www.miroguide.com/
2011-04-30 23:12:28,413 INFO     Running movie data process: ('/usr/bin/python2.7', '/usr/lib/pymodules/python2.7/miro/plat/renderers/gst_extractor.py', '/media/Seagate/Miro/Lab-Rats---QuickTime-720x480/block-URL=httpmedia.libsyn.commedialabratstvlabrats-206.mov_IP=170.158.38.254_CAT=IRADIO_USER=IP.cgi.mov', '/home/travis/.miro/icon-cache/extracted/block-URL=httpmedia.libsyn.commedialabratstvlabrats-206.mov_IP=170.158.38.254_CAT=IRADIO_USER=IP.cgi.mov.vrflQ.png')
2011-04-30 23:12:28,753 INFO     Running movie data process: ('/usr/bin/python2.7', '/usr/lib/pymodules/python2.7/miro/plat/renderers/gst_extractor.py', '/media/Seagate/Miro/Macworld-Video/block-URL=httpwww.pheedo.comefe9cdebcec0c606dbca2abd633d763b8mwvodcast139.mp4_IP=170.158.38.254_.cgi.mp4', '/home/travis/.miro/icon-cache/extracted/block-URL=httpwww.pheedo.comefe9cdebcec0c606dbca2abd633d763b8mwvodcast139.mp4_IP=170.158.38.254_.cgi.mp4.EyaeZ.png')
2011-04-30 23:12:29,178 INFO     Running movie data process: ('/usr/bin/python2.7', '/usr/lib/pymodules/python2.7/miro/plat/renderers/gst_extractor.py', '/media/Seagate/Miro/Hak5--HD-MP4-/hak5--0809--test--hd.h264.mp4', '/home/travis/.miro/icon-cache/extracted/hak5--0809--test--hd.h264.mp4.MdDxB.png')
2011-04-30 23:12:29,977 INFO     updating http://www.apple.com/podcasts/apple_keynotes/apple_keynotes.xml
2011-04-30 23:12:29,986 INFO     updating http://feeds.media.mit.edu/labcast-hd?format=xml
2011-04-30 23:12:29,990 INFO     updating http://gdata.youtube.com/feeds/api/users/ubuntudevelopers/uploads?orderby=updated
2011-04-30 23:12:30,493 INFO     updating http://feeds.feedburner.com/meetthegimp
2011-04-30 23:12:32,340 INFO     updating http://rss.macworld.com/macworld/weblogs/mwvodcast
2011-04-30 23:12:32,377 TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.media.mit.edu/labcast-hd?format=xml)) too slow (0.857 secs)
2011-04-30 23:12:33,209 INFO     updating http://linuxjournal.blip.tv/rss/itunes/
2011-04-30 23:12:33,382 TIMING   idle (Thread Pool Callback (Feedparser callback - http://gdata.youtube.com/feeds/api/users/ubuntudevelopers/uploads?orderby=updated)) too slow (0.602 secs)
2011-04-30 23:12:34,368 INFO     updating http://labratstv.video.butterscotch.com/quicktime
2011-04-30 23:12:34,375 TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/meetthegimp)) too slow (0.645 secs)
2011-04-30 23:12:35,374 INFO     Launching Downloader Daemon
2011-04-30 23:12:35,464 INFO     libtorrent: 0.15.5.0
2011-04-30 23:12:35,465 INFO     pycurl:     libcurl/7.21.3 GnuTLS/2.8.6 zlib/1.2.3.4 libidn/1.18
2011-04-30 23:12:35,560 INFO     Daemon ready
2011-04-30 23:12:35,560 INFO     libtorrent:  0.15.5.0
2011-04-30 23:12:35,561 INFO     pycurl:      libcurl/7.21.3 GnuTLS/2.8.6 zlib/1.2.3.4 libidn/1.18
2011-04-30 23:12:37,877 INFO     updating http://feeds.theonion.com/OnionNewsNetwork
2011-04-30 23:12:38,087 TIMING   feed update for: http://rss.macworld.com/macworld/weblogs/mwvodcast too slow (1.895 secs)
2011-04-30 23:12:38,087 TIMING   idle (Thread Pool Callback (Feedparser callback - http://rss.macworld.com/macworld/weblogs/mwvodcast)) too slow (1.896 secs)
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:142: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
2011-04-30 23:12:40,996 INFO     updating http://feeds.feedburner.com/tedtalksHD
2011-04-30 23:12:41,621 TIMING   feed update for: http://feeds.theonion.com/OnionNewsNetwork too slow (1.969 secs)
2011-04-30 23:12:41,621 TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.theonion.com/OnionNewsNetwork)) too slow (1.969 secs)
2011-04-30 23:12:42,445 INFO     updating http://feeds2.feedburner.com/Category5_480p_H264?format=xml
2011-04-30 23:12:43,775 INFO     updating http://revision3.com/hak5/feed/MP4-High-Definition
2011-04-30 23:12:43,782 TIMING   feed update for: http://labratstv.video.butterscotch.com/quicktime too slow (1.220 secs)
2011-04-30 23:12:43,782 TIMING   idle (Thread Pool Callback (Feedparser callback - http://labratstv.video.butterscotch.com/quicktime)) too slow (1.221 secs)
2011-04-30 23:12:48,519 INFO     start_download: http://dl.meetthegimp.org/meetthegimp159.mp4
2011-04-30 23:12:49,635 INFO     start_download: http://feeds.theonion.com/~r/OnionNewsNetwork/~5/sqvAxRHsMvs/podcast_redirect.mp4
2011-04-30 23:12:51,158 INFO     updating http://doctype.tv/rss
2011-04-30 23:12:51,199 TIMING   idle (Thread Pool Callback (Feedparser callback - http://revision3.com/hak5/feed/MP4-High-Definition)) too slow (0.881 secs)
2011-04-30 23:12:53,165 TIMING   feed update for: http://feeds.feedburner.com/tedtalksHD too slow (1.810 secs)
2011-04-30 23:12:53,166 TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/tedtalksHD)) too slow (1.811 secs)
2011-04-30 23:12:55,178 TIMING   feed update for: http://feeds2.feedburner.com/Category5_480p_H264?format=xml too slow (1.743 secs)
2011-04-30 23:12:55,179 TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds2.feedburner.com/Category5_480p_H264?format=xml)) too slow (1.744 secs)
2011-04-30 23:12:56,971 INFO     move_to_movies_directory: filename is /home/travis/.miro/Movies/Incomplete Downloads/podcast_redirect.mp4.part
2011-04-30 23:12:57,057 INFO     Running movie data process: ('/usr/bin/python2.7', '/usr/lib/pymodules/python2.7/miro/plat/renderers/gst_extractor.py', '/home/travis/.miro/Movies/Onion-News-Network/despite-repeated-calls-for-him-to-do-so-donald-tru-podcast.mp4', '/home/travis/.miro/icon-cache/extracted/despite-repeated-calls-for-him-to-do-so-donald-tru-podcast.mp4.CDtPC.png')
2011-04-30 23:12:58,665 INFO     start_download: http://video.ted.com/talk/podcast/2010P/Ink/ArvindGupta_2010P-480p.mp4

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
2011-04-30 23:13:03,128 INFO     updating http://www.apple.com/podcasts/apple_keynotes/apple_keynotes.xml
2011-04-30 23:13:03,137 INFO     updating http://feeds.media.mit.edu/labcast-hd?format=xml
2011-04-30 23:13:03,149 INFO     updating http://gdata.youtube.com/feeds/api/users/ubuntudevelopers/uploads?orderby=updated
2011-04-30 23:13:03,211 INFO     updating http://feeds.feedburner.com/meetthegimp
2011-04-30 23:13:03,290 INFO     updating http://rss.macworld.com/macworld/weblogs/mwvodcast
2011-04-30 23:13:05,108 INFO     updating http://linuxjournal.blip.tv/rss/itunes/
2011-04-30 23:13:05,430 INFO     updating http://labratstv.video.butterscotch.com/quicktime
2011-04-30 23:13:06,146 INFO     updating http://feeds.theonion.com/OnionNewsNetwork
2011-04-30 23:13:06,361 INFO     updating http://feeds.feedburner.com/tedtalksHD
2011-04-30 23:13:06,777 INFO     updating http://feeds2.feedburner.com/Category5_480p_H264?format=xml
2011-04-30 23:13:06,871 INFO     updating http://revision3.com/hak5/feed/MP4-High-Definition
2011-04-30 23:13:09,472 INFO     updating http://doctype.tv/rss
2011-04-30 23:13:12,131 TIMING   idle (Thread Pool Callback (Feedparser callback - http://labratstv.video.butterscotch.com/quicktime)) too slow (0.587 secs)
2011-04-30 23:15:25,072 INFO     move_to_movies_directory: filename is /home/travis/.miro/Movies/Incomplete Downloads/ArvindGupta_2010P-480p.mp4.part
2011-04-30 23:15:25,148 INFO     Running movie data process: ('/usr/bin/python2.7', '/usr/lib/pymodules/python2.7/miro/plat/renderers/gst_extractor.py', '/home/travis/.miro/Movies/TEDTalks--hd-/ArvindGupta_2010P-480p.mp4', '/home/travis/.miro/icon-cache/extracted/ArvindGupta_2010P-480p.mp4.gfPZV.png')
2011-04-30 23:19:00,928 INFO     move_to_movies_directory: filename is /home/travis/.miro/Movies/Incomplete Downloads/meetthegimp159.mp4.part
2011-04-30 23:19:00,995 INFO     Running movie data process: ('/usr/bin/python2.7', '/usr/lib/pymodules/python2.7/miro/plat/renderers/gst_extractor.py', '/home/travis/.miro/Movies/Meet-the-GIMP/meetthegimp159.mp4', '/home/travis/.miro/icon-cache/extracted/meetthegimp159.mp4.QwdOn.png')
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


NOTE: child process received `Goodbye', closing down

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1491): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: banshee window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
2011-04-30 23:29:04,007 INFO     Shutting down video conversions manager
2011-04-30 23:29:04,010 INFO     Shutting down Downloader...
2011-04-30 23:29:04,011 INFO     Shutting down downloaders...
2011-04-30 23:29:04,012 INFO     Shutting down torrent session...
2011-04-30 23:29:04,012 INFO     shutdown() finished
2011-04-30 23:29:04,015 INFO     Shutdown complete
2011-04-30 23:29:04,068 INFO     Shutting down libCURL thread
2011-04-30 23:29:04,070 INFO     Writing HTTP passwords
2011-04-30 23:29:04,075 INFO     Shutting down event loop thread
2011-04-30 23:29:04,076 INFO     Closing Database...
2011-04-30 23:29:04,076 INFO     closing database
2011-04-30 23:29:04,077 INFO     Vacuuming the db before shutting down.

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
2011-04-30 23:29:05,417 INFO     Shutting down...
2011-04-30 23:29:05,417 TIMING   WARNING: Running: <miro.dl_daemon.command.ShutDownResponseCommand object at 0xa25464c> too slow (1.367 secs)
2011-04-30 23:29:05,418 INFO     Saving preferences...
2011-04-30 23:29:05,418 INFO     Shutting down icon cache updates
2011-04-30 23:29:05,418 INFO     Shutting down movie data updates
2011-04-30 23:29:05,419 INFO     Done shutting down.
2011-04-30 23:29:05,419 INFO     Remaining threads are:
2011-04-30 23:29:05,419 INFO     <_MainThread(MainThread, started -1216555328)>

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:6873): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

** (<unknown>:1482): WARNING **: bool IconLoader::ProcessIconNameTask(IconLoader::IconLoaderTask*): Unable to load icon atanks at size 48
** (<unknown>:1482): DEBUG: Cannot activate anything
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** (gnome-system-monitor:7069): WARNING **: SELinux was found but is not enabled.

** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Gnome-system-monitor window size doesn't fit
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:7075): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1491): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: Firefox window size doesn't fit

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1497): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1482): DEBUG: MaximizeIfBigEnough: banshee window size doesn't fit

** (<unknown>:1482): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1482): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1482): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1482): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```

This is a Dell Inspiron 1520, lspci output is in my first post. Once the freeze occurs, I can move the mouse, that is all. Windows, desktop, Unity panel, everything is there, I just can't interact with it at all, even the seconds on the clock stop. I can ctrl + alt + F1 and the console is perfectly usable. Htop shows no outrageous memory or CPU usage. I can't associate it with any peripherals or anything like that; it isn't caused by the screensaver coming on or closing the lid. The only way to reproduce it is to wait for it to randomly occur again, usually between half an hour and four hours. I have Ubuntu 11.04 on several other computers, and this is the only one it happens to. I wasn't sure where Unity keeps it's logfiles, if it does at all, and I didn't have the chance to gdb. if there's anything else I can post to help, please don't hesitate to ask.

---

### Post by corncob on 2011-05-01
Maybe somebody who can interpret those outputs will jump in here but in the meanwhile, since you're blaming it on Unity, try using the classic desktop and see if it still happens.  If so, I would suspect your hardware and would disconnect any peripherals, drives, printers, etc by way of trouble shooting.

---

### Post by pi.boy.travis on 2011-05-01
I think I've found the corresponding bug report:

[https://bugs.launchpad.net/unity/+bug/760769](https://bugs.launchpad.net/unity/+bug/760769)


I'll log into the Ubuntu Classic desktop next time it happens and see if I can reproduce the bug there.

---

### Post by pi.boy.travis on 2011-05-03
I upgraded the kernel to 2.6.39, and it ran very nicely, but it didn't fix the bug. . . I'm honestly not even sure which package has the bug, I'm more of a server kind of guy.

---

### Post by GreatKeyHunter on 2011-05-04
something similar happens to me after i re-log after the screen saver.  except it works fine, but moving a window around the desktop becomes very laggy.

---

### Post by Nickjpost on 2011-05-04
pi.boy.travis, 

What type of video card are you using on your machine? Is it ATI?

---

### Post by sadaruwan12 on 2011-05-04
Same thing happens to but I just type in my password and press enter. I can log in to my ubuntu session.

---

### Post by pi.boy.travis on 2011-05-04
> **Nickjpost said:**
> pi.boy.travis, 

What type of video card are you using on your machine? Is it ATI?

Nope, Intel integrated. But from the looks of the bug report it's affecting all sorts of cards. . .

---

### Post by K_45 on 2011-05-04
Have you ruled out hardware? Maybe try running Memtest and HItachi's DFT to check the RAM and HDD. Maybe try a different distro?

---

### Post by pi.boy.travis on 2011-05-04
> **K_45 said:**
> Have you ruled out hardware? Maybe try running Memtest and HItachi's DFT to check the RAM and HDD. Maybe try a different distro?

Definitely not hardware. It doesn't happen using the Ubuntu Classic Desktop, and I've had no such problem with the Debian install that is also on this machine. In the bug report there is a link to an upstream kernel build that solves the issue, I'm going to give that a shot when I get the chance. It's on it's way to being SRU'd.

---

### Post by wyth on 2011-06-24
Older thread and most people probably found their answer on the bug report, but just in case:

It seems to be a Compiz issue, and one thing to try is to turn of Sync to VBlank.

If you're using the the CompizConfig Settings Manager, it's under General > OpenGL. Just make sure it isn't ticked on.

If you don't have the CompizConfig Settings Manager installed, first ask yourself where you went wrong. 

Then open gconf-editor -- either under Applications > System Tools > Configuration Editor, or just hit alt+f2 and enter gconf-editor in the Run Application dialog.

You'll find the necessary key in the following location:
```
apps > compiz-1 > plugins > opengl > screen0 > options 

```

In there you'll see sync_to_vblank, and just make sure it isn't ticked on.

It may work, it may not; I'm not using Unity, so I can't speak to that. But I know Sync to VBlank seems to be turned on by default (clean install), and until I turned it off, this issue plagued me for weeks.

---

### Post by ZaHACKieL on 2011-07-02
I'll try you solution wyth. Just want to say that I'm having the same issue under classic desktop with Compiz and Nvidia GT555M 3GB.

---

### Post by wildmanne39 on 2011-07-02
> **ZaHACKieL said:**
> I'll try you solution wyth. Just want to say that I'm having the same issue under classic desktop with Compiz and Nvidia GT555M 3GB.Hi, the issues with compiz in unity and in classic is two different issues, in classic you need to revert compiz to the previous version, here is a link on how to do it and why.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by amjjawad on 2011-07-02
Personally, I never liked 11.04 but that's me.
I installed the latest release (11.04 32-bit) and I couldn't even login to Unity or use it.

I'm logging in to Classic Desktop with no effect and it's working but much slower than 10.04.

If stability is what you seek, then 10.04.2 is your best choice.
That's what I would do.

Unity is not mature yet as GNOME. Perhaps only time will tell whether it will be successful like GNOME or not?!

---

### Post by ZaHACKieL on 2011-07-04
> **wildmanne39 said:**
> Hi, the issues with compiz in unity and in classic is two different issues, in classic you need to revert compiz to the previous version, here is a link on how to do it and why.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

Thanx man. Anyway I tried the former solution and it worked but I'll also do what you say because that my be related to some freezes I'm having. That's been discused here:

[http://ubuntuforums.org/showthread.php?t=1754844](http://ubuntuforums.org/showthread.php?t=1754844)

Thanx for the tip!! :D

---

### Post by wildmanne39 on 2011-07-05
> **ZaHACKieL said:**
> Thanx man. Anyway I tried the former solution and it worked but I'll also do what you say because that my be related to some freezes I'm having. That's been discused here:

[http://ubuntuforums.org/showthread.php?t=1754844](http://ubuntuforums.org/showthread.php?t=1754844)

Thanx for the tip!! :DHi, here is a link for freezing issues maybe it will help.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

