---
title: "Actiontec 56k v92 external EX560LKA serial modem disconnecting"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by don_m on 2006-07-25
I have a 56k v92 external EX560LKA serial modem. This modem has worked with Knoppix, Damn Small Linux, and Fedora Core 4 without too much hassle.

I was able to get it working one evening with Ubuntu 6.06 after entering the DNS host numbers from my internet provider. The modem is detected and such through the Networking setup, even though I notice that eth0 is the only option for a default connection.

I have not been able to get to the internet again with Ubuntu 6.06  even though the DNS numbers were saved. It dials up and connects, but then the Ping tool and web browsers can't find any web address. I did a scan with the networking tools and come up with some network addresses while Networking indicates that the modem is activated.

I used wvdial while in Terminal and found that the modem is detected and I am able to dial with wvdial, but then receive a code 16 after less than minute, which means that the link is terminated by the modem hanging up. It then goes into a redial and disconnecting.

I did not have to do the DNS bit with the internal modem on my IBM T23 laptop.

I have read the modem setup wiki for clues and followed a couple of procedures like the wvdial, but can not come to any conclusion why this is happening.

---

### Post by don_m on 2006-07-29
I went ahead and reinstalled Ubuntu 6.06 since I could no longer even get to the Networking setup. I would select it, watch the dial move for a few seconds and then nothing.

Anyway, I determine that the modem worked with the installation CD. I reinstalled and turned of the etho0 card and setup the modem.

I went to properties, and was able to detect the modem. Under options, I made sure to make it the default way to the internet and use the internet provider's nameservers. Don't forget to "enable" connection under the General tab.

I rebooted a couple of times and it seems I am able to log on to the internet with dial-up with this modem.

---

