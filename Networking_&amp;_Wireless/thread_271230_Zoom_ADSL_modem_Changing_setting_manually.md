---
title: "Zoom ADSL modem: Changing setting manually"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by public_void on 2006-10-04
I'm using this modem...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=11257&stc=1&thumb=1&d=1150366330[/IMG]
...and following this howto [https://help.ubuntu.com/community/UsbAdslModem/EagleUsb]("https://help.ubuntu.com/community/UsbAdslModem/EagleUsb") which works great except for the settings. After I enter "sudo eagleconfig" it guides you through setting it up. The problem is the first step asks for a pre-defined location, and none of them match. The reason is I'm currently living in Hull the only place in the UK that doesn't use BT, and uses Kingston Communications and its ISP Karoo.

So the question is how do I change the VPI, VCI and Encapsulation settings.

Thanks in advance.

---

### Post by public_void on 2006-10-05
I've solved it. The file /etc/eagle-usb/eagle-usb.conf holds the settings. The best way is to follow eagleconfig, but set the location as somewhere else, then change the file manually.

---

