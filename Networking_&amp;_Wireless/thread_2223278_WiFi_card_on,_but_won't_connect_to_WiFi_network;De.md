---
title: "WiFi card on, but won't connect to WiFi network;Dell Inspiron E1505(ethernet working)"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by themik2 on 2014-05-10
[COLOR=#333333][FONT=UbuntuRegular]Followed these threads:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://ubuntuforums.org/showthread.php?t=2153290](http://ubuntuforums.org/showthread.php?t=2153290)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Getting Wireless to Work, Dell Inspiron E1505 (bcm4311)]("http://askubuntu.com/questions/271044/getting-wireless-to-work-dell-inspiron-e1505-bcm4311")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Unable to connect to wifi on a Dell Inspiron e1505]("http://askubuntu.com/questions/90712/unable-to-connect-to-wifi-on-a-dell-inspiron-e1505")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Being new to linux/ubuntu, i was still able to follow the threads above and get the ethernet connection to work. **I also got the wifi card turned on but it will not connect with my wifi network.** 

Full wifi status readout is available at:  **pastebin.ubuntu.com/7404098**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Please help. Thanks.[/FONT][/COLOR]

---

### Post by twinkel1961 on 2014-05-10
Have you tried to associate your network card with your router / access point?

you need to enter the passphrase for your network in Network Manager (in the system bar)

if so, what is the output of /var/log/syslog when it' s tryig to do that?

---

### Post by themik2 on 2014-05-10
Thanks for replying.
I am new to this so the terminology is not something I'm familar with.
But I went to system settings and typed in the password for the router and tried to connect without success.
I researched what a /var/log/syslog is and did a sudo gedit on that.
I came up with a very long result of which I will copy and paste just today's results below:
" May 10 10:05:37 yw-MM061 kernel: [ 1067.444540] PM: Syncing filesystems ... done.
May 10 10:05:37 yw-MM061 kernel: [ 1067.684255] PM: Preparing system for mem sleep
May 10 10:05:37 yw-MM061 kernel: [ 1067.684495] Freezing user space processes ... (elapsed 0.003 seconds) done.
May 10 10:05:37 yw-MM061 kernel: [ 1067.688161] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
May 10 10:05:37 yw-MM061 kernel: [ 1067.689361] PM: Entering mem sleep
May 10 10:05:37 yw-MM061 kernel: [ 1067.689380] Suspending console(s) (use no_console_suspend to debug)
May 10 10:05:37 yw-MM061 kernel: [ 1067.689705] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 10 10:05:37 yw-MM061 kernel: [ 1067.689942] sd 0:0:0:0: [sda] Stopping disk
May 10 10:05:37 yw-MM061 kernel: [ 1068.660069] PM: suspend of devices complete after 970.493 msecs
May 10 10:05:37 yw-MM061 kernel: [ 1068.660176] PM: late suspend of devices complete after 0.103 msecs
May 10 10:05:37 yw-MM061 kernel: [ 1068.694351] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.710277] uhci_hcd 0000:00:1d.3: System wakeup enabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.712533] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.714686] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.716885] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.717025] PM: noirq suspend of devices complete after 56.845 msecs
May 10 10:05:37 yw-MM061 kernel: [ 1068.717295] ACPI: Preparing to enter system sleep state S3
May 10 10:05:37 yw-MM061 kernel: [ 1068.721104] PM: Saving platform NVS memory
May 10 10:05:37 yw-MM061 kernel: [ 1068.721106] Disabling non-boot CPUs ...
May 10 10:05:37 yw-MM061 kernel: [ 1068.721106] ACPI: Low-level resume complete
May 10 10:05:37 yw-MM061 kernel: [ 1068.721106] PM: Restoring platform NVS memory
May 10 10:05:37 yw-MM061 kernel: [ 1068.721106] Force enabled HPET at resume
May 10 10:05:37 yw-MM061 kernel: [ 1068.721106] ACPI: Waking up from system sleep state S3
May 10 10:05:37 yw-MM061 kernel: [ 1068.778197] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.780175] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.782075] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.783975] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.797927] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
May 10 10:05:37 yw-MM061 kernel: [ 1068.860069] firewire_ohci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
May 10 10:05:37 yw-MM061 kernel: [ 1068.860071] firewire_ohci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
May 10 10:05:37 yw-MM061 kernel: [ 1068.908178] PM: noirq resume of devices complete after 160.735 msecs
May 10 10:05:37 yw-MM061 kernel: [ 1068.908304] PM: early resume of devices complete after 0.092 msecs
May 10 10:05:37 yw-MM061 kernel: [ 1068.993168] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
May 10 10:05:37 yw-MM061 kernel: [ 1068.993414] usb usb2: root hub lost power or was reset
May 10 10:05:37 yw-MM061 kernel: [ 1068.993593] usb usb3: root hub lost power or was reset
May 10 10:05:37 yw-MM061 kernel: [ 1068.993772] usb usb4: root hub lost power or was reset
May 10 10:05:37 yw-MM061 kernel: [ 1068.993948] usb usb5: root hub lost power or was reset
May 10 10:05:37 yw-MM061 kernel: [ 1068.995538] ata1.00: _GTF evaluation failed (AE 0x1001)
May 10 10:05:37 yw-MM061 kernel: [ 1068.995566] ata2.00: _GTF evaluation failed (AE 0x1001)
May 10 10:05:37 yw-MM061 kernel: [ 1069.508302] ata2.00: configured for UDMA/33
May 10 10:05:37 yw-MM061 kernel: [ 1069.548074] firewire_core 0000:03:01.0: rediscovered device fw0
May 10 10:05:37 yw-MM061 kernel: [ 1070.516436] ata1.00: configured for UDMA/100
May 10 10:05:37 yw-MM061 kernel: [ 1070.517095] sd 0:0:0:0: [sda] Starting disk
May 10 10:05:37 yw-MM061 kernel: [ 1070.552148] PM: resume of devices complete after 1643.839 msecs
May 10 10:05:37 yw-MM061 kernel: [ 1070.552361] PM: Finishing wakeup.
May 10 10:05:37 yw-MM061 kernel: [ 1070.552363] Restarting tasks ... done.
May 10 10:05:37 yw-MM061 kernel: [ 1070.892471] video LNXVIDEO:01: Restoring backlight state
May 10 10:05:37 yw-MM061 anacron[3864]: Anacron 2.3 started on 2014-05-10
May 10 10:05:37 yw-MM061 anacron[3864]: Will run job `cron.daily' in 5 min.
May 10 10:05:37 yw-MM061 anacron[3864]: Will run job `cron.weekly' in 10 min.
May 10 10:05:37 yw-MM061 anacron[3864]: Jobs will be executed sequentially
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> wake requested (sleeping: yes  enabled: yes)
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> waking up and re-enabling...
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0): bringing up device.
May 10 10:05:38 yw-MM061 kernel: [ 1071.795919] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0): preparing device.
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0): deactivating device (reason 'managed') [2]
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> NetworkManager state is now CONNECTED_GLOBAL
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 10:05:38 yw-MM061 kernel: [ 1071.882788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (eth0): bringing up device.
May 10 10:05:38 yw-MM061 kernel: [ 1071.893317] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (eth0): preparing device.
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (eth0): deactivating device (reason 'managed') [2]
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> NetworkManager state is now DISCONNECTED
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0) supports 4 scan SSIDs
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: starting -> ready
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 10 10:05:38 yw-MM061 NetworkManager[714]: <warn> Trying to remove a non-existant call id.
May 10 10:05:38 yw-MM061 wpa_supplicant[794]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
May 10 10:05:38 yw-MM061 wpa_supplicant[794]: wlan0: Reject scan trigger since one is already pending
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: ready -> disconnected
May 10 10:05:38 yw-MM061 NetworkManager[714]: <info> (wlan0) supports 4 scan SSIDs
May 10 10:05:39 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: disconnected -> inactive
May 10 10:06:01 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 10 10:07:25 yw-MM061 dbus[518]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
May 10 10:07:25 yw-MM061 dbus[518]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) starting connection 'MASUS'
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> NetworkManager state is now CONNECTING
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0/wireless): connection 'MASUS' has security, and secrets exist.  No new secrets needed.
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Config: added 'ssid' value 'MASUS'
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Config: added 'scan_ssid' value '1'
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Config: added 'psk' value '<omitted>'
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> Config: set interface ap_scan to 1
May 10 10:08:30 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: inactive -> scanning
May 10 10:08:55 yw-MM061 NetworkManager[714]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
May 10 10:08:55 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
May 10 10:08:55 yw-MM061 NetworkManager[714]: <info> NetworkManager state is now DISCONNECTED
May 10 10:08:55 yw-MM061 NetworkManager[714]: <warn> Activation (wlan0) failed for connection 'MASUS'
May 10 10:08:55 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 10 10:08:55 yw-MM061 NetworkManager[714]: <info> (wlan0): deactivating device (reason 'none') [0]
May 10 10:08:54 yw-MM061 wpa_supplicant[794]: message repeated 8 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
May 10 10:08:55 yw-MM061 wpa_supplicant[794]: wlan0: Reject scan trigger since one is already pending
May 10 10:08:55 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: scanning -> disconnected
May 10 10:08:55 yw-MM061 NetworkManager[714]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 10 10:08:58 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 10 10:16:40 yw-MM061 dbus[518]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
May 10 10:16:40 yw-MM061 dbus[518]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 10 10:17:01 yw-MM061 CRON[4055]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) starting connection 'MASUS'
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> NetworkManager state is now CONNECTING
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0/wireless): connection 'MASUS' has security, and secrets exist.  No new secrets needed.
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Config: added 'ssid' value 'MASUS'
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Config: added 'scan_ssid' value '1'
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Config: added 'psk' value '<omitted>'
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> Config: set interface ap_scan to 1
May 10 10:21:00 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 10 10:21:13 yw-MM061 wpa_supplicant[794]: message repeated 16 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
May 10 10:21:14 yw-MM061 wpa_supplicant[794]: wlan0: SME: Trying to authenticate with c8:60:00:e7:d5:10 (SSID='MASUS' freq=2412 MHz)
May 10 10:21:14 yw-MM061 kernel: [ 2007.550601] wlan0: authenticate with c8:60:00:e7:d5:10
May 10 10:21:14 yw-MM061 kernel: [ 2007.550879] wlan0: send auth to c8:60:00:e7:d5:10 (try 1/3)
May 10 10:21:14 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 10 10:21:14 yw-MM061 kernel: [ 2007.752110] wlan0: send auth to c8:60:00:e7:d5:10 (try 2/3)
May 10 10:21:14 yw-MM061 wpa_supplicant[794]: wlan0: Trying to associate with c8:60:00:e7:d5:10 (SSID='MASUS' freq=2412 MHz)
May 10 10:21:14 yw-MM061 kernel: [ 2007.758264] wlan0: authenticated
May 10 10:21:14 yw-MM061 kernel: [ 2007.760079] wlan0: associate with c8:60:00:e7:d5:10 (try 1/3)
May 10 10:21:14 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 10 10:21:14 yw-MM061 kernel: [ 2007.964075] wlan0: associate with c8:60:00:e7:d5:10 (try 2/3)
May 10 10:21:14 yw-MM061 kernel: [ 2008.168075] wlan0: associate with c8:60:00:e7:d5:10 (try 3/3)
May 10 10:21:15 yw-MM061 kernel: [ 2008.372069] wlan0: association with c8:60:00:e7:d5:10 timed out
May 10 10:21:15 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: associating -> disconnected
May 10 10:21:15 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 10 10:21:15 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 10 10:21:21 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 10 10:21:22 yw-MM061 wpa_supplicant[794]: wlan0: SME: Trying to authenticate with c8:60:00:e7:d5:10 (SSID='MASUS' freq=2412 MHz)
May 10 10:21:22 yw-MM061 kernel: [ 2015.680994] wlan0: authenticate with c8:60:00:e7:d5:10
May 10 10:21:22 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 10 10:21:22 yw-MM061 kernel: [ 2015.692584] wlan0: send auth to c8:60:00:e7:d5:10 (try 1/3)
May 10 10:21:22 yw-MM061 kernel: [ 2015.896087] wlan0: send auth to c8:60:00:e7:d5:10 (try 2/3)
May 10 10:21:22 yw-MM061 kernel: [ 2016.100114] wlan0: send auth to c8:60:00:e7:d5:10 (try 3/3)
May 10 10:21:22 yw-MM061 kernel: [ 2016.304116] wlan0: authentication with c8:60:00:e7:d5:10 timed out
May 10 10:21:22 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
May 10 10:21:23 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 10 10:21:23 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 10 10:21:25 yw-MM061 NetworkManager[714]: <warn> Activation (wlan0/wireless): association took too long.
May 10 10:21:25 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 10:21:25 yw-MM061 NetworkManager[714]: <warn> Activation (wlan0/wireless): asking for new secrets
May 10 10:21:25 yw-MM061 NetworkManager[714]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 10 10:21:25 yw-MM061 NetworkManager[714]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 10 10:21:29 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: scanning -> inactive
May 10 10:21:31 yw-MM061 NetworkManager[714]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Activation (wlan0/wireless): connection 'MASUS' has security, and secrets exist.  No new secrets needed.
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Config: added 'ssid' value 'MASUS'
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Config: added 'scan_ssid' value '1'
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Config: added 'psk' value '<omitted>'
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> Config: set interface ap_scan to 1
May 10 10:21:31 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: inactive -> scanning
May 10 10:21:31 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 10 10:21:32 yw-MM061 wpa_supplicant[794]: wlan0: SME: Trying to authenticate with c8:60:00:e7:d5:10 (SSID='MASUS' freq=2412 MHz)
May 10 10:21:32 yw-MM061 kernel: [ 2025.884977] wlan0: authenticate with c8:60:00:e7:d5:10
May 10 10:21:32 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 10 10:21:32 yw-MM061 kernel: [ 2025.896568] wlan0: send auth to c8:60:00:e7:d5:10 (try 1/3)
May 10 10:21:32 yw-MM061 wpa_supplicant[794]: wlan0: Trying to associate with c8:60:00:e7:d5:10 (SSID='MASUS' freq=2412 MHz)
May 10 10:21:32 yw-MM061 kernel: [ 2026.100078] wlan0: send auth to c8:60:00:e7:d5:10 (try 2/3)
May 10 10:21:32 yw-MM061 kernel: [ 2026.102555] wlan0: authenticated
May 10 10:21:32 yw-MM061 kernel: [ 2026.104082] wlan0: associate with c8:60:00:e7:d5:10 (try 1/3)
May 10 10:21:32 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 10 10:21:32 yw-MM061 kernel: [ 2026.308080] wlan0: associate with c8:60:00:e7:d5:10 (try 2/3)
May 10 10:21:33 yw-MM061 kernel: [ 2026.512074] wlan0: associate with c8:60:00:e7:d5:10 (try 3/3)
May 10 10:21:33 yw-MM061 kernel: [ 2026.716084] wlan0: association with c8:60:00:e7:d5:10 timed out
May 10 10:21:33 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: associating -> disconnected
May 10 10:21:34 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 10 10:21:34 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 10 10:21:56 yw-MM061 NetworkManager[714]: <warn> Activation (wlan0/wireless): association took too long.
May 10 10:21:56 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 10:21:56 yw-MM061 NetworkManager[714]: <warn> Activation (wlan0/wireless): asking for new secrets
May 10 10:21:56 yw-MM061 NetworkManager[714]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 10 10:21:56 yw-MM061 NetworkManager[714]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 10 10:21:58 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: scanning -> inactive
May 10 10:21:59 yw-MM061 NetworkManager[714]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Activation (wlan0/wireless): connection 'MASUS' has security, and secrets exist.  No new secrets needed.
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Config: added 'ssid' value 'MASUS'
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Config: added 'scan_ssid' value '1'
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Config: added 'psk' value '<omitted>'
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 10 10:21:59 yw-MM061 NetworkManager[714]: <info> Config: set interface ap_scan to 1
May 10 10:22:00 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: inactive -> scanning
May 10 10:22:00 yw-MM061 wpa_supplicant[794]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
May 10 10:22:01 yw-MM061 wpa_supplicant[794]: wlan0: SME: Trying to authenticate with c8:60:00:e7:d5:10 (SSID='MASUS' freq=2412 MHz)
May 10 10:22:01 yw-MM061 kernel: [ 2054.452817] wlan0: authenticate with c8:60:00:e7:d5:10
May 10 10:22:01 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 10 10:22:01 yw-MM061 kernel: [ 2054.464452] wlan0: send auth to c8:60:00:e7:d5:10 (try 1/3)
May 10 10:22:01 yw-MM061 wpa_supplicant[794]: wlan0: Trying to associate with c8:60:00:e7:d5:10 (SSID='MASUS' freq=2412 MHz)
May 10 10:22:01 yw-MM061 kernel: [ 2054.668104] wlan0: send auth to c8:60:00:e7:d5:10 (try 2/3)
May 10 10:22:01 yw-MM061 kernel: [ 2054.670595] wlan0: authenticated
May 10 10:22:01 yw-MM061 kernel: [ 2054.672088] wlan0: associate with c8:60:00:e7:d5:10 (try 1/3)
May 10 10:22:01 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 10 10:22:01 yw-MM061 kernel: [ 2054.803111] wlan0: RX AssocResp from c8:60:00:e7:d5:10 (capab=0x411 status=0 aid=1)
May 10 10:22:01 yw-MM061 kernel: [ 2054.803837] wlan0: associated
May 10 10:22:01 yw-MM061 kernel: [ 2054.803892] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 10 10:22:01 yw-MM061 wpa_supplicant[794]: wlan0: Associated with c8:60:00:e7:d5:10
May 10 10:22:01 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: associating -> associated
May 10 10:22:01 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
May 10 10:22:03 yw-MM061 avahi-daemon[691]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:ceff:fe76:1ac.
May 10 10:22:03 yw-MM061 avahi-daemon[691]: New relevant interface wlan0.IPv6 for mDNS.
May 10 10:22:03 yw-MM061 avahi-daemon[691]: Registering new address record for fe80::216:ceff:fe76:1ac on wlan0.*.
May 10 10:22:07 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c8:60:00:e7:d5:10 reason=4 locally_generated=1
May 10 10:22:07 yw-MM061 wpa_supplicant[794]: wlan0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
May 10 10:22:07 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="MASUS" auth_failures=1 duration=10
May 10 10:22:07 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="MASUS" auth_failures=2 duration=20
May 10 10:22:07 yw-MM061 NetworkManager[714]: <warn> Connection disconnected (reason -4)
May 10 10:22:07 yw-MM061 kernel: [ 2060.504081] ieee80211 phy0: wlan0: No probe response from AP c8:60:00:e7:d5:10 after 500ms, disconnecting.
May 10 10:22:07 yw-MM061 kernel: [ 2060.506808] cfg80211: Calling CRDA to update world regulatory domain
May 10 10:22:07 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
May 10 10:22:07 yw-MM061 NetworkManager[714]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.
May 10 10:22:07 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: config -> need-auth (reason 'supplicant-disconnect') [50 60 8]
May 10 10:22:07 yw-MM061 NetworkManager[714]: <info> (wlan0): supplicant interface state: disconnected -> inactive
May 10 10:22:07 yw-MM061 kernel: [ 2060.777747] cfg80211: World regulatory domain updated:
May 10 10:22:07 yw-MM061 kernel: [ 2060.777755] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 10:22:07 yw-MM061 kernel: [ 2060.777758] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 10:22:07 yw-MM061 kernel: [ 2060.777761] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 10:22:07 yw-MM061 kernel: [ 2060.777764] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 10:22:07 yw-MM061 kernel: [ 2060.777766] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 10:22:07 yw-MM061 kernel: [ 2060.777769] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 10:24:07 yw-MM061 NetworkManager[714]: <warn> No agents were available for this request.
May 10 10:24:07 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 10 10:24:07 yw-MM061 NetworkManager[714]: <info> NetworkManager state is now DISCONNECTED
May 10 10:24:07 yw-MM061 NetworkManager[714]: <info> Marking connection 'MASUS' invalid.
May 10 10:24:07 yw-MM061 NetworkManager[714]: <warn> Activation (wlan0) failed for connection 'MASUS'
May 10 10:24:07 yw-MM061 NetworkManager[714]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 10 10:24:07 yw-MM061 NetworkManager[714]: <info> (wlan0): deactivating device (reason 'none') [0]
May 10 10:24:07 yw-MM061 wpa_supplicant[794]: wlan0: CTRL-EVENT-SCAN-STARTED "

---

### Post by themik2 on 2014-05-13
bump

---

### Post by themik2 on 2014-05-15
OK, i took care of this by installing an intel wifi card......

---

