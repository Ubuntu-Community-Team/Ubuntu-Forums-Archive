---
title: "WiFi for Desktop PC...How?"
date: 2015-05-26
forum: Networking &amp; Wireless
---

### Post by djscrig on 2015-05-26
I have a desktop PC and want to run Ubuntu 14.04 with a Netgear WiFi adapter, as I cannot hardwire. It seems Ubuntu does not recognize the adapter because it acts like there is not one plugged in. I have never had this problem when installing Ubuntu on a laptop. Is there a special WiFi adapter I can buy that Ubuntu will automatically recognize or do I have too be hardwired to the internet. 
Thanks.

---

### Post by chili555 on 2015-05-26
Before we go to the store, let's see what we can find out about the Netgear. I assume it is a USB device. Please insert it and open a terminal and run and post:```
lsusb
```If it is PCI, then:```
lspci -nn | grep 0280
```Thanks.

---

### Post by djscrig on 2015-05-26
Thanks, I will try it tonight from live CD when I get home from work. If it works, I will be setting up to dual boot :)

---

### Post by chili555 on 2015-05-26
Please don't misunderstand; the command is not supposed to magically start your wireless. It is to gather information to tell us how to *probably *start your wireless with a few steps. 

There are devices that can be made to work easily, some not so easily and some not at all. Let's see what you have first. I'll make a recommendation or two and then you can decide to install.

---

### Post by djscrig on 2015-05-26
I am on my phone now with ubuntu live on Pc. Enter the two commands. Lsusb: Netgear, Inc. WNDA31002v2 802.11abgn [Broadcom BCM4323]

The command lspci -nn | grep 0280 dis nothing.

---

### Post by chili555 on 2015-05-26
> Netgear, Inc. WNDA31002v2 802.11abgn There are many threads here about this tricky device; some with 150+ replies and not all successful. Here is a sample: [http://ubuntuforums.org/showthread.php?t=1695036&highlight=wnda3100](http://ubuntuforums.org/showthread.php?t=1695036&highlight=wnda3100)  Or:  [http://ubuntuforums.org/showthread.php?t=1965989&highlight=wnda3100](http://ubuntuforums.org/showthread.php?t=1965989&highlight=wnda3100) Some posts refer to v.1 and some to v.2; be sure you follow the correct usb.id.

If you are determined to try, the instructions are all there and I'll be glad to help. On the other hand, there are also threads about working by default USB wireless devices and you could buy one and be done.

---

### Post by djscrig on 2015-05-26
Thanks for your help, chili! Think I might just rather go the route of buying a default device. Can you recommend one that is cheap and will work? Thanks.

---

### Post by PhilGil on 2015-05-26
> **djscrig said:**
> Thanks for your help, chili! Think I might just rather go the route of buying a default device. Can you recommend one that is cheap and will work? Thanks.
This is what I am using, it's been flawless in both Debian and Ubuntu and doesn't cost much. Chipset is Atheros Communications, Inc. AR9271.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045)

---

### Post by chili555 on 2015-05-26
> **PhilGil said:**
> This is what I am using, it's been flawless in both Debian and Ubuntu and doesn't cost much. Chipset is Atheros Communications, Inc. AR9271.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045)As it happens, I have one of these, too. It works fine out of the gate.

You might also look here: [http://ubuntuforums.org/showthread.php?t=2233349](http://ubuntuforums.org/showthread.php?t=2233349)  Or here: [http://ubuntuforums.org/showthread.php?t=2166676](http://ubuntuforums.org/showthread.php?t=2166676)

There are several such threads here.

---

### Post by djscrig on 2015-05-26
I just ordered an [Asus USB-N13 802.11n/g/b]("http://in.asus.com/product.aspx?P_ID=UI3ejenXyxqQTIcJ&templete=2") based on the readings..Thanks both of you.

---

### Post by djscrig on 2015-06-27
Thanks to PhilGil and CHili555 for suggesting the Atheros Communications, Inc. AR9271. The Asus adapter was no good so I went and ordered your suggested chipset. Cheap and works perfectly. Thanks!

---

