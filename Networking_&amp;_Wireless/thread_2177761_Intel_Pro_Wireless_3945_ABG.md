---
title: "Intel Pro Wireless 3945 ABG"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by joyce-nord on 2013-09-30
Intel Pro Wireless 3945 abg no gateway address after update.

Running Ubuntu 12.10 and an update ran last Wednesday which stopped my network card from working properly.  I could see my network card connect wirelessly with no problems.  It showed connected, but when I attempted to access the internet or ping anything it wouldn't resolve.  I ran an ifconfig to verify the card was assigned an IP from my local network 192.168.2.x, and it was.  I ran route -n only to find that although the wireless card had an IP address, for some reason the gateway was not set properly. 

I plugged in via ethernet cable and tried to report the bug yesterday several times but each time it locked up on me, so I decided to just delete the partition and reload with 12.04 LTS.  Of course now I have to go about installing samba, my printers, etc once again.

Is there a problem with updates? I am hesitant to download any updates now for fear of losing wireless.  A laptop without wireless is kind of useless as a laptop.

---

### Post by SeijiSensei on 2013-09-30
There was a kernel update along the way in the 12.04 series that [broke]("http://ubuntuforums.org/showthread.php?t=2143218") my Intel wireless as well.  I reverted back to the previous kernel to solve the problem.  The next kernel update fixed the problem entirely.

I don't see much value in upgrading from 12.04 to 12.10.  I've been running 13.04 after I bought an Android device since that is the first release with solid support for the MTP protocol that Android now uses to handle file transfers via USB.  If I were going to upgrade from 12.04, I'd go to 13.04 or wait a couple of months and move to 13.10 after it has been released for a while.  I expect to move to 14.04 next spring as it will be the next LTS release.

(BTW, the "fragility" I mentioned about 13.04 in the linked post has largely gone away.  The one persistent problem I have with audio is a KDE issue.)

---

