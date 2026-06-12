---
title: "Shut Down Hangs if Connected to Server"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Het Irv on 2008-04-28
If I connect a shared folder on a local server, when I shut down Hardy the network connection will not disconnect cleanly which seems to cause the shut down to hang on the server.  I had to take a pic with my cell phone, but I will try my best to give you the output.
```
Network Manager: <INFO> Deactivating device wlan0.

Network Manager: <INFO> Deactivating device eth0. 

Network Manager: <WARN> nm_hal_deinit():libhal shutdown failed - Connection is
closed

Network Manager: <WARN> nm_dbus_signal_device_status_change: assertion `cb_data->data-d
bus_connection' failed

Network Manager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system
bus. Make sure the message bus daemon is running!

Network Manager: <WARN> nm_dbus_signal_device_status_change: assertion `cb_data->data-d
bus_connection' failed

Network Manager: <WARN> nm_dbus_signal_device_status_change: assertion `cb_data->data-d
bus_connection' failed

[ 1918.842140] CIFS VFS: server not responding
[ 1918.842210] CIFS VFS: No response for cmd 114 mid 328
```

I think this is a bug, because this has happened on a fresh install and the only samba package that is installed is smbfs. The last two numbers will change almost every time, and It doesn't hang if I do not connect to the share.

---

### Post by gareth_005 on 2008-04-29
I also get this when shutting down.
I do not have samba shares connected, but nfs shares are connected.

Shutdown never completes, even with no shares mounted.
Restart does work though!

---

### Post by Het Irv on 2008-04-29
Sorry about the wait, we had a power outage at work yesterday (the thing with the Tornados in South Virginia) and I had to work off site today.

---

### Post by john6six on 2008-05-01
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=293513&highlight=cifs+vfs](http://ubuntuforums.org/showthread.php?t=293513&highlight=cifs+vfs)

---

### Post by hamishau on 2008-05-02
This is a known issue and is registered on Launchpad here: [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/211631](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/211631)

Have a look at the solution there and see if that works for you.

Hamish

---

### Post by Het Irv on 2008-05-02
The fix in post 44 of the ubuntuforums thread link, worked for me.  Thanks for the link!

---

