---
title: "Error Message while shutdown about NetworkManager"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by adnansanni on 2008-05-06
from today I have get a error message while shutdown my laptop. Anybody has idea to solve it? Here is the code:

* Starting periodic command scheduler crond		[OK]
* Checking batterystate...				[OK]
* Running local boot scripts (/etc/rc.local)		[OK]
NetwokManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.
NetwokManager: <info> Caught terminiation signal
NetwokManager: <debug>[1210091816.740501] nm_print_open_socks(): Open Sockets List:
NetwokManager: <debug>[1210091816.740687] nm_print_open_socks(): Open Sockets List:
NetwokManager: <info> Deactivating device eth0.
NetwokManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed
NetwokManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus deamon is running!
NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb-data->data->dbus_connection' failed

---

### Post by JeppeM on 2008-05-11
I have the same problem - Anyone able to help?

---

### Post by koma77 on 2008-05-11
I have the same problem on my two Hardy machines.

It looks ugly...

The network-manager seems to be a bit unstable in this release...

---

### Post by Yannick Le Saint kyncani on 2008-05-11
One component not shutting down cleanly, not to worry I'd say as long as it starts up and works fine.

Btw, I've always had nm errors at shutdown.

---

### Post by JeppeM on 2008-05-11
Still kind off annoying that you have to wait those extra 10 secs when shutting down :P

I guess it's nothing big, but on a system like linux it should be possible to fix it... I would expect it on Windows, but not on Linux :D (yes, i'm a newcomer to ubuntu, but i'm loving it alot) Just have the last few small issues before i convert totally..

---

### Post by koma77 on 2008-05-12
I'm having other issues related to network-manager in 8.04.

I can't help but thinking that they might be related...

What is the error message really about? I don't have time to read it all before it shuts down. Something about a bus I think.

---

### Post by Tom--d on 2008-05-12
I have that. To me, its normal ;)

---

### Post by High Roller on 2008-05-12
This is actually a bug.
I've found a workaround [here]("http://ubuntuforums.org/showpost.php?p=4934956&postcount=10").

---

### Post by JeppeM on 2008-05-13
Worked for me - Wierd issue :S Thanks High Roller :)

---

### Post by koma77 on 2008-05-13
Worked for me too!

---

