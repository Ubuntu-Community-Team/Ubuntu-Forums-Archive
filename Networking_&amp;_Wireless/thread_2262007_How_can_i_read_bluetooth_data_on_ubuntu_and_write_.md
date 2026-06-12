---
title: "How can i read bluetooth data on ubuntu and write it to file"
date: 2015-01-22
forum: Networking &amp; Wireless
---

### Post by Abhijit_Jawalkar on 2015-01-22
Hi All,

I am working on project wherein i am required to read data from temperature sensor on ubuntu through bluetooth.

Temperature sensor is mounted on hardware kit , it senses data and send that data over bluetooth to ubuntu desktop.

I want to read that on ubuntu machine and write it to some file.

i came across hcidump hci0 command , but its not working on my end. Not sure if bluetooth device i have added on ubuntu has hci0 association.

I appreciate if someone can provide me shell script to do above job, 

Thanks in advance.

Regards,
Abhijit

---

### Post by QIII on 2015-01-22
Hello!

Is this something for a project at work?

---

### Post by tgalati4 on 2015-01-23
Here's one method using a Ruby script:  [http://stackoverflow.com/questions/15799076/accessing-serial-data-from-neurosky-mindset-over-bluetooth-in-linux](http://stackoverflow.com/questions/15799076/accessing-serial-data-from-neurosky-mindset-over-bluetooth-in-linux)

Don't *forget* the bluez utilities:

> 
bluez-btsco - Bluez Bluetooth SCO tool
bluez-gstreamer - Bluetooth GStreamer support
bluez-hcidump - Analyses Bluetooth HCI packets
bluez-pcmcia-support - PCMCIA support files for BlueZ 2.0 Bluetooth tools
bluez-tools - Set of tools to manage Bluetooth devices for linux


If you are using an Arduino to read the temperature sensor, then there are a lot of methods to use.  If you are using some proprietary hardware, then you will have to figure out the data packets yourself.

---

