---
title: "RT61 ndiswrapper driver"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by tangibleorange on 2008-01-24
hello,

I recently switched my home network to WPA-PSK encryption after being told of the weaknesses of WEP. I have a wireless card with an RT2561/RT61 chipset and use serialmonkey's rt61pci driver to connect. However, I am experiencing frequent disconnections using it, and wish to use ndiswrapper. Unfortunately,  I can't find an appropriate .inf file for use with it. I was just wondering if anyone could point me in the direction of one?

Thanks in advance!

---

### Post by rustybronco on 2008-01-24
> **tangibleorange said:**
> hello,

I recently switched my home network to WPA-PSK encryption after being told of the weaknesses of WEP. I have a wireless card with an RT2561/RT61 chipset and use serialmonkey's rt61pci driver to connect. However, I am experiencing frequent disconnections using it, and wish to use ndiswrapper. Unfortunately,  I can't find an appropriate .inf file for use with it. I was just wondering if anyone could point me in the direction of one?

Thanks in advance!
May I ask that you try wicd first? the reason why I ask is because of this post. [http://ubuntuforums.org/showpost.php?p=4122646&postcount=9](http://ubuntuforums.org/showpost.php?p=4122646&postcount=9)

but in answer to your question, this [http://ralink.rapla.net/](http://ralink.rapla.net/)  
this [http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html)
and this [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) should help.

wieman01's post... [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by tangibleorange on 2008-01-24
yeah i'm actually using WICD at the moment! i like the program (great for wired connections and wireless when it decides to work) but the disconnection (from the rt2x00 driver issue) is just so annoying.

The link on the first site (rapla) is broken for my Foxconn card - I then searched on the foxconn website with no luck

The second one all i get is an exe file which I then can't extract to get the .inf file

And the third one I try and compile it and get thousands of errors!

Thanks anyway! Should I just go with another card's driver and see what happens?

---

### Post by rustybronco on 2008-01-24
> **tangibleorange said:**
> y
The second one all i get is an exe file which I then can't extract to get the .inf file

Thanks anyway! Should I just go with another card's driver and see what happens?Sure  as long as it's for the same chipset and for the buss used. 
how's this... [http://www.brazilfw.com.br/forum/viewtopic.php?f=11&t=56094&start=0&st=0&sk=t&sd=a](http://www.brazilfw.com.br/forum/viewtopic.php?f=11&t=56094&start=0&st=0&sk=t&sd=a)
open with archive manager. (/etc/ndiswrapper/rt61/ at the bottom)

---

### Post by tangibleorange on 2008-01-25
OK I'll make a note of that website. However, the rt2x00 legacy drivers that did not previosuly work seem to now be working, so I think I'l just stick with that!

I'm sure it will break again though, so I'll be ready!

---

### Post by rustybronco on 2008-01-25
> **tangibleorange said:**
> I'm sure it will break again though, so I'll be ready!Spoil sport  :)

---

