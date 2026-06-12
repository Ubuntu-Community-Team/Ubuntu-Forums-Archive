---
title: "Printing Problem - Errors and Logs Provided"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-04
Hi,

Could some one take a look at this and help explain why this printer wont print ?

***************************************************************************
misty@KAOS:~$ $ lsmod | grep usb
bash: $: command not found


misty@KAOS:~$ lsmod | grep usb
usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            82752  0 
libusual               30356  1 usb_storage
usbcore               149360  7 isp1760,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
scsi_mod              155212  6 sbp2,sd_mod,sr_mod,usb_storage,sg,libata


misty@KAOS:~$ tail -f /var/log/messages
Feb  4 15:06:54 KAOS kernel: [   33.975474] NET: Registered protocol family 17
Feb  4 15:07:10 KAOS pulseaudio[6048]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  4 15:07:10 KAOS pulseaudio[6050]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  4 15:07:10 KAOS pulseaudio[6050]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  4 15:07:26 KAOS kernel: [   65.116465] UDF-fs: No VRS found
Feb  4 15:07:41 KAOS kernel: [   80.428523] NET: Registered protocol family 10
Feb  4 15:07:41 KAOS kernel: [   80.430645] lo: Disabled Privacy Extensions
Feb  4 15:07:52 KAOS kernel: [   91.580455] type=1503 audit(1233778072.527:5): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6364 profile="/usr/sbin/cupsd"
Feb  4 15:07:53 KAOS kernel: [   92.148255] type=1503 audit(1233778073.098:6): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6369 profile="/usr/sbin/cupsd"
Feb  4 15:07:53 KAOS foo2lava-wrapper: foo2lava-wrapper -z1 -r1200x600 -p2 -m0 -s255 -d1 -Gkm2530-jconner-d50.icm
Feb  4 15:14:38 KAOS kernel: [  497.624044] usb 2-2: new high speed USB device using ehci_hcd and address 8
Feb  4 15:14:38 KAOS kernel: [  497.760624] usb 2-2: configuration #1 chosen from 1 choice
Feb  4 15:14:39 KAOS kernel: [  498.120574] usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x132B pid 0x2001
Feb  4 15:14:39 KAOS kernel: [  498.120616] usbcore: registered new interface driver usblp
Feb  4 15:14:42 KAOS foo2lava-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN -dMaxBitmap=500000000  
Feb  4 15:14:42 KAOS foo2lava-wrapper: foo2lava -r1200x600 -g10200x6600 -pna_letter_8.5x11in -mplain -n1 -d1 -s255 -z1  -u 204x100 -l 204x100       
^C


misty@KAOS:~$ lpinfo -v
network socket
network beh
direct hpfax
direct hp
network http
network ipp
direct hal:///org/freedesktop/Hal/devices/usb_device_132b_2001_noserial_if0_printer_noserial
direct usb://KONICA%20MINOLTA/magicolor%202400W
network lpd
direct parallel:/dev/lp0
direct scsi
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS1?baud=115200
network smb


************************************************************************

THANKS !!!:p

---

### Post by mistypotato on 2009-02-04
Anyone?

---

### Post by plucky on 2009-02-04
Tell us the make and model of the printer.

Have you searched the forum for a Howto install your printer?

Have you checked the [Open Printing Database](http://www.openprinting.org/printer_list.cgi) to see if your printer is supported?

Is it parallel or USB connected?

If USB post output of a terminal of ```
lsusb
```

Can you see the printer in **System > Administration > Printing**

Or Open Firefox and input into the browser address bar ```
http://localhost:631/admin/
```

Can you see your printer?


Good luck

---

