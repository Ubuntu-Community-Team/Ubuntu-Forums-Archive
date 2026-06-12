---
title: "Bluetooth and D-Bus with Gutsy: Unable to become primary owner of org.bluez ?  Help!"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by eletha on 2008-08-07
I am using Gutsy with a Dell630 with built in bluetooth. Hciconfig brings up hci0 with my BT address. But hcitool scan brings up nothing

```
@ubuntu1:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:1A:6B:E6:A9:4D ACL MTU: 310:10 SCO MTU: 64:8
        UP RUNNING PSCAN 
        RX bytes:985 acl:0 sco:0 events:30 errors:0
        TX bytes:617 acl:0 sco:0 commands:28 errors:0
```

```
@ubuntu1:~$ hcitool scan
Scanning ...
@ubuntu1:~$ 
```


```
@ubuntu1:/var/run/dbus$ sudo rm -f /var/run/dbus/*
[sudo] password for :
@ubuntu1:/var/run/dbus$ dbus-uuidgen --ensure
@ubuntu1:/var/run/dbus$ dbus-daemon --system
Failed to start message bus: Failed to bind socket "/var/run/dbus/system_bus_socket": Permission denied
@ubuntu1:/var/run/dbus$ sudo dbus-daemon --system
@ubuntu1:/var/run/dbus$ modprobe bluetooth
@ubuntu1:/var/run/dbus$ modprobe l2cap
@ubuntu1:/var/run/dbus$ modprobe rfcomm
@ubuntu1:/var/run/dbus$ modprobe hci-usb
@ubuntu1:/var/run/dbus$ hcid -n
hcid[7798]: Bluetooth HCI daemon
hcid[7798]: HCI dev 0 registered
hcid[7799]: Can't init device hci0: Permission denied (13)
hcid[7798]: HCI dev 0 already up
hcid[7798]: Device hci0 has been added
hcid[7800]: Can't set link mode on hci0: Permission denied (13)
hcid[7800]: Can't set link policy on hci0: Permission denied (13)
hcid[7798]: Starting security manager 0
hcid[7798]: Can't write inquiry mode for hci0: Operation not permitted (1)
hcid[7798]: Created local server at unix:abstract=/var/run/dbus-BVnoISlG8C,guid=8a5aabd33609a28fc1307d0048998408
hcid[7798]: Can't create server address file
input[7801]: Bluetooth Input daemon
input[7801]: Registered input manager path:/org/bluez/input
input[7801]: Failed to listen on control channel
serial[7802]: Bluetooth Serial Port daemon
serial[7802]: Registered manager path:/org/bluez/serial
network[7803]: Bluetooth Network daemon
network[7803]: Can't create bridge
network[7803]: Bind failed. Permission denied(13)
hcid[7798]: Got NameOwnerChanged signal for :1.3 which has no listeners
```

Can someone help me make sense of these errors and how I can explore them/ fix them? Are all these permission denied warnings coming up because I am not executing the command as root user? I tried the command as root user, but it still wouldn't work. 

When I normally type hcid -n, it tells me the following:
```
Jul 28 12:32:11 ubuntu1 hcid[9176]: Bluetooth HCI daemon
Jul 28 12:32:11 ubuntu1 hcid[9176]: Could not become the primary owner of org.bluez
Jul 28 12:32:11 ubuntu1 hcid[9176]: Unable to get on D-Bus
```

What does is mean to not be able to become the primary owner of an object path?  How can I check why this is happening?

I am also suspecting that the hcid and DBUS session bus are not listening in on the same socket. 

```
$ dbus-launch
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-KPh3xmCqvf,guid=99a32f2da779f2875fca52004899685b
DBUS_SESSION_BUS_PID=7442
```

But in (from /etc/dbus-1/session.conf), session dbus listens to  ```
<listen>unix:tmpdir=/tmp</listen>
```

While Bluetooth (from /var/run/dbus/bluetoothd_address) listens to
```
unix:abstract=/var/run/dbus-YTFIvIHHn3,guid=7e076046a505b17fa2548b004899667e
```

And (from /etc/dbus-1/system.conf) the System DBUS listens in on:
```
<listen>unix:path=/var/run/dbus/system_bus_socket</listen>
```

These directories are different, but session dbus which is the one i'm probably interacting with is listening to a different directory all together... should i hardcode this directory setting to change it to /var/run/dbus?

I've also modified the system.con and session.conf to include system-local.conf that allows user="root" and all active users to own "org.bluez" but to still no avail. 

Thanks!

---

