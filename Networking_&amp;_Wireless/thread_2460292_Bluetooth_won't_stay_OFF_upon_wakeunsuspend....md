---
title: "Bluetooth won't stay OFF upon wake/unsuspend..."
date: 2021-04-06
forum: Networking &amp; Wireless
---

### Post by lakester on 2021-04-06
Thinkpad P15gen1, Ubuntu 20.04:

Repeat-by:
[LIST]
[*]Enable BT using the top menu bar dropdown and connect with a BT speaker (a BT stereo adapter in this case).
[*]Play some music..., whatever.
[*]Disable BT using the top menu bar dropdown.
[*]Sleep the machine (close the lid).  Note:  machine is set to suspend and lock screen upon lid closure.
[*]Wake the machine (open the lid) and unlock screen.
[*]BT is enabled and connects even though it was disabled prior to suspend.
[/LIST]

Heh, the funny thing is that BT has been very reliable in every other way.

How do I get BT to stay OFF when I turn it off? (..., and still have it turn on, and work, when I turn it on ;) ).

---

### Post by lakester on 2021-04-10
[COLOR=#000000][FONT=LatoMedium]I've spent some time trying to characterize the problem.  None of the settings related to power management seemed to relate to the BT failing to stay OFF problem, however..., along the way, I did find another interesting and perhaps related problem:[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]The following setting:[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]"Power"->"Power Saving"->"Bluetooth (Bluetooth can be turned off to save power)"->OFF/ON[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]appears to duplicate the function of the "Bluetooth"->OFF/ON switch setting.[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]They do the EXACT same thing.  They mirror each other.[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]E.g., when BT is turned on, the BT power save switch will be on.  Turn BT off..., and the BT power save switch will turn off.[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]Now..., turn BT back on, and then turn the BT power save switch off..., the entirety of BT will turn off..., EVEN if there is an active, running connection.  Turn the BT power save switch back ON..., and BT will turn back ON.[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]This is bogus.  If the mapping of the GUI functionality to BT settings is broken, it's not a long stretch to think some other mapping or use/management of BT settings is broken as well..., especially since it's in the neighborhood of power management.[/FONT][/COLOR]

---

### Post by lakester on 2021-04-12
[COLOR=#000000][FONT=LatoMedium]More annoyance:  I delete the pairing that the unwanted connection keeps using (because BT won't stay OFF when turned OFF).  Now I just get to watch the BT icon appear and disappear endlessly while it tries to connect with other inactive pairings.[/FONT][/COLOR]

---

### Post by lakester on 2021-04-12
[COLOR=#333333][FONT=monospace]Some observations:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]/etc/bluetooth/main.conf:
  AutoEnable is set to "true". This causes BT to be enabled upon boot REGARDLESS of any GNOME
  settings the user might have set. When I set it to "false", I've tried rebooting in these two
  scenarios:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  1. If the GNOME setting is OFF prior to reboot..., BT stays OFF upon reboot.
  2. If the GNOME setting is ON prior to reboot..., BT turns ON upon reboot.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]HOWEVER..., in ALL suspend/wake scenarios, regardless of the AutoEnable setting or the GNOME setting, OR even if a "systemctl stop bluetooth" is performed prior to suspend/wake, (or any permutation of all 3)..., BT is re-enabled upon wake.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]This SEEMS to be some sort of lack of coordination between systemd configuration and some GNOME component.

[/FONT][/COLOR][COLOR=#333333][FONT=monospace]Correction: "systemctl stop bluetooth" appears to have more durable results wrt suspend/wake than I first thought, though I thought I tested it pretty thoroughly. If I stop the service..., it appears to stay stopped following suspend/wake. For the moment then, my workaround is to set AutoEnable=false and whenever I want to turn BT off..., do a "systemctl stop bluetooth".

[/FONT][/COLOR][COLOR=#333333][FONT=LatoMedium]Correction to the "correction":  Sigh. So I repeatedly tested suspend/wake following a systemctl stop bluetooth..., and BT stayed off. Until now. I left the machine to sleep for maybe an hour..., just woke it..., boom..., BT is back on. So..., I guess I retract my prior "correction".[/FONT][/COLOR]

---

### Post by lakester on 2021-04-12
So..., I think I figured out why "systemctl stop bluetooth" sometimes works to disable BT thru a suspend/wake cycle, and sometimes not.
If you turn OFF BT using the GNOME settings, regardless of whether or not you do a "systemctl stop bluetooth"..., BT will ALWAYS be turned back ON after a suspend/wake cycle.
If you leave the GNOME BT setting as ON however, and if you do a "systemctl stop bluetooth", BT will stay OFF following a suspend/wake cycle, presumably because the GNOME power management code thinks BT
is already ON..., and so takes no action to enable it.  Basically..., the left hand doesn't know what the right hand is doing.  My inclination is to pin this bug on the GNOME power management code at this point.

---

### Post by lakester on 2021-04-13
[COLOR=#000000][FONT=LatoMedium]Because I have better things to do, but for some reason I'm not doing them..., here's some more info:[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]Started playing around with dbus-monitor. While I don't know if what I'm seeing is "normal", it is kinda interesting. The command:[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]#dbus-monitor --system "path=/org/bluez/hci0"[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]yields some interesting output. The pasted log is what happens when you switch BT OFF using the Gnome Settings app.[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]I know zip about dbus..., but taking things at face value..., at the beginning of the log, you can see activity that would seem consistent with turning BT off..., values set to false, etc. BUT at the end of the log, you see activity that seems to suggest that something, somewhere, is being told that it is ON.[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]As an aside, I've been spending time looking at the code for the gnome-settings-daemon, in particular the gsd-rfkill plugin. Also looking at things related to systemd-rfkill. Still looking.[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]Anyways..., here's the output from dbus-monitor when BT is switched OFF by gnome settings:[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium] [/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]signal time=1618356308.901616 sender=:1.548 -> destination=(null destination) serial=237 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=PropertiesChanged
   string "org.bluez.Adapter1"
   array [
      dict entry(
         string "Class"
         variant             uint32 0
      )
      dict entry(
         string "Powered"
         variant             boolean false
      )
      dict entry(
         string "Discovering"
         variant             boolean false
      )
   ]
   array [
   ]
method call time=1618356308.901917 sender=:1.545 -> destination=:1.548 serial=143 path=/org/bluez/hci0; interface=org.bluez.Adapter1; member=SetDiscoveryFilter
   array [
      dict entry(
         string "Discoverable"
         variant             boolean true
      )
   ]
method call time=1618356308.902564 sender=:1.545 -> destination=:1.548 serial=144 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=Set
   string "org.bluez.Adapter1"
   string "Discoverable"
   variant       boolean true
method call time=1618356308.902619 sender=:1.545 -> destination=:1.548 serial=145 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=Set
   string "org.bluez.Adapter1"
   string "DiscoverableTimeout"
   variant       uint32 0
method call time=1618356308.902671 sender=:1.545 -> destination=:1.548 serial=146 path=/org/bluez/hci0; interface=org.bluez.Adapter1; member=StartDiscovery
signal time=1618356308.914808 sender=:1.548 -> destination=(null destination) serial=242 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=PropertiesChanged
   string "org.bluez.Adapter1"
   array [
      dict entry(
         string "DiscoverableTimeout"
         variant             uint32 0
      )
   ]
   array [
   ]
method call time=1618356308.914862 sender=:1.545 -> destination=:1.548 serial=147 path=/org/bluez/hci0; interface=org.bluez.Adapter1; member=SetDiscoveryFilter
   array [
      dict entry(
         string "Discoverable"
         variant             boolean true
      )
   ]
method call time=1618356308.915545 sender=:1.545 -> destination=:1.548 serial=148 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=Set
   string "org.bluez.Adapter1"
   string "Discoverable"
   variant       boolean true
method call time=1618356308.916566 sender=:1.545 -> destination=:1.548 serial=149 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=Set
   string "org.bluez.Adapter1"
   string "DiscoverableTimeout"
   variant       uint32 0
method call time=1618356308.916586 sender=:1.545 -> destination=:1.548 serial=150 path=/org/bluez/hci0; interface=org.bluez.Adapter1; member=StartDiscovery
method call time=1618356308.916591 sender=:1.155 -> destination=:1.548 serial=881 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=Set
   string "org.bluez.Adapter1"
   string "Powered"
   variant       boolean true
method call time=1618356308.916599 sender=:1.40 -> destination=:1.548 serial=509 path=/org/bluez/hci0; interface=org.freedesktop.DBus.Properties; member=Set
   string "org.bluez.Adapter1"
   string "Powered"
   variant       boolean true[/FONT][/COLOR]

---

