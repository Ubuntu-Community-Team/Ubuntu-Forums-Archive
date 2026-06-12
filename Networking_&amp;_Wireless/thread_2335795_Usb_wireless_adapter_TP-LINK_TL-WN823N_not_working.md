---
title: "Usb wireless adapter TP-LINK TL-WN823N not working"
date: 2016-09-01
forum: Networking &amp; Wireless
---

### Post by geeko9876 on 2016-09-01
Hi,
I bought a TP-LINK TL-WN823N wireless adapter. My Ubuntu version is the 16.04. Official drivers for this device have no compatibility for kernel 4+. I managed to have it working anyway following this guide:
[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

Unfortunately in order to have the graphic card working I had to update the kernel to the 4.7.2. After the update the device has stopped working. I also installed the linux-firmware package, I don't know what caused the issue.

I actually noticed the graphic card works with any kernel version  >= 4.4.0-36. So it would be ok for me to use an older version of the kernel than the 4.7.2.

I also tried to start Ubuntu with the previous kernel version using the option from the grup menu at startup, but it didn't change anything.

This is the lshw result:

*-usb:0 UNCLAIMED
    description: Generic USB device
    product: 802.11n NIC
    vendor: Realtek
    physical id: 4
    bus info: usb@1:4
    version: 2.00
    serial: 00e04c000001
    capabilities: usb-2.10
    configuration: maxpower=500mA speed=480Mbit/s


and this lsusb:

Bus 001 Device 006: ID 2357:0109


It's an entire day I'm trying to have it working.

I hope I'll not have to reinstall everything from scratch. It took me several days to install the software I use for my work. That would be very bad. :(

Please help me.

---

### Post by jeremy31 on 2016-09-01
*Thread moved to **Networking & Wireless**.*

The fix might be to change the source code in rtl8192cu-fixes/blob/master/os_dep/linux/usb_intf.c on line 163 to
```
	{USB_DEVICE(0x2357, 0x0109)}, /* TP-Link - TP-Link */ \
```

And then compile it.  I am not sure how rtl8192cu fixes could have worked for your device with any kernel as your USB ID is not included

---

### Post by geeko9876 on 2016-09-02
Thank you for your answer.
I did a google search for these strings: 0x2357, 0x0109.

I found these drivers:
[https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)

Then installed them in this way:
git clone [https://github.com/Mange/rtl8192eu-linux-driver.git](https://github.com/Mange/rtl8192eu-linux-driver.git)
sudo make install

Now it works. 

Thanks :)

---

### Post by geeko9876 on 2016-09-02
After having the adapter working I also had another issue. At startup it wasn't working. I had to unplug and replug it to make it work.

I solved in this way:

```

[COLOR=#555555][FONT=Monaco]sudo -i[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]echo 8192eu >> /etc/modules[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]exit[/FONT][/COLOR]

```

---

### Post by jeremy31 on 2016-09-02
Not sure why you would need to have added 8192eu to /etc/modules as the Makefile runs depmod after the install so that the module alias list is updated.  I thought that USB ID was familiar and it wasn't until you posted the link to mange's github that I remembered [https://github.com/Mange/rtl8192eu-linux-driver/commit/86007a1387e14096da5806933882975c58854b83](https://github.com/Mange/rtl8192eu-linux-driver/commit/86007a1387e14096da5806933882975c58854b83)

Use the thread tools menu at the top of the page to "Mark as Solved" if you are happy with the results

---

### Post by geeko9876 on 2016-09-02
If it weren't for you it'd taken ages for me to figure it out.

Thanks :)

---

### Post by texpat on 2016-12-18
After getting the driver from github as described above, this is what actually made it work.

Thanks for the insight!

---

### Post by texpat on 2016-12-18
This made it work for me: thanks!

---

