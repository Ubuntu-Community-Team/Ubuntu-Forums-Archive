---
title: "Powering off after unplugging power source"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by bbright20 on 2011-03-02
I am running Ubuntu 10.10 on an Acer Aspire One netbook. I can use my netbook with or without the power source. 

However, if I am using it while plugged into the wall and then unplug it to move to another location my netbook hibernates and I have to power it back on. This can be somewhat annoying.

Is there a setting that I need to change to prevent this from happening.

Thanks in advance!

---

### Post by bprins on 2011-03-02
have you checked Main Menu > Preferences > Power Management ?

Maybe under no battery tab you selected hibernate?

---

### Post by Quackers on 2011-03-02
Have a look at the last bit of the first post here
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
I know it seems to be in Lucid and referring to MSI wind and Dell's but it may be worth a try.

---

### Post by bbright20 on 2011-03-02
> **bprins said:**
> have you checked Main Menu > Preferences > Power Management ?

Maybe under no battery tab you selected hibernate?

Here is a screenshot of my settings...

---

### Post by bbright20 on 2011-03-02
> **Quackers said:**
> Have a look at the last bit of the first post here
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
I know it seems to be in Lucid and referring to MSI wind and Dell's but it may be worth a try.

Tried that as well but no luck. Thanks anyways!

---

### Post by bprins on 2011-03-02
Hmm I think I rattled a bit with my reply. Didn't make much sense since the options in power management say nothing about the action "unplug", just the behaviour plugged or unplugged.

I google-d a bit on your issue, and its clear to me that you are far from the only 1 with this problem.

I found a somewhat "scary" workaround, it might help you out:
[http://www.linuxquestions.org/questions/ubuntu-63/laptop-goes-off-when-plug-unplug-ac-cable-781970/](http://www.linuxquestions.org/questions/ubuntu-63/laptop-goes-off-when-plug-unplug-ac-cable-781970/)

You might check you log files (kern.log, messages.log) around the timestamps when you unplug your laptop. Maybe it helps in finding out why ubuntu decides to hibernate.

---

### Post by bbright20 on 2011-03-02
> **bprins said:**
> 
I found a somewhat "scary" workaround, it might help you out:
[http://www.linuxquestions.org/questions/ubuntu-63/laptop-goes-off-when-plug-unplug-ac-cable-781970/](http://www.linuxquestions.org/questions/ubuntu-63/laptop-goes-off-when-plug-unplug-ac-cable-781970/)

You might check you log files (kern.log, messages.log) around the timestamps when you unplug your laptop. Maybe it helps in finding out why ubuntu decides to hibernate.

Thanks that workaround works; however, I can no longer hibernate my system (which is a feature I use a lot since I'm constantly moving from one class to another.

Since I am a newb, is there any way that you can elaborate on checking log files. Thanks again!

---

### Post by bprins on 2011-03-02
E.g. check your clock and remember the time (say 7:00PM).
Then unplug your laptop.
Wake up your laptop.
Open a terminal, and open /var/log/kern.log in your favo text editor (vi, nano, gedit).

And check if your kernel is trying to warn you about something that went wrong directly after 7:00PM.

If I unplug, my kern.log states nothing else then:
```

EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=600

```

Maybe yours state an error which we can google and see if we can figure out what goes wrong.

---

### Post by bprins on 2011-03-02
What also might help getting more information, is running gnome power management in verbose mode.

Type this in a terminal in order to do so
```

killall gnome-power-manager 
gnome-power-manager --verbose

```

---

### Post by bbright20 on 2011-03-02
> **bprins said:**
> E.g. check your clock and remember the time (say 7:00PM).
Then unplug your laptop.
Wake up your laptop.
Open a terminal, and open /var/log/kern.log in your favo text editor (vi, nano, gedit).

And check if your kernel is trying to warn you about something that went wrong directly after 7:00PM.

If I unplug, my kern.log states nothing else then:
```

EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=600

```

Maybe yours state an error which we can google and see if we can figure out what goes wrong.

This is what I get:
```

EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
ata3: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
ata3: irq_stat 0x00400000, PHY RDY changed
ata3: SError: { PHYRdyChg CommWake }
ata3: hard resetting link
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
ata3.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
ata3.00: configured for UDMA/133
ata3: EH complete
wlan0: deauthenticating from 00:27:0d:08:db:30 by local choice (reason=3)
cfg80211: All devices are disconnected, going to restore regulatory settings
cfg80211: Restoring regulatory settings
cfg80211: Calling CRDA to update world regulatory domain
cfg80211: World regulatory domain updated:
  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
PM: Marking nosave pages: 0000000000002000 - 0000000000010000
PM: Marking nosave pages: 000000000009f000 - 0000000000100000
PM: Basic memory bitmaps created
PM: Syncing filesystems ... done.
Freezing user space processes ... (elapsed 0.01 seconds) done.
Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
PM: Preallocating image memory... done (allocated 129049 pages)
PM: Allocated 516196 kbytes in 0.31 seconds (1665.14 MB/s)
Suspending console(s) (use no_console_suspend to debug)
sd 2:0:0:0: [sda] Synchronizing SCSI cache
ata2: port disabled. ignoring.
ata_piix 0000:00:1f.1: PCI INT A disabled
HDA Intel 0000:00:1b.0: PCI INT A disabled
PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 117.885 msecs
PM: freeze of drv: dev:pci0000:00 complete after 117.522 msecs
PM: freeze of devices complete after 132.263 msecs
PM: late freeze of devices complete after 1.197 msecs
ACPI: Preparing to enter system sleep state S4
PM: Saving platform NVS memory
Disabling non-boot CPUs ...
CPU 1 is now offline
SMP alternatives: switching to UP code

```

Sorry for so much code..It continues on with more code that is executed when I power my machine back up.

---

### Post by bprins on 2011-03-02
seems that remounting your disk triggers an error that causes the system to hibernate. But I'm no expert either, maybe I am wrong.

Run this in terminal

```

killall gnome-power-manager  
gnome-power-manager --verbose

```

And pipe the output to file. Then unplug and see if you can figure out more why your system forces hibernation

---

### Post by bprins on 2011-03-02
Ehm, I mean redirect, not pipe ofc :).

So the last command should be something like:
gnome-power-manager --verbose > mydebuginfo.txt

Then unplug, wake up laptop, control C to break the gnome-power-manager in verbose mode and restart normally, then check the log file.

---

### Post by bbright20 on 2011-03-02
> **bprins said:**
> Ehm, I mean redirect, not pipe ofc :).

So the last command should be something like:
gnome-power-manager --verbose > mydebuginfo.txt

Then unplug, wake up laptop, control C to break the gnome-power-manager in verbose mode and restart normally, then check the log file.

Here is the output. I'm not really sure what I'm looking for.
```

TI:15:40:25	TH:0x94c28b8	FI:egg-debug.c	FN:egg_debug_init,306
 - Verbose debugging 1 (on console 0)GPM_VERBOSE
TI:15:40:25	TH:0x94c28b8	FI:gpm-main.c	FN:main,210
 - GNOME Power Manager 2.32.0
TI:15:40:25	TH:0x94c28b8	FI:gpm-session.c	FN:gpm_session_init,511
 - idle: 0, idle_inhibited: 0, suspend_inhibited: 0
TI:15:40:25	TH:0x94c28b8	FI:gpm-session.c	FN:gpm_session_register_client,367
 - registered startup '(null)' to client id '/org/gnome/SessionManager/Client21'
TI:15:40:25	TH:0x94c28b8	FI:egg-console-kit.c	FN:egg_console_kit_init,305
 - ConsoleKit session ID: /org/freedesktop/ConsoleKit/Session2
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=124
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=213
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=150
*** WARNING ***
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_xevent_key,203
 - could not map keysym 1008ffa8 to keycode
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=233
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=232
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=160
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=244
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=238
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=237
TI:15:40:25	TH:0x94c28b8	FI:gpm-button.c	FN:gpm_button_grab_keystring,176
 - Grabbed modmask=8000, keycode=236
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_update_cache,844
 - screen 1 of 1
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_update_cache,849
 - watching ::monitors_changed on 0x94e60c8
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_update_cache,869
 - adding resource 0x9530fa0
TI:15:40:25	TH:0x94c28b8	FI:gpm-prefs-server.c	FN:gpm_prefs_server_set_capability,84
 - capability now 4
TI:15:40:25	TH:0x94c28b8	FI:gpm-prefs-server.c	FN:gpm_prefs_server_set_capability,84
 - capability now 5
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_dim,296
 - Current idle time=374ms, timeout was 10s, becomes 10s after adjustment
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_dim,299
 - Setting dim idle timeout: 10s
TI:15:40:25	TH:0x94c28b8	FI:gpm-dpms.c	FN:gpm_dpms_clear_timeouts,312
 - set timeouts to zero
TI:15:40:25	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,311
 - 1. main brightness 1.000000
TI:15:40:25	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,331
 - 2. battery scale 1.000000, brightness 1.000000
TI:15:40:25	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,349
 - 3. idle scale 1.000000, brightness 1.000000
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_screen,537
 - using resource 0x9530fa0
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 1 of 2
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 2 of 2
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_get_percentage,333
 - hard value=10, min=0, max=10
TI:15:40:25	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_get_percentage,335
 - percentage 100
TI:15:40:25	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,357
 - values are the same, no action
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_check_cpu,122
 - Setting the CPU load check to 0
TI:15:40:25	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_init,2010
 - creating new control instance
TI:15:40:25	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_init,2015
 - creating new tray icon
TI:15:40:25	TH:0x94c28b8	FI:gpm-phone.c	FN:gpm_phone_dbus_connect,240
 - get connection
TI:15:40:25	TH:0x94c28b8	FI:gpm-phone.c	FN:gpm_phone_dbus_connect,251
 - get proxy
*** WARNING ***
TI:15:40:25	TH:0x94c28b8	FI:gpm-phone.c	FN:gpm_phone_dbus_connect,259
 - Cannot connect, maybe the daemon is not running: Could not get owner of name 'org.gnome.phone': no such name
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_init,1146
 - Using percentage notification policy
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_blank,320
 - Setting blank idle timeout: 900s
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_sleep,337
 - Setting sleep idle timeout: 0s
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:40:25	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:40:25	TH:0x94c28b8	FI:gpm-disks.c	FN:gpm_disks_set_spindown_timeout,125
 - disk spindown disabled
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_icon,398
 - no devices (dis)charging, so no icon will be displayed.
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: 
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,481
 - ** EMIT: summary-changed(1): 
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,449
 - ** EMIT: icon-changed: gpm-battery-020-charging
TI:15:40:25	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_set_icon,152
 - Setting icon to gpm-battery-020-charging
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:15 until charged
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,489
 - ** EMIT: summary-changed(2): Laptop battery 2:15 until charged
TI:15:40:25	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:40:25	TH:0x94c28b8	FI:gpm-prefs-server.c	FN:gpm_prefs_server_set_capability,84
 - capability now 13
*** WARNING ***
TI:15:40:25	TH:0x94c28b8	FI:gpm-phone.c	FN:gpm_phone_coldplug,76
 - not connected
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:25	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:15 until charged
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:40:25	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_add,764
 - adding /org/freedesktop/UPower/devices/line_power_AC with state unknown
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_add,764
 - adding /org/freedesktop/UPower/devices/battery_BAT0 with state charging
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_add,768
 - updating because we added a device
TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:40:10 PM CST (15 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              3.4344 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             10.923 V
    time to full:        2.3 hours
    percentage:          15%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299101979	15.000	charging
    1299101938	14.009	discharging
  History (rate):
    1299101944	8.348	charging
    1299101941	12.323	charging
    1299101938	12.344	discharging

TI:15:40:25	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:40:41 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              3.672 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             10.966 V
    time to full:        2.3 hours
    percentage:          16.0377%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102041	16.038	charging
    1299101979	15.000	charging
    1299101938	14.009	discharging
  History (rate):
    1299101944	8.348	charging
    1299101941	12.323	charging
    1299101938	12.344	discharging

TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:40:41	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:15 until charged
TI:15:40:41	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:40:41	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:41:12 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              3.672 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.003 V
    time to full:        2.3 hours
    percentage:          16.0377%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102041	16.038	charging
    1299101979	15.000	charging

TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:12	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:15 until charged
TI:15:41:12	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:41:12	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:41:43 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              3.8988 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.028 V
    time to full:        2.3 hours
    percentage:          17.0283%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102103	17.028	charging
    1299102041	16.038	charging

TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:41:43	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:15 until charged
TI:15:41:43	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:41:43	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:42:14 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              3.8988 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.026 V
    time to full:        2.3 hours
    percentage:          17.0283%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102103	17.028	charging
    1299102041	16.038	charging

TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:14	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:15 until charged
TI:15:42:14	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:42:14	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:42:45 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.1256 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.042 V
    time to full:        2.2 hours
    percentage:          18.0189%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102165	18.019	charging
    1299102103	17.028	charging

TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:42:45	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:10 until charged
TI:15:42:45	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,489
 - ** EMIT: summary-changed(2): Laptop battery 2:10 until charged
TI:15:42:45	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:43:16 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.1256 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.079 V
    time to full:        2.2 hours
    percentage:          18.0189%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102165	18.019	charging
    1299102103	17.028	charging

TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:16	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:10 until charged
TI:15:43:16	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:43:16	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:43:47 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.3524 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.077 V
    time to full:        2.2 hours
    percentage:          19.0094%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102227	19.009	charging
    1299102165	18.019	charging

TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:43:47	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:10 until charged
TI:15:43:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:43:47	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:44:00	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_alarm_expired_cb,376
 - idletime alarm: 1
TI:15:44:00	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=1
TI:15:44:00	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,221
 - normal to dim
TI:15:44:00	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: dim
TI:15:44:00	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,229
 - setting up blank callback for 900s
TI:15:44:06	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_reset_cb,391
 - idletime reset
TI:15:44:06	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:44:06	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: normal
TI:15:44:06	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_idle_changed_cb,804
 - lid is closed, so we are ignoring ->NORMAL state changes
TI:15:44:06	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:44:18	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_alarm_expired_cb,376
 - idletime alarm: 1
TI:15:44:18	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=1
TI:15:44:18	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,221
 - normal to dim
TI:15:44:18	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: dim
TI:15:44:18	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,229
 - setting up blank callback for 900s
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:44:18 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.3524 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.077 V
    time to full:        2.2 hours
    percentage:          19.0094%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102227	19.009	charging
    1299102165	18.019	charging

TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:18	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:10 until charged
TI:15:44:18	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:44:18	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:44:31	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_reset_cb,391
 - idletime reset
TI:15:44:31	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:44:31	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: normal
TI:15:44:31	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_idle_changed_cb,804
 - lid is closed, so we are ignoring ->NORMAL state changes
TI:15:44:31	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:44:49 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.5792 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.113 V
    time to full:        2.2 hours
    percentage:          20%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102289	20.000	charging
    1299102227	19.009	charging

TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:44:49	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:10 until charged
TI:15:44:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:44:49	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:45:20 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.5792 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.121 V
    time to full:        2.2 hours
    percentage:          20%
    capacity:            96.3636%
    technology:          lithium-ion
  History (charge):
    1299102289	20.000	charging
    1299102227	19.009	charging

TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:45:20	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:10 until charged
TI:15:45:20	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:45:20	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:45:30	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_alarm_expired_cb,376
 - idletime alarm: 1
TI:15:45:30	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=1
TI:15:45:30	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,221
 - normal to dim
TI:15:45:30	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: dim
TI:15:45:30	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,229
 - setting up blank callback for 900s
TI:15:45:43	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_reset_cb,391
 - idletime reset
TI:15:45:43	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:45:43	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: normal
TI:15:45:43	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_idle_changed_cb,804
 - lid is closed, so we are ignoring ->NORMAL state changes
TI:15:45:43	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:45:50	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_client_changed_cb,1028
 - on_battery: 1
TI:15:45:50	TH:0x94c28b8	FI:gpm-disks.c	FN:gpm_disks_set_spindown_timeout,125
 - disk spindown disabled
TI:15:45:50	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_blank,320
 - Setting blank idle timeout: 600s
TI:15:45:50	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:45:50	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:45:50	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_sleep,337
 - Setting sleep idle timeout: 1800s
TI:15:45:50	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:45:50	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:45:50	TH:0x94c28b8	FI:gpm-screensaver.c	FN:gpm_screensaver_add_throttle,224
 - adding throttle reason: 'On battery power': id 366867280
*** WARNING ***
TI:15:45:50	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_play,324
 - failed to play power-unplug: File or data not found
TI:15:45:50	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_perform_policy,681
 - action: /apps/gnome-power-manager/buttons/lid_battery set to hibernate (The lid has been closed, and the ac adapter removed (and gconf is okay).)
TI:15:45:50	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_action_hibernate,652
 - hibernating, reason: The lid has been closed, and the ac adapter removed (and gconf is okay).
TI:15:45:50	TH:0x94c28b8	FI:gpm-control.c	FN:gpm_control_get_lock_policy,128
 - Using custom locking settings (1)
TI:15:45:50	TH:0x94c28b8	FI:gpm-screensaver.c	FN:gpm_screensaver_add_throttle,224
 - adding throttle reason: 'hibernate': id 1441106535
TI:15:45:50	TH:0x94c28b8	FI:gpm-screensaver.c	FN:gpm_screensaver_lock,161
 - doing gnome-screensaver lock
TI:15:45:51	TH:0x94c28b8	FI:gpm-control.c	FN:gpm_control_hibernate,246
 - emitting sleep
TI:15:47:45	TH:0x94c28b8	FI:gpm-control.c	FN:gpm_control_hibernate,251
 - emitting resume
TI:15:47:45	TH:0x94c28b8	FI:gpm-screensaver.c	FN:gpm_screensaver_poke,313
 - poke
TI:15:47:45	TH:0x94c28b8	FI:gpm-screensaver.c	FN:gpm_screensaver_remove_throttle,244
 - removing throttle: id 1441106535
TI:15:47:45	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,311
 - 1. main brightness 1.000000
TI:15:47:45	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,331
 - 2. battery scale 0.500000, brightness 0.500000
TI:15:47:45	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,349
 - 3. idle scale 1.000000, brightness 0.500000
*** WARNING ***
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_trust_cache,565
 - using cache for value 100 (probably okay)
*** WARNING ***
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_trust_cache,565
 - using cache for value 100 (probably okay)
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_screen,537
 - using resource 0x9530fa0
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 1 of 2
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 2 of 2
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_set,430
 - percent=50, absolute=5
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_set,432
 - hard value=10, min=0, max=10
TI:15:47:45	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_set,461
 - using step of 1
TI:15:47:46	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,374
 - emitting brightness-changed : 50
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_alarm_expired_cb,376
 - idletime alarm: 1
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=1
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,221
 - normal to dim
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: dim
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,229
 - setting up blank callback for 600s
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_idletime_reset_cb,391
 - idletime reset
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_mode,108
 - Doing a state transition: normal
TI:15:47:46	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_idle_changed_cb,804
 - lid is closed, so we are ignoring ->NORMAL state changes
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:45:50 PM CST (116 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.134 V
    time to empty:       34.6 minutes
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now discharging
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,944
 - ** EMIT: discharging
TI:15:47:46	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020
TI:15:47:46	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_notify,493
 - notification 0x955bc40: Battery Discharging : 0:35 of battery power remaining (21%)
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,459
 - ** EMIT: icon-changed: gpm-battery-020
TI:15:47:46	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_set_icon,152
 - Setting icon to gpm-battery-020
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 0:30 left
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,489
 - ** EMIT: summary-changed(2): Laptop battery 0:30 left
TI:15:47:46	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/line_power_AC state is now unknown
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 0:30 left
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:46	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:46	TH:0x94c28b8	FI:gpm-session.c	FN:gpm_session_presence_status_changed_cb,145
 - emitting idle-changed : (1)
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_session_idle_changed_cb,354
 - Received gnome session idle changed: 1
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=1, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:47:46	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:46 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.061 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,459
 - ** EMIT: icon-changed: gpm-battery-020-charging
TI:15:47:46	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_set_icon,152
 - Setting icon to gpm-battery-020-charging
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,489
 - ** EMIT: summary-changed(2): Laptop battery 2:05 until charged
TI:15:47:46	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:46 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.061 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:46	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:46	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:46	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:47	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_client_changed_cb,1008
 - clearing notify due ac being present
TI:15:47:47	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_client_changed_cb,1028
 - on_battery: 0
TI:15:47:47	TH:0x94c28b8	FI:gpm-disks.c	FN:gpm_disks_set_spindown_timeout,125
 - disk spindown disabled
TI:15:47:47	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_blank,320
 - Setting blank idle timeout: 900s
TI:15:47:47	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=1, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:47:47	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:47:47	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_set_timeout_sleep,337
 - Setting sleep idle timeout: 0s
TI:15:47:47	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=1, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:47:47	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:47:47	TH:0x94c28b8	FI:gpm-screensaver.c	FN:gpm_screensaver_remove_throttle,244
 - removing throttle: id 366867280
*** WARNING ***
TI:15:47:47	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_play,324
 - failed to play power-plug: File or data not found
TI:15:47:47	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,311
 - 1. main brightness 1.000000
TI:15:47:47	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,331
 - 2. battery scale 1.000000, brightness 1.000000
TI:15:47:47	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,349
 - 3. idle scale 1.000000, brightness 1.000000
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_screen,537
 - using resource 0x9530fa0
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 1 of 2
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 2 of 2
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_get_percentage,333
 - hard value=5, min=0, max=10
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_get_percentage,335
 - percentage 50
*** WARNING ***
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_trust_cache,565
 - using cache for value 50 (probably okay)
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_screen,537
 - using resource 0x9530fa0
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 1 of 2
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_foreach_resource,491
 - resource 2 of 2
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_set,430
 - percent=100, absolute=10
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_set,432
 - hard value=5, min=0, max=10
TI:15:47:47	TH:0x94c28b8	FI:gpm-brightness.c	FN:gpm_brightness_output_set,447
 - using step of 1
TI:15:47:47	TH:0x94c28b8	FI:gpm-backlight.c	FN:gpm_backlight_brightness_evaluate_and_set,374
 - emitting brightness-changed : 100
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:46 PM CST (1 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.061 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:47	TH:0x94c28b8	FI:gpm-manager.c	FN:gpm_manager_notification_closed_cb,462
 - caught notification closed signal 0x955bc40
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/line_power_AC state is now unknown
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:47 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.061 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:47 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.061 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:47	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:47	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:47	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:48 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.064 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:48	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:48	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:48	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:49 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.064 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:49	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:49	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:49	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0
TI:15:47:49	TH:0x94c28b8	FI:gpm-session.c	FN:gpm_session_presence_status_changed_cb,145
 - emitting idle-changed : (0)
TI:15:47:49	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_session_idle_changed_cb,354
 - Received gnome session idle changed: 0
TI:15:47:49	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,187
 - session_idle=0, idle_inhibited=0, suspend_inhibited=0, x_idle=0
TI:15:47:49	TH:0x94c28b8	FI:gpm-idle.c	FN:gpm_idle_evaluate,192
 - X not idle
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,929
 - updating because /org/freedesktop/UPower/devices/battery_BAT0 changed
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,666
 - printing device 1:
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  vendor:               SANYO
  model:                GC86508SAT0
  power supply:         yes
  updated:              Wed 02 Mar 2011 03:47:50 PM CST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              4.8168 Wh
    energy-empty:        0 Wh
    energy-full:         22.896 Wh
    energy-full-design:  23.76 Wh
    energy-rate:         8.3484 W
    voltage:             11.09 V
    time to full:        2.2 hours
    percentage:          21.0377%
    capacity:            96.3636%
    technology:          lithium-ion

TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_update_composite_device,687
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_device_changed_cb,938
 - /org/freedesktop/UPower/devices/battery_BAT0 state is now charging
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_composite_device,608
 - using original device as only one primary battery
TI:15:47:50	TH:0x94c28b8	FI:gpm-upower.c	FN:gpm_upower_get_device_icon,173
 - got filename: gpm-battery-020-charging
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_icon,464
 - no change
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_get_summary,275
 - tooltip: Laptop battery 2:05 until charged
TI:15:47:50	TH:0x94c28b8	FI:gpm-engine.c	FN:gpm_engine_recalculate_state_summary,493
 - no change
TI:15:47:50	TH:0x94c28b8	FI:gpm-tray-icon.c	FN:gpm_tray_icon_add_device,261
 - adding device /org/freedesktop/UPower/devices/battery_BAT0

```

Thanks again!

---

### Post by bbright20 on 2011-03-02
I was able to find a "work around" here:

[http://www.dslreports.com/forum/r25526232-Ubuntu-10.10-Unplug-laptop-from-AC-suspends-computer.]("http://www.dslreports.com/forum/r25526232-Ubuntu-10.10-Unplug-laptop-from-AC-suspends-computer.")

It seems to me that it is treating unplugging the ac adapter as closing the laptop lid...

---

### Post by bprins on 2011-03-03
And now it does not hibernate when unplugging but still hibernates when you close the lid?

---

### Post by bbright20 on 2011-03-03
> **bprins said:**
> And now it does not hibernate when unplugging but still hibernates when you close the lid?

The screen just goes blank (which is the setting for closing the lid) when unplugging and I just have to move the mouse to bring the screen back up; however, it actually doesn't do anything when the lid is closed. Any suggestions to what's going on?

As far as I can tell the setting that is suppose to be effected when closing the lid is trigger by the unplugging of the ac adapter.

---

