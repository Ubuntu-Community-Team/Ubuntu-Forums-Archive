---
title: "Failed to pair from mobile to laptop via bluetooth, 15.04, x64"
date: 2015-07-13
forum: Networking &amp; Wireless
---

### Post by Qingtao on 2015-07-13
Dear Ubuntu community,

I have used Ubuntu for a couple of years but am relatively new to internals of bluez and dbus. I can smoothly find my mobile phone (Samsung S3, GT-I9300) and pair it from Vivid (15.04) via either blueman GUI or low-level dbus messages. BTW, I have been using a universal USB-Bluetooth dongle (hci1) since the Boardcom wireless chip in my Dell laptop doesn't seem to work efficiently when it comes to bluetooth (hci0).

My mobile can detect the hci1 adapter exposed by the USB-Bluetooth dongle on the laptop easily, however, when I clicked on the mobile to pair it, a message box was prompted on the mobile:

"Confirm passkey is xxxxxx to pair with yyyy"

At this moment, I noticed there was a device icon created in blueman GUI. However, when I further clicked "Confirm" on the mobile, another message box said:

"Unable to pair with yyyy, incorrect pin or passcode"

Meanwhile the device icon in blueman became disappeared, and there was no message box popped up asynchronously on my laptop to ask me if I would like to pair with the mobile device.

If I use dbus-monitor to monitor all messages / signals sent from org.bluez in this scenario, I can see that the object of the mobile phone, "/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31", as in my case, was created but then immediately removed:[INDENT]$ sudo dbus-monitor --system "sender='org.bluez'" | tee tmp
signal sender=org.freedesktop.DBus -> dest=:1.121 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.121"
signal sender=:1.2 -> dest=(null destination) serial=379 path=/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31; interface=org.bluez.Device; member=PropertyChanged
   string "Vendor"
   variant       uint16 117
signal sender=:1.2 -> dest=(null destination) serial=380 path=/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31; interface=org.bluez.Device; member=PropertyChanged
   string "Product"
   variant       uint16 256
signal sender=:1.2 -> dest=(null destination) serial=381 path=/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31; interface=org.bluez.Device; member=PropertyChanged
   string "Version"
   variant       uint16 512
signal sender=:1.2 -> dest=(null destination) serial=382 path=/org/bluez/972/hci1; interface=org.bluez.Adapter; member=DeviceCreated
   object path "/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31"
signal sender=:1.2 -> dest=(null destination) serial=383 path=/org/bluez/972/hci1; interface=org.bluez.Adapter; member=PropertyChanged
   string "Devices"
   variant       array [
         object path "/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31"
      ]
signal sender=:1.2 -> dest=(null destination) serial=384 path=/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31; interface=org.bluez.Device; member=PropertyChanged
   string "Connected"
   variant       boolean true
signal sender=:1.2 -> dest=(null destination) serial=405 path=/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31; interface=org.bluez.Device; member=PropertyChanged
   string "Connected"
   variant       boolean false
signal sender=:1.2 -> dest=(null destination) serial=406 path=/org/bluez/972/hci1; interface=org.bluez.Adapter; member=PropertyChanged
   string "Devices"
   variant       array [
      ]
signal sender=:1.2 -> dest=(null destination) serial=407 path=/org/bluez/972/hci1; interface=org.bluez.Adapter; member=DeviceRemoved
   object path "/org/bluez/972/hci1/dev_D8_57_EF_39_9F_31"
[/INDENT]


BTW, if I pair from my laptop to my mobile, such object can be successfully created.

The syslog on my laptop also revealed below error messages:[INDENT]Jul 13  15:07:14 harry-brkawy bluetoothd[999]: Agent replied with an error:  org.freedesktop.DBus.Python.NameError, Traceback (most recent call  last):#012  File "/usr/lib/python2.7/dist-packages/dbus/service.py",  line 707, in _message_cb#012    retval = candidate_method(self, *args,  **keywords)#012  File  "/usr/lib/python2.7/dist-packages/blueman/main/applet/BluezAgent.py",  line 203, in RequestConfirmation#012    pixbuf=get_icon("blueman", 48),  status_icon=self.status_icon)#012  File  "/usr/lib/python2.7/dist-packages/blueman/gui/Notification.py", line  174, in __new__#012    return NotificationDialog(summary, message,  timeout, actions, actions_cb, pixbuf, status_icon)#012  File  "/usr/lib/python2.7/dist-packages/blueman/gui/Notification.py", line 23,  in __init__#012    GObject.GObject.__init__(self, parent=None, flags=0,  type=Gtk.MessageType.QUESTION,#012NameError: global name 'GObject' is  not defined
[/INDENT]

Is it caused by some missing parts of blueman that I should have installed?

Well, so far the version of bluez and blueman I have installed on my laptop are:[INDENT]$ dpkg -l | grep blueman
ii  blueman                                              1.99~alpha1-1ubuntu1                       amd64        Graphical bluetooth manager

$ dpkg -l | grep bluez
ii   bluez                                                 4.101-0ubuntu25                            amd64        Bluetooth tools  and daemons
ii  bluez-alsa:amd64                                      4.101-0ubuntu25                            amd64        Bluetooth ALSA  support
ii  bluez-compat                                          4.101-0ubuntu25                            amd64        BlueZ 3.x  compatibility binaries
ii   bluez-cups                                            4.101-0ubuntu25                            amd64        Bluetooth  printer driver for CUPS
ii   bluez-hcidump                                         2.5-1                                      amd64        Analyses  Bluetooth HCI packets
ii   bluez-pcmcia-support                                  4.101-0ubuntu25                            amd64        PCMCIA support  files for BlueZ 2.0 Bluetooth tools
ii   bluez-tools                                           0.1.38+git662e-3                           amd64        Set of tools to  manage Bluetooth devices for linux
ii   libbluedevil1:amd64                                   2.0~rc1really1.9.4-0ubuntu1                amd64        Qt wrapper for  bluez
ii  python-bluez                                          0.20-1                                     amd64        Python wrappers  around BlueZ for rapid bluetooth development
[/INDENT]


How should I better attack this issue next? Any comments would be highly appreciated!

Cheers,
Harry

---

### Post by Qingtao on 2015-07-14
Hello,

By some trial and error, the problem has been "fixed" after hacking the Notification.py script of blueman. However, as I am a rookie to blueman and python, I have no idea whether this is a decent fix or an ugly hack:

[ATTACH]263193[/ATTACH]

GObject was imported simply enlightened by bluez-simple-agent script, and unsupported attributes such as "flags" and "message_format" were simply discarded.

blueman-applet needs to be killed and restarted to make such change effective.

Now the mobile phone and laptop can pair each other bilaterally :-)

---

