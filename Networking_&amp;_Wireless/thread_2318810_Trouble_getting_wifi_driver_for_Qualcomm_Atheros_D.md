---
title: "Trouble getting wifi driver for Qualcomm Atheros Device"
date: 2016-03-29
forum: Networking &amp; Wireless
---

### Post by Atinesh on 2016-03-29
I have a `Lenovo z51-70` laptop. I've dual booted it with windows and ubuntu. In windows, wifi is working fine. But in ubuntu, I'm having trouble installing wifi driver. I tried updating the system using the command

```
sudo apt-get update
```

But still wifi doesn't work. I searched everywhere on the internet, But can not be able to find the driver. Please anybody help...


I'm having wifi adapter of `Qualcomm Atheros`

> Qualcomm Atheros Device 0041 (rev 20)


On running the following command

```
lspci -vvnn | grep -A 9 Network
```


I'm getting the output as

[https://s11.postimg.org/ij0bakg3n/Screenshot.png](https://s11.postimg.org/ij0bakg3n/Screenshot.png)

---

### Post by jeremy31 on 2016-03-29
Search google for linux 168c:0041 and you should find the answer, a lot of the results should be from me

---

### Post by wildmanne39 on 2016-03-29
Please use url's or thumbnails when  posting images.
Thanks

---

### Post by Atinesh on 2016-03-30
This link solved my problem

[http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in)

---

