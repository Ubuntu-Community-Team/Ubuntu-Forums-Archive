---
title: "modprobe and FTDI"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by marker5a on 2009-01-09
Hey everybody
I am very new to Ubuntu, so please be gentle.

I am working with the FTDI FT232RL chip as an RS232 to USB chip for embedded systems.  I am using some software that is trying to access this device through the COM port, however I am still trying to figure out the COM port setup.  I followed the directions on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251952)

> 
cd /usr/src
apt-get source linux-image-$(uname -r)
cd linux-2.6.24  //Changed it to cd linux-2.6.27 for my version

Now you have to edit the drivers/usb/serial/ftdi_sio.c/h files (add your VID PID combination).

make oldconfig
make drivers/usb/serial/ftdi_sio.ko
rmmod ftdi_sio
cp -b drivers/usb/serial/ftdi_sio.ko /lib/modules/$(uname -r)/kernel/drivers/usb/serial/
modprobe ftdi_sio


I have made it through the steps up until the "modprobe ftdi_sio" command, but I upon running that line, I get the following error:
"FATAL: Error inserting ftdi_sio (/lib/modules/2.6.27-7-generic/kernel/drivers/usb/serial/ftdi_sio.ko): Invalid module format"

Does anyone have any ideas for me?

Thanks in advance

---

### Post by Sealbhach on 2009-01-09
Hi amigo, just found this link here:

[http://www.murga-linux.com/puppy//viewtopic.php?p=90883&sid=9db4bd09b7be07ac1ffeabf567f6be4e](http://www.murga-linux.com/puppy//viewtopic.php?p=90883&sid=9db4bd09b7be07ac1ffeabf567f6be4e)

Have a read but it seem to suggest trying:

```
modprobe usbserial
modprobe ftdi_sio 
```

Hope it helps.:D


.

---

### Post by jonglauser on 2009-09-14
I'll bump this thread. I have the exact same problem. I followed the exact same steps given in that link, though I have 2.6.28-15 (Jaunty)

"sudo modprobe ftdi_sio" results in:
FATAL: Error inserting ftdi_sio (/lib/modules/2.6.28-15-generic/kernel/drivers/usb/serial/ftdi_sio.ko): Invalid module format

dmesg shows:
[ 2536.574376] ftdi_sio: no symbol version for struct_module

I would love for my converter to work and it seems all I have to do is add a new PID to the driver file. And get it to compile and work with the rest of the system. Please, any help?

-Jon

---

