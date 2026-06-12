---
title: "Can't get (broadcom) WiFi working, don't have ethernet connection"
date: 2015-11-15
forum: Networking &amp; Wireless
---

### Post by praz_nin on 2015-11-15
I'm using Ubuntu 14.04 and I followed several guides, but nothing seems to have worked.

lspci -nn -d 14e4:


gave me:


Broadcom Corporation BCM43142 802.11bgn Wireless Network Adapter [14e4:4365] (rev 01)

I have tried putting the drivers on a usb stick, transfering them to the other laptop and copying them to /lib/firmware/b43, but there no matter what I do, nothing works. 

Can someone please help, in a step by step fashion? I know this would have been easier if I had an ethernet connection (I did it 3 years ago somehow), but as a noob I'm having trouble with this. 

Thanks

---

### Post by carl4926 on 2015-11-15
Your device requires the 'wl' driver
'b43' is not supported

'wl' is the proprietary driver from broadcom

So you are saying you have no active wired connection? And can't even tether a mobile device to provide such?

---

### Post by Hadaka on 2015-11-15
Hi, carl4926 is corret, your device requires the 'wl' broadcom-kenel-source driver not
the b43. Please do these commands prior to loading the broadcom-kernel-source driver.
The b43 probably didnt load but just incase please do..
```
sudo apt-get remove --purge firmware-b43-installer
```
then some clean up.
```
sudo apt-get autoremove && sudo apt-get autoclean
```
*next follow chilli555's directions on how to load the 'WL' driver offline no internet.
[http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)
when that is loaded and you have a working internet connetion dont forget to bring your os up to date
```
sudo apt-get update
```

---

### Post by praz_nin on 2015-11-15
Thank you so much Hadaka, wireless seems to be working now. ^_^

---

### Post by Hadaka on 2015-11-15
GREAT ! glad that worked for you, I'll pass along  your thanks to
the good doctor chilli555 as well. Please take the time to sign back in
your thread,click thread tools and mark this as SOLVED
thank you.

---

