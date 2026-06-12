---
title: "pamusb-conf problem"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by A_M_S on 2010-11-12
Hello

I'm trying to install pamusb-tools on Ubuntu 10.4 using [this link]("http://pamusb.org/doc/quickstart") as a reference.

But after connecting a USB device panusb-conf don't detect any removable devices.

```

sudo pamusb-conf -v -d test

Inspecting /org/freedesktop/Hal/devices/storage_serial_SPCC_USB_DISK_000000000068EA_0_0
	Invalid: Device does not contain any volume
Inspecting /org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_T10N
	Invalid: 'storage.serial'
Inspecting /org/freedesktop/Hal/devices/storage_serial_HTS541010G9AT00_MP20XAX0KS4RHS
	Invalid: Not a removable device
No devices detected.

```

Using pmount i can see my usb pen mounted


```
pmount
Printing mounted removable devices:
/dev/sdb on /media/TRABALHO type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro)
To get a short help, run pmount -h
```


Anybody know how to fix this?

Tnx.

---

### Post by A_M_S on 2010-11-12
I think fix the issue.

The problem was the pen filesystem (FAT32).

If someone need it a workaround can be found [here]("http://mattmole.wordpress.com/2008/04/28/authenticate-using-usb/")

---

