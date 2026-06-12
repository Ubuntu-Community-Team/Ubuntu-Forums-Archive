---
title: "Need a upload/download monitor"
date: 2019-05-27
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2019-05-27
Hi,

I am using a 4G hotspot. I connect to the hotspot using WiFi.

The daily limit is 1.5GB.

After that the speed drops to 64kbps.

I need to keep an eye on how much I upload/download.

What is the best way to do this ?

---

### Post by SeijiSensei on 2019-05-27
Try Tobi Oetiker's MRTG.

[https://oss.oetiker.ch/mrtg/](https://oss.oetiker.ch/mrtg/)

It's in the Ubuntu repositories, and there are lots of article about it on the Internet.

---

### Post by Ogden on 2019-05-27
[https://www.softperfect.com/products/networx/](https://www.softperfect.com/products/networx/)

It says 30 day free trial but I've been using it for 2.5 years and it never expired.  It may reduce some of the functionality after 30 days, but it does not affect daily limit warnings.

---

### Post by linuxyogi on 2019-05-28
> **SeijiSensei said:**
> Try Tobi Oetiker's MRTG.

[https://oss.oetiker.ch/mrtg/](https://oss.oetiker.ch/mrtg/)

It's in the Ubuntu repositories, and there are lots of article about it on the Internet.

I have installed mrtg. 

Found [this]("https://www.cyberciti.biz/nixcraft/linux/docs/uniqlinuxfeatures/mrtg/mrtgconifg.php") article but its too complicated. Is there an easy alternative ?

---

### Post by SeijiSensei on 2019-05-28
Basically, you want run cfgmaker to create a configuration file, then edit /etc/crontab to run mrtg every five minutes or so.

Browse down this page until you see the reference to "cfgmaker".

[https://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html](https://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html)

I don't recall whether the machine needs to be running snmpd; it's been a while since I used MRTG.  But it certainly wouldn't hurt to install it.

```
sudo apt install snmpd
```

---

