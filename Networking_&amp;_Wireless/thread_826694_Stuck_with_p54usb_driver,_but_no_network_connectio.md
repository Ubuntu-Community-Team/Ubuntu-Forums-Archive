---
title: "Stuck with p54usb driver, but no network connection"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by rekked on 2008-06-12
Hi all,

I have just installed Ubuntu and I'm stuck when trying to set up the wifi adapter. I am using a US Robotics 5422 usb device, but I can't get it to work.

I've followed these two threads:

[http://ubuntuforums.org/showthread.php?t=554688&highlight=usr5422](http://ubuntuforums.org/showthread.php?t=554688&highlight=usr5422)
[http://ubuntuforums.org/showthread.php?t=712017&highlight=usr5422](http://ubuntuforums.org/showthread.php?t=712017&highlight=usr5422)

But I still can't seem to connect. I as following the 2nd thread, and I got stuck here:

```
rsc4usb driver installed
device (0BAF:0118) present (alternate driver: p54usb) 
```

I have managed to download the drivers, I have set up all driver file names as lower case, and I blacklisted the p54usb drive, and  it still shows up. However, If I go to System > Administration > Networking, I don't see the device.

What's worrying me though is that if I do:

```
modprobe p54usb
```

The device DOES show up, but it can't connect to the network (no response from the internet/ping to the gateway whatsoever).

Another thing that worries me is that if I execute:

```
lshw -C network
```

Nothing shows up. Not even the ethernet connection (which works flawlessly). lsusb does show up the device.

Questions:

1) Has anyone succesfully configured this device with the p54usb drivers? I am willing to kick ndiswrapper in the nuts and let go with the p54usb driver.

2) I have been tempted to move the p54usb driver files out of the usual folder to ensure it doesn't load. Why is it loading?

3) Has anyone got any pointers as to what I am doing wrong?

Thanks in advance!

---

### Post by Bikerbob on 2008-09-08
IF your still around.. hows your luck been on this issue.

I would assume with no responses and 3 months now you have either solved it from help somewhere else, or given up.

I have the same issue with the p54usb .. though I am trying it with the driver not ndsiwrapper.

---

### Post by rekked on 2008-09-16
Hello there!

I'm sorry I can't help you. I ended giving up, it was my brother's computer and he ended up using Windows (shame, I know).

If you manage to make it work, I'd love to hear how you managed it.

---

