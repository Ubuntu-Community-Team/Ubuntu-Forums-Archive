---
title: "Just installed ubuntu yesterday, but wireless simply will not work"
date: 2017-01-19
forum: Networking &amp; Wireless
---

### Post by slippyhands on 2017-01-19
good day everyone, I installed ubuntu on my laptop yesterday.  This is my first linux experience and I must say it's been rough so far.  My laptop is an HP Pavilion X360.  Apparently that's a bad thing.  I can't get the internal wireless card to work, despite spending about three hours on it yesterday, so I went to Fry's and grabbed a Panda PAU05 USB wireless dongle.  Multiple reviews and the salesperson all assured me that it works fine out of the box.  It doesn't.  I've run through countless help guides all over the place.  I downloaded the driver but I don't know how to use it.  I've looked at guides to try to figure it out, but I'm not getting the same information that the guides seem to expect.  Any help would be very much appreciated.  Thank you.

---

### Post by wildmanne39 on 2017-01-19
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags. 

Have the usb adapter plugged in when you run the script so we can see both devices.

---

### Post by slippyhands on 2017-01-19
Hi there.  I ran the wireless script as instructed, but the forum is not letting me post the response.  Apparently there is some sort of security token error

---

### Post by wildmanne39 on 2017-01-19
Paste the file at the following link then post the link to the file here.
[http://pastebin.com/](http://pastebin.com/)
Thanks

---

### Post by slippyhands on 2017-01-19
This is the output from the script you instructed me to run

[http://pastebin.com/dFQJs3TR](http://pastebin.com/dFQJs3TR)

---

### Post by wildmanne39 on 2017-01-19
Please paste this command into the terminal:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
shutdown your computer unplug usb adapter and boot up, does wifi try to connect? if not please run the wireless script again so we can see what effect the changes had on your wifi, leave the usb adapter unplugged for now.
Thanks

---

### Post by slippyhands on 2017-01-19
I did that and restarted.  Wifi is apparently functioning perfectly normally.  I am still familiarizing myself with terminal commands (brand new user here), so I am interested to know how blacklisting acer-wmi helped my problem, and what the nature of the issue was, if that's not too much trouble.  Thank you very much for the help.

---

### Post by wildmanne39 on 2017-01-19
That module tells the kernel to turn the wifi on and for some reason in many case that particular module does not work correctly.
Please use thread tools at the top of the page to mark the thread solved.
Thanks and Enjoy!

---

