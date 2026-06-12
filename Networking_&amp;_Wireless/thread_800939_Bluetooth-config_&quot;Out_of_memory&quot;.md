---
title: "Bluetooth-config &quot;Out of memory&quot;"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by art_s on 2008-05-20
Hi all, 

I'm trying to connect to my BT-359 gps under Hardy.

after running bluetooth-properties and trying to add the device to the list I get this:

> process 19365: arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 1074.
This is normally a bug in some application using the D-Bus library.

** ERROR **: Out of memory
aborting...
Aborted

I tried to find a fix for that but all I found was some patches to bluez-utils package. I applied that and tried to build that but no luck - it complaing that cannot find gconf

> gconf >= 2.16 is required

At this stage I'm pretty much lost and hoping to hear your suggestions

Thanks!

---

### Post by art_s on 2008-05-21
I'm having problems believing that no one had the same issue out of the box.

Anyone?

---

