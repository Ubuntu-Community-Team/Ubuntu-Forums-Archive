---
title: "How to disable pemanently Wake on lan ubuntu 16.10"
date: 2017-05-03
forum: Networking &amp; Wireless
---

### Post by alejandrofig on 2017-05-03
Hello, I have been trying to disable wol the last few days, I installed ethtool and run the following commands:

sudo ethtool eno1 | grep Wake-on

sudo ethtool -s eno1 wol d

After that the wol was disable, I restarted the computer a few times and everything seemed fine, but after a few hour I realized that restarting the computer the wol was back on. I have also tried to do the following tutorial: [http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/](http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/)  with the same result.

Before anyone asks, I don't have the option to disable it from bios, I have and hp notebook and it seems that that option is not included in the Bios. Does anyone has any suggestion? Thanks.

---

### Post by Xian on 2017-05-03
If this command at least works upon being executed:

```
sudo ethtool -s eno1 wol d
```

I would suggest setting up a cron job to issue during boot.

Something like:

```
@reboot /sbin/ethtool -s eno1 wol d
```

If you need a refresher on cron jobs .... see link below.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by alejandrofig on 2017-05-03
Ok, thanks, i will give it a try and let you know. In the future if I want to enable it again it what should I do?

---

### Post by Xian on 2017-05-03
> **alejandrofig said:**
> Ok, thanks, i will give it a try and let you know. In the future if I want to enable it again it what should I do?

```
sudo ethtool -s eno1 wol g
```

---

### Post by alejandrofig on 2017-05-04
Thanks!! it worked!!

---

