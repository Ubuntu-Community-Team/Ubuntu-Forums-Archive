---
title: "Bandluxe C100"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Maha1980 on 2008-04-27
i just installed ubuntu 8.04
i need to install Bandluxe C100 for my internet connection
i'm a newbie

how can i install it?
do i need a driver for it or not?

FYI, when i plugged the Bandluxe through the express card, it showed up on my desktop..
so that's a good thing :)

---

### Post by bv8ag on 2008-04-28
> **Maha1980 said:**
> i just installed ubuntu 8.04
i need to install Bandluxe C100 for my internet connection
i'm a newbie

how can i install it?
do i need a driver for it or not?

FYI, when i plugged the Bandluxe through the express card, it showed up on my desktop..
so that's a good thing :)
Pls see attach file!!
FYI

---

### Post by the guitarist on 2008-04-28
hi everyone,

i downloaded the attachment file and the tutorial looks great..but i want to ask u ?..did't work with u ?..and how r u connecting the bandluxe trough the PCMIA port or a USB?..

thanx

---

### Post by Maha1980 on 2008-05-12
[http://marvinrebooted.wordpress.com/]("http://marvinrebooted.wordpress.com/")

---

### Post by gnuskool on 2008-06-06
bandrich - c100

Add a file called /etc/hal/fdi/preprobe/10-bandrich-c100.fdi 
(You'll need to put it there with root privileges) 

It will force the dynamic device mounting software higher up the tree to ignore the fake CD-ROM on the modem, and the bus resets don't occur. 

From Terminal     gksudo gedit /etc/hal/fdi/preprobe/10-bandrich-c100.fdi


Copy this and paste it into the file:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
<device>
<match key="usb.vendor_id" int="6797">
<match key="usb.product_id" int="4096">
<merge key="info.ignore" type="bool">true</merge>
</match>
</match>
</device>
</deviceinfo>



##################################################################
This very simple code simply instructs HAL to tell other software to ignore a device with vendor id (integer) 6797 and product id (integer) 4096. 

To get it working immediately just reset the DBUS system from terminal using

sudo /etc/init.d/dbus restart



another way to try if this does not work..
[http://marvinrebooted.wordpress.com/index/bandluxe-gsm-modem-with-ubuntu/](http://marvinrebooted.wordpress.com/index/bandluxe-gsm-modem-with-ubuntu/)

Also checkout the bug report
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/199887](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/199887)

Reply whether it works or not reply with the modem type (c100a, c100s ....)kernel etc

---

### Post by link194 on 2009-06-29
hi...this can be connect to wireless router or a normal router...with a usb-lan  convector ???or  can i connect this more then one pc  the same time...?

thx

---

