---
title: "Network connection failure"
date: 2017-10-03
forum: Networking &amp; Wireless
---

### Post by plaidshirtakos on 2017-10-03
There is network connection loss on an Ubuntu 16.04.3 desktop machine.
systemctl status networking.service gives following output:

Failed to start Raise network interfaces.

sudo service networking restart command failed too.

ifconfig -a gives 3 interfaces as output: docker0, eno1 and lo.

There wasn't any configuration change on machine, I tried to restart it too.

I modified /etc/network/interfaces file with the following content:


    ```
auto eno1
iface eno1 inet  dhcp
```


Command sudo /etc/init.d/networking restart` was successful too, but status is: active(exited).

Is it possible to restore default network settings?

---

### Post by TheFu on 2017-10-04
> **plaidshirtakos said:**
> 
Is it possible to restore default network settings?

Yes.  2 options that I know work.
* restore from that backup you have.  Right?
* reinstall the OS.

There are likely other options that might work, but that wasn't the question posed.

Generally, a desktop machine would be using network-manager, not the server stuff.  network-manager used to get confused by non-trivial setups.  I stopped using it when that happened ... about 5-7 yrs ago.  

Since then, I've manually handled network connections.  16.04 was my first run-in with  systemd ... it gets really confused by non-trivial network stuff.

I don't know anything about docker, so ... 

In my world (I run lots of virtual machines and use manual Linux bridges as necessary), I have to bring down the linux bridge manually, then the interface, then bring up the interface and finally the linux bridge, to get networking restarted.  The order for each step is critical. Of course, a reboot seems to always bring up the networking ... at least in my world.  ifup/ifdown are the commands I use.

Don't know if this will be helpful or not. Hope it is.

---

