---
title: "CDMA USB Modem"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by farmannawaz on 2006-09-01
Hello
I have CDMA USB Wireless telephone set. it has builtin qualcomm modem. i have configured it in redhat 9 using wvdial.conf and wvdial. now over here in ubuntu i am not able to find the file for configuration . i need some body help to connect to internet. the modem is detected and its there in device manager.

---

### Post by mimoh_mi on 2006-10-01
*@farmannawaz*
I hope this post is comming late. Are you using a usb adater,
if yes, plug in the adapter to both your system and the phone,
kill all the tty process or restart your system, ubuntu hotplug
for usb device will detech and assign the usb to the device.
do a dmesg to check where the usb is assigned.
You should see something like usb serial --> ttyUSB0,
this is your modem port. Do a wvdialconf to detech
the modem, it might require several trials.
If all is ok, run pppconfig and fill in the required fields.
For, authentication, if you are not sure of the type used by
your ISP, choose PAP, save the file. Then run pon <nameOfFile>,
Your connection should be up. Happy surfing.

---

### Post by knight17 on 2006-10-16
I think this link will help you:
[http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto](http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto)

---

### Post by nat123 on 2008-02-21
Can I have pointer to the following:

Where do I get Driver for Linux port?

I want this for ARM-LINUX Embedded controller LN2410?

Also I need the steps to compile and load the driver.

Thanks

Natarajan

---

