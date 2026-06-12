---
title: "very slow boot of USB live Xubuntu"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by bholtby on 2010-02-16
I created a live USB installation of Xubuntu 9.1 on a 16gb stick using the "USB Startup Disk Creator" running from a live CD session. The machine is an IBM T42 laptop with 1gB RAM. 4gB was reserved on the stick for saving whatever is saved for persistency. After a cold start on the machine and selecting the USB as the boot device, there is a brief flicker of activity (the usb light flickers) and a couple of lines flit by on the screen and then a little mouse that fades in and out appears. The mouse remains for 1.5 minutes. Then there is a short flicker, mouse goes and an underline cursor top left appears. That cursor remains with no disk activity for 5 min. and then linux boots. 2 min. later and all seems to work. Same sequence on an Acer Aspire 5516 (new machine). For many attempts I turned the machine off because I thought it had frozen. On one of those attempts there was a cryptic message about a timeout detecting a noise threshold?? Then I discovered that it would boot eventually. This is much slower than booting a live CD. Is such a slow boot normal for a USB live installation or is something amiss?

---

### Post by zeroseven0183 on 2010-02-16
No, booting should be normal when you have a good USB. Considering that you tested it on two different laptops, you probably might have a troubled USB. Not sure if it's hardware or could possibly be the disk creation. Have you tried reinstalling it?

---

### Post by bholtby on 2010-02-16
Stick appears to be very fast on my Windows desktops and the diagnostics don't report problems. I have installed both ubuntu and xubuntu many times (~15) over the past few days using unetbootin and the USB Startup Disk Creator with the same result everytime. In fact I initially gave up on the Startup Creator because it appeared that the install didn't work because of the long boot time. Between each attempt I reformat as FAT32 in Windows.

The only thing "weird" (I should have mentioned this) is that in the Startup Creator panel there are two 16gB partitions shown on the stick both of which are flagged as needing to be formatted. One of them can't be reformatted (shown first) while formatting the other works.

---

### Post by zeroseven0183 on 2010-02-16
It happens to me some times. Have you tried the instructions here
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) ?

Download the USB Installer for Ubuntu.EXE from that site and run it on one of your Windows machine to create a live USB.

---

### Post by bholtby on 2010-02-16
Thanks for the suggestion!!! I hadn't seen that article. Also hints at how I can reserve more space for apps. Will try soon and post my experience.

---

### Post by NightwishFan on 2010-02-16
Booting the USB with elevator=noop seems to improve performance.

---

### Post by bholtby on 2010-02-17
I followed the instructions at pendrivelinux and used their neat installation program. Same result. I then installed ubuntu instead of xubuntu. Same problem but ubuntu defaults to a verbose mode, so the problem was revealed. The machine sat for almost 7 minutes with a boot sector error on device \fd0 - not surprising since there is no floppy. I went into the bios and sure enough support for a legacy floppy drive was enabled on both laptops. Disabling the support and rebooting resulted in lightning fast boots.

---

### Post by NightwishFan on 2010-02-17
I had that happen to me with puppy linux, glad you solved it.

---

