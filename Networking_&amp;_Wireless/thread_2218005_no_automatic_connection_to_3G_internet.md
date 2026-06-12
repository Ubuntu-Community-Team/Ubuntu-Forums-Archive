---
title: "no automatic connection to 3G internet"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by dontunderstand on 2014-04-19
just installed Lubuntu 14.04.

What i want to have:
Push the start button of the laptop computer, after that it logins automagically to the desktop and connects to internet via usb gsm 3G dongle.

What happens:
(somehow managet to find the place to setup the connection, why wont it pop out if i put in the dongle? not to mention the nm-applet is not coming up even if put to lxde startup settings)
I cheked every possible checkbox for automatic connection (nm-applet i think) and entered sim card pin code and press save button.
After restart nothing works, it asks for some keyring password, it asks for sim unlock pin, and still does not connect because Mobile Broadband Connections are not activated.

Help me god! Its like nothing has changed for 4 years since i first got that huawei dongle and installed ubuntu-gnome.

Could you please fix it once and for all.

I have no idea where to report the bugs.
I read some of the reports, answers are like this: no, this is not pam-module bug, this is gnome-login bug etc... I dont care and i dont know about specific packages or wheter its part of Lubuntu or Gnome or something else!
I just know that simple things dont work for at least 4 years.

Would someone with knowledge, please report the correct bugs, and make them to correct those bugs.

Thank you!

---

### Post by Lars Noodén on 2014-04-19
For my Lubuntu machine, I had to modify /etc/modules, adding the following:

```

option 
usb_wwan
usbserial
usb_storage

```

I'm not entirely sure which package it applies to, but here was my guess:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1212997](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1212997)

If that is the same problem you have,  you can register that it affects you, too.

---

