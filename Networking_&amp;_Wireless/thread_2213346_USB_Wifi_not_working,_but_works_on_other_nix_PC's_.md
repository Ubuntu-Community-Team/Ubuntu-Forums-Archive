---
title: "USB Wifi not working, but works on other *nix PC's seamlessly"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by HLA91 on 2014-03-26
Hi All

I have a bit of a weird problem. My Think pad X201 internal WiFi is knackered, has been for a while so I use a USB WiFi dongle. 
This dongle works fine on my Desktop running Fedora 20 and on my friends laptop running Ubuntu 13.10, both plug and play no messing around. 
If I plug it into my thinkpad is says "disabled by hardware switch" but rfkill says it isn't hard blocked or soft blocked. The USB ports work fine with USB Pen Drives but with any Wifi Dongle, it doesn't work. Any ideas? I have also tried Fedora on the Think pad but still no joy so something must be up with the USB ports. Any clues?

Thanks

HLA91

---

### Post by varunendra on 2014-03-26
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there (when the USB adapter is connected), and post back the report it generates.

Apart from the above report, also post the full output of "lsmod" command.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by HLA91 on 2014-03-27
I managed to solve the problem.
It turns out because the inbuilt Wifi Switch is stuck int eh "Off" position that was disabling all Wifi regardless of whether it was inbuilt or not. I blacklisted the iwlwifi driver that the inbuilt card used and now my USB wifi works perfectly.

---

