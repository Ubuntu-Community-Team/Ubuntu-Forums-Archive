---
title: "WiFi not working on HPStream 11 with 16.04.4 LTS"
date: 2018-04-18
forum: Networking &amp; Wireless
---

### Post by steveca96 on 2018-04-18
I am a total newbie and do not know Linux. I over wrote Windows 10 on the laptop but WiFi is not working. I read other threads and using lspci and is says the network Controller is a Broadcom BCM43142.
I do not have an ethernet port. So if I need to load up some drivers can someone spell out where I get them from and how I load them onto laptop?

---

### Post by howefield on 2018-04-18
Thread moved to the "Networking & Wireless" forum.

---

### Post by kerry_s on 2018-04-18
netbook, check out elementary os.
wifi should work on that. always run them live to make sure things work before you install.

---

### Post by steveca96 on 2018-04-18
I guess you mean retain Windows and run of USB, yep shoudl have done that but too late now.
What do you mean "check out elementary os"?

---

### Post by jeremy31 on 2018-04-18
Try booting into Ubuntu, then put in the media you installed from, go into the /pool directory and the files you need to install the driver are there, like described in [https://askubuntu.com/questions/626642/how-to-install-broadcom-wireless-drivers-offline](https://askubuntu.com/questions/626642/how-to-install-broadcom-wireless-drivers-offline)

---

### Post by kerry_s on 2018-04-18
> What do you mean "check out elementary os"?

it's barebones to run faster on low ram machines.  your netbook will be a lot faster with out all that overhead.
[https://elementary.io/](https://elementary.io/)

---

### Post by steveca96 on 2018-04-18
Brillaint, that worked thanks. I had to disable secure boot as instructions said and I guess that is why they were not installed initially

---

