---
title: "Wireless Signal Strength Low"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by gtno on 2008-10-09
Hello, I have a Realtek Wireless card in my Toshiba Satellite A215-S4737 and a D-Link DIR-615 router.

I am currently using rtl8187b-modified wireless drivers and they load up just fine on start up etc. However, my signal strength shows a constant 30% and I am not sure how to go about making the signal stronger.  I have sat my laptop right next to the router and nothing changes.

I have looked around to try and find similar problems, but I haven't had any luck. I typed in the following:

```

gtno@gtno:~$ iwconfig wlan0
wlan0     802.11b/g linked  ESSID:"Spheresystems"  
          Mode:Managed  Channel=11  Access Point: 00:1C:F0:57:D4:D7   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I currently have it setup up on a WEP connection, because WPA was giving me some trouble.  The ESSID is visible to anyone. Any suggestions or help is very much so appreciated! Thanks in advanced.

---

### Post by AlexBellisBrown on 2008-10-09
I have the same wireless card as you, my wifi signal strengh is always wrong, and the wireless card doesnt work perfectly with Linux... I use a usb wifi card now. Though i belive you can get ure internal card working perfectly with Ndiswrapper. Theres a thread dedicated EXACTLY to this somewhere in the forums. Ill have a look for it now.

---

### Post by AlexBellisBrown on 2008-10-09
[http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187)

Have a look here, you can try reinstalling the drivers if you wish. Just give it a good read! :)

---

### Post by gtno on 2008-10-09
> **AlexBellisBrown said:**
> [http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187)

Have a look here, you can try reinstalling the drivers if you wish. Just give it a good read! :)

Wow, thank you very much. I will give it a good read :)

---

### Post by AlexBellisBrown on 2008-10-09
No problem, anything else you know where to find us! :)

---

