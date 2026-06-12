---
title: "How do I turn off network manager"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by zackf on 2007-11-04
I'm sorry but I don't know how to turn this off in ubuntu, I'd rather it just not start at all.

I come from fedora and ntsysv doesn't work in Ubuntu.

Thank you.

---

### Post by wieman01 on 2007-11-04
This would remove Network Manager completely:
> sudo apt-get remove network-manager-gnome

---

### Post by zackf on 2007-11-05
Thank you wieman01,

I've been settting up an old laptop for my son with 7.10 and am getting it to connect to my hidden SSID with wpa_supplicant, I just didn't want NM to interefere.

---

### Post by wieman01 on 2007-11-05
> **zackf said:**
> Thank you wieman01,

I've been settting up an old laptop for my son with 7.10 and am getting it to connect to my hidden SSID with wpa_supplicant, I just didn't want NM to interefere.
No problem. Let me know if you need help there. :-)

---

### Post by zackf on 2007-11-06
Well...since you asked :-)

Everything works fine when I power down and start up, but it will not work upon reboot. Does that sound like a config error?

Don't discount the possibility of this just being a really old laptop, we're talking PII here with one usb port (WUSB54GS Linksys USB Wireless for net access) and not even an ethernet port. (Had to use a flash drive just to put ndiswrapper on ;-)

I can't seem to get the screen to be active on boot/shut down to see what's starting up or shutting down but after about 5 years the login screen does appear and Ubunut actually runs pretty well given what it has to work with.

On a totally unrelated note, I have been reading up on Xubuntu - do you think I would get a noticeable performance increase by switching to XFCE over GNOME - and can I install that over what I have now or would I have to start over? (I put Ubuntu 7.10 on now).

Thanks!

---

### Post by kevdog on 2007-11-06
I think the command you want is

sudo aptitude install xfce-desktop

---

### Post by wieman01 on 2007-11-06
Switching to XFCE will certainly tweak your performance. You should give it a try.

As for the reboot issue, you could follow instructions given in post #2 of this thread:

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

That's a pretty common problem and I have posted a workaround.

---

