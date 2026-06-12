---
title: "How to execute wlan0up on networking start"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by skanxalot on 2007-10-22
After many days of struggling with the R8187B drivers for my integrated usb wifi card, I've finally got it working.  Thanks to the folks at Realtek for emailing the proper drivers and scripts. Now my next question. My wifi card is not loaded on bootup, and I can only get it to work after executing the wlan0up script given to me by realtek.  I have this script in my home directory, in a folder called r8187B_drivers.  How can I execute this automatically?

I have tried adding pre-up /home/tyson/r8187B_drivers/wlan0up to my interfaces file, but it doesn't seem to work.  I think because the device isn't even recognized initially.  I'm not sure though.  Anyways, if I run this wlan0up script from the terminal, the device is loaded and starts working great.  I just don't want to have to do it manually every time.

Thanks for any help...
Tyson

---

### Post by Fran89 on 2007-12-04
Same here please help...

---

### Post by csat on 2007-12-04
Hello Friends

Look at 

[http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/](http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/)

Cheers

---

### Post by bemused0 on 2007-12-26
Alternatively, I've also seen it mentioned that you can add a line to 

/etc/network/interfaces

```
pre-up wlan0up
```


This would work if wlan0up is in your path, otherwise provide the full path ie:
```
pre-up /usr/local/bin/wlan0up
```


Not my solution, found elsewhere, may be incorrect but I'm using it without trouble.

---

