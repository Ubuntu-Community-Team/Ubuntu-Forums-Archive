---
title: "[SOLVED] $20 bounty: Pantech UM175AL USB EVDO recognition under Hardy Heron"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by ziesemer on 2008-09-27
I have a Pantech UM175AL USB EVDO device that I need to get working under Linux.  I haven't got any real response at #ubuntu on IRC, and I just bought new hardware for this purpose, so I'd really like to get it working.

I believe the main issue is that this device is a "USB Composite Device", that at least under Windows, is recognized as both a USB Mass Storage Device / CD-Rom (that contains the Windows & Mac drivers), as well as a serial / COM port for the EVDO access.  Under Ubuntu, while the storage portion is easily recognized, I can't seem to get it to recognize the EVDO portion.

The relevant output from "lsusb" is attached: [ATTACH]86533[/ATTACH].

See also: [http://ubuntuforums.org/showthread.php?t=913204](http://ubuntuforums.org/showthread.php?t=913204) , where theosib is having almost the exact same issue, but actually is having slightly better luck than I am.  I never have any /dev/ttyACM* or /dev/ttyUSB* devices created, nor do I have any mention of cdc_acm, ttyACM, or "USB ACM" anywhere in my logs.

Note that under Windows, I see a "PANTECH UM175AL Composite Device" with a "Device Instance Id" of "USB\VID_106C&PID_3715\5&BFE1B0B&0&2".  It includes 3 immediate children, including the EVDO serial port, "USB\VID_106C&PID_3715&MI_00\6&1AA75A5D&0&22136", the Diagnostic Port, "USB\VID_106C&PID_3715&MI_01\6&1AA75A5D&0&4660", and the "USB Mass Storage Device", "USB\CLASS_08&SUBCLASS_06&PROT_50\6&1AA75A5D&0&12288".  The MSC then has a child "UM175AL CD-ROM USB Device", "USBSTOR\CDROM&VEN_UM175AL&PROD_CD-ROM&REV_2.31\7&3F45724&0".

I'm running a clean install of Ubuntu Hardy Heron with all the latest updates as of today (2008-09-26), kernel 2.6.24-19.

This was the first set of instructions I followed: [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/) .  However, after the simple "step 1", I have no /dev/ttyACM0 device, so that's a no-go.

Several pages mention a conflict with the Airprime driver, and that it should be disabled.  However, I'm not seeing any reference to Airprime in the logs.

Many pages refer to doing a cat on /proc/bus/usb/devices .  devices does not exist under /proc/bus/usb for me.  I believe those instructions are outdated?

I've also read through the 270+ posts at [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989) , again, with no help.  Much of the posts are related to working with an existing device, while I'm missing the needed device from /dev.  I did specifically try [http://ubuntuforums.org/showpost.php?p=4205671&postcount=153](http://ubuntuforums.org/showpost.php?p=4205671&postcount=153) , updating the vendor and product IDs with my own, but still had no success.

I've tried using modprobe to load various combinations (including all) of cdc_acm, usbserial, and ohci_hcd, as described at [http://www.raincitystory.com/wp/2007/05/31/pantech-px-500-evdo-rev-a-card-on-linux/](http://www.raincitystory.com/wp/2007/05/31/pantech-px-500-evdo-rev-a-card-on-linux/) .


Please reply with any additional tasks you'd like me to try, tests to run, etc. - as they apply to Ubuntu Hardy Heron (8.04 LTS).


Once we get the device properly recognized and working with pppd, etc., it needs to be configured similar to the "NDIS Mode" under Windows, where the connection will remain persistent and automatically reconnect after a reboot, be available to services prior to user login, etc.

While not required for the bounty, a bonus would be some way to retrieve the RSSI / signal strength indicator value - during and without seriously interrupting or disconnecting the PPP connection.  I know this can be retrieved with the "AT+CSQ" command, and it is presented with regular updates under Windows.


Thanks!!

---

### Post by ziesemer on 2008-09-27
Finally, thanks to usb_modeswitch and some work finding the proper message to send to get the UM175AL put in the proper mode, I'm making this post from Linux while connected through EVDO.

I've documented this all on my blog at [http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html](http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html).

---

