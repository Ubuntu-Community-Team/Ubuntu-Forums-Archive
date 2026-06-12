---
title: "new to ubuntu and get my wireless card to work"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by pjustice72 on 2008-09-24
Hello I have a Broadcom Corporation BCM#)^  802.11 b/g wireless lan controller   (rev 02) And for some reason I can not get it to detect wireless signals. I am new to linux/ubuntu and I could use any help thats out there.

Thanks

---

### Post by pedro_orange on 2008-09-24
Hmmm. Broadcom are notoriously a pain in the a$$ on linux. 
I would suggest you do a:

```
lshw -C network
```

Find the name of your hardware device, and google it with ubuntu to see if people have got it to work with ubuntu.

This may help: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

Otherwise, I'd suggest you use the ndiswrapper and a Windows driver.

Find more info on it here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

