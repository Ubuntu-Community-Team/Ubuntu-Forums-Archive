---
title: "wireless adapter issue, keep connecting the wifi"
date: 2014-08-03
forum: Networking &amp; Wireless
---

### Post by ispurs on 2014-08-03
I have a TL-WN822N wireless adapter for my pc running lubuntu 12.04. It can scan, but it keeps asking me for the password. So I searched in google and found this. 

[http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html](http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html) 

But when I was doing step 2, the terminal came with some sort of make cleaning ,"bash: command not found" and "compile make drive error 127". 
So I wanna get some help from all you guys. BTW, the wireless adapter works great in the windows 7.

---

### Post by varunendra on 2014-08-04
Welcome to the forums ispurs !

Which version of the card do you have?

It seems there are three revisions of it (see [here]("https://wikidevi.com/wiki/TP-LINK_TL-WN822N_v2")), only the third containing a realtek card for which the tutorial you linked to *may* work (won't on the latest kernels, unless Realted releases an updated driver).

To let us see which variant of the card and which kernel version you have, plus a lot of other useful info, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

