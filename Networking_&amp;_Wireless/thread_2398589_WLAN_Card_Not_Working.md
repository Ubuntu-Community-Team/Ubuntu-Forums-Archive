---
title: "WLAN Card Not Working"
date: 2018-08-14
forum: Networking &amp; Wireless
---

### Post by martinssm on 2018-08-14
Hello,

Im using Lubuntu, so I dont know if i can even post here, but here it goes...

Just installed Lubuntu and Im just trying to get my WLAN card working. Cant find a link to the drivers.
I am a regular on Windows. **Please help me... **:P

Thanks.

---

### Post by QIII on 2018-08-14
Moved to Networking & Wireless

---

### Post by wildmanne39 on 2018-08-14
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by martinssm on 2018-08-14
[http://paste.ubuntu.com/p/DyyQNQMjBd/](http://paste.ubuntu.com/p/DyyQNQMjBd/)

---

### Post by wildmanne39 on 2018-08-14
Is there a reason you are not using your internal wireless card?

---

### Post by martinssm on 2018-08-14
Well, It just doesnt work. When I unplug my USB Wi-Fi adapter I can use only ethernet

---

### Post by chili555 on 2018-08-14
> **martinssm said:**
> Well, It just doesnt work. When I unplug my USB Wi-Fi adapter I can use only ethernetThe Wild Man hopes that you will hook up that ethernet and issue a terminal command:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```After it runs, he hopes you will detach the USB wireless, reboot and mark the question Solved.

---

### Post by wildmanne39 on 2018-08-14
Apologies for the delay I had a phone call I had to take, thanks for stepping in chili555, yes that is what I was thinking.

---

### Post by martinssm on 2018-08-14
Thanks everybody!

---

### Post by wildmanne39 on 2018-08-15
I will say your welcome from chili555 and myself.

Glad it worked!

---

