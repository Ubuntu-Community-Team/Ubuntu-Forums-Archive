---
title: "Broadcom wireless light on but..."
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by Gargamella on 2006-10-08
hi guys,
i was a mandriva user and i migrate to ubuntu and i like this linux...
but in mandriva i was able to set up with ndiswrapper my broadcom wireless chipset on lenovo 3000 c100 in a minute,here is quite impossible i think, isn't it?

the wireless light came on when i made

#ifeth1 up

...

but is still useless,i tried with ndiswrapper and fw-cutter but my drivers 
 (bcmwl5a.inf and bcmwl5.sys) do not work

i think surely ubuntu has to improve heavily in wireless support,

have you ideas 4 the problem ?

---

### Post by MasonM on 2006-10-08
I set up my Broadcom card using ndiswrapper and at first it simply wouldn't work. I noticed that during boot the Broadcom kernel driver was being loaded. I went into /etc/modprobe.d/blacklist and added that driver. Once I had blacklisted the Linux Broadcom driver the card worked fine with ndiswrapper.

---

### Post by crwnsop on 2006-10-08
I had the same problem(Acer Aspire 5003 w/BCM 4318 and Ubuntu 6.06). I made it work with the cutter, and pressing the wlan button once each time I start the cpu. It defaults to have the card off, but pressing 1x will turn it on. Then you can run something like "sudo iwlist eth1 scan" to see if you are in business. The light should flicker with activity, but not stay on as it does in Windows. BTW, does anyone know how to change the default setting to zero.

---

### Post by unco on 2006-10-09
check out [this howto]("http://ubuntuforums.org/showthread.php?t=259355"), it is how I got it to work, take about 10 minutes if you already have your card driver (I have broadcom based and use ndiswrapper).  You shouldn't need the WPA part if you don't use it ...

---

### Post by Gargamella on 2006-10-09
> **unco said:**
> check out [this howto]("http://ubuntuforums.org/showthread.php?t=259355"), it is how I got it to work, take about 10 minutes if you already have your card driver (I have broadcom based and use ndiswrapper).  You shouldn't need the WPA part if you don't use it ...


thank you very much i finally found smone to explain me how to pass from eth1 to wlan0 thanks ;D



andrea

---

