---
title: "[resolved] wifi does not reconnect on reboot"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by virgo977virgo on 2007-12-02
with ubuntu/xubuntu 7.10 my wifi connection is not restored on reboot.

I tried with two laptops (Dell D610 with builtin wifi and an old IBM laptop with the Us Robotics 5423 usb dongle) and the problem is the same.

then, I resolved placing a script on rcS.d on runlevel 99 as follows:

**step #1 - create the "networking-restart" script on /etc/init.d **

```
sudo gedit /etc/init.d/networking-restart
```

place the following text inside "networking-restart":
> #!/bin/sh
# Short-Description: Force restart of network interfaces on rcS.d level 90

# for two times ping to a test site (e.g. google) and restart network
# interfaces if ping fails
for i in $(seq 2)
do
        ping [www.google.com](www.google.com) -c 3
        [ "$?" = 0 ] && exit
        /etc/init.d/networking restart
done

save and exit gedit.

**step #2 - set owner (root) and permissions (executable) of "networking-restart"**

```
sudo chown root:root /etc/init.d/networking-restart
sudo chmod 755 /etc/init.d/networking-restart
```

**step #3 - link "networking-restart" to /etc/rcS.d/S99networking-restart**

```
sudo ln -s /etc/init.d/networking-restart /etc/rcS.d/S99networking-restart
```

**conclusion/explanation**

on boot, my script tests the connection to a test site (in my script [www.google.com);](www.google.com);) if the test site does not respond the network is restarted.

then, the connection to the test site is tried one more time, and if the test site does not respond the network is restarted one more time.

no further test is done, and the script ends.


bye

---
Stefano Spinucci

---

