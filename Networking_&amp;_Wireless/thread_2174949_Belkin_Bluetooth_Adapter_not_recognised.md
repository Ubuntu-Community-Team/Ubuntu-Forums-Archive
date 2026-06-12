---
title: "Belkin Bluetooth Adapter not recognised"
date: 2013-09-16
forum: Networking &amp; Wireless
---

### Post by maccard on 2013-09-16
I'm using a dell Latitude E6500, running 12.04, which has bluetooth built in, but I need Bluetooth LE 4.0. I have a Belkin F8T065bf device, which is not recognised at all using blueman. 
lsusb lists it as "ID 050d:065a Belkin Components"
hcitool dev returns the built in bluetooth chip, which I don't want to use. Is there any way to get this working?

---

### Post by bytefish on 2013-12-31
This thread is rather old, but I had the same problem on my distribution. Actually the chip is supported, but its ID is not known by the **btusb** driver. I am sure, this has been patched already, but nevertheless here's how to use the device.

You can use the following commands (as root) to load the **btusb** driver and add the Belkin Bluetooth adapter:

```

modprobe btusb 
echo "050d 065a" >> /sys/bus/usb/drivers/btusb/new_id

```

And then you should be able to see the device using **hcitool**.

---

### Post by arnaudlecam on 2014-04-14
I tried bytefish', without any success...
but i found the solution on .... [amazon.co.uk]("http://www.amazon.co.uk/Belkin-USB-4-0-Bluetooth-Adapter/dp/B009IQB3US") by [ChrisW]("http://www.amazon.co.uk/gp/pdp/profile/A3R14FL4E2T9TO/ref=cm_cr_dp_pdp/276-2102948-7273850") !!!!

As root:
1) Create the file:
sudo /etc/udev/rules.d/99-local-bluetooth.rules

2) Add the following line to the file:
SUBSYSTEM=="usb",  ATTRS{idVendor}=="050d", ATTRS{idProduct}=="065a", RUN+="/bin/sh -c  'modprobe btusb; echo 050d 065a > /sys/bus/usb/drivers/btusb/new_id'"

3) To pick up the change
  either
  Restart the udev service:
sudo services udev restart

bluetooth' applet suddenly appeared, and was working well !!!

Thank you

Ubuntu 12.04 LTS / Linux 3.8.0-38-generic

---

