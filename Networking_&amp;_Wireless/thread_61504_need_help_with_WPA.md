---
title: "need help with WPA"
date: 2005-09-01
forum: Networking &amp; Wireless
---

### Post by k94382 on 2005-09-01
i installed the drivers for my WMP54GS with ndiswrapper and it's up and running but i just cant figure out how to enter my WPA key anywhere. it's so frustrating, i could really use some help. im a complet noob, btw. thx in advance

---

### Post by npaladin2000 on 2005-09-01
Can you change your router/AP to WEP for now?   

You need a utility called wpa_supplicant in order to do any sort of WPA encryption.  It might take you a while to get it working, and I don't want you to get too frustrated and give up. ;)

Anyway, if you can switch to WEP first temoprarily (just to get it working initially) then download the wpa_supplicant package from Synaptic, and make sure to read both the readme file and example config.  You're mainly going to be worried about setting up a config file that identifies your SSID, and the pre-shared WPA key (or user/password if using RADIUS).  Make sure in the areas where you can put TKIP or CCMP, to put both (I think there's 2 entries but I can't recall them off the top of my head).  CCMP is the identifier for the AES algorithm; most access points support one, the other, or both. If you have both listed as options you'll have fewer problems connecting.

One other thing: sometimes wpa_supplicant and ndiswrapper don't always get along realy well, depending on the Windows driver.  So if you have problems, you can always go back to WEP, like I had you switch to before you started trying to get wpa_supplicant working, right? ;)

---

### Post by k94382 on 2005-09-01
ok, cool thx. i will try that

---

