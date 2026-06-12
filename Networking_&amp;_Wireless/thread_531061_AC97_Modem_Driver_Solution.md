---
title: "AC97 Modem Driver Solution"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by gcsrochester on 2007-08-21
Great news for all of us who have struggled to get the AC97 / Intel 82801 modem working in Ubuntu/Kubuntu - there is a solution! I won't bore you with the details but after 3 days of digging I deduced that the Smartlink Driver will never work for this modem. You must use a Conexant HSF driver and Dell has provided a driver specifically for Ubuntu/Kubuntu Feisty. Here's what you do:

1. Using Adept, uninstall both the Smartlink Daemon and the source code.
2. Download the Conexant HSF driver from: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)
3. Install the .deb package
4. At the end of the installation, it will say the device can be found at /dev/ttySHSF0. In my case it was not. It was /dev/modem.
5. In your wvdial / kppp / Knet configuration you must set the modem to run unlocked.
6. Enter your account info and you're on your way!

Many thanks to Dell!

---

