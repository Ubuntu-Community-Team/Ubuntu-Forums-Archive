---
title: "No Wi-Fi adapter found error"
date: 2018-08-19
forum: Networking &amp; Wireless
---

### Post by punkosti-csaba on 2018-08-19
Hello everyone. I've just had a fresh 18.04 ubuntu install on my Lenovo Y520. It's installed on an external hdd so I can use it on other PC as well. The main problem is that my Wi-Fi is not working. Looked around the web for the past 3 hours but I found nothing that could help. The bluetooth works and I can use the internet shared from my phone through usb cable. In my BIOS there is no option to disable/enable Secure Boot, there is an Intel Trusted Device (or something like that) option, but tried turning it on and off but no change. This is what wireless info got: [http://paste.ubuntu.com/p/ghvkBShMXv/](http://paste.ubuntu.com/p/ghvkBShMXv/)

---

### Post by jeremy31 on 2018-08-19
In terminal do ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf && sudo apt-get purge bcmwl-kernel-source
```
Reboot

---

### Post by punkosti-csaba on 2018-08-20
Thank you so much, I don't even know what it did exactly but it works like a charm!

---

