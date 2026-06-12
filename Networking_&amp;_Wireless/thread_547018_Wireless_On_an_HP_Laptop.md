---
title: "Wireless On an HP Laptop?"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by GatorGreen on 2007-09-09
Hello, 

I've really been enjoying Ubuntu the past few days I've had it. I have everything configured the way I need it except for wireless. I've been searching the forums and help guides, but I am unfamiliar with many of the terms used. I realize ndiswrapper could be a possible solution, however I don't know how to operate it correctly. The only information I know about the card is that it is an internal Broadcom card. 

Also, I am unsure if it's a driver problem or just a problem with connecting to the access point. I use a WEP key for security. I always enter it while connecting and the network icon just shows the spinning blue dot. 

Thanks in advance.

---

### Post by noob12 on 2007-09-09
The first step is to identify your wireless device precisely.   Get the output of these in a terminal window and post the results:
```

lspci -nn

sudo lshw -C network

```
Based on that people can provide guidance.  If these show that you do have a Broadcom 43xx series wireless ethernet card, I would recommend this thread
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

