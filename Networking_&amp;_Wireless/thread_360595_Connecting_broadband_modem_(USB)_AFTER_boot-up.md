---
title: "Connecting broadband modem (USB) AFTER boot-up"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by TobyReynolds on 2007-02-13
Hello,

I installed Ubuntu 6.10 a week or so ago and managed to get my SpeedTouch 300 modem to connect to the Internet (Virgin ISP) by following the excellent instructions here: [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

However, the connection only works if I boot into Linux (I have dual-boot with Windows XP) with the modem's USB cable already plugged into the computer. If I try to plug in and connect when already booted (as is possible in Windows), the lights on the modem come on as normal but no connection results (at least, web pages don't load, emails don't download, etc.). I would like to know if there is a way to get connected without re-booting, as I have a laptop and need to connect and disconnect several times during the day as I move about the house; perhaps there is some command to type into the Terminal to redo whatever the computer does when it loads up and initialises the connection?

As an aside, is there also some way to see how many bytes have been sent and received since connection?

The modem setup instructions in the above link are actually for Ubuntu 6.06. Is it the same procedure for the latest version, or is there a better way which would allow the computer to recognise when it has been connected? As you may have guessed, I am fairly new to Linux, so simple answers (if possible, or otherwise step-by-step instructions) would be greatly appreciated.

Many thanks for any help with this, and apologies if I missed this information in a previous thread.

Toby Reynolds

---

### Post by matogrosso on 2007-09-25
Yes. I do it at home. When Ubuntu is already up and running, just plug the USB modem and run this command:

> sudo ./dial

It has to be run from the same directory where your "dial" file is.

Regards,
Matogrosso


HOWTO SpeedTouch 330 USB modem and Virgin under UBUNTU in the UK.
[http://ubuntuforums.org/showthread.php?t=559395](http://ubuntuforums.org/showthread.php?t=559395)

---

