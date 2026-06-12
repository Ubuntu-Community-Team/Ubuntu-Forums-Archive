---
title: "Writing udev script to autoconnect CDMA Wireless Modem when inserted"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by Ohmu on 2008-10-14
Hello!

I'm currently in India.  I get internet via a USB Wireless Modem.

I have it working, but I would like to make it work automatically when it is plugged in.

To make it work, I simply edit /etc/wvdial.conf, and sudo wvdial TATA.  I got this off a google search...

Here's the new wvdial.conf:
[INDENT]
[Dialer Defaults]
Init = ATZ

[Dialer TATA]
stupid mode = 1
Init1 = ATZ
Init2 = AT+CRM=1
Modem = /dev/ttyACM0
Modem Type = USB Modem
Baud = 230400
Phone = #777
ISDN = 0
Dial Command = ATDT
Username = internet
Password = internet[/INDENT]

(dmesg showed me it's ttyACM0).

This is great - it works!  But it's messy - every time I plug in the modem, I have to open a terminal window, and run sudo wvdial.conf TATA.  I guess I could fork a new process by adding a  &, then close the terminal window... but I'd like to automate it.

Looks like I need to create a udev script that does this whenever it gets plugged in.

Here's my try:  Tagging this onto the end of 
/etc/udev/rules.d/20-names.rules

[INDENT]# My USB Modem
# udevinfo -a -p $(udevinfo -q path -n /dev/ttyACM0)  gives us the numbers
SUBSYSTEM=="usb_device" ACTION=="add" SYSFS{idVendor}=="1b7d",SYSFS{idProduct}=="070a" \
SYSFS{bNumConfigurations}=="1" \
SYSFS{bConfigurationValue}=="1" \
**RUN+="/bin/sh -c 'wvdial TATA &'"**[/INDENT]

I stick the device in.  It doesn't connect.  nslookup [www.google.com](www.google.com) times out.  sudo wvdial TATA reports device is busy.

Removing this code, manually plugging in the device then _immediately_ running 'sudo wvdial TATA' -- it fails! It works the second time.  So it seems the device needs some time to stabilize.

So I need to either (a) put in a pause, (b) keep retrying, or (c) maybe the device emits an 'ok I'm ready now', and I can catch this.  What to do?


It's that last line of my edit I'm really not sure about. 
 
[INDENT]**RUN+="/bin/sh -c 'wvdial TATA &'"**[/INDENT]

This intro to udev ...
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)
... explains that if a rule hits non-terminating code it will hang.  So I've added the  & to fork a new process.  Is this correct?

Finally, how can I get an icon to show it's connected?  I guess I'll have to write my own script and call it from the udev rules.  and this script should pause, invoke wvdial, and catch the output, examine it and update the icon accordingly.  Can I do that from a script?  What to use?  I'd like to make a little offering for Linux users in India, and learn how to deploy an app at the same time.

Please help if you can!

Sam

---

### Post by idx on 2009-05-14
BUMP

Need a solution. Planning to buy a Tata Photon + HSIA modem most probably Huawei. will do so only if it works on UBUNTU

---

### Post by idx on 2009-05-14
Thanks for the Post by the way.

---

