---
title: "PSP WiFi Max Help"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by Vert on 2006-11-05
"I'm trying to setup a PSP Wifi Max USB 802.11G made by Datel, which uses the ZyDAS 1211. So I tried to install the 1211's drivers from source and install the mod, but to no luck, even with the module showing up as being loaded, it won't show up in ifconfig, and dmesg keeps tossing weird errors.

Has anyone successfully setup the WifiMAX? And if so how?

Thanks in advance." -- [email]kariudo@gmail.com[/email]

That was an old thread back in June and it was never answered.  I just wanted to know if it is possible.  [http://us.codejunkies.com/shop/product.asp?c=US&cr=USD&cs=$&r=0&l=1&ProdID=711](http://us.codejunkies.com/shop/product.asp?c=US&cr=USD&cs=$&r=0&l=1&ProdID=711)
That is the site for the WiFi Max.  It would be a shame if it didn't work because it cost 50 USD.  Pretty expensive for someone who doesn't have a job ^^  Well... like kariudo said, "Thanks for your help in advance."

---

### Post by FrodoB on 2006-11-05
Are you running Edgy? If so then you need to blacklist the kernel zd1211rw module. It supposedly does not work well until kernel 2.6.18.1 and higher.

Then the modules from:

[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

Should work. Note that there are two zd1211 chipsets out there and the make both option will install them both.

---

### Post by Vert on 2006-11-06
Hey! Thank you very much, but would you be kind enough to help me out on the black listing part.  I'm fairly new to Linux and don't understand all the kernel-related stuff just yet.  Thanks a lot ^^

---

