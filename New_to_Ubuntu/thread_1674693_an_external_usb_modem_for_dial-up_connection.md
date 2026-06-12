---
title: "an external usb modem for dial-up connection"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by mustafa.alberta on 2011-01-24
hi friends,
struggling for adsl connection was unsuccessful.this made me to explore for an external USB modem so that i can surf the net through dial-up connection.
i will wonder if you could help me to find an external USB modem for dial-up connection. please tell the model and manufacturer brand so that i can find easier.by the way, i will wonder if you're sure that this modem will work fine with Ubuntu and Kubuntu.
kind regards,

---

### Post by cascade9 on 2011-01-24
The only USB 56K dialup modem I know of that has linux support and is still on sale is the US Robitics USR5637. I cant say I'm 100% sure it will work with unbuntu out of teh box, you might have to complie a module to get it going- 

[http://ubuntuforums.org/showthread.php?t=728384](http://ubuntuforums.org/showthread.php?t=728384)

---

### Post by madmax75 on 2011-01-24
I think you are meaning USB broadband modems, like the ones that the Chinese Huawei makes.

I've had a couple of these ones on my Ubuntu - Huawei E169 and Nokia CS-15. I've also tried one from Option. All have worked pretty well.

Make sure that you have *usb-modeswitch* and *usb-modeswitch-data* installed! 

It would also be advisable to back up these two deb packages, in case you update to a newer Ubuntu version and the USB modem support stops to work for some reason (like it happened with 9.10). This way you can reinstall this usb-modeswitch stuff without an internet connection.

Then just plug the modem into the USB port, go to Network Manager (should be there on the panel) and select your country, ISP and so on. For the last couple of years these broadband modems have been working pretty much out-of-the-box, as far as I can tell.

---

### Post by sadaruwan12 on 2011-01-24
I know the thing you want I know this chines brand called PROLiNK and they have a dial-up modem model number H5200U which works with Ubuntu.

I know this I've used this model on several Ubuntu computers just nothing to do plug it in configure it and browse the net no hassle what so ever.

But with Linux I advice you to use a modem/router where you can use your LAN port and theres no driver installation or anything long as your LAN works you have internet.

---

### Post by sammiev on 2011-01-24
[This]("http://ubuntuforums.org/showthread.php?t=1589966&page=3") worked for my dialup modem, post#22. GL :)

---

