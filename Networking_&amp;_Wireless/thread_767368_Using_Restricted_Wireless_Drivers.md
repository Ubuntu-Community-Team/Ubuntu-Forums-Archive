---
title: "Using Restricted Wireless Drivers"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by azurepancake on 2008-04-25
I just installed Hardy Heron on my P205-S6307 Toshiba laptop. The laptop comes equipped with a Atheros 802.11 g/b wireless card and when I installed Hardy, it says there are two restricted drivers that are related to the wireless card. Gutsy did not have any known restricted drivers.

The two drivers are:
Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 wireless LAN cards

They are both enabled and in use.

But I cannot see any wireless networks and it doesn't have any options for wireless networks when I click on the icon. 

I'm not sure where to go from here. Does anyone have any advice? I'd be ever grateful.

Thanks!

---

### Post by JesCed on 2008-04-27
Hello. I am also having this same problem on an Acer Aspire 3690-2767. However, I DID have one restricted driver in Gutsy. In Gutsy I had the HAL driver enabled, but I was never able to get wireless LAN to work. I hope someone will be able to help us this time.

---

### Post by kevdog on 2008-04-27
You need to post the specific chipset number of the Atheros card -- b/c all atheros chipset are not compatible with the madwifi drivers -- and others need a patch to be applied.

lspci -nn

---

### Post by JesCed on 2008-05-03
Thank you very much for your response, but the problem has since been solved. I found another thread (not sure how to link to it) with information relative to my specific atheros card, and it said that the way to get this working was to use the Windows XP drivers via ndiswrapper and the Windows Wireless Drivers GUI. I have since tried that, and it worked perfectly! In fact, I am writing this response using my WiFi connection.

Thanks again.

Here is (hopefully) the link to the thread where I found my solution
[http://ubuntuforums.org/showthread.php?t=739998]("http://ubuntuforums.org/showthread.php?t=739998")

---

