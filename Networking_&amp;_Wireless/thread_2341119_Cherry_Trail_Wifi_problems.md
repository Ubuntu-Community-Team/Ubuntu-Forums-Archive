---
title: "Cherry Trail Wifi problems"
date: 2016-10-25
forum: Networking &amp; Wireless
---

### Post by mediawiz on 2016-10-25
I have an Intel Cherry Trail (Atom z8700) tablet on which I have been trying to get Ubuntu (x86 64) installed/working. With some help from Linuxium (thank you Ian Morison), I have gotten it "mostly" working. The one major issue I still have is that Wifi is not working. (Ubuntu says "no interface found" in the Wifi setup.)

All of the info that I have found about fixing this issue seems to involve being connected to the internet and downloading something via a Linux utility, but if I don't have Wifi, I can't connect to the internet. (It's kind of a "chicken and egg" sort of thing.)

Any suggestions?

---

### Post by Hadaka on 2016-10-25
Hi, here is a link that has the Ubuntu iso and patches to allow wifi
bluetooth and graphics on your device. Depending on your kernel.
[https://linuxiumcomau.blogspot.com.au/2016/10/running-ubuntu-on-intel-bay-trail-and.html](https://linuxiumcomau.blogspot.com.au/2016/10/running-ubuntu-on-intel-bay-trail-and.html)
This is an up to date article,Oct 2016 so hopefully it will help. 
Good Luck !

---

### Post by mediawiz on 2016-10-25
As mentioned in my original post, I had already found Linuxium's blog, and gotten help from Ian Morison.  The Wifi on my tablet it still not working. 

Thanks anyway.

---

### Post by Hadaka on 2016-10-25
ok, please boot to ubuntu, and post the output of..
```
lspci -n | awk '/0280/{print$3}'
```
this will determine the driver that is needed.
you can also overcome the chicken/egg situation with
a usb/ethernet converter cable and plug directly into your
your router.
thanks.

---

