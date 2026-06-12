---
title: "usb problems"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by gokul10 on 2009-12-26
hi all i am new to ubuntu and i find it very good just have one problem i am having some problems with usb ubuntu doesnt detect my external hard drive and mouse plssss somebody help me thnks

---

### Post by cartisdm on 2009-12-26
What version of Ubuntu are you running? Do they work when you run a LiveCD? I haven't come across any USB mice that didn't work in Ubuntu/Linux so that's a little odd to me

---

### Post by gokul10 on 2009-12-27
hi i got the mouse working but the problem with my external drive is tht if i connect it right from the time i switch on the system it gets mounted but once i unmount and unplug it ubuntu doesnt detect it again when i plug it in

---

### Post by gokul10 on 2009-12-27
i am using ubuntu 9.10

---

### Post by Methuselah on 2009-12-27
I am assuming you have a powered external USB hard drive enclosure?
I have a similar problem with mine in that it is recognized by the operating system unreliably.
Unfortunately, I don't have a solution right now.

---

### Post by gokul10 on 2009-12-27
hi mine is not an external powered hard drive its an normal 2.5 inch 160gb SATA harddrive with an enclosure i just have this problem once this is fixed i am planning to quit windows 7

---

### Post by cmcanulty on 2009-12-27
This to me is the major drawback to Ubuntu, USB devices shouldn't be a constant struggle to mount or be recognized. Hopefully they will improve this issue soon.

---

### Post by cartisdm on 2009-12-28
When you plug the drive into your computer via USB and it DOESN'T appear to recognize it, post the output of

```
sudo fdisk -l
```

It's possible that it's mounting it but maybe not allowing you to view it for some reason.  This should tell us if the OS is at least seeing the storage device connected

---

### Post by cmcanulty on 2009-12-29
```
cmcanulty@Gateway:~$ sudo fdisk -l

Disk /dev/sda: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       38539   309564486   83  Linux
/dev/sda2           38540       38913     2996122    5  Extended
/dev/sda5           38540       38913     2996122   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.
cmcanulty@Gateway:~$ ^C
cmcanulty@Gateway:~$ 













```

---

### Post by nothingspecial on 2009-12-29
Unplug it then plug it back in again

Then post the results of ```
dmesg | tail -n 25
```

---

### Post by cmcanulty on 2009-12-29
Here it is 
> cmcanulty@Gateway:~$ dmesg | tail -n 25
[ 2543.006666] PM: Image restored successfully.
[ 2543.038909] Restarting tasks ... done.
[ 2543.050875] PM: Basic memory bitmaps freed
[ 2544.739640] sky2 eth0: enabling interface
[ 2544.739871] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2544.908058] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2544.908068] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2544.908073] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2544.948478] Registered led device: b43-phy0::tx
[ 2544.948523] Registered led device: b43-phy0::rx
[ 2544.948567] Registered led device: b43-phy0::radio
[ 2544.949470] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2545.501983] [drm] Loading R300 Microcode
[ 2545.502013] [drm] Num pipes: 1
[ 2546.422695] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 2546.423225] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2557.016030] eth0: no IPv6 routers present
[ 5283.076217] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 5283.076230] usb 2-1: USB disconnect, address 2
[ 5283.384051] usb 2-1: new low speed USB device using ohci_hcd and address 3
[ 5283.597427] usb 2-1: configuration #1 chosen from 1 choice
[ 5283.604904] input: Logitech N48 as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input8
[ 5283.605094] generic-usb 0003:046D:C001.0002: input,hidraw0: USB HID v1.00 Mouse [Logitech N48] on usb-0000:00:13.0-1/input0
[ 5287.524083] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 5287.604108] hub 1-0:1.0: unable to enumerate USB device on port 3
cmcanulty@Gateway:~$ 



---

### Post by gokul10 on 2009-12-29
hi everyone its workin now thnks for helpin me out guys

---

