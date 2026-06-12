---
title: "Problem while connecting to internet using 3G USB modem"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by sagar6 on 2014-08-25
Ive dual booted ubuntu 14.04 with windows 8.1. Im trying to connect to internet using a DLink 3G USB modem(dongle).When for the first time I connected it to ubuntu, It asked me to create new mobile broadband network, I created it and connected to the internet successfully. But when next time I tried to connect it, I was unable. I am unable to tick Enable Mobile Broadband option , whenever I click on it i get an message -Disconnected you are now offline(At the right top corner.) Ive created a mobile broadband connection named TATA Docomo. But when I click on it I again get the message>>Disconnected modem network .I tried lot of times but Im getting the same error. I also got a message>System program problem detected and when I clicked on report problem, it said >>Sorry Ubuntu 14.04 has experienced an internal error; giving executable path as /usr/sbin/ModemManager  and problem type as crash .I tried lots commands including start,stop,restart,kill modemmanage/networkmanager but nothing worked. Im including the photos of this message. Please suggest me the proper solutions asap. Thank you.

---

### Post by Malcolm_Gaissert on 2014-08-25
Had the same problem. Win 8.1 worked with the USB adapter. But would not work with the Ubuntu distro 13.10. Then it finally dawned on me. The problem was that Ubuntu was actually blocking the original WiFi device that was still in the laptop and therefore not allowing the USB device to function.

What to do? I turned off the computer turned it over, found the door that the internal wifi device was behind and carefully removed it. Remove the screws first then when the device lifts up gently remove the antenna wires. If at some time you wish to replace the device with a new one make note of where the wires were attached.

Powered up the laptop and I have had WiFi since the moment I filled in the correct info. (I have a D-Link DWA140 attached to its short USB cord.)

Good luck

---

