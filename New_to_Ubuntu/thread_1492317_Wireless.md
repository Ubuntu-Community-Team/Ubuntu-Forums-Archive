---
title: "Wireless?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by bernadotte on 2010-05-24
Hello. I've used Ubuntu for about two weeks now. It worked fine until I installed some windows wireless drivers using ndiswrapper. There seems to be no way to connect to wireless networks. I've tried several tutorials, but none of them work. My computer is a Dell d620.

---

### Post by SlidingHorn on 2010-05-24
More information needed.  Please see: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by bernadotte on 2010-05-24
I've attached a .doc file containing the outputs of the different commands.

---

### Post by v1ad on 2010-05-24
i needed to do this the first time.
also if wireless worked why did you bother installing drivers also through ndiswrapper?

and make sure the inf file that you used was for windows xp. for me vista & 7 did not work that well.
```
ifconfig wlan0 up
```

---

### Post by bernadotte on 2010-05-24
```
wlan0: ERROR while getting interface flags: No such device
```

Any way to fix this?

---

### Post by bernadotte on 2010-05-24
> **v1ad said:**
> 
also if wireless worked why did you bother installing drivers also through ndiswrapper?

The driver didn't seem to work properly on my home network. Some pages finished loading quickly, but most pages didn't load at all. There weren't any problems on my Windows computer, so I installed a compitable Windows driver from the Dell support page. I chose XP as operating system and made sure it was the right one.

---

### Post by v1ad on 2010-05-24
that first comment means that the driver is not installed. verify that you got the right .inf file going to ndiswrapper. also did you select the exe or did you extract the exe and select the .inf file?

---

### Post by bernadotte on 2010-05-24
> **v1ad said:**
> that first comment means that the driver is not installed. verify that you got the right .inf file going to ndiswrapper. also did you select the exe or did you extract the exe and select the .inf file?
 I extracted the .exe and selected the .inf file. I'll try over again and see if it works.

---

### Post by anaconda on 2010-05-24
One solution is to buy a cheap usb wlan dongle, which is supported in ubuntu straight out of the box. they cost about $10

Yeah I have used ndiswrapper, and if it works easily with it then good, if not then I would buy a new dongle...

---

### Post by v1ad on 2010-05-24
give me 1 sec and ill post the .inf file here.

---

### Post by v1ad on 2010-05-24
[http://www.2shared.com/fadmin/13640741/5d1693fd/DRIVER.zip.html](http://www.2shared.com/fadmin/13640741/5d1693fd/DRIVER.zip.html)

download extract reselect.

i named the file u need to select. "select this 1"


remember: if there is a will, there is a way.

---

### Post by mikewhatever on 2010-05-24
If ndiswrapper doesn't work for you, try this method.
[http://ubuntuforums.org/showthread.php?t=1491147](http://ubuntuforums.org/showthread.php?t=1491147)

---

