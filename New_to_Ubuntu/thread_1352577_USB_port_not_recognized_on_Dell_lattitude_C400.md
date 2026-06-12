---
title: "USB port not recognized on Dell lattitude C400"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by dennyb on 2009-12-11
I installed 9.10 on my crashed C400 laptop by swapping the hard drive to my Dell Inspiron B130 with a CD player.
 
The USB port is the only transportable media access I have  on the C400 eg Flash storage, USB external hard drive and USB CD/DVD player.

As a first time Linux user I would like to go cold turkey to Ubuntu but no USB function will force me back to Windows.
  
Any ideas to diagnose and get USB port running?

---

### Post by cariboo on 2009-12-14
Could you open an Applications-->Accessories-->Terminal, and type:

```
dmesg | grep usb
```

and paste the output into your next post.

---

### Post by dennyb on 2009-12-15
The 1st response is with nothing plugged into the single USB 1.1 port on my 
Dell Latitude C400. The 2nd response is with a old 64MB Flash stick plugged in.

Thanks for your help so far.

dlb@dlb-mini-laptop:~$ dmesg | grep usb
[    0.380150] usbcore: registered new interface driver usbfs
[    0.380210] usbcore: registered new interface driver hub
[    0.380292] usbcore: registered new device driver usb
[    1.794644] usb usb1: configuration #1 chosen from 1 choice
[   23.702368] usbcore: registered new interface driver usb-storage
[ 2531.800098] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 2531.920100] usb 1-1: device descriptor read/64, error -71
[ 2532.144085] usb 1-1: device descriptor read/64, error -71
[ 2532.360083] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 2532.480082] usb 1-1: device descriptor read/64, error -71
[ 2532.704105] usb 1-1: device descriptor read/64, error -71
[ 2532.920092] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 2533.336090] usb 1-1: device not accepting address 4, error -71
[ 2533.448096] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 2533.860086] usb 1-1: device not accepting address 5, error -71


dlb@dlb-mini-laptop:~$ dmesg | grep usb
[    0.380150] usbcore: registered new interface driver usbfs
[    0.380210] usbcore: registered new interface driver hub
[    0.380292] usbcore: registered new device driver usb
[    1.794644] usb usb1: configuration #1 chosen from 1 choice
[   23.702368] usbcore: registered new interface driver usb-storage
[ 2531.800098] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 2531.920100] usb 1-1: device descriptor read/64, error -71
[ 2532.144085] usb 1-1: device descriptor read/64, error -71
[ 2532.360083] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 2532.480082] usb 1-1: device descriptor read/64, error -71
[ 2532.704105] usb 1-1: device descriptor read/64, error -71
[ 2532.920092] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 2533.336090] usb 1-1: device not accepting address 4, error -71
[ 2533.448096] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 2533.860086] usb 1-1: device not accepting address 5, error -71
[ 5988.396088] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 5988.516120] usb 1-1: device descriptor read/64, error -71
[ 5988.740083] usb 1-1: device descriptor read/64, error -71
[ 5988.956100] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 5989.076102] usb 1-1: device descriptor read/64, error -71
[ 5989.300086] usb 1-1: device descriptor read/64, error -71
[ 5989.516242] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 5989.932142] usb 1-1: device not accepting address 8, error -71
[ 5990.044104] usb 1-1: new full speed USB device using uhci_hcd and address 9
[ 5990.460087] usb 1-1: device not accepting address 9, error -71
dlb@dlb-mini-laptop:~$

---

### Post by mfrag on 2010-02-12
Did you ever get this figured out?  I'm having the same issue with a dell inspiron 4150.  Thanks.

---

