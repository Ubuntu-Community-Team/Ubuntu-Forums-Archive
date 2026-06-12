---
title: "Tp Link usb device slower than Windows 10"
date: 2019-06-01
forum: Networking &amp; Wireless
---

### Post by samtoon on 2019-06-01
So I just installed Ubuntu 18.04 along with Windows 10. I'm pretty amazed with it's speed when booting, starting apps, etc. However, the only problem so far has been Wi fi.

You'll see, since I got this laptop 2 years ago, it had wi fi issues: it identified the surrounding networks and it was able to connect with them, but not to actually use internet. I tried everything, from trying everything I found in the internet, to ask for technical support. One guy even said that the problem was windows 8, and proceeded to install windows 10, nothing changed at all. I gave up and resigned to use my ethernet cable (so i couldn't use internet out of the modem room). One day my mom brought this wireless usb device, hoping that it'd solve my problem. It came with a disk. I just ran it in my laptop, and it worked. I finally got wi fi.

That was like one and a half year ago. Back to a few days, the device wasn't working on Ubuntu. Later i realized that it was due to Ubuntu not having installed the driver that the Tp Link CD had previously installed on Windows 10. When i tried to run it again, it couldn't run the executable file. Even after properly installing wine and the executable file "running", it couldn't install the driver due to it not recognizing it.

Long story short, I had to find the driver on the internet (using my ethernet cable) and install it, thus making the usb device work again. That moment truly was glorius, or at least that's what i thought...

Recently I found that Firefox was reaaaally taking it's time to load sites. I updated it, installed chromium, but it was the same. When plugged the ethernet cable, I found out that the problem weren't the browsers.

Again, I've been looking on the web an answer, and although I see similar situations, none of the solutions works for me. The driver is TL WN-725N (V2). The drivers on the internet don't really specify the version of the driver, so i don't know where to find it. Please, I need help.

PS: The CD actually has a folder called "Linux Driver", but it only contains a .txt file, which reads "For Linux users, please visit the TP-LINK support website, find and download the compatible version of driver for your network adapter at www.tp-link.com.". According to the support site, only the V3 supports Linux. V2 supports only Windows and Mac.

---

### Post by HermanAB on 2019-06-02
With Wifi, it is generally best to get a proper Linux compatible USB dongle.  Edimax widgets come packaged with a friendly Linux penguin on the wrapper and will save you many a head-ache since the Just Work (TM).

---

### Post by jeremy31 on 2019-06-02
Moved to Network & Wireless, please see the wireless script link in my signature and post results

---

### Post by samtoon on 2019-06-02
[ATTACH]283362[/ATTACH]

Like this?

---

### Post by kurt18947 on 2019-06-02
I'm not going to be able to help with your problem, I'm not really versed in wifi issues. I don't use wifi much, discovered MoCA so have mostly wired networking. I don't see a TP-Link device though i do see a Broadcom wifi device. Unfortunately it's a model that I think has been a challenge. As a rule linux drivers that come on a disk are old and probably useless. Linux does things differently than Windows when it comes to hardware support. As Herman says, it's best to spend a bit of time in the networking forum here to find devices that are plug 'n' play. They do exist but are not plentiful and are sometimes not the latest and greatest. While on the networking forum you could search for your Broadcom device and see if there has been any recent progress with it.

Edit: I was able to open the archive once but didn't save it and when I tried a second time I was unable to open it, has a lock icon. You could get the model of the Broadcom wifi (network) device listed and search. Be careful of non-Ubuntu sources, some give good advice and some don't.

Edit 2:

Here's a thread where someone had a Broadcom 43421 (I think that's the device you have) and the fix. I don't know if this will work for you so I wouldn't advise trying that solution  unless someone more knowledgeable comes along and says to try it. I'm trying to give you an example of how Linux/Ubuntu does things, quite unlike Windows.

[https://ubuntuforums.org/showthread.php?t=2353325&page=2&highlight=43142](https://ubuntuforums.org/showthread.php?t=2353325&page=2&highlight=43142)

---

### Post by jeremy31 on 2019-06-02
Can you change the wifi encryption on the router so it no longer uses TKIP?

---

### Post by samtoon on 2019-06-03
How can I do that?

---

### Post by kurt18947 on 2019-06-08
> **samtoon said:**
> How can I do that?

It has to be done at the router. If you don't have access to the router you can't change that. Whoever does have access to the router should change it though. TKIP has been insecure for some time.

[https://lifehacker.com/the-difference-between-wi-fi-security-protocols-wpa2-a-1672256222](https://lifehacker.com/the-difference-between-wi-fi-security-protocols-wpa2-a-1672256222)

---

