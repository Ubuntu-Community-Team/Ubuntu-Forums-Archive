---
title: "3G modem slower on linux than Windows"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by LeeDavies on 2008-05-21
Hi Everyone,

I have a Telit based 3G usb modem. After using the following command -

   modprobe usbserial vendor=0x1bc7 product=0x1003

Ubuntu produces /dev/ttyUSB0, /dev/ttyUSB1 and /dev/ttyUSB2. I can then use /dev/ttyUSB0 to establish a 3G connection to the internet with downloads rates of 30KBytes/sec

However using the same hardware (including external aerial), windows has a download rate of 110KBytes/sec - More than three times the speed !!!

Is there anything I can do it increase the thoughput rate under Linux?

Regards,

Lee

---

### Post by christianxxx on 2008-05-21
Sound like it's not 3G at all. Is there any indicators on the modem?
I don't have much experience with 3G, but surely it must be a fix.

---

### Post by LeeDavies on 2008-05-21
I don't have the best 3G reception, but it's definitely a step up from the GPRS download rates of 5KBytes/sec (6 times slower).

With the same conditions, Windows can still achieve download rates of 110KBytes/sec.

Looking into the Kernel source, I've noticed one or two Edge/3G modems have there own drivers (airprime.c, sierra.c, etc), rather than the standard usbserial driver.

I wounder it's a limitation of the standard usbserial driver?

---

### Post by marks_linux on 2008-05-21
I use umtsmon and notice no difference between windows and Linux, other than the device connects quicker in Linux

---

### Post by LeeDavies on 2008-05-21
Thanks for that, I tried umtsmon and the data rate doubled. It was because I had an older /etc/ppp/options files with most of the compression switched of and the asyncmap set to 0xFFFFFFFF.

So Ubuntu now has a download rate of nearly 60kBytes/sec, but it's still short of the 100KBytes/sec achieved by windows?

---

### Post by christianxxx on 2008-05-21
> **LeeDavies said:**
> I don't have the best 3G reception, but it's definitely a step up from the GPRS download rates of 5KBytes/sec (6 times slower).


There shouldn't be any difference in reception, no matter what OS. 
I suspect it's the module. Have you tried the umtsmon referred to in the above post?

I usually don't rely much on the speeds reported by windows. It seems to me they are reported higher than actual speed, possible due to some kind of compression. 

Just saw your new post, never mind...

---

### Post by LeeDavies on 2008-05-21
According to the following article -

[http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html)

With the standard usb-serial drivers Ubuntu will not achieve transfer rates higher than 60 KB/sec. This happens to be my maximum transfer rate.

There are drivers written for specific devices to tackle this problem, unfortunately my Telit 3G modules isn't one of them.

I'm now compiling a modified airprime.c with the Telit module included, hopefully it may address the bottleneck

Regards

Lee

---

