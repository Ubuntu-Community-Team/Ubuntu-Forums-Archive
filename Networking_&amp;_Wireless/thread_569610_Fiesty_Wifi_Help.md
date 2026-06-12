---
title: "Fiesty Wifi Help"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by tophatandy on 2007-10-07
Well.. I finally got my bro to come back over to linux (he needed windows for some school applications for a while). While he had windows he decided to move his pc and put a cheap wifi card in it (you can probably see where this is going). He purchased an allied data tornado 122 pci card. We put it in and it worked in windows for months. We have a WPA encrypted network, and as you probably know WPA isnt too kind in linux. The suprising thing is that the company that makes the card actually has a wifi module and utility for it. The only problem is that the driver and the instructions dont seem to work with Ubuntu (idk if it is because it is debian, but the company says it has been tested on with slackware, fedora, and red hat [i think]). The driver says it is compatible with the kernel, but I cant get it to work. Would love some help. here is the link to the page that gets you closest to my cards page:
[http://www.allieddata.com/asp/support.asp?menu=support](http://www.allieddata.com/asp/support.asp?menu=support)
I am the Tornado 122

any help would be greatly appreciated

Thanks
-Andy

---

### Post by tophatandy on 2007-10-07
Bump

---

### Post by scrooge_74 on 2007-10-07
Did you compile the drivers?

---

### Post by tophatandy on 2007-10-07
honestly.. I have no idea what to do when it comes to drivers in linux. so.. no.

---

### Post by HokeyFry on 2007-10-07
To install the wireless card, try using Ndiswrapper if you can't get the card itself to work. See the How To in my sig.

For a WPA How To, look at [this]("http://ubuntuforums.org/showthread.php?t=318539") thread

---

### Post by kevdog on 2007-10-07
How about giving some info on your card:

lspci -nn
lshw -C network

---

### Post by tophatandy on 2007-10-07
I am going to try a reinstall.. and see what i can do from there.. I will come back on in like a half an hour.. I am pretty sure I messed up the wireless driver (yay..idiot points for me!) sorry to keep you guys waiting.

---

