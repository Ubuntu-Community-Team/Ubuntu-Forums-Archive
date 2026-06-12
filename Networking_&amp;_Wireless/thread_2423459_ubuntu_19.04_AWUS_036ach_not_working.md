---
title: "ubuntu 19.04: AWUS 036ach not working"
date: 2019-07-23
forum: Networking &amp; Wireless
---

### Post by jafshredder on 2019-07-23
Hey, the device used to work and now I wasnt able to make it work. I have another TPLINK wifi adapter and it works so I dont know what could be happening. I ran a command I found on this same forum and this is the output:

```
mokutil --sb-state; dkms status
SecureBoot disabled
Platform is in Setup Mode
nvidia, 418.56, 5.0.0-17-generic, x86_64: installed
nvidia, 418.56, 5.0.0-19-generic, x86_64: installed
nvidia, 418.56, 5.0.0-20-generic, x86_64: installed
nvidia, 418.56, 5.0.0-21-generic, x86_64: installed
rtl8812au, 4.3.14, 4.15.0-42-generic, x86_64: built
rtl8812au, 4.3.14, 4.15.0-47-generic, x86_64: built
rtl8812au, 5.2.20.2, 4.15.0-42-generic, x86_64: built
rtl8812au, 5.2.20.2, 4.15.0-43-generic, x86_64: built
rtl8812au, 5.2.20.2, 4.15.0-45-generic, x86_64: built
rtl8812au, 5.2.20.2, 4.15.0-46-generic, x86_64: built
rtl8812au, 5.2.20.2, 4.15.0-47-generic, x86_64: built
rtl8812au, 5.2.20.2, 4.18.0-18-generic, x86_64: built
rtl8812au, 5.3.4, 4.15.0-47-generic, x86_64: built
rtl8812au, 5.3.4, 4.15.0-48-generic, x86_64: built
rtl8812au, 5.3.4, 4.18.0-18-generic, x86_64: built
rtl8812au, 5.3.4, 5.0.0-13-generic, x86_64: built
rtl8812au, 5.3.4, 5.0.0-17-generic, x86_64: installed
rtl8812au, 5.3.4, 5.0.0-19-generic, x86_64: installed
rtl8812au, 5.3.4, 5.0.0-20-generic, x86_64: installed
rtl8812au, 5.3.4, 5.0.0-21-generic, x86_64: installed
```


Do you know what could be wrong?. Thanks in advance!

---

### Post by wildmanne39 on 2019-07-23
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by jafshredder on 2019-07-24
Thanks wildmanne, I followed the inscrtructions with the wireless script and everything and here's the output  [http://paste.ubuntu.com/p/KPzK92NcfX/](http://paste.ubuntu.com/p/KPzK92NcfX/)

---

### Post by chili555 on 2019-07-24
I think that the Wild Man hoped to see a wireless report involving the Realtek device that does *not *work. Your report shows a perfectly working Atheros.

---

### Post by jafshredder on 2019-07-24
it's not working at all, I also have a tp link wifi adapter that works fine and the device that have the problem was unplugged at the time of running the script. Does it need to be plugged in at the moment of running the script? I tried to plug the device in, the lights of the awus ach036 light up and I can even connect to the network but there&#347; no connectivity when I try to open a website, what should I do?

---

### Post by chili555 on 2019-07-25
> **jafshredder said:**
> it's not working at all, I also have a tp link wifi adapter that works fine and the device that have the problem was unplugged at the time of running the script. Does it need to be plugged in at the moment of running the script? I tried to plug the device in, the lights of the awus ach036 light up and I can even connect to the network but there&#347; no connectivity when I try to open a website, what should I do?Unplug the TP-Link, plug in the non-working device, then run and paste the script.

We can't tell what driver loads or fails to load and what errors or warnings appear in the logs, if any, unless the non-working device is in the system when the script is run.

---

### Post by jafshredder on 2019-07-25
The issue was solved after changing the device from a front usb port to a back usb port. Thank you very much to both of you

---

### Post by wildmanne39 on 2019-07-25
Glad it is working.

---

