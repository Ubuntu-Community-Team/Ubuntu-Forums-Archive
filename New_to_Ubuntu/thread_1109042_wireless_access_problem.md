---
title: "wireless access problem"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by KenCranford on 2009-03-28
I recently installed Ubuntu 8.10 on my Dell Inspiron E1505 laptop, but cannot access my (or any other) wireless network. System > Administration lists "Network Tools", but not "Network". Per ~$ sudo lshw -C network, the adapter is Broadcom BCM4328 but network is DISABLED. Per "Hardware Drivers",  wl is actived and is in use. My network is DLink using WTA2 encryption. I've spent hours searching Ubuntu documentation without success. Please help! Thanks.:confused:

---

### Post by acimmarusti on 2009-03-28
Unfortunately you broadcom 4328 is not supported by native linux drivers nor by extra firmware as can be evidenced here: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

However you can probably make it work using ndiswrapper (a tool that uses the windows drivers). I've never used ndiswrapper myself, but there is a walkthrough here: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Hope this works for ya

---

### Post by KenCranford on 2009-03-28
Thanks for your response, but I'm still confused. Per Ubuntu Documentation > Community Documentation > WifiDocsWirelessCardsSupported, my BCM4328 adapter is supported by driver wl, and wl is included with Ubunto 8.10. I prefer to avoid using the ndis wrapper approach because it entails using the overhead of MS Windows. Any other suggestions?

---

### Post by lkraemer on 2009-03-29
One solution is to use a USB Wifi device, and Amazon has a good price.
[http://www.amazon.com/Hawking-HWUG1-Wireless-Network-External/dp/B000HCMTJG/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1238383834&sr=8-1](http://www.amazon.com/Hawking-HWUG1-Wireless-Network-External/dp/B000HCMTJG/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1238383834&sr=8-1)

lkraemer

---

### Post by KenCranford on 2009-03-31
Thanks - I ordered the Amazon USB adapter per your suggestion. Also, I did use an ethernet connection to install "linux-backports-modules-intrepid" per a TIP in Kier Thomas' superb manual "Ubuntu Pocket Guide and Reference" - but my wireless connection still doesn't work.

---

### Post by KenCranford on 2009-04-02
Problem solved - before the USB adapter arrived. I first followed the instructions in jwernecke's "Using a Broadcom 4318 wireless card" post to see if it fixed my Broadcom 4328 problem - without success. Howeve, when I clicked System > Administration > Hardware Drivers I noticed that I had two Broadcom wireless drivers listed - a non-proprietary "B43" that was enabled and a "STA" that was not enabled. I then Googled "Broadcom STA adapter" and found a link to "Technix Update" - which instructed me to enable the STA driver, and steps to follow to access my WPA2 home network. It worked!):P

---

