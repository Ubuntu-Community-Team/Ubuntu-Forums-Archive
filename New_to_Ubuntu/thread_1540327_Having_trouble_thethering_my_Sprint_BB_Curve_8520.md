---
title: "Having trouble thethering my Sprint BB Curve 8520"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by BriarHood on 2010-07-27
I am having an issue getting berry4all to work on my laptop. I am running Ubuntu 9.10 and I have a Sprint BlackBerry Curve 8520 with unlimited data. I am really hoping to be able to use my phone as a modem. I have followed the instructions for install on Berry4All with no results. Please help. I know everything is installed correctly but I still get a Bus error when trying to run with terminal. I am getting frustrated. Help?

---

### Post by LowSky on 2010-07-27
have you tried a battery pull on the device? also just because you have unlimited data plan doesn't nessarily ean you have tethering included.

Did you install these packages, they are required: python, libusb-dev, ppp, python-usb?

it can be easily done from this command

```
sudo apt-get install python libusb-dev ppp python-usb
```

---

### Post by BriarHood on 2010-07-27
Everything is installed. I just tried a battery pull.

---

### Post by BriarHood on 2010-07-27
Also, I am positive we have tethering. Someone else on the plan uses it with Windows.

---

