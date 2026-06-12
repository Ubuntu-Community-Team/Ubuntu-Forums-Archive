---
title: "Zoom 3095 USB fax modem: Why  cdc_acm and /dev/ttyACM0 are removed?"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by yodawise on 2009-10-13
Hello all,
I am running Ubuntu Desktop on a Sony VAIO - Intel Pentium 4 CPU 3.60 MHz.

I was able to configure a Zoom 3095 USB fax modem on Ubuntu 9.04  after a lot of web surfing through numerous *how tos*.  This is how I installed the driver and ran Efax-gtk:

1) I installed the driver hsfmodem-7.80.02.03full from the dell website and followed the instructions in the INSTALL file.

2) After I rebooted, I created */dev/modem* symlink to */dev/ttyACM0*.

  3) I ran *Applications -> Office -> Efax-gtk* and selected *File -> Setting->Modem * tab and entered *modem *in the device field. Also set the fields in the *Identity* tab.

I was able to send a fax successfully using the *Single File* option and by entering the path of a *postscript* file. The 2nd attempt to send a fax failed. I traced the problem down to */dev/ttyACM0* having disappeared.

I reboot the system which resulted in */dev/ttyACM0* to be regenerated. I re-created the symlink  */dev/modem -> /dev/ttyACM0* and was able to send two test faxes and then */dev/ttyACM0 *disappeared again.

I can reproduce the error by rebooting, sending one or more faxes successfully (so far up to 3 times), before */dev/ttyACM0* disappears.

I have attached a Efax-gtk log to capture the flow for a successful send and a failed send. Please note that /*dev/ttyACM0* is no longer there when the fax send fails.

Please note that dmesg lists:
> [   17.318478] cdc_acm 5-2:1.0: ttyACM0: USB ACM device
[   17.321544] usbcore: registered new interface driver cdc_acm
[   17.321551] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters.However, *cdc_acm* is no longer listed in the output for*  dpkg --get-selections*. I recall seeing *cdc_acm* in the the *dpkg* manager output.

**Correction1**: My mistake. *cdc_acm is not listed in the dpkg get-sellections *output.

I also noticed the following messages in */var/log/syslog*:
> Oct 13 10:37:12 shoxbaz NetworkManager: <info>  starting...
Oct 13 10:37:12 shoxbaz NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000')
Oct 13 10:37:12 shoxbaz NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_11_2f_ed_e2_91
.....
Oct 13 10:37:12 shoxbaz NetworkManager: <info>  (ttyACM0): ignoring due to lack of mobile broadband capabilties
Oct 13 10:54:54 shoxbaz kernel: [ 1112.580467] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Oct 13 10:55:08 shoxbaz pulseaudio[4462]: asyncq.c: q overrun, queuing locally
Oct 13 10:55:08 shoxbaz last message repeated 3 times
Oct 13 10:56:13 shoxbaz kernel: [ 1191.204055] usb 1-4: reset high speed USB device using ehci_hcd and address 4
Oct 13 10:56:13 shoxbaz kernel: [ 1191.451719] usb 1-6: reset high speed USB device using ehci_hcd and address 5
Oct 13 10:56:32 shoxbaz kernel: [ 1209.877106] cdc_acm 5-2:2.0: ttyACM0: USB ACM device
Oct 13 10:56:32 shoxbaz usb_id[5793]: unable to access '/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:2.0/tty/ttyACM0'
Oct 13 10:56:32 shoxbaz pulseaudio[4462]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_803_3095_24680246_if0_serial_unknown_0
I am wondering if VirtualBox is causing any conflict? Note that I am not very knowledgeable.  Any ideas what causes *cdc_acm *and hence (I guess) */dev/ttyACM0* to disappear?  Thanks in advance.

---

### Post by yodawise on 2009-10-13
Well it turns out that /*dev/ttyACM0* disappears when I start VirtualMachine with the filter for the  USB device for Conextant USB modem enabled.  
If I start VirtualBox with the filter for the USB Modem disabled, then */dev/ttyACM0*  re-appears (as shown by the time stamp for /dev/ttyACM0 being newer and coinciding with when the VirtualBox gets started).

EFax-gtx seems to resume functionality after I remove *Z *from the *Reset Params* field  in* Gfax-gtk File->Settings-Params* tab.

I consider this  issue as a pilot error and will mark this thread as solved.

Thanks to those who tried to help me.

---

