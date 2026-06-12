---
title: "install windows drivers in linux"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by computerguts on 2010-07-14
Is it possible to install windows driver in linux? If so how would I do that?
Thanks

---

### Post by Miljet on 2010-07-14
What kind of drivers?

---

### Post by Zeike on 2010-07-14
Its possible to do this for some network drivers using ndiswrapper.

---

### Post by Mark Phelps on 2010-07-15
> **computerguts said:**
> Is it possible to install windows driver in linux? 
In general, no.  The exception, as mentioned above, is using NDISwrapper to install networking drivers.  But you can't use Wine or any similar product to install other Windows drivers.

> If so how would I do that?
Go to the Networking forum and do a search on NDISwrapper.  You should then find some posts dealing with installing it.

---

### Post by computerguts on 2010-07-15
The Particular device that I need to install the driver for is a wireless adapter, to be more specific it is a 
** 					TP-LINK TL-WN422G IEEE 802.11b/g USB 2.0 High Gain Wireless Adapter Up to 54Mbps Wireless Data Rates 64/128/256 bit WEP  WPA/WPA2, WPA-PSK/WPA2-PSK (TKIP/AES) 					**

Thanks 

					 					****

---

### Post by vagrale13 on 2010-07-15
> **computerguts said:**
> The Particular device that I need to install the driver for is a wireless adapter, to be more specific it is a 
**                     TP-LINK TL-WN422G IEEE 802.11b/g USB 2.0 High Gain Wireless Adapter Up to 54Mbps Wireless Data Rates 64/128/256 bit WEP  WPA/WPA2, WPA-PSK/WPA2-PSK (TKIP/AES)                     **

Thanks 

                                         
I think your Wireless adapter, can be works fine on Ubuntu, and you don' t need the drivers of windows! :popcorn:
Give us the output of 
```
lsusb
```and see here [http://ubuntuforums.org/showthread.php?t=1473867](http://ubuntuforums.org/showthread.php?t=1473867)
read all answers, before try something!

---

### Post by mike555 on 2010-07-15
you might want to read this ;
[http://www.newegg.com/Product/ProductReview.aspx?Item=33-704-046&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=ubuntu](http://www.newegg.com/Product/ProductReview.aspx?Item=33-704-046&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=ubuntu)

---

### Post by HereInOz on 2010-07-15
Most TP-Link cards use Atheros chipsets, and these work fine with Ubuntu.  Plug it in and it should work.

---

### Post by HereInOz on 2010-07-15
Sorry, just read the link in the previous post.  Clearly it doesn't work out of the box - my humble aplogies.

---

### Post by computerguts on 2010-07-16
Here is the ouput from the terminal for lsusb 

```
porter@porter-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0cf3:1006 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
porter@porter-desktop:~$ 
```

---

### Post by Mark Phelps on 2010-07-17
Did you read through the thread that post #6 links to? 

It has detailed steps on how someone else solved the same problem.

---

### Post by vagrale13 on 2010-07-17
**@computerguts**

Your usb wireless is this one 
```
Bus 001 Device 004: ID 0cf3:1006 Atheros Communications, Inc.
```You can just see here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578267](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578267)
and try with the *.deb* package, read all posts before you try it, 
and i think after that, must be works great your usb wireless! :popcorn:

---

### Post by computerguts on 2010-07-19
Thanks, it works!

---

