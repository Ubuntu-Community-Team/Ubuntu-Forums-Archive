---
title: "usb stick: sometimes detects, sometimes not."
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Sejanus on 2010-01-26
I've got kinda weird problem. My Ubuntu 9.04 sometimes sees and auto-mounts USB stick, sometimes not. It's one and the same stick all the time. At the moment it's not automounted. sudo fdisk -l returns all known partitions (but not USB). Anything I could do...?

---

### Post by byStanderone on 2010-01-26
...had the same problem with my other pc, corrected it by not using a usb keyboard/mouse when using a usb stick.

---

### Post by Psumi on 2010-01-26
This will also happen when you install from mini.iso and install the xfce4, openbox or lxde packages but not the gnome-core or gnome metapackages.

Apparently, there's something special about nautilus or gnome that these lightweight systems don't have. Anyway, was just an idea.

---

### Post by jd65pl on 2010-01-26
Do you get any info from dmesg when you plug it in? It should be the last information displayed if run right after the usb drive is plugged in.
```
sudo dmesg
```

Also check the log
```
tail -f /var/log/messages
```

You can check udev is running,
```
ps aux | grep udevd | grep -viE 'grep'
```

---

### Post by Sejanus on 2010-02-01
Thanks jd65pl ;)

I've got some error messages with sudo dmesg:

> 
[ 9531.532091] usb 2-3: new high speed USB device using ehci_hcd and address 3
[ 9531.965027] usb 2-3: configuration #1 chosen from 1 choice
[ 9532.009223] Initializing USB Mass Storage driver...
[ 9532.009557] scsi6 : SCSI emulation for USB Mass Storage devices
[ 9532.009737] usb-storage: device found at 3
[ 9532.009742] usb-storage: waiting for device to settle before scanning
[ 9532.009753] usbcore: registered new interface driver usb-storage
[ 9532.009761] USB Mass Storage support registered.
[ 9537.008389] usb-storage: device scan complete
[ 9543.113070] usb 2-3: reset high speed USB device using ehci_hcd and address 3
[ 9558.224064] usb 2-3: device descriptor read/64, error -110
Log shows this:

> 
Feb  2 02:38:56 username kernel: [ 9614.720103] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Feb  2 02:39:07 username kernel: [ 9625.129156] usb 2-3: USB disconnect, address 3
Feb  2 02:39:07 username kernel: [ 9625.131928] scsi 6:0:0:0: Device offlined - not ready after error recovery
And the last command returned
> 
root       895  0.0  0.0   2356   612 ?        S<s  Feb01   0:00 /sbin/udevd --daemon


---

