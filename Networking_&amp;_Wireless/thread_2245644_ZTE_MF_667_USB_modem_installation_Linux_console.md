---
title: "ZTE MF 667 USB modem installation Linux console"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by cosworth2 on 2014-09-25
Hi everyone! 

Given a Hungarian telecommunications company, the "Telenor" received ZTE MF 667 USB modem type. My problem is the following: we want to use this machine without a graphical interface to the modem, but in any event so as to be asked for a PIN. This machine is connected to the modem driver cdc_ether help create an Ethernet interface (eth1 in my case), which bears the IP address 192.168.0.1, and the modem, and that the IP is entered in the browser web interface of the device where you can enter your PIN, then click the "Apply" button clicked to enter virtually the device configuration page, or in a "Connect" button to activate the Internet connection. (Incidentally, no PIN code of the device would work beautifully, but it was specifically requested that the PIN you have to give). That would be the question of the feasibility of this, that the PIN may be administered in some way the console device operation, and if so, how? (Any solution you are interested.)

The device:
Bus 001 Device 009: ID 19d2:1405 ZTE WCDMA Technologies MSM
dmesg:
[http://pastebin.com/aLujzYmZ](http://pastebin.com/aLujzYmZ)
Screenshots of the modem web interface:
[http://kepfeltoltes.hu/140924/01_www.kepfeltoltes.hu_.png](http://kepfeltoltes.hu/140924/01_www.kepfeltoltes.hu_.png)
[http://kepfeltoltes.hu/140924/02_www.kepfeltoltes.hu_.png](http://kepfeltoltes.hu/140924/02_www.kepfeltoltes.hu_.png)

Moreover, while the problem is that the web interface of the modem contains elements that the browser character falls apart, not a bit, and can not be entered in either the PIN...
Lynx:
[http://kepfeltoltes.hu/140925/03_www.kepfeltoltes.hu_.png](http://kepfeltoltes.hu/140925/03_www.kepfeltoltes.hu_.png)
Links/Links2:
[http://kepfeltoltes.hu/140925/04_www.kepfeltoltes.hu_.png](http://kepfeltoltes.hu/140925/04_www.kepfeltoltes.hu_.png)
The program also tried wget, many option (downloads the environmental files etc)., It downloads and views in Firefox I get the following result:
[http://kepfeltoltes.hu/140925/05_www.kepfeltoltes.hu_.png](http://kepfeltoltes.hu/140925/05_www.kepfeltoltes.hu_.png)
Wget command:
wget -H -N -k -p -H -K -p --convert-links -r "http://192.168.0.1/index.html"
Wget output:
[http://pastebin.com/0kqn31iH](http://pastebin.com/0kqn31iH)
Wget command to download files:
[http://data.hu/get/8079861/zte.tar.gz](http://data.hu/get/8079861/zte.tar.gz)
If Firefox option "ctrl + s" I went down the page, you will get the following files:
[http://data.hu/get/8079868/firefox.tar.gz](http://data.hu/get/8079868/firefox.tar.gz)





   The idea is possibly someone that could carry out the thing? It would also be good if it actually recognizes it as a modem for a computer modem, not the ethernet interface, and then you can write your PIN ... 

PS: Sorry for the correctness of language, but I used a translator because my English is little ...

---

### Post by cosworth2 on 2014-09-26
Nobody can help? Actually, if we could somehow be made &#8203;&#8203;to / dev / * ttyUSB interfaces, that would be good (if you can do that ...)

---

